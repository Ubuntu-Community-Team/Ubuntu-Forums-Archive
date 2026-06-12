---
title: "Boot up problem"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Rewstama on 2007-03-27
I bet that's a post title you never see here, eh ?

Ok, here's my first post and question to this board.. hope y'all can help.

I just installed 6.10 on my wife's IBM T22 laptop last night.
She got tired of waiting what seemed forever for WXP to load just to check something on the web.

Everything went just dandy with only a couple of minor snags on the screen resolution and the Aironet wireless.  Both work fine now though.  (thank god I use WEP)

I then rebooted the laptop at least a half-dozen times to make sure everything worked as it should; and it did.

This morning, as my wife boots up the laptop, she gets the UBUNTU splash, then it just hangs.  Blank screen.
I tried it three times myself and then figured out that I can boot to an older Kernel by pressing Esc.

So.. my Question
Can I edit something to make the older Kernel the default on startup ?

BTW, boot time is now down to 1 minute.

---

### Post by dstew on 2007-03-27
At the grub menu listing, press 'E' and you can edit the list.

---

### Post by seshomaru samma on 2007-03-27
```
sudo gedit /boot/grub/menu.list
```
this command will give the GRUB menu you accessed by pressing esc
comment out the new kernels by putting a # before the line
just to be on the safe side - maybe you should post it here first 
if you mess up the boot menu you may have problems booting up


(for more boot-up speed ,download BUM
```
sudo aptitude install bum
```
this application allows you to chose some of the processes that start on boot , you probably dont need some of them so you can shorten the boot time, in case of doubt -post here)

btw - you should **dstew'**s method first - it sounds easier , i never tried it myself

---

### Post by Rewstama on 2007-03-27
Wow, that was an easy fix.  Thanks.

Should I be looking at what causes the newer Kernel from loading?
Can I trace through the boot sequence?

---

### Post by zvacet on 2007-03-27
Maybe you just need video card tweak.But your newer kernel must be runinig.If you don´t know wich card you have find it in** etc/X11/xorg.conf** You don´t have to edit it just open with text editor.After that **ctrl+alt+F1** to go to terminal.
```
sudo dpkg-reconfigure xserver-xorg
```

---

