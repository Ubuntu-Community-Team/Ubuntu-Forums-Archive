---
title: "shh via http proxy"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by sanitus on 2007-02-28
hi, everyone!
So heres my problem: i need to connect to ssh server using htpp proxy
What was i trying to do: i have downloaded connect scritp ([http://zippo.taiyo.co.jp/~gotoh/ssh/connect.html](http://zippo.taiyo.co.jp/~gotoh/ssh/connect.html)) compilled and installed it

but somehow i get this when trying to connect whit debug option 

connect -d -H 192.168.21.9:3128 84.240.51.82 8080

> 
DEBUG: No direct address are specified.
DEBUG: relay_method = HTTP (3)
DEBUG: relay_host=192.168.21.9
DEBUG: relay_port=3128
DEBUG: relay_user=sani
DEBUG: local_type=stdio
DEBUG: dest_host=84.240.51.82
DEBUG: dest_port=8080
DEBUG: Program is $Revision: 1.96 $
DEBUG: not matched, addr to be SOCKSified: 84.240.51.82
DEBUG: connecting to 192.168.21.9:3128
DEBUG: begin_http_relay()
DEBUG: >>> "CONNECT 84.240.51.82:8080 HTTP/1.0\r\n"
DEBUG: >>> "\r\n"
DEBUG: <<< "HTTP/1.0 403 Forbidden\r\n"
DEBUG: http proxy is not allowed.
FATAL: failed to begin relaying via HTTP.


Then to be shure that proxy connects to this ip i tryed it in firefox and it perfectly connected me to my ssh server.

can anyone help?
--sorry if this question is very noobish i am new to linux 
--sorry for my bad english :)

---

