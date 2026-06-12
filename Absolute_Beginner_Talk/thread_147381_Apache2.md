---
title: "Apache2"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-03-20
Hello,

I've installed Apache2 but when I want to go to localhost```
http://localhost
```
I get this massage:```
The connection was refused when attempting to contact localhost. 
```
Could you guide me please?!

Thanks,

---

### Post by timas on 2006-03-20
If the installation went as it should, I would check to see and make sure that Apache is running like it should..

Open a console and type this: 'telnet localhost 80', if Apache is running you will end up with a blank screen ( CTR+] ) to get out of it. If apache isn't running, you'll get an error.

Another posibility is that you don't have telnet, typing 'ps xu' should give you a list of running programs, one of which should be 'apache'.. If not, try typing 'apachectl start'  to start it..

---

### Post by linux-beginner on 2006-03-20
You are right. My apache is not runnig. I get this massage:
```
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```
Could you tell me how I can start the apache, pleas?

---

### Post by timas on 2006-03-20
[QUOTE=timas]If not, try typing 'apachectl start'  to start it..[/QUOTE]

I already had ;)  Typing "**apachectl start**" should work methinks

---

### Post by mlind on 2006-03-20
to start apache httpd server use *sudo /etc/init.d/apache2 start*

---

