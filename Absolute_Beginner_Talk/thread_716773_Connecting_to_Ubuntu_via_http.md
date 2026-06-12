---
title: "Connecting to Ubuntu via http"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Frank_F on 2008-03-06
Hello

I am currently at work and able to connect to my Ubuntu server via PUTTY using the address frank@ipaddress, however when I try in Internet explorer (IE) with the same address [http://frank@ipaddress](http://frank@ipaddress) I get an error "Page cannot be diplayed". 

When I was @ home yesterday on a Windows box using IE wirless I was able to connect


Thanks
Frank

---

### Post by neurostu on 2008-03-06
To connect to a computer over http:// I don't think you need to specify a username. 

Webservers are run by users but they monitor traffic coming on on a certain port, then they serve pages bases upon a directory that is preassigned (usually /var/www)

so you should really only have to connect to [http://ipaddress](http://ipaddress) not [http://user@ipaddress](http://user@ipaddress)

try that....

---

### Post by Frank_F on 2008-03-06
thanks you are correct and it worked

---

