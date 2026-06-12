---
title: "iBook 500Mhz ATI Rage 128 M3"
date: 2005-01-25
forum: Apple PPC Users
---

### Post by rvdb on 2005-01-25
Dear all,

i have Ubuntu running on the iBook but with a few glitches.

- now and then the suspend doesn't work and after pressing the button i cant control sound and backlighting anymore (but when i powerdown it suddenly goes to sleep and when i resume it finally powersdown, so somehow it has registered my wish to sleep). I have pbbuttonsd installed.

- after a sleep / resume cycle, the cursor is not drawn anymore (leaving some black shadow of the cursor). After i click in a title bar (changing the cursor shape) it is normal again. (only a minor problem)

- i don't have any idea how to use the vga-out (and i need it badly for presentations, i'm even surprised to learn that other people use laptops for other things then presentations...).

I installed m3mirror and indeed i can switch of the lcd but i cant switch on the external crt. 

The VGA out is crucial for me. There are a lot of threads on this. Some very old (kernel 2.4) and most about other iBooks. 

Is there anyone out there with a machine like i have who known what to do?

A VGA-out fac would be nice i think. If i can get it to work i will start for my machine.

Kind regards

Rein van den Boomgaard

---

### Post by robsta on 2005-01-26
Hi, 

i also have a G3/600 M3, there seem to be only very few such models out there.

> - now and then the suspend doesn't work and after pressing the button i cant 
>  control sound and backlighting anymore (but when i powerdown it suddenly 
> goes to sleep and when i resume it finally powersdown, so somehow it has 
> registered my wish to sleep). I have pbbuttonsd installed.

> - after a sleep / resume cycle, the cursor is not drawn anymore (leaving 
> some black shadow of the cursor). After i click in a title bar (changing the cursor
>  shape) it is normal again. (only a minor problem)

Hmm, my ibook doesn't sleep at all. It can't recover after opening the lid again. There seem to be new patches for alBooks, but i have no idea if they work for ibooks as well.

> I installed m3mirror and indeed i can switch of the lcd but i cant switch on the 
> external crt. 

For vga-out i'm using an old benh kernel (2.4.25.ben5) with a patch by owen stampflee ( [http://stampflee.com](http://stampflee.com) ). It works very well, i even hacked a simple gnome applet a few years ago with a toggle button for lcd and crt respectively. If you are interested i can send you the tarball, but i've not used it with anything more recent than gnome-2.0 i think.

BTW, are you running a resolution > 1024 x 768 on your crt? I'd be really interested in having that.

Cheers, 
Rob

---

### Post by cutterjohn on 2005-01-26
"- now and then the suspend doesn't work and after pressing the button i cant control sound and backlighting anymore (but when i powerdown it suddenly goes to sleep and when i resume it finally powersdown, so somehow it has registered my wish to sleep). I have pbbuttonsd installed.

- after a sleep / resume cycle, the cursor is not drawn anymore (leaving some black shadow of the cursor). After i click in a title bar (changing the cursor shape) it is normal again. (only a minor problem)"

suspend: there's a bug report on this for warty, 1940 IIRC, if thats not right, or if you wish do a search on sleep in this forum.  Basically it's a matter of adding some scripts in /etc/apm to shutdown/restart hald/dbus.  (It usually works, although I have had a few occassions where the ibook does not awake properly, i.e. LCD is turned on but the machine is unresponsive to keyboard and network connections.   BTW: don't use the scripts in the forum as they do not work correctly, just go ahead and manually apply the scripts in the patch attachment to the bug report, or patch and rebuild the appropriate package as you so choose. I, originally, tried the scripts in the forum message and was like you, sometimes sleep worked sometimes not, and GUI cursors not redrawing properly.  Those scripts just did not work properly, as the case statements were malformed, and I suspect that apm emulation was behaving differently than expected, which I haven't bothered to investigate as the bug report fix works for me.)

"- i don't have any idea how to use the vga-out (and i need it badly for presentations, i'm even surprised to learn that other people use laptops for other things then presentations...).

I installed m3mirror and indeed i can switch of the lcd but i cant switch on the external crt.

The VGA out is crucial for me. There are a lot of threads on this. Some very old (kernel 2.4) and most about other iBooks. "

Again, do a search on the forums as IIRC someone else had some posts on this, but I am not certain if they got it to work, etc.  I don't use this feature myself, and I no longer have any clue as to where my dongle for VGA out has gone.

(If you really want a shortcut, try IRC, freenode network, channel #ubuntu, the people in there will help you out.  Lastly: I am assuming in my responses, that you are using Warty(4.10) and not Hoary.  If you are using Hoary, I'd strongly suggest taking advantage of the IRC option.)

---

### Post by cow_racer on 2005-01-26
m3mirror works for my ibook 500 Mhz ATI Rage 128 M3.  The only problem is the picture is fuzzy  on external screen.

---

### Post by robsta on 2005-01-26
You can use the patch from [http://stampflee.com/kernel/index.shtml](http://stampflee.com/kernel/index.shtml) to improve things.  There are also more recent versions for 2.6 series kernels floating around.

---

### Post by tgomas on 2005-02-26
[QUOTE=cow_racer]m3mirror works for my ibook 500 Mhz ATI Rage 128 M3.  The only problem is the picture is fuzzy  on external screen.[/QUOTE]

I've same problem with same ibook. Has anyone successed to display a clean image on an external screen?

---

### Post by Castaa on 2005-02-27
For those of you that have this series of iBook.  Have any of you gotten smooth DVD playback in Linux?

---

### Post by robsta on 2006-02-09
> For those of you that have this series of iBook. Have any of you gotten 
> smooth DVD playback in Linux?

I have the 600Mhz one but no luck with DVDs in all the years (spent quite some time fiddling).
Usually (in mailing lists, fora) buggy audio drivers are blamed, dunno, it's also too slow without audio (even in mplayer which is said to be fastest).
Also I have yet to find a single person who got it working, everyone is just telling me "it should work".

---

### Post by jtappin on 2007-11-09
> **robsta said:**
> Hi, 


> I installed m3mirror and indeed i can switch of the lcd but i cant switch on the 
> external crt. 

For vga-out i'm using an old benh kernel (2.4.25.ben5) with a patch by owen stampflee ( [http://stampflee.com](http://stampflee.com) ). It works very well, i even hacked a simple gnome applet a few years ago with a toggle button for lcd and crt respectively. If you are interested i can send you the tarball, but i've not used it with anything more recent than gnome-2.0 i think.


Cheers, 
Rob

I know this is a long time after the event! but I have a port of Owen Stampflee's patch to the 2.6 kernel. The attached one should apply cleanly to the Gutsy kernel source, and with offsets to Feisty and Edgy (I think anything earlier than that needs a patch to one of the header files as well). 

Note however it does NOT work for 24 bit graphics, only for 16 (I've not tried 8 bits).

---

### Post by kops.lnx on 2008-01-25
Thanks ! I have been trying to turn on this external VGA for few months. This patch fixed the fuzzy screen in both framebuffer and X. 

I had to put two new lines in my xorg.conf ; 
```
Option "UseFBDev" "true"
Option "Display" "Mirror"
```

Hotkey Ctrl + F7 turn on and off the external display.

---

