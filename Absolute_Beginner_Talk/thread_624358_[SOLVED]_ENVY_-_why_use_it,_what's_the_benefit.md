---
title: "[SOLVED] ENVY - why use it, what's the benefit?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-11-26
**"ENVY"** also installs the ATI drivers, but which one? open source or restricted? and why does envy exist, can't the ATI drivers be installed thought ubuntu enable restricted drivers?

**Update**
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
> If it doesn&#8217;t work, you can boot in Recovery mode and type:
sudo envy &#8211;uninstall-all

---

### Post by brennydoogles on 2007-11-26
> **MozartlovesUbun2 said:**
> **"ENVY"** also installs the ATI drivers, but which one? open source or restricted? and why does envy exist, can't the ATI drivers be installed thought ubuntu enable restricted drivers?

Before Feisty there was no restricted driver manager, so installing drivers could be a pain. Envy was super useful back then. I don't think it has much use now in Ubuntu (although there could be reasons I don't know about), so I recommend the restricted drivers manager. As for which driver Envy installs, I am mostly clueless.

---

### Post by FuturePilot on 2007-11-26
> **MozartlovesUbun2 said:**
> **"ENVY"** also installs the ATI drivers, but which one? open source or restricted? and why does envy exist, can't the ATI drivers be installed thought ubuntu enable restricted drivers?

I'm not sure which ATI driver it installs, but the reason it exists is so you can get the latest driver. The drivers that are in the Ubuntu repos will never be updated to a newer version unless you upgrade to the next version of Ubuntu. For example, the most recent Nvidia driver in Feisty is the 9755 driver, even though it's not the latest driver. It will always be 9755. The only way to get a newer driver without leaving the repos is to upgrade to Gutsy.
However by using Envy you can get the very latest drivers without having to upgrade Ubuntu.

---

### Post by MozartlovesUbun2 on 2007-11-26
> **FuturePilot said:**
> I'm not sure which ATI driver it installs, but the reason it exists is so you can get the latest driver. The drivers that are in the Ubuntu repos will never be updated to a newer version unless you upgrade to the next version of Ubuntu. For example, the most recent Nvidia driver in Feisty is the 9755 driver, even though it's not the latest driver. It will always be 9755. The only way to get a newer driver without leaving the repos is to upgrade to Gutsy.
However by using Envy you can get the very latest drivers without having to upgrade Ubuntu.

ah ok, well so then i need ENVY even if i am using Gutsy to get the latest drivers? hmm is there a way i can keep my gutsy ATI always up to date and not have to wait until release of Hardy?

---

### Post by FuturePilot on 2007-11-26
> **MozartlovesUbun2 said:**
>  hmm is there a way i can keep my gutsy ATI always up to date and not have to wait until release of Hardy?
Envy ;)

---

### Post by MozartlovesUbun2 on 2007-11-27
> **FuturePilot said:**
> Envy ;)

ok so then i should install ENVY to my Gutsy, as it keeps everything up to date.

and if i use gutsy restricted enable, then it will only install the old drivers.

is that right so?

---

### Post by FuturePilot on 2007-11-27
> **MozartlovesUbun2 said:**
> ok so then i should install ENVY to my Gutsy, as it keeps everything up to date.
Pretty much yes. But when a new driver is released you'll need to install the newer version of Envy. The script is usually updated whenever a new driver is released.
> and if i use gutsy restricted enable, then it will only install the old drivers.

It will install whatever version is in the repos.

---

### Post by MozartlovesUbun2 on 2007-11-27
> **FuturePilot said:**
> Pretty much yes. But when a new driver is released you'll need to install the newer version of Envy. The script is usually updated whenever a new driver is released.

It will install whatever version is in the repos.

ok, much thanks for the info, well so i'll install my ATI drivers through ENVY then i guess,

======

so ATI is still working on and releasing restricted drivers for Linux, which ENVY will install for me

plus there are open source ATI driver being developed for linux, but there are not totally ready yet, right.

did i get that much right?

---

### Post by FuturePilot on 2007-11-27
Yep, you got it. :)

---

### Post by MozartlovesUbun2 on 2007-11-27
question: if i enable the backports in Gutsy would it then update to the latest ATI 7.11 driver?

is that advisable?

---

### Post by Banacek on 2007-11-27
I had not heard of Envy before now. Instead, on my main panel, I had gone to *System>Administration>Restricted Drivers Manager* to try to get ATI Radeon drivers enabled for my Radeon 9600 Pro 128MB DDRSDRAM card. It just wouldn't work.

So it takes Envy to get those drivers enabled? Why put a restricted drivers manager on that doesn't even work; why don't they just make the manager so it works? I don't know a thing about Envy. How do I use it properly and what are the steps to get it to enable the ATI restricted drivers? I'm on a Gusty install.

Before this I had already gone to [http://wiki.x.org/wiki/ATIProprietaryDriver](http://wiki.x.org/wiki/ATIProprietaryDriver) and there it had said that at [www.ati.com](www.ati.com) a driver that performs well was hosted there. So I ended up at [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) where I downloaded the ati-driver-installer-7-11-x86.x86_64.run driver. Rather than using Envy, wouldn't it be better to just install this driver since I already have it downloaded? How do I do that? What are the proper steps?

---

### Post by MozartlovesUbun2 on 2007-11-28
> **Banacek said:**
> I had not heard of Envy before now. Instead, on my main panel, I had gone to *System>Administration>Restricted Drivers Manager* to try to get ATI Radeon drivers enabled for my Radeon 9600 Pro 128MB DDRSDRAM card. It just wouldn't work.

So it takes Envy to get those drivers enabled? Why put a restricted drivers manager on that doesn't even work; why don't they just make the manager so it works? I don't know a thing about Envy. How do I use it properly and what are the steps to get it to enable the ATI restricted drivers? I'm on a Gusty install.

Before this I had already gone to [http://wiki.x.org/wiki/ATIProprietaryDriver](http://wiki.x.org/wiki/ATIProprietaryDriver) and there it had said that at [www.ati.com](www.ati.com) a driver that performs well was hosted there. So I ended up at [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) where I downloaded the ati-driver-installer-7-11-x86.x86_64.run driver. Rather than using Envy, wouldn't it be better to just install this driver since I already have it downloaded? How do I do that? What are the proper steps?

i understand your fustration, but things are getting better
it's just all muddeled up right now

take some time and read here about Envy
[http://albertomilone.com/wordpress/?p=140](http://albertomilone.com/wordpress/?p=140)
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Alberto is putting a lotta work into it.

for more info just click on my profile and go through the older posts, i was asking the same questions as you, so lets see new ATI 7.11 drivers are out now, minimal change though, try it out and read carefully how to use Envy.


[B]as far as i understand, using the restricted drivers ubuntu will install the old ATI drivers until Hardy comes out

Envy will install the newer ones[/B]

---

### Post by Banacek on 2007-11-28
Thank you, MozartlovesUbun2. Yeah, I went ahead and did
```
su root
password:
sh ati-driver-installer-7-11-x86.x86_64.run
``` (*right-click>Properties* told me it's a shell script). It ran through the entire driver installation script, telling me everything was done. Lies! Still on the VESA driver.

So, it looks like what you just said is the case. I will try to read through the Envy info you gave links for (I hope it's not too convoluted) and see what I can do with it. I really need the video card's direct rendering abilities to be enabled, amongst other things.

---

### Post by MozartlovesUbun2 on 2007-11-28
> **Banacek said:**
> Thank you, MozartlovesUbun2. Yeah, I went ahead and did
```
su root
password:
sh ati-driver-installer-7-11-x86.x86_64.run
``` (*right-click>Properties* told me it's a shell script). It ran through the entire driver installation script, telling me everything was done. Lies! Still on the VESA driver.

So, it looks like what you just said is the case. I will try to read through the Envy info you gave links for (I hope it's not too convoluted) and see what I can do with it. I really need the video card's direct rendering abilities to be enabled, amongst other things.

no problemo, when we turn grey and 50 I guess alas the drivers will be ready for some proper 3D **PS3** style gaming :-)

(no i seriously hope they manage to do it sooner)

---

### Post by Banacek on 2007-11-28
Too LATE!!

I've already turned fifty and I have a considerable amount of white throughout my hair.







After using Envy I rebooted and for a few moments it looked like it was going to work. So close, but **NO-O-O-O-O!** I get to the login screen and log in. It blanks out to the empty orange screen. Then it's replaced by an empty screen of my chosen background colors (damn, I hate that burnt-orange/orange scheme). Then the screen blacks out with the locations I placed my panels in white. Next, I see my desktop with my chosen background picture for almost a second. That is promptly replaced with a bright white screen with the tiny circle and the dots rotating near the perimeter. The little circle goes away and white screen stays and stays until I do ctrl+alt_backspace.


Let's backtrack a tad. Okay, I installed Envy and ran it. For one second I pondered choosing a manual install of the ATI drivers instead of having Envy do it on automatic mode. I selected for Envy to do it for all for me. I managed to get a few screenshots.


[IMG]http://i18.tinypic.com/81hmx5e.png[/IMG]


[IMG]http://i10.tinypic.com/81hpn5t.png[/IMG]



However, I did NOT get the last screenshot. It went by me a litte too fast and I was slow on the keyboard. I think I saw a fatal error about something not being present in /proc ... fglrx? I can't be sure as it went by too fast to be sure I wasn't looking at two different errors on two different lines. It said done and closed too quickly. Then something popped up saying it was complete and asked if I wanted to restart (recommended). So that fooled me into thinking it completed and I chose restart.

---

### Post by Banacek on 2007-11-28
Booted into recovery mode (no GUI, command line and text only) and as root I did this:
```
dpkg-reconfigure -phigh xserver-xorg
```

It generates a new /etc/X11/xorg.conf file and makes a backup of the prior one, apparently. After that I reboot into the normal mode of the kernel and I get logged into GNOME with no apparent problems. Quite smoothly, really.

I am seeing graphic effects and more speed (in opening, manipulating and closing various windows for sundry applications) that wasn't there before. This leads me to guess that direct rendering is enabled but I need confirmation of it. I bring up a terminal and get this:
```
glxinfo | grep direct
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual
```


What is going on? Before, the grep would at least tell me "NO" on the direct rendering. Now it doesn't mention anything about direct rendering but my DRI is gone??? Damn. How do I fix this?

---

### Post by ukripper on 2007-11-28
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by misfitpierce on 2007-11-28
Envy installs newest driver for Nvidia and ATI. Also did the roundabout for ATI to auto whitelist fglrx in compiz. It's a very useful tool and I support it fully.

---

### Post by Banacek on 2007-11-28
That guide is using the restricted package manager. I used Envy. Is there anything at all in there that I can use? Offhand, some of it is even just plain wrong, e.g. *LIBGL_DEBUG=verbose glxinfo* gives```
LIBGL_DEBUG=verbose: Command not found.
```

---

### Post by MozartlovesUbun2 on 2007-11-28
**Banacek**
I'm no expert on ENVY or ATI driver installations, but I think before running ENVY you gotta have all other ATI drivers cleanly uninstalled (i think there are step by step instructions on Albertos site)

um, also depending which ATI card you have, the newer ATI drivers might not be good for it,  please check before using

> If it doesn&#8217;t work, you can boot in Recovery mode and type:
sudo envy &#8211;uninstall-all

===========

oh i didn't know that
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
> By default Ubuntu will use the open source 'ati' or 'radeon' driver for cards that manufactured by ATI. Some users however prefer the proprietary 'fglrx' driver for various reasons. The instructions on this page will tell you how to use this driver.
There are 2 ways you can install proprietary fglrx drivers. The preferred way is to use the drivers provided via the Ubuntu repositories. More advanced users can also try the drivers from ati.com. Both approaches are documented below and you need to take only one of them. The Ubuntu-provided ones are the safest bet, the ati.com ones however may be needed (eg: when you need **hibernation**).

good read, check it out

---

### Post by MozartlovesUbun2 on 2007-11-28
can someone answer this please for me:

[B]question: if i enable the backports in Gutsy would it then update to the latest ATI 7.11 driver?

is that advisable?[/B]

coz i thought the backports always get the latest updates, but are untested and therefore maybe unstable, right?

---

### Post by Banacek on 2007-11-29
Today I booted into rescue mode and switched my /etc/X11/xorg.conf file with an earlier one and did *dpkg-reconfigure -phigh xserver-xorg* (as root, of course). Then I rebooted normally and looked this thread up for the command to undo the Envy stuff so as to start out fresh before trying it all over again. So, I do *sudo envy --uninstall-all* and it undoes everything, apparently. (Yeah, for me it's *--uninstall-all* instead of *-uninstall-all* but I run tcsh instead of bash or even dash. I would have thought something fundamental to a command as that wouldn't change from shell to shell. Is it or is something else entirely different going on with that?) Afterwards, I do *sudo dpkg-reconfigure -phigh -xserver.xorg* and then uncomment the Wacom lines in the /etc/X11/xorg.conf file because my trackball, apparently, is using a Wacom stylus or tablet (or at least that's what devices are shown in the xorg.conf file as being used for pointers, cursors and such). Finally, I reboot.

After I login (no problems it seems) I bring up a terminal to see if I can get a simple "yes" or "no" answer from grep for direct rendering of glX. I expect a "no" but instead ...

```
glxinfo | grep direct
direct rendering: Yes
```


Okay, that was totally unexpected but the whole point of this entire exercise of trying to get the actual ATI drivers is to have direct rendering. Yes? At least for me, it is.

So, rather than doing the next part of the plan, being, making sure to uninstall Ubuntu's default drivers for Radeon ***CLEANLY*** prior to installing Envy, why the hell don't I just leave well enough alone as it's now got direct rendering already enabled???





Hey, if it's already got what I want ... if it's not broken, then don't fix it. Right?

Or is there something else going on here? Who here knows?

---

### Post by Banacek on 2007-11-29
About that glxinfo ...












**[SIZE="3"]LIES!!![/SIZE]**

It lies!

---

### Post by MozartlovesUbun2 on 2007-11-29
> **Banacek said:**
> About that glxinfo ...

**[SIZE="3"]LIES!!![/SIZE]**

It lies!

sorry, which one do you mean?

===================

> **So, rather than doing the next part of the plan, being, making sure to uninstall Ubuntu's default drivers for Radeon CLEANLY prior to installing Envy, why the hell don't I just leave well enough alone as it's now got direct rendering already enabled???**

I thought ENVY does this automatically, can someone please comment on this, thanks

---

### Post by LauraSakura on 2007-11-29
Using envy was the only way I was able to get the drivers to work for my nvidia geforce4 mx  440. I tried all of the packages in Synaptic and none worked right until I tried envy. I think perhaps having it compile itself like that from the binary is what my system needed. so yeah, I'm really glad envy exists. However, I Don't know how different things are on the ATI side of things

---

### Post by Banacek on 2007-11-29
> **MozartlovesUbun2 said:**
> sorry, which one do you mean?

===================



I thought ENVY does this automatically, can someone please comment on this, thanks


Maybe, but the thing is I had just undone everything that Envy had done. After using Envy and it hadn't gone quite right, you had told me that I needed to do a clean uninstall of the drivers already in use before using Envy. So, I had to put my machine back to the state it was before I used Envy. After that I can uninstall the default drivers and then I can try to use Envy again.

What lied, you ask? After I undid Envy I did *glxinfo | grep direct* and it told me "*direct rendering: Yes*". That was the lie.

---

### Post by MozartlovesUbun2 on 2007-11-29
> **Banacek said:**
> Maybe, but the thing is I had just undone everything that Envy had done. After using Envy and it hadn't gone quite right, you had told me that I needed to do a clean uninstall of the drivers already in use before using Envy. So, I had to put my machine back to the state it was before I used Envy. After that I can uninstall the default drivers and then I can try to use Envy again.

What lied, you ask? After I undid Envy I did *glxinfo | grep direct* and it told me "*direct rendering: Yes*". That was the lie.


Also I think Ubuntu restricted drivers should be not check marked, maybe also double check through synaptics

anyway uninstalling Envy should be easy
> If it doesn&#8217;t work, you can boot in Recovery mode and type:
sudo envy &#8211;uninstall-all

---

