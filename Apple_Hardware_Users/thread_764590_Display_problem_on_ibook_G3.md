---
title: "Display problem on ibook G3"
date: 2008-04-24
forum: Apple Hardware Users
---

### Post by deamon_knight on 2008-04-24
I have an ibook G3 I'm trying to install hardy on, the model is [http://www.everymac.com/systems/apple/ibook/stats/ibook_500.html](http://www.everymac.com/systems/apple/ibook/stats/ibook_500.html)

Using the Alt installer from today, Ubuntu loads but the display resolution is all wrong, i get a white bar near the bottom of the screen, and the display above the whote bar uses about 2/3 of the display area. Finally, below the white bar, the top of the "good" region is mirrored.

In display settings the system only allows 800x600, and says the display is mirrored. Unclicking mirrored makes it worse (mostly white, no desktop).

I tried
sudo dpkg-reconfigure xserver-xorg

and it looked like the PCI address was incorrect. I changed that entry but fouled things up worse.

Any suggestions how I can undo what I did short of a reinstall? And after that, how do I get the correct screen settings?

Thanks

---

### Post by stream303 on 2008-04-24
> **deamon_knight said:**
> I tried
sudo dpkg-reconfigure xserver-xorg

Yikes!  This utility no longer works like it used to.  I hope you have backed up your original xorg.conf.  I would not use this utility until it is confirmed as being compatible with the new xorg 7.3.  I don't believe it is.

If you can get to some sort of desktop gnome terminal, can you try using xrandr to get in the ballpark?

```
xrandr -s 1024x768 -r 60
```

and then following that, you may need to go into the screen manager again - or you can start it manually with

```
gksudo displayconfig-gtk
```

Do you have an old copy of your xorg.conf from previous installations for troubleshooting purposes?

---

### Post by GVCarroll on 2008-04-24
I always used this post [http://ubuntuforums.org/showthread.php?p=3227440#post3227440]("http://ubuntuforums.org/showthread.php?p=3227440#post3227440") to fix that issue.

---

### Post by deamon_knight on 2008-04-24
Thanks guys, I'll try that GVCarroll. However, I can't even get to a prompt right now. I believe that dpkg-reconfigure created a backup of my xorg config. I think I'll have to boot to a live CD an try to edit it that way.

---

### Post by deamon_knight on 2008-04-24
Editing from the live CD got me closer. The Xorg.config you linked to gets a properly sized display resolution. However, I have some graphical errors (the blinking cursor from the startup script is now a black cube in my upper left) and the refresh rate seems wrong, I'm getting some subtle blinking. Also, the splash doesn't work, but I've heard thats fairly common.

Looks like I have to tweak xorg.conf. But If I foul up refresh rates I fear I'll damage the display. Any advice on where to go from here?

---

### Post by deamon_knight on 2008-04-25
And I've created more problems! Well, its a learning experience right? I installed the xubuntu desktop since this is a less powerful system, but while the display is still normal, 1024x786 isn't available in the display setup anymore. Also, I just noticed I don't have sound (I don't think I ever did, even before the xubuntu install)

---

### Post by stream303 on 2008-04-25
> **deamon_knight said:**
> dpkg-reconfigure created a backup of my xorg config.

Be very careful with dpkg-reconfigure xorg-xserver as it will make a new xorg.conf, but the values contained may not be correct as xorg 7.3 is still being worked on, and dpkg may not be quite up to snuff yet.  Just be sure to make a backup of the original xorg.conf before making any additions.

Black screen - no splash.  I encountered this too, and the solution for me was to use the nosplash kernel parameter at the second stage boot: prompt with:  (hit -tab- to pause it so you can type it)

```
Linux nosplash
```

Now I can see the boot messages instead of just having the cursor going into empty space before the gdm login appears. :)

Once that worked, I made it permanent by adding it to my **/etc/yaboot.conf file:**

Actually, you can also see my addition of fb=false, which may not be an improvement on your machine...

-snip-
```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="nosplash fb=false"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="nosplash fb=false"
```
--snip--

Now just make that change known to openfirmware with:
```
sudo ybin -v -C /etc/yaboot.conf
```

Sound - I run alsamixer in a terminal, and make sure that the master volume is UNmuted, and also that the PCM level isn't blasting at 100% in the red, and usually back it down to 75% or so.

Can you run
```
xrandr -s 1024x768 -r 60
```

to see if you can get to a more normal display?

Hopefully there will be something here that might get you over a bump or two...

---

### Post by deamon_knight on 2008-04-28
Well, altering those startup options seems to have helped, but I still don't have sound. When I try to start alsamixer I get:

alsamixer: function snd_ctl_open failed for default: No such file or directory


Not sure where to go from here. I'm also not sure how to go about making sure My system is using the right video driver.

---

### Post by jtappin on 2008-04-28
I've had similar experience checking out the Hardy Desktop live-CD (I want to be reasonably sure I'm not going to have the kind of hassles that went with the Gutsy install and the ide modules).

This does appear to be a long-standing issue with G3 iBooks (at least) that the screen is not correctly returning its capabilities and so X is falling back to a minimal 800x600. By telling the Kubuntu system settings tool that I had a 1024x768 LCD I then restarting X I got a proper resolution.

However the question I have is where does X find the monitor capabilities? And is it possible to get at that information it raw form to see what it is being told, so that that can be passed on to the relevant X-developers for future releases?

---

### Post by jtappin on 2008-04-28
I've had similar experience checking out the Hardy Desktop live-CD (I want to be reasonably sure I'm not going to have the kind of hassles that went with the Gutsy install and the ide modules).

This does appear to be a long-standing issue with G3 iBooks (at least) that the screen is not correctly returning its capabilities and so X is falling back to a minimal 800x600. By telling the Kubuntu system settings tool that I had a 1024x768 LCD then restarting X I got a proper resolution.

However the question I have is where does X find the monitor capabilities? And is it possible to get at that information it raw form to see what it is being told, so that that can be passed on to the relevant X-developers for future releases?

---

### Post by deamon_knight on 2008-04-30
Good Question, thats well beyond my knowledge though.

It does look like editing the x.org config as posted by GVCarroll gets the display working acceptably, it still has no-splash  and I get a weird moire rainbow on shutdown though.

Its a work in progress, I'm still trying to get sound working and partitions automounted!

Also, anyone know why a G3 laptop wouldn't boot to an OEM DVDRW?

Thanks!

---

