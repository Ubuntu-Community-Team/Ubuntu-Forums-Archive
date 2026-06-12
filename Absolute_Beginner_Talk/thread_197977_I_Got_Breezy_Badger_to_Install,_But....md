---
title: "I Got Breezy Badger to Install, But..."
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by cubdukat on 2006-06-16
...I have no display and no idea how to get it working.

I have an NVIDIA GeForce 6600GT AGP card, and when I start up BB, the splash screen is fine, but the login screen is completely distorted. I'm able to log in because I know that it starts up with the username prompt, but after that I can't use it in graphical mode. 

I then go into a shell session and tried to install the NVIDIA driver as per instructions I saw elsewhere on this board, but it tells me that it can't find them. 

Right now what I'm wondering is if there's some way to drop the system back to "default VGA" drivers so that I can at least get a usable display so that I can get the system set up to the point where I can install the NVIDIA drivers from CD. By this I mean, copying the files onto a CD-RW and then into BB so that I have the drivers right there.

All this is being done from a completely virgin install of BB (it gave me very little choice in what it did and didn't install, so I don't even know if I have kernel-source installed; that's why I want to get the GUI working, so that I can install them from there since I don't want to work with the shell too much).

---

### Post by mscman on 2006-06-16
When you're in a shell session, run the command:
```
sudo dpkg-reconfigure xserver-xorg
```
and select either VESA or VGA drivers on the appropriate screen, then reboot (once you've finished pressing 'enter' through the rest of the dialogue...)

That should get you back to generic drivers.

---

### Post by brentoboy on 2006-06-16
In breezy, I had the same issue, and almost exactly the same card.

if you can get dapper, use it, there is no issue to work around.

otherwise,  you could just 
```
 sudo apt-get install nvidia-glx
```

then you can run 
```
 sudo dpkg-reconfigure xserver-xorg 
```

and select nvidia (instead of nv -- the open source driver for nvidia cards)
that will install the official nvidia driver, so it should work next time you start X.

which can be done without rebooting if you want by doing this..
```
 sudo /etc/init.d/gmd restart 
```

---

### Post by cubdukat on 2006-06-16
[QUOTE=brentoboy]In breezy, I had the same issue, and almost exactly the same card.

if you can get dapper, use it, there is no issue to work around.

otherwise,  you could just 
```
 sudo apt-get install nvidia-glx
```

then you can run 
```
 sudo dpkg-reconfigure xserver-xorg 
```

and select nvidia (instead of nv -- the open source driver for nvidia cards)
that will install the official nvidia driver, so it should work next time you start X.

which can be done without rebooting if you want by doing this..
```
 sudo /etc/init.d/gmd restart 
```[/QUOTE]

Thanks for the advice. It worked like a charm. Now if I could figure out how to install the DVD version of Unreal Tournament 2004, I'd be happy.

Now all I have to do is get my modem working, but given my experiences with the past few distros I've been using, I don't have much hope of that. I think it might be something in the 2.6 kernel. I've only been able to get it to work once, and that was in Suse 10.0, and even then it was intermittent. And the most aggravating thing is that it's an older hardware serial modem--something that is allegedly guaranteed to work.

Just think...I'll just end up repeating all of this when I get my Kubuntu CDs in a few weeks.

The things I do just to get away from XP...

---

### Post by adam.tropics on 2006-06-16
> The things I do just to get away from XP...

Hours of fun for the whole family!!

---

