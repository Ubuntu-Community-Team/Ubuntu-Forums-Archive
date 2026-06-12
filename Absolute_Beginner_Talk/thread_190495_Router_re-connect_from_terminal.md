---
title: "Router re-connect from terminal?"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by J-Gaming on 2006-06-06
Hi! is it possible to make router re-connect from terminal?

Router: D-Link DI-604

To (dis)connect router I simply must go to a web address..
Disconnect: [http://192.168.0.1/cgi-bin/dial?rc=@&A=H0&rd=status](http://192.168.0.1/cgi-bin/dial?rc=@&A=H0&rd=status)
Connect: [http://192.168.0.1/status.htm?RC=@](http://192.168.0.1/status.htm?RC=@)

also, to access this page, I need to enter user and password - put that I think can be fixed by changing address to [http://user:apass@192.168.0.1/](http://user:apass@192.168.0.1/)

And heres what I need:

How to make router reconnect from terminal, so that router page doesnt even open?

---

### Post by mlind on 2006-06-06
you could send HTTP request using telnet
or use terminal based browser like lynx.

---

### Post by J-Gaming on 2006-06-06
How to use telnet option?

---

