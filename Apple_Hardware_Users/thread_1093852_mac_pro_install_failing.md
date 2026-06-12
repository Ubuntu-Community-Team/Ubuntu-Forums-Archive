---
title: "mac pro install failing"
date: 2009-03-12
forum: Apple Hardware Users
---

### Post by babag on 2009-03-12
followed the tutorial at geeklimit.com for triple booting and
ubuntu is not succeeding in the install. actually, it may be 
succeeding but it's not correctly booting after the install.

[http://blog.geeklimit.com/2008/07/02/triple-boot-macbook-pro-osx-leopard-vista-64-bit-and-ubuntu-804-64-bit/](http://blog.geeklimit.com/2008/07/02/triple-boot-macbook-pro-osx-leopard-vista-64-bit-and-ubuntu-804-64-bit/)

when i try to boot into ubuntu 8.10 (i do see all three os's
at the refit boot screen), the boot begins but after i see a
brown progress bar for a second the screens go blank and stay 
that way, forcing a hard reboot back to osx.

this is an intel mac pro, dual quad core. i have ATI Radeon HD 
2600 XT display adapter. that's hooked up to a hannsg 28" and a 
matrox triplehead2go with three 20" envision displays. during 
the entire install the hannsg and the far left of the three 
envisions both displayed the same info. as the boot starts now, 
they both show the brown progress bar, then both go blank.

for the install i used the 8.10 64bit alternate (text) install
disk because using the regular 64bit disk gave me a blank screen 
during the install, making the install impossible to complete.

anybody got any ideas as to how to get this install working?

thanks,
BabaG

---

### Post by pxwpxw on 2009-03-12
> **babag said:**
> followed the tutorial at geeklimit.com for triple booting and
ubuntu is not succeeding in the install. actually, it may be 
succeeding but it's not correctly booting after the install.

[http://blog.geeklimit.com/2008/07/02/triple-boot-macbook-pro-osx-leopard-vista-64-bit-and-ubuntu-804-64-bit/](http://blog.geeklimit.com/2008/07/02/triple-boot-macbook-pro-osx-leopard-vista-64-bit-and-ubuntu-804-64-bit/)

when i try to boot into ubuntu 8.10 (i do see all three os's
at the refit boot screen), the boot begins but after i see a
brown progress bar for a second the screens go blank and stay 
that way, forcing a hard reboot back to osx.

this is an intel mac pro, dual quad core. i have ATI Radeon HD 
2600 XT display adapter. that's hooked up to a hannsg 28" and a 
matrox triplehead2go with three 20" envision displays. during 
the entire install the hannsg and the far left of the three 
envisions both displayed the same info. as the boot starts now, 
they both show the brown progress bar, then both go blank.

for the install i used the 8.10 64bit alternate (text) install
disk because using the regular 64bit disk gave me a blank screen 
during the install, making the install impossible to complete.

anybody got any ideas as to how to get this install working?

thanks,
BabaG

Here on a imac8,1 with a ATI Radeon HD 2600 XT I had to start into a root console and edit /etc/X11/xorg.conf, to get started, until the Desktop option <System/Hardware Drivers> could get the fglrx driver installed.

/etc/X11/xorg.conf

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"radeon"
EndSection

```

You should be able to stop the grub boot menu with <escape> and select the  'recovery mode' option to edit the xorg.conf file.
```

# cp /etc/X11/xorg.conf   xorg.confbakup
# nano /etc/X11/xorg.conf

```

---

### Post by babag on 2009-03-12
thanks, pxwpxw.

that&#347; getting me to the next step. have a fresh desktop in front of me 
now. now all i have to do is figure out how to configure it. 

the way i have it in osx and windows is with the 28" screen as the 
secondary screen, centered above the three 20"screens which act together
as the primary screen.

right now, the primary seems pretty much normal. the secondary, though, 
seems to have issues. it is ´squeezed´ and not filling the screen. it is 
not centered above the primary, but left justified. right now, firefox is 
positioned on the leftmost of the three primaries. it is, however, 
positioned a bit high on the screen, such that the top, where i would grab 
it to move it, goes out the top of the screen. that would be ok 
except the top does not appear on the secondary monitor where, based on 
the position, i´d expect it. that means the top of the browser is not
visible and that it cannot be repositioned. hmmm.

well, thanks again. i&#314;l leave this for another day, happy that, after 
months of off-and-on trying, i now know linux is, in fact, installable
on my mac pro.

BabaG

---

