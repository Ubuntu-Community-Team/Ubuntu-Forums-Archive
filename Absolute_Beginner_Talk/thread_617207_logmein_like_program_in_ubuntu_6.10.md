---
title: "logmein like program in ubuntu 6.10"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by redon12 on 2007-11-19
I liked using logmein in windows
is there a program like that I heard about VNC but don't know how to install it
I also would like to know how to use logmein in ubuntu firefox 'cause I need some java driver to use it
thanks

---

### Post by rdd on 2007-11-19
VNC is a protocol that allows you to use your computers desktop across a network. It is already installed by default on Ubuntu. To enable it, go to System -> Preferences  -> Remote Desktop. 

You can then go to another computer and start the VNC viewer.

```
vncviewer <IPadress>
```
regards

rdd

---

### Post by redon12 on 2007-11-19
is there any way I can control ubuntu computer over the internet using windows xp system?
thank you

---

### Post by rdd on 2007-11-19
Havent used Windows in a while but there seems to be a client for it too. 

[http://www.realvnc.com/products/free/4.1/winvncviewer.html](http://www.realvnc.com/products/free/4.1/winvncviewer.html)

You will however have to open a port on your firewall that protects the ubuntu machine. VNC listens on 5900.


regards

tom

---

### Post by redon12 on 2007-11-19
isn't there any program I could use just like logmein (I mean like without installing any programs just go straight to the Internet and control my computer?

---

### Post by rdd on 2007-11-20
You will have to explain a little more. I am not sure what LogMeIn is like and since it's for windows I can't really try it. Does the client work in a browser?

There's vnc-java which serves a java client that works in a browser.

check out this Howto

[http://ubuntu-unleashed.blogspot.com/2007/10/setup-vnc-server-for-ubuntu-gutsy.html](http://ubuntu-unleashed.blogspot.com/2007/10/setup-vnc-server-for-ubuntu-gutsy.html)

---

### Post by redon12 on 2007-11-20
to control computer using logmein you need to install (free or you can buy other) logmein program on windows computer, then go to logmein.com from any computer log in to your account, select computer you want to control, and control it in the web browser
that is actually what i like about logmein you don't need to install things on computer you are controling from
please help me control my computer
thank you

---

### Post by redon12 on 2007-11-20
how do I control my ubuntu computer with windows xp pc because when I type in "(my name)-desktop:5800" it doesn't work
thank you

---

### Post by rdd on 2007-11-21
> **redon12 said:**
> how do I control my ubuntu computer with windows xp pc because when I type in "(my name)-desktop:5800" it doesn't work
thank you

Maybe the dns-resolution doesn't work. Trx using the ip-address directly.

---

### Post by AlanRogers on 2007-11-21
> **redon12 said:**
> to control computer using logmein you need to install (free or you can buy other) logmein program on windows computer, then go to logmein.com from any computer log in to your account, select computer you want to control, and control it in the web browser
that is actually what i like about logmein you don't need to install things on computer you are controling from
please help me control my computer
thank youNot entirely true; you have to have either Java or the LogMeIn ActiveX installed before it'll work. I agree that it's a very useful application but you should really be directing your question to [LogMeIn]("https://secure.logmein.com/go.asp?page=contact"), as it's them (not Ubuntu) who haven't yet released a version for controlling Linux computers. The LogMeIn forum has otherwise happy users howling for a Linux client, (K/X)Ubuntu being a regular request. Ubuntu developers can't easily deliver what doesn't yet exist.

---

