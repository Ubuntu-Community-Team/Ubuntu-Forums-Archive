---
title: "X Server unable to start"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by AirRaven on 2006-04-03
I'm a complete newbie to Linux, so this can probably be solved instantly by anyone with the simplest knowledge of how this works. But I saw that the LiveCD managed to start up and run flawlessly on my system, so I figured it should work fine.

What happens is basically this- I've installed and dualbooted Ubuntu with Windows XP, and, barring a slight hitch in the networking setup, everything went smoothly. The trouble starts when I start the OS itself- it boots up fine, but when it starts loading the X Window system, I get an error, resulting it being disabled.

The net result is that I'm left with a fully functional Ubuntu, sans anything more graphical than a command line. Not quite what I enjoyed about the LiveCD, which worked fine in Vesa mode.

I'm using the AMD64 version of Ubuntu. The LiveCD was the i386 version, which works perfectly. It's Breezy Badger, of course. I'm holding back from the obvious step of downloading the i386 CD image of the Install disc because I'd rather not spend another day on downloads unless there's no other real viable option.

Any suggestions? I apologise for the lack of any error messages in particular. I'll try and get some images and edit in a few minutes. The error logs are too long to paste here.

---

### Post by Qrk on 2006-04-03
Try this

```
sudo dpkg-reconfigure xserver-xorg
```

On the second screen, select "Vesa" from the list of available drivers. Go through the rest of the configuration to your liking.

Then type:

```
startx
```

after you are done. This should start you up with Gnome. 

Once you have a GUI, its much easier to find the correct drivers for you graphics card from the internet. ;)

---

### Post by AirRaven on 2006-04-03
[QUOTE=Qrk]Try this

```
sudo dpkg-reconfigure xserver-xorg
```

On the second screen, select "Vesa" from the list of available drivers. Go through the rest of the configuration to your liking.

Then type:

```
startx
```

after you are done. This should start you up with Gnome. 

Once you have a GUI, its much easier to find the correct drivers for you graphics card from the internet. ;)[/QUOTE]
Just gave it a go. No luck, unfortunately.

I get this list of errors:
[[IMG]http://img47.imageshack.us/img47/6812/picture421kb.th.jpg[/IMG]](http://img47.imageshack.us/img47/6812/picture421kb.jpg)
(Sorry for the appaling image quality. It's the best camera I had to hand at the time)

EDIT: Current hardware:
Athlon64 3700+
VIA/S3G UniChrome Pro IGP (Ghastly integrated graphics. 64MB VRAM)
1GB RAM

---

### Post by taurus on 2006-04-03
If LiveCD runs fine on your machine with X, here is what I think you should do.  Boot your machine with the LiveCD.  Then mount your harddrive on say /mnt/ubuntu and copy /etc/X11/xorg.conf (from your LiveCD) to /mnt/ubuntu/etc/X11/xorg.conf (your harddrive).  Shutdown, remove the CD, and reboot.  See if you still have problems with X now...

---

### Post by AirRaven on 2006-04-03
[QUOTE=taurus]If LiveCD runs fine on your machine with X, here is what I think you should do.  Boot your machine with the LiveCD.  Then mount your harddrive on say /mnt/ubuntu and copy /etc/X11/xorg.conf (from your LiveCD) to /mnt/ubuntu/etc/X11/xorg.conf (your harddrive).  Shutdown, remove the CD, and reboot.  See if you still have problems with X now...[/QUOTE]
I'm not quite sure how to give myself root permissions- I need to copy the file across to the X11 folder, but the whole mounted disk requires root access to write to.

How can I set myself to root for this task?

---

### Post by AirRaven on 2006-04-03
I've copied the file across, and I still get the same result when I reboot into Ubuntu proper.

I'll just try the i386 build. There seems to be no reason not to give it a go.

---

### Post by ignorance on 2006-04-03
lol, just had that error just an hour ago. Just install a videocart driver and it should work fine.

---

