---
title: "geforce2 installation"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by strahil on 2005-09-27
I want to install my nvidia geforce2 mx 400 on ubuntu(I'm a total newb).
It does this x error thing(blue screen).
I read all the instructions on the site but I cant use 'apt' because I am behind a proxy server!
I am currently using an old voodoo 3.
How do I get ubuntu to even start up with my geforce2?
:confused:

---

### Post by xmastree on 2005-09-27
[QUOTE=strahil]I am currently using an old voodoo 3.
How do I get ubuntu to even start up with my geforce2?[/QUOTE]Use Ctrl-Alt-F2 to switch to a different console, then run:```
sudo dpkg-reconfigure xserver-xorg
```This will reconfigure your x server configuration file to remove the voodoo and install the basic nvidia driver. That will get you up and running, but you really need to download the proper nvidia driver if you can.
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by strahil on 2005-09-27
so after I do this code I restart my pc and insert the nvidia card?

---

### Post by xmastree on 2005-09-27
[QUOTE=strahil]so after I do this code I restart my pc and insert the nvidia card?[/QUOTE]You should install the nvidia card first, so that the reconfigure can detect it.

---

### Post by strahil on 2005-09-27
ok I did xconfig recognized it but now whenever I restart it goes to the command prompt thingy(not sure of the name in ubuntu language).
it like ask me username and pass but in a command prompt(terminal).
could the card be causing this

---

### Post by xmastree on 2005-09-27
Log in and type ```
startx
```

---

### Post by SilentCacophony on 2005-09-27
The card likely would not cause that. Did you see any error messages? 

Anyway, if you enter:

*startx*

after you log into the console. It should boot up X. If not, post the errors.

This is something that I'm curious about, myself. Does anyone know if a s*udo dpkg-reconfigure gdm* might be worth a try in this case? I'm not sure if it does anything with typical packages...

---

