---
title: "New, need help"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by JesseDL on 2008-01-30
Hi i'm new :d 

I have a vista laptop, I don't like it at all, so I downloaded Wubi and installed Kubuntu 7.04. Its my first linux ever XD so i was wondering if you guys could help me on the many problems i'm bound to encounter.

Here goes the first one:

I was logged in once, I installed my wireless back then and apt-get Firefox. Then I shut it down. 
Now I tried to log in again, the visual login accepts my password, BUT he just keeps loading the login screen :lolflag: so my password gets accepted, but i can't login. If i press alt+ctrl+ F1-F6 and login there is no problem, but i can't work with text-based stuff. so someone help me run KDE or Gnome or w/e i need a graphical environement

Thank You in advance

---

### Post by jan quark on 2008-01-30
not every hardware is supported by wubi
I would just download the gutsy liveCD and install ubuntu on a second partition
if you need help with repartitioning in vista just ask

---

### Post by JesseDL on 2008-01-30
Well the thing is, i was already logged in. So i'm pretty sure its supported

---

### Post by seventhc on 2008-01-30
I don't know about the wubi cd..never used it but if you do as posted above you can use it before installing it and if it works there, it will work after it's installed. :)

---

### Post by seventhc on 2008-01-30
[quote="JessDL"]
[quote="JesseDL"]
so my password gets accepted, but i can't login
[/quote]
Well the thing is, i was already logged in. So i'm pretty sure its supported
[/quote] 
Which is it???

---

### Post by JesseDL on 2008-01-30
both really.
Wubi is an application form of linux, so you install it like an application in windows :p
I installed Wubi, i logged in, played around a little, shut down, then today i tried again, but couldn't log in anymore, because i was alwyas getting returned to the login screen. 
Thanks for showing interest so far :p

---

### Post by jan quark on 2008-01-30
as I said if you are really interested in switching to linux ubuntu wubi is a nice starting point
but not the end

the full potential and stability of linux can be experienced only by a fresh install
using the live or the alternate CD

---

### Post by seventhc on 2008-01-30
Yeah, dl the live cd, you'll be able to use it without installing it, so you can test it out and see how you like it. If you do like it, then you can install it from the same cd. :)
Sorry I can't help with wubi :(

---

### Post by JesseDL on 2008-01-30
as i said wubi is just the installer, its kubuntu 7.04. so in fact its a clean install

---

### Post by seventhc on 2008-01-30
One note, if you try the live cd, it will be slower b/c it has to read from the cd, after the install it will run much faster. :)
Just thought I'd let you know.

---

### Post by JesseDL on 2008-01-31
not trying the live cd, kinda useless imo since i have kubuntu already but yeah ... so no one can tell me how to run KDE or Gnome ( think i have to install though) from prompt?

---

### Post by seventhc on 2008-01-31
> **JesseDL said:**
> not trying the live cd, kinda useless imo since i have kubuntu already but yeah ... so no one can tell me how to run KDE or Gnome ( think i have to install though) from prompt?

The live cd is also the install cd, and it's a good way to see what hardware issues you might have, or show that everything works without issues. either way, it is still the cd you use to install ubuntu unless you use the alternate cd. But IMO the live cd is the easiest way to install ubuntu....
kubuntu has the live cd too.
Sorry I can't help on anything about wubi. :(

---

### Post by motion parallax on 2008-01-31
I used the alternate cd, and it worked as a live cd.  Let me test everything, then installed Ubuntu on a second partition dual boot with vista on my laptop.  

Could you try downloading the ubuntu cd, then install the KDE packages after it's working?

---

### Post by seventhc on 2008-01-31
Yes, you can install the kde desktop and many others. When you get to the login screen you choose 'sessions' then select either gnome or kde ( or whatever others you have installed.
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```
heres a link [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by rubbsdecvik on 2008-01-31
Here is the deal with WUBI.  It only installs a Virtual disk on your Vista drive and allows the computer to boot from it.  So in a sense you are only "half" installed.

The reason people say to try the LiveCD is because it will actually run as it would if it were "truly" installed.  

I've used Wubi before, and I thought it was grand, but it lacked many things that a true install can give you.  

I'm not telling you what to choose (I have a wubi install on one computer and a "real" install on another and love them both), but if you are having issues with Wubi, I would strongly recommend using the LiveCD over Wubi.  

I understand that the nature of this problem has little to do with Wubi and it's methods, but because wubi uses virtual installs, it tends to run into some strange issues.

I hope some of the info I gave is helpful.

---

### Post by JesseDL on 2008-01-31
will try this later, when i can setup my laptop next to my desktop, and follow instructions , because i'm really bad at this stuff. I just remembered, could 'sudo apt-get firefox' possibly have corrupted my install, NOTE firefox did not launch after install

---

### Post by rubbsdecvik on 2008-01-31
I doubt the install of firefox did that, but I suppose it is possible.

If you want to double check though there is something you can do!

When grub loads choose the recovery mode and when you are in there type

```
apt-get remove firefox
```

that will get rid of firefox and we can see if that fixes the problem.

Might save us some steps.

---

