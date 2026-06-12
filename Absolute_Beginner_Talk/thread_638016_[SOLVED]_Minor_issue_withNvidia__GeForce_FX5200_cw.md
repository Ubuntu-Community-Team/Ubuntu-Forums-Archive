---
title: "[SOLVED] Minor issue withNvidia  GeForce FX5200 cw GeForce 7300"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-12-11
Hi

Very minor issue here, but I like to check things out.


On one of my ubuntu boxes (both Gutsy) I have an Nvidia  Geforce 7300 LE:

When I boot it I get an Nvidia fllash screen before getting to the login page, and then a nice compiz fusion 'overlay'  on the desktop (I don't know how else to describe it) as the thing boots up.

On my other box which has GeForce FX 5200, I get neither of these things, although there are some green and silver lines and a box or two saying 'Dell' which pop up for a fraction of a second during boot.

Any clues?
Don't all rush at once now... It's a tiny cosmetic problem, but I would like to understand why one box works nicely and the other doesn't. (advanced desktop effects a.k.a. compiz fusion) works OK on both boxes. It's just the startup screens.

TIA

---

### Post by Existentialist on 2007-12-11
I'm not sure on the "compiz fusion overlay," but the nvidia logo is something that can by changed in your xorg.conf file.  If you want to enable it or disable it:

>sudo nano /etc/X11/xorg.conf

There should be a section that looks something like this:

Section "Device"
	[INDENT]Identifier	"NVIDIA 8800gt"[/INDENT]
	[INDENT]Driver		"nvidia"[/INDENT]
	[INDENT]BusID		"PCI:3:0:0"[/INDENT]

Add the line:

        [INDENT]Option		"NoLogo"[/INDENT]

or comment it out to enable the nvidia logo.
Mine used to have the logo by default, but since upgrading to ubuntu 7.10 I noticed that the logo seems to be disabled by default after installing the newer nvidia drivers.

---

### Post by ubername on 2007-12-13
> **Existentialist said:**
> I'm not sure on the "compiz fusion overlay," but the nvidia logo is something that can by changed in your xorg.conf file.  If you want to enable it or disable it:

>sudo nano /etc/X11/xorg.conf

There should be a section that looks something like this:

Section "Device"
	[INDENT]Identifier	"NVIDIA 8800gt"[/INDENT]
	[INDENT]Driver		"nvidia"[/INDENT]
	[INDENT]BusID		"PCI:3:0:0"[/INDENT]

Add the line:

        [INDENT]Option		"NoLogo"[/INDENT]

or comment it out to enable the nvidia logo.
Mine used to have the logo by default, but since upgrading to ubuntu 7.10 I noticed that the logo seems to be disabled by default after installing the newer nvidia drivers.

Thanks, that got the logo sorted!

Do you know what I mean about the compiz fusion overlay? I don't think I described it very well.
On my other box after the desktop shows, some swirly lines with Compiz fusion' written in the middle of them appear for a second or so. 

As I say, it's a tiny thing: I wouldn't miss it if my other comp didn't show it, but if I can learn something, I'ld like to.

TIA

---

### Post by Existentialist on 2007-12-13
Unfortunately, I don't have much experience with compiz fusion.  I played with it for a little while in ubuntu 7.10 and gentoo, but never had a splash screen like that come up.  Is it an older version of compiz on the comp with the splash screen?

---

### Post by ubername on 2007-12-16
> **Existentialist said:**
> Unfortunately, I don't have much experience with compiz fusion.  I played with it for a little while in ubuntu 7.10 and gentoo, but never had a splash screen like that come up.  Is it an older version of compiz on the comp with the splash screen?

I'm not sure. I always install the automatic software upgrades so I have been living in the belief that both machines should be at the same level of software, but  I haven't explicitly checked. Is my assumption that they both run the same version of stuff flawed?

TIA

---

### Post by BLTicklemonster on 2007-12-16
On the 5200 machine, if you want the compiz, go to applications, add/remove, then change it to all available applications, then chose ubuntu restricted drivers, perhaps at that point, you will be notified that there are restricted drivers available (either then or when you reboot, I don't remember). Click the icon, and chose to use the new nvidia drivers. Reboot, and you should be on your way to having compiz working. If it doesn't right off the bat, go to synaptic, and look under the compiz files to be sure you have them all. Well, not all, but compiz, and the compiz settings manager, and the plugins.

---

### Post by ubername on 2007-12-17
> **BLTicklemonster said:**
> On the 5200 machine, if you want the compiz, go to applications, add/remove, then change it to all available applications, then chose ubuntu restricted drivers, perhaps at that point, you will be notified that there are restricted drivers available (either then or when you reboot, I don't remember). Click the icon, and chose to use the new nvidia drivers. Reboot, and you should be on your way to having compiz working. If it doesn't right off the bat, go to synaptic, and look under the compiz files to be sure you have them all. Well, not all, but compiz, and the compiz settings manager, and the plugins.

Hi

Thanks for this. Compiz works fine on both boxes, I just wanted to understand why one shows a 'flash screen' when compiz starts (the 7300 box) and the other (the 5200 box) doesn't. As I say, it is a minor (vanishingly minor!) issue, but thanks for the help,

---

### Post by Jengle on 2007-12-17
I have a FX5200 and I have never seen the Compiz splash screen.  I have the Nvidia screen initially, but not the second.  Do you have any added capabilities?  I would like to tweak the gamma on my monitor, but I do not have any of those settings for my GeForce card like I did when running M$ Windows.

---

### Post by confy on 2007-12-17
I don't know if this will help but it might give a clue to somebody...

I'm having problems with Geforce 7300 SE so to fix it i need to run *sudo dpkg-reconfigure xserver-xorg* each time after login. Then to logout (and here is magic) when i logout after reconfigure i get that logo and with resolution that i want. 
I know it doesn't help you but it seems when changing resolution or when accessing hardware for first time then it shows nvidia logo...

---

### Post by zekica on 2007-12-17
@ubername:

You can install package 'compizconfig-settings-manager' from Synaptic. Then you should have "Advanced Desktop Effect Settings" application for fine-tuning Compiz.

In it, you will see module named 'Splash' under 'Extras', and if it is enabled, then this splash screen will show on startup. You can disable or enable it if you want.

---

### Post by ubername on 2007-12-17
> **zekica said:**
> @ubername:

You can install package 'compizconfig-settings-manager' from Synaptic. Then you should have "Advanced Desktop Effect Settings" application for fine-tuning Compiz.

In it, you will see module named 'Splash' under 'Extras', and if it is enabled, then this splash screen will show on startup. You can disable or enable it if you want.

What a star!!

Thanks very much. That is exactly what I was looking for. I don't much mind whether I have the splash screen or not, but I am really hapopy to know how to get it  / loose it. I am a bit ashamed that I didn't compare my settings on each box, Thanks again.

---

### Post by Jengle on 2007-12-17
Thanks!  That worked and gave me what I was looking for.:)

---

