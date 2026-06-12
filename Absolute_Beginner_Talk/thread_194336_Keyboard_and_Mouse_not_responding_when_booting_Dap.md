---
title: "Keyboard and Mouse not responding when booting Dapper Drake Desktop CD"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Foster on 2006-06-11
Hello,

I've used the search engine but didn't find anything about my problem, although some people talked about mouse-freezes and such. 

I'm using an Athlon 64 cpu on an Abit AV8 (VIA K8T800 Pro) mainboard, therefore I downloaded the "64-bit PC (AMD64) desktop CD" from Dapper Drake/6.06. 

I selected "Start/Install Ubuntu" in the CD's menu (when initially booting with the CD) - when the mouse cursor first appears, I can move it without problems, but as soon as the desktop is loaded, the mouse is no longer working. Same goes for the keyboard. All I can still do, is a hardware reset. Safe mode doesn't help either - same problem occurs. 

I thought maybe the 64 bit version is less compatible and I tried the same with the 32 bit Desktop CD x86, but everything was identical, first the mouse works and after the desktop starts/finishes loading nothing is responding anymore. 

My mouse is a Logitech MX 900 and my keyboard is a Logitech UltraX, both are connected to my PC via USB. 

I hope there is a solution for this, I can't believe that I'm already unable to use the LiveCD, let alone install it. 

Thanks for any help,

Foster

---

### Post by christhemonkey on 2006-06-11
How much RAM do you have?

Hate to say it, but did you wait for a while to see if it loaded?

Does it respond to  Ctrl+Alt+F2  ?

Also, if it really doesnt work with your hardware, you could try the alternate text based install CD if your wanting to install.

---

### Post by Foster on 2006-06-11
The PC has 1024 MB RAM. 

I tried it several times with 32 and 64 bit editions, one time I left the room and after ~10 minutes still nothing. 

Yes! Ctrl+Alt+F2 takes me to the console, what do I do now? :oops: And what does it mean? The mouse stops working because...? :confused:

What I'm trying to say: can this be fixed someway? Because I would really like to see the desktop via the LiveCD, before installation to disk.

---

### Post by christhemonkey on 2006-06-11
Ok just checking.

Well, your system hasnt crashed.  Which is reassuring.  Just the GUI.

Not sure what you can do, if it happens recursively.

If you type:
```
sudo killall gdm
startx 
```

And then try again, what happens?

Does pressing Alt+F2 when your sat at the crashed desktop do anything?

---

### Post by Foster on 2006-06-11
I'm such an idiot! _Nothing_ crashed! It was only my mouse, which didn't respond anymore, I used another mouse and then everything went fine. I still don't know why my mouse isn't working with the LiveCD, but it's easy to "fix". 

Thanks!

---

### Post by christhemonkey on 2006-06-12
Good to see you "fixed" your problem!

If you choose to install and *really *want to use that mouse, there is probably a fix for it.

---

### Post by Breezy Badger on 2006-06-27
Ok I now have the same problem

MX900 will not work unless you unplug it and plug it back in.  Dapper does not pick it up on startup.  Breezy was fine, this is really annoying.

Anyone know a solution yet, other mice are fine as Foster already stated, but I want to use my MX 900

---

### Post by Foster on 2006-07-05
Sorry for answering so late - no, unfortunately I found no fix so far I'm still happy that I fixed my Grub problem (Grub didn't find the Ubuntu installation, but it's booting up now as it should =D> ). 

I have some other issues that are more urgent, that's why I haven't looked into the mouse problem. 

When/If I find a solution I will post it here.

---

### Post by Breezy Badger on 2006-07-05
ok thanks man, let me know

---

### Post by CuBone on 2006-07-11
Doesn't mx900 connect wireless through Bluetooth? If so I think I can help. Got my logitech bluetooth mouse working yesterday. (Wohoo, I've been a linux user for a few days and maybe I can help someone else allready!)

---

### Post by Breezy Badger on 2006-07-11
Yeah man exactly, It uses blue tooth.  Any help would be greatly appriciated

---

### Post by wakediktion on 2006-07-24
Yeah I am having the same issue with the Logitech Bluetooth Keyboard and mouse. I have had to plug in other devices in order to get into Ubuntu. I have tried removing the bluez files and still nothing. Any help would be greatly appreciated!

---

