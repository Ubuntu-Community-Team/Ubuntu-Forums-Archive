---
title: "Ubuntu won't start after following a beryl howto"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-12
I forgot what howto is that and had a hard time seeking for it because there are so many threads tagged with beryl. 

The howto was all about running beryl on a live CD but I was too silly that I tried that howto even if I was running Ubuntu from my hard drive so right now, I end up typing this thread using the edgy live CD.

I remember installing beryl and editing the file with the Section "Device". Unfortunately, I forgot what file it was. Other than those things, I don't remember doing anything else that would do this to my computer.

I also remember that the howto stated that if there are problems encountered while following the howto, I just had to open the console by pressing ctrl+alt+1 and entering "startx", but the console wont even start.

Right now, after booting Ubuntu and after the loading screen (the one with the black screen, ubuntu logo with the loading progress below it), I would just see a black screen.

How do I fix this?

---

### Post by ChrisUK on 2007-04-12
This sounds very similar to the problem I am having.
Was it this guide by any chance: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

I am having the exact same problems... As soon as I edit the device section and press alt + ctrl + backspace to restart the X server. I get a blue screen saying my X server has failed. I restart and get that black login screen.
Press ctrl + alt + F1 and login (be careful with your caps lock, I tried to use a 7 and when I had caps lock on, it used a & instead).
If you backed up your xorg.conf file, you can get it back by logging in at the black screen, then typing the following into the console:

> sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Then restart your PC and it should be working, as long as you backed the xorg file up as the guide asked.

I really want to find out what the problem is with this Device section of the file because I can't get passed that section. You can read my thread here: [http://ubuntuforums.org/showthread.php?t=406734](http://ubuntuforums.org/showthread.php?t=406734)

Hope this helps.

---

### Post by NIKOSHIBA on 2007-04-12
> I remember installing beryl and editing the file with the Section "Device". Unfortunately, I forgot what file it was. 
that would be xorg.conf file in /etc/X11/ folder

> ctrl+alt+1
ctrl+alt+F1

when you get to console by pressing ctrl+alt+F1. replace foulty xorg.conf file by backed up one (i hope you did made a backup)
otherwise undo changes you made earlyer

---

### Post by wersdaluv on 2007-04-12
Actually, my case is different. 

You know why? I cant even open a console by pressing ctr+alt+<f1 to f7>!

---

### Post by wersdaluv on 2007-04-12
I'm thinking of uninstalling and installing xserver-xorg. 

Would that be a good idea?

I tried to do it by entering **sudo aptitude remove xserver-xorg install xserver-xorg**, but what I saw was a downgrade. 

Is that okay or would it damage my system?

---

### Post by aberry5555 on 2007-04-12
Try this command, it will re-do the xorg.conf configuration file so it will be like you had just installed Ubuntu.

```
sudo dpkg-reconfigure xserver-xorg
```

This should either find your graphics card and select the right driver or, if you had to do that yourself after you installed ubuntu, it will install the "vesa" driver which will give you basic but stable graphics.

Good luck!

<--EDIT-->

I presume you can get to a console to do this, if not then leave another message and I'll try to remember how to get a console up otherwise :p

---

### Post by wersdaluv on 2007-04-12
> **aberry5555 said:**
> Try this command, it will re-do the xorg.conf configuration file so it will be like you had just installed Ubuntu.

```
sudo dpkg-reconfigure xserver-xorg
```

This should either find your graphics card and select the right driver or, if you had to do that yourself after you installed ubuntu, it will install the "vesa" driver which will give you basic but stable graphics.

Good luck!

<--EDIT-->

I presume you can get to a console to do this, if not then leave another message and I'll try to remember how to get a console up otherwise :p

I'll do it in Ubuntu Safe Mode. Will that work?

---

### Post by aberry5555 on 2007-04-12
Yep, if your using it from the grub menu (rather than opening the LiveCD) then that should work OK.

---

### Post by wersdaluv on 2007-04-12
Thanks or that.

Now, I have Ubuntu up and running again.

The problem is, all my settings are deleted including my /home's mount point.

Is there a way for me to restore my old settings?

---

### Post by wersdaluv on 2007-04-12
Ooops! When I started Ubuntu a while ago, it was by running **startx** after configuring x with **sudo dpkg-reconfigure xserver-xorg**.

When I rebooted, I logged in in a console then tried **startx**, but the output stated that no monitor was found. 

What do I do now?

---

### Post by aberry5555 on 2007-04-12
hmmm, thats strange, try starting in the normal startup rather than safe-mode, as it sounds like you still have to use a terminal to start.

---

### Post by wersdaluv on 2007-04-12
> **aberry5555 said:**
> hmmm, thats strange, try starting in the normal startup rather than safe-mode, as it sounds like you still have to use a terminal to start.

Actually, I was unsuccessful when I started with the normal start-up.

I reconfigured x in safe mode and started x successfully there. I restarted the normal mode and apparently, x was not properly configured there. It was looking for a monitor. 

How do I fix it?

---

### Post by aberry5555 on 2007-04-12
ok, if you have a terminal after this then try re-doing the command when not in safe-mode. This shouldn't really make a difference but try anyway, as I cannot see how it would work in safe-mode and not in normal ubuntu unless the file changed itself.

---

### Post by wersdaluv on 2007-04-12
> **aberry5555 said:**
> ok, if you have a terminal after this then try re-doing the command when not in safe-mode. This shouldn't really make a difference but try anyway, as I cannot see how it would work in safe-mode and not in normal ubuntu unless the file changed itself.

Thanks!

It worked!

Now that my Firefox session is recovered, here is the howto that I followed--> [http://ubuntuforums.org/showthread.php?t=301364](http://ubuntuforums.org/showthread.php?t=301364) :D

---

### Post by aberry5555 on 2007-04-12
No problem, hopefully it doesn't revert when it restarts again!

Also, from that walkthrough, the bit where you add on to devices "AGP mode 8" may not be the right setting for your card, what type is it? is it it AGP or PCI-E?

---

