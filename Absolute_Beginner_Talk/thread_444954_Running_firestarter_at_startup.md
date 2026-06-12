---
title: "Running firestarter at startup"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-15
Could someone tell me how to run firestarter at startup?  I tried putting it in the startup programs list but because it requires root permission to run that didn't work.  Then I tried adding 'gksudo' before to the command, but when I started Ubuntu it popped up with a request for password before the desktop had even been loaded and seemed to freeze up the screen, plus I'd rather not have to enter in the password everytime I start up my computer.

Any ideas?

Thanks

---

### Post by heimo on 2007-05-15
See this thread:
[http://ubuntuforums.org/showthread.php?t=409375](http://ubuntuforums.org/showthread.php?t=409375)

---

### Post by zhinker on 2007-05-15
Thanks man.  Just to make sure I understood the information in that thread properly, Ubuntu always has a firewall running even if you don't see it?  And firestarter is just a graphical interface to that firewall?

---

### Post by oilchangeguy on 2007-05-15
> **zhinker said:**
> Thanks man.  Just to make sure I understood the information in that thread properly, Ubuntu always has a firewall running even if you don't see it?  And firestarter is just a graphical interface to that firewall?

that's correct.

---

### Post by zhinker on 2007-05-15
Sweet, thanks dude

---

### Post by heimo on 2007-05-15
> **zhinker said:**
> Thanks man.  Just to make sure I understood the information in that thread properly, Ubuntu always has a firewall running even if you don't see it?  And firestarter is just a graphical interface to that firewall?

Yeah, the firewall part is in the kernel and it's called net filter. You can use several tools to configure it. Always make sure that it actually is running and properly configured. But the point is: You do not need to have firestarter running to have a firewall up and running.

Personally I use two methods to test my firewall. Mainly I use port scanner called nmap, and then I also use outside services like [http://www.grc.com/default.htm](http://www.grc.com/default.htm) (ShieldsUp) to double check whenever I can't use some other computer to check my firewall "from outside".

---

### Post by umarvlie on 2007-05-15
> **oilchangeguy said:**
> that's correct.

True, iptables is active, but there are no rules in it untill i start firestarter i noticed... 
> 
me@me-main:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
me@me-main:~$ 



so everything is wideopen in the beginning. How can i ensure that teh rules/settings i create in firestarter are loaded on startup?

---

### Post by heimo on 2007-05-15
> **umarvlie said:**
> so everything is wideopen in the beginning. How can i ensure that teh rules/settings i create in firestarter are loaded on startup?

During boot, do you get (if you watch boot messages):
```
* Starting the Firestarter firewall...                                  [ OK ] 
```Firestarters init-script (script that gets executed during boot) should configure net filter using iptables (which is another tool for configuring net filter rules).

About the "wide open" part: By default there are no listening services in Ubuntu (at least in desktop version). So if you make a default install, do not install or configure firewall and scan your system from outside, you will see zero ports open.

---

