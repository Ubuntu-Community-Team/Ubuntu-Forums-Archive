---
title: "rdesktop to connect windows system"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-12-27
hi
i want to connect windows system with GUI utilities like( ssh -X ,xdmcp)

how to connect windows-2000 and windows-xp from ubuntu by using rdesktop or some other tools ?

any one give me a sample ?

thank you

---

### Post by bodhi.zazen on 2007-12-27
Yes, it is quite easy.

[http://www.propeller.com/viewstory/2007/04/19/how-to-connect-to-a-windows-terminal-server-from-ubuntu/?url=http%3A%2F%2Fwww.watchingthenet.com%2Fhow-to-connect-to-a-windows-terminal-server-from-ubuntu.html&frame=true](http://www.propeller.com/viewstory/2007/04/19/how-to-connect-to-a-windows-terminal-server-from-ubuntu/?url=http%3A%2F%2Fwww.watchingthenet.com%2Fhow-to-connect-to-a-windows-terminal-server-from-ubuntu.html&frame=true)

tsclient is installed by default :

Applications -> Internet -> Terminal Server Client

You need to configure windows to allow connections.

[http://www.windowsnetworking.com/articles_tutorials/Using-Remote-Desktop-Windows-XP-Pro.html](http://www.windowsnetworking.com/articles_tutorials/Using-Remote-Desktop-Windows-XP-Pro.html)

---

### Post by mokkai on 2007-12-27
thank you for reply 
Applications -> Internet -> Terminal Server Client
is ok for connecting windows 2003 

it is not connect with windows-2000
it say the error 
p@ubuntu7.04:~$rdesktop 192.168.1.178 
ERROR: recv: Connection reset by peer
p@ubuntu7.04:~$ 

or ,should i install anything in windows-2000?

thank you ...

---

### Post by bodhi.zazen on 2007-12-27
I am not sure if you can connect to windows 2000 with this protocol.

If not you may want to look at VNC, try tight VNC

---

