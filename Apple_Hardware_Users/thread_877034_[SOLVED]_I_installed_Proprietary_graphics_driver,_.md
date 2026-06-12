---
title: "[SOLVED] I installed Proprietary graphics driver, now there's no x server or GUI."
date: 2008-08-01
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-08-01
Hi,
  I am on an aluminum 24" iMac and I installed the ATI proprietary (accelerated) driver using Ubuntu's 'Hardware Drivers' program. Now I can't even get to my login screen since my x server seems to have crashed on the reboot after the ATI install.

All I get is a black screen. Will ctl+alt+F1 give me a console? I used to know how to fix the x server a long time ago (on PCs) but this is a mac so I'm cautious here. 

I'm using rEFIt, so I need to somehow get to a console during the boot up. Keep in mind, I'm not even getting to the Login screen here, so be aware of what you suggest.

Then I need to know how to fix this server if possible. I appreciate any help, please.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-08-01
Ok, First, I have an ATI Radeon HD2600 graphics card. I traced down old commands I use to use. So I think I need to do this:

```
sudo dpkg-reconfigure xserver-org
```

But I don't know how to get to a command prompt during the boot up so that I can run that code.

I tried ctl-alt-F1 and that did nothing. I also tried ctl-alt-del and that came up short as well. Also, I tried running all these using the liveCD to boot from the hard drive.

Also I know that I DO already have EnvyNG-gtk installed so if I could somehow run EnvyNG to install my ATI driver from the command line, that might fix the problem at its source.

I appreciate any help anyone could offer...
Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-08-01
Hi,
  Talking to myself here folks. Anyways, I DID finally get a command prompt: one has to press the fn key to enable F1, (at least on my keyboard) so you're pressing ctl-alt-fn-F1 which, to say the least, takes 2 hands. 

I tried to run this:
```
sudo dpkg-reconfigure xserver-org
```

And Ubuntu says 'xserver not installed' and mentions something about an old version. 

Also I should mention, I'm on wireless here so I have NO internet connection yet at the command line. Maybe there's a line of code to start ndiswrapper but I could be wrong.

I do appreciate any help anyone could offer.

Many Thanks, Frank B.

---

### Post by tiresia on 2008-08-01
I'm not sure, and I can't test it right now. But I think you should type

```
sudo dpkg-reconfigure xserver-xorg
```

I mean xserver-**x**org

Just another suggestion. If you have problems getting a shell, you can always start from you Installer-CD, mount the HD and work on it.

---

### Post by djxcon on 2008-08-01
To get to a shell, you can also boot to a recovery console.

Definitely try this first:
sudo dpkg-reconfigure xserver-xorg

If that doesn't work, try removing the restricted driver.
```
sudo apt-get remove --purge xorg-driver-fglrx
```

---

### Post by cyberdork33 on 2008-08-01
> **Brightbelt said:**
> Also I know that I DO already have EnvyNG-gtk installed so if I could somehow run EnvyNG to install my ATI driver from the command line, that might fix the problem at its source.If you are trying to install the new ATI drivers manually, you should first uninstall Envy and start with a clean slate. Also, ,the command that you probably want is ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` unless you want it to explicitly ask you questions. the -phigh lets the server detect everything and write a new xorg.conf just like it was first installed.

> **Brightbelt said:**
> Hi,
  Talking to myself here folks. Anyways, I DID finally get a command prompt: one has to press the fn key to enable F1, (at least on my keyboard) so you're pressing ctl-alt-fn-F1 which, to say the least, takes 2 hands. 

Also I should mention, I'm on wireless here so I have NO internet connection yet at the command line. Maybe there's a line of code to start ndiswrapper but I could be wrong.Yes the Fn thing is a bit annoying, but it is done that way to match functionality in OS X. There is a bug report about it, and having it both ways has been argued for.

Unfortunately, you have to install some ndiswrapper packages before you can use it. Convenient, I know.

It looks like the other posts will get you a bit further. (had a typo there). P.S. The "recovery mode" is one of the options you have to select from in GRUB. It starts the system into a console so you can fix things if needed.

---

### Post by Brightbelt on 2008-08-01
Thanks to you all for jumping in.:) Yes the 'xorg' thing really threw me for a bit and I did finally figure that out, but I think there's a post still out there with that same 'xserver-org' typo.

I HAVE gotten the reconfiguring process going, but I can't get past the Keyboard stuff - at a certain point, it stops the process and warns me that an initial configuration is being overwritten.

It happens right after the Meta Keys part. I tried leaving it blank and I also tried entering:
```
metawin:meta_win
```
which is supposed to be the default. No matter what I seem to do the process gets stopped and I get that warning. I don't know if Cyber's suggestion about putting 'phigh' into the initial command would get me past this. 

Also, initially, I seemed to encounter a default setting of 'PC105' for the keyboard, but the instructions say to enter 'macintosh', so I'm not sure which to do. 

Interestingly enough, I now seem to be able to boot to the login screen, but then I get a blank white screen after I log in.  

Btw, I used Ubuntu's 'Hardware Drivers' program to install this; if I use Synaptic, will the results be any different? You can help me avoid a 2nd crash here.

Many Thanks for all of you helping,...Frank B.

---

### Post by djxcon on 2008-08-01
I have used the following command to get a basic working xorg.conf file, though I have not tried with an iMac.

```
sudo dpkg-reconfigure -pcritical xserver-xorg 
```

After running this command, my xorg file resulted in the following:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Notice the keyboard section...

---

### Post by Brightbelt on 2008-08-01
Thanks Djxcon for your help in uninstalling the restricted driver. That allowed me to get to my desktop.

From what I see, there's no reason to go into xserver-xorg and reconfigure at this point. Everything looks right.

But my question still stands: If I use Synaptic to install the ATI restricted driver, will I get the same results?

Many Thanks to you all,...Frank B.

---

### Post by cyberdork33 on 2008-08-01
> **Brightbelt said:**
> I HAVE gotten the reconfiguring process going, but I can't get past the Keyboard stuff - at a certain point, it stops the process and warns me that an initial configuration is being overwritten.

It happens right after the Meta Keys part. I tried leaving it blank and I also tried entering:
```
metawin:meta_win
```which is supposed to be the default. No matter what I seem to do the process gets stopped and I get that warning. 
....
Also, initially, I seemed to encounter a default setting of 'PC105' for the keyboard, but the instructions say to enter 'macintosh', so I'm not sure which to do.
pc105 should work. If you are really concerned about it, I think you can make that section look like:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"mac"
EndSection
```
 You seem to be following a guide somewhere but you haven't linked to it. I don't know anything about the metawin part...

> **Brightbelt said:**
> Interestingly enough, I now seem to be able to boot to the login screen, but then I get a blank white screen after I log in.  

Btw, I used Ubuntu's 'Hardware Drivers' program to install this; if I use Synaptic, will the results be any different? You can help me avoid a 2nd crash here.

That usually happens because compiz tries to start, but there is a problem with the driver so it makes everything screwy. You can login, and after you are sure that everything is started up (and you have a white screen) you can (blindly) do ALT+F2 (opens the run window) and type exactly "metacity --replace" and press enter. Then you will magically see your desktop. Then you can turn off desktop effects in the appearance menu.

> **Brightbelt said:**
> But my question still stands: If I use Synaptic to install the ATI restricted driver, will I get the same results?Unfortunately, yes you probably will. I would guess that Envy maybe causing an issue for you if you had installed it previously. You should be able to run that script again, and completely uninstall it.

---

### Post by Brightbelt on 2008-08-01
Many Thanks for all your specifics Cyber. I think I may have found an unexpected element to all this of which I was unaware at first.

Tell me if I'm correct or not....

When I initially checked the 'Hardware Drivers' section before all this happened, the box by the restricted graphics driver was UNchecked, which is what led me to go ahead and enable it. Thus, I checked the box.

BUT perhaps I didn't notice the green light? I believe there was a green light there that signals driver is (already?) "In Use" - meaning that it is in use, but installed by another program (that is, EnvyNG).

Is this correct? Or am I over-analyzing the situation? If so, this means that I caused the xserver crash by re-installing the restricted driver OVER EnvyNG's previous installation.

Does that sound right?

Thanks, Frank B.

---

### Post by cyberdork33 on 2008-08-01
> **Brightbelt said:**
> When I initially checked the 'Hardware Drivers' section before all this happened, the box by the restricted graphics driver was UNchecked, which is what led me to go ahead and enable it. Thus, I checked the box.

BUT perhaps I didn't notice the green light? I believe there was a green light there that signals driver is (already?) "In Use" - meaning that it is in use, but installed by another program (that is, EnvyNG).

Is this correct? Or am I over-analyzing the situation? If so, this means that I caused the xserver crash by re-installing the restricted driver OVER EnvyNG's previous installation.

Does that sound right?
yes exactly.

---

