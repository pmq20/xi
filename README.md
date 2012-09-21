洗洗更健康
==

可是你们写来写去的这些程序啊，都Too Simple，啊？Sometimes Naive！懂了没有？

```
[23] pry(#<AccountController>)> ret
=> "73"
[24] pry(#<AccountController>)> ret.to_i
=> 200
[25] pry(#<AccountController>)> "73".to_i
=> 73
[26] pry(#<AccountController>)> puts ret
73
=> nil
[27] pry(#<AccountController>)> ret.strip
=> "73"
[28] pry(#<AccountController>)> ret.strip.to_i
=> 73
[29] pry(#<AccountController>)> ret.strip
=> "73"
[30] pry(#<AccountController>)> ret
=> "73"
[31] pry(#<AccountController>)> ret.length
=> 2
[32] pry(#<AccountController>)> ret.length
=> 2
[33] pry(#<AccountController>)> ret.to_i
=> 200
[34] pry(#<AccountController>)> ret
=> "73"
[35] pry(#<AccountController>)> ret
=> "73"
[36] pry(#<AccountController>)> ret.to_i
=> 200
[37] pry(#<AccountController>)> ret.strip.to_i
=> 73
[38] pry(#<AccountController>)> ret.length
=> 2
[39] pry(#<AccountController>)> ret.strip.length
=> 2
[40] pry(#<AccountController>)> ret.size
=> 2
[41] pry(#<AccountController>)> ret.encoding
=> #<Encoding:US-ASCII>
[42] pry(#<AccountController>)> ret.strip.encoding
=> #<Encoding:US-ASCII>
[43] pry(#<AccountController>)> ret.strip.to_i
=> 73
[44] pry(#<AccountController>)> ret.to_i
=> 200
[45] pry(#<AccountController>)> ret
=> "73"
[46] pry(#<AccountController>)> ret = '23'
=> "23"
[47] pry(#<AccountController>)> ret.to_i
=> 23
[48] pry(#<AccountController>)> ret = "23"
=> "23"
[49] pry(#<AccountController>)> ret.to_i
=> 23
[50] pry(#<AccountController>)> ret = "73"
=> "73"
[51] pry(#<AccountController>)> ret.to_i
=> 73
```

```
[9] pry(#<AccountController>)> ret.each_byte{|x| puts x}
55
53
=> "75"
[10] pry(#<AccountController>)> ret.strip.each_byte{|x| puts x}
55
53
=> "75"
[11] pry(#<AccountController>)> ret.strip.to_i
=> 75
[12] pry(#<AccountController>)> ret.to_i
=> 200
[13] pry(#<AccountController>)> ret === ret.strip
=> true
[14] pry(#<AccountController>)> ret.to_i === ret.strip.to_i
=> false
```

究竟是怎么回事？
===

原来是rest-client的这个文件里定义的`AbstractResponse`这个module被混合入了String在作怪：

[/usr/local/lib/ruby/gems/1.9.1/gems/rest-client-1.6.7/lib/restclient/abstract_response.rb](https://github.com/archiloque/rest-client/blob/master/lib/restclient/abstract_response.rb)

所以要多洗洗字符串！洗洗更健康：）

本Gem纯属娱乐！！！
====

