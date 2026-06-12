---
title: "Problem with ATi driver?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Gandalf 1 on 2008-03-11
Hi, very much in the sense of the word "absolute", I am an ABSOLUTE beginner. 
I really have no idea of anything, so please dont bomb me with technical terms. 

A few days ago I installed Ubuntu 7.10 on my notebook and as the system rebooted to finally launch Ubuntu it freezes at:
```
 running local boot scripts (/etc/rc.local) [OK] 
```

And thats it. 
My notebook has an ATI radeon X1250 working inside.
In other forums I read about Ubuntu struggling with ATI graphic cards. So maybe thats the problem, BUT: I am a complete noob and as I said I dont know nothing. 
and in addition to that: I dont have the time to read through hundreds of pages abot Ubuntu/Linux basics, cause I need my laptop as soon as possible (and installing windows again would suck like hell).

So please, can somebody help me with detailled information? Cause I googled nearly the whole internet, but all I get is solutions for people who know what they re doing. 
thanks in advance

---

### Post by njparton on 2008-03-11
That's a startup script that can run many different things or nothing at all.

Do you get as far as grub?  If so try booting into recovery mode.

---

### Post by forrestcupp on 2008-03-11
When you get to the GRUB boot menu, the 2nd choice should say some Linux kernel, and it should say 'recovery console'.  Use your arrow keys to choose that.  It will boot to a command line.  When you get to your prompt, type:
```
dpkg-reconfigure xserver-xorg
```
That will guide you through manually setting up X, which has to do with your video and input settings.  For most of it, you can probably just choose the default and simple options, but when it asks you for your video card or adapter, you need to scroll down and choose 'vesa'.  Go through the rest of the setup choosing defaults and simple setups.

When your done, type
```
exit
```
And hopefully, you will be able to boot to your desktop.  Vesa drivers don't take advantage of any of your hardware acceleration, so eventually, you'll want to install the proper ATI drivers.  You can try using the Restricted Drivers Manager that you'll find in System->Administration.  If that doesn't work, you may need to redo all of this, and try to download [Envy](http://albertomilone.com/nvidia_scripts1.html) to automatically install the latest ATI drivers.

---

### Post by Gandalf 1 on 2008-03-11
Hi, 

thanks for your advice. I just tried to do that (boot in recovery mode) and i got till choosing the color depth. 
No matter what I choose, a small black strip appears at the bottom of the screen and says: 
```
 xserver-xorg postinst warning: overwriting possibly-customised  configuration file; backup in /etc/X11/xorg.conf.20080311191530
root@ubuntu:~#

```

and again, thats it. Is there anything I have to type in to continue????????
Help me please. 
Thanks

EDIT: I just tried to write "exit" as you told me (maybe the wizard was finished without telling me) into the small strip on the bottom of the screen. 
That leads to my initial problem: "running local boot scripts" and then it freezes.

---

