---
title: "Compiz+aiglx is very very slow"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Young Breezy on 2006-08-09
Hello everyone, 

Ok so i dont know if what happened here is just that my graphics card and system are not upto par, or that I havent done some necessary adjustments that is causing compiz to be absurdly slow.  I followed the instructions on the compiz+aiglx thread thats posted on Ubuntu Forums and everything seemed to go smoothly.  Except that once compiz starts up, my system goes so slow that I am forced to stop it.  

I am using an IBM T41 1.4Ghz, 512MB RAM, Radeon R250 Lf [FireGL 9000]

Anyway, this isnt a that big of a deal, i just think compiz looks great, but it is far from a necessity.  Any advice or help would be appreciated.

Thanks

---

### Post by linuksamiko on 2006-08-10
I tryed XGL with ubuntu too and it was very slow. It was very faster when I used the Kororaa-LiveCD (maybe you want to chack it out: [http://en.wikipedia.org/wiki/Kororaa](http://en.wikipedia.org/wiki/Kororaa) ) but with ubuntu I had alot of problems with this "wobbly window effect". I have almost the same system like you but xgl should work just fine (as I've seen with Kororaa) but there must be something that you can change to make it work a little better.

---

### Post by aeiah on 2006-08-10
try disabling the plugins one by one and see if you can isolate which of them are causing the slowdown. compiz.net should have workarounds for aiglx slowdown problems, its usually just a matter of unticking a box or two or using an alternative plugin etc.

---

### Post by calvinthomas on 2006-08-10
HAve you got the correct graphics card drivers installed? If you go to a terminal and type fglrxinfo, what do you get?

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

That is the output I get, if you get mesa in the vendor and renderer then your graphics card is not set up properly and will be causing the trouble. It is almost unuseable for me without the correct graphics card.

Calv

---

### Post by Young Breezy on 2006-08-10
> **calvinthomas said:**
> HAve you got the correct graphics card drivers installed? If you go to a terminal and type fglrxinfo, what do you get?

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

That is the output I get, if you get mesa in the vendor and renderer then your graphics card is not set up properly and will be causing the trouble. It is almost unuseable for me without the correct graphics card.

Calv

Thanks for the tip, but unfortuantely when i type in fglrxinfo this is what i get:

root@shyder-laptop:~# fglrxinfo
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0


and by the way, when i dont sign in as root, it just logs me out.

Any ideas?

---

### Post by calvinthomas on 2006-08-10
Err, quite honestly, I have no idea but you shouldn't need to run it as root and it shouldn't give you what it is giving you (or at least I don't think it should, it may be correct for your card but it seems wrong) I would suggest starting a new thread asking if that is correct and someone much more knowledgable should be able to help! Sorry I can't help any more.

Its worth looking at this if you haven't already though:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29)

---

### Post by John.Michael.Kane on 2006-08-10
Young Breezy frist off you need to find out why you have to log in as root, before you go getting all the eyecandy.

---

### Post by Young Breezy on 2006-08-10
Well, i dont need to log into root, I log in as a regular user to get the eye candy, its just that when i type in fglrxinfo into the termial not logged in as root, for some reason i get logged out of gnome.  For me not to get booted when i type in fglrxinfo, i have to log in as root (in termial), and i get the message stated above.  But like I said earlier, I was hoping it was some minor tweaking that would make compiz run smoothly, but apparently, there are larger issues that probably arent worth investing my time right not for some fancy graphics.  

Thanks for the help and advice everyone, i think i will start from scratch and reinstall and modify everything from square one.

---

