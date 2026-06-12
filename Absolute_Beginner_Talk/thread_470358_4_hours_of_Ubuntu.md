---
title: "4 hours of Ubuntu"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Jorakae on 2007-06-10
OK, I am not going to pretend to be a Linux power user or anything like that. I hail from the Windows world and occasionally make an attempt to give Linux a try every now and then to see if its worth my time. I'm really trying to give it a go this time and so far here is what I have installing Ubuntu out of the box.

Wireless will not work. I use 128 bit WEP encryption and I cannot for the life of me get wireless to work. I can connect fine to unsecured networks but not to my own. What the ef do I have to do to make this work. It is really pissing me off. I'm connecting to a Linksys WRV54G. I've tried 128bit hex, ascii, nothing friggin' works. It keeps asking for my WEP key. Meanwhile my Windows laptop is connected to it and running just fine. 

When I plugged in the wired connection, I got nothing It didn't even list the interface when I did an ifconfig. I looked in the device manager and the gigabyte controller was there but still nothing. I had to reboot with the wired connection in and only then did it show up and let me use it. Are you joking me? That is just ridiculous. I think even Windows 95 would see I plugged in a wired connection without rebooting. 

Went to install Opera, my favorite browser, straight to dependency hell. Error: Dependency is not satisfiable: libqt3-mt. Come on!!! As I've said, I'm not a Linux user and these errors are worthless to me. I wouldn't even know what to do with that file if I did find it. 

So I went to getdeb.net to see if I could install anything there (The Ubuntu Software Portal). I wanted to check out a couple games, went to install, again more dependencies. python-pygame. 

I mean really, in 4 hours I've gotten nothing done but get my wired connection to work. This is just absurd. I am really trying here and in most cases I would have just formatted and installed Windows. But I'm actually seeking help so I hope someone can wake me up from this nightmare called Ubuntu and show me the light. 

Lost in frustration...

-Jorakae

---

### Post by lazyart on 2007-06-10
Since you're not a linux user, you should use the easy way to get your software. Get your apps from Synaptic (System->Administration->Synaptic Package Manager) and there are no dependancy issues-- they resolve themselves.  As for connecting by wire, if you don't get an ip, just do

sudo ifdown -a
sudo ifup -a

WEP worked out of the box on my laptop.  Did you try cutting and pasting the WEP key from your router (obviously, while connected by wire).

You'll attract more flies with honey than vinegar.  If you want help, stop hollering about how simple WIndows is (if Linux had the same hardware support from vendors it would be so much easier).

---

