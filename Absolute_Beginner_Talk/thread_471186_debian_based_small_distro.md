---
title: "debian based small distro?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by johnny4north on 2007-06-11
sys specs; Plll 733, 384mb ram, cd burner, and usb stick 1gig.  i would like to set-up a new workhorse Linux distro based on smallest debian distro[my current Linux box is updated to Linux gaming box:D] i love zenwalk and puppy linux, but want a small Debian distro.  my buddy killed my laptop(w/zenwalk), and now i want to build a new work horse pc[which will run all night and day.  AK electricity is $.42 kwh:(].  i want to be able to move the downloaded files and etc. in the usb stick, or burn to cd.  does anyone know of very small debian based distro?  thank you..:)

---

### Post by Bachstelze on 2007-06-11
Why run a "Debian-based distro" when you can run Debian itself ? ;)

---

### Post by Lord Illidan on 2007-06-11
> **HymnToLife said:**
> Why run a "Debian-based distro" when you can run Debian itself ? ;)

Aye, I agree.

The smallest distro I know which is debian based is Damn Small Linux.

---

### Post by johnny4north on 2007-06-11
ty i will look into debian distro.  sometimes the simple way is the best.  i m very busy, and i was looking for easy install like puppy Linux. DSL is and debian distro ?!?! really?

---

### Post by johnny4north on 2007-06-11
oo.. thank you Lord :D.  and Hymn.  i will try DSL and then Debian it self.:D

---

### Post by bodhi.zazen on 2007-06-11
You might want to look at Puppy Linux, Graff is very interesting.

also Fluxbuntu or [BeaFanatIX](http://bea.cabarel.com/)

Wolvix

Zenwalk.

Not all these are Debian, but most are a little more full featured then DSL

---

### Post by Lord Illidan on 2007-06-11
> **johnny4north said:**
> oo.. thank you Lord :D.  and Hymn.  i will try DSL and then Debian it self.:D

Hehe..DSL is based on Knoppix, which in turn is based on Debian.

It depends how simple you want to go..DSL is very small, but it's got a nice selection of features. Debian..you can customise it how you want.

Of course, there is no reason to lock yourself to Debian. Try gentoo, slackware or any other distro.

---

### Post by johnny4north on 2007-06-11
i love zenwalk, but i also like the debian apps.  i currently have DSL and fluxbuntu, i will try both tonight.  i will try debian tomorrow morning.  i will make my final choice tomorrow night.  helpful links i found for possible solutions -  [http://www.debian-administration.org/articles/446](http://www.debian-administration.org/articles/446)
[http://www.damnsmalllinux.org/wiki/index.php/USB_Booting](http://www.damnsmalllinux.org/wiki/index.php/USB_Booting)
[http://doc.gwos.org/index.php/Edgy_USB_Install](http://doc.gwos.org/index.php/Edgy_USB_Install)
very new [http://bea.cabarel.com/index.php?page=Features](http://bea.cabarel.com/index.php?page=Features)
thank you all..:D

---

### Post by johnny4north on 2007-06-13
i have chosen puppy linux 2.15 ce final.  why, well because of the ease of install, on the usb stick and saving data on the usb, cd-r or harddrive.  it took 5min to install and set-up networkcard. 40 seconds to boot.  i tested seamonkey(ok) and watched a dvd.  the dvd keep blinking. i wasted 3hrs trying to correct.  installed mplayer and  firefox:).  installed 3DCC utilitty and other pet packages, then finally the nividia drivers;-) w/ the 3DCC.  the kittens and i watched the best "the two towers", very clear and smooth. i will save about 10-20 watts per hour(est.)  somemore tweaking and customizing, then remaster a custom live-cd. done. good call bodhi.zazen  thank you all.

---

### Post by kerry_s on 2007-06-13
Debian is very nice you should go custom for the best speed. I use a debian+fluxbox on a 450mhz 256ram and it flies.

mini net installer-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

use> installgui  <if you want the fancy installer
otherwise just press enter. When it comes to the selection part just unselect everything, so you get just a minimal system(nogui yet)

reboot
login as root
apt-get install xorg gdm synaptic fluxbox emelfm mousepad dillo
reboot
select fluxbox in the session
login
open synaptic and get what ever else you want.

That is for a mini dsl like install with out the dsl limits. :)

---

### Post by bodhi.zazen on 2007-06-13
> **johnny4north said:**
> i have chosen puppy linux 2.15 ce final.  why, well because of the ease of install, on the usb stick and saving data on the usb, cd-r or harddrive.  it took 5min to install and set-up networkcard. 40 seconds to boot.  i tested seamonkey(ok) and watched a dvd.  the dvd keep blinking. i wasted 3hr trying to correct.  installed mplayer and  firefox:).  installed 3DCC utilitty and other pet packages. then finally the nividia drivers;-) w/ the 3DCC.  the kittens and i watched best "the two towers". very clear and smooth. i will save about 10-20 watts per hour(est.)  somemore tweaking and customizing, then remaster a custom live-cd. done. good call bodhi.zazen  thank you all.

LOL, you are most welcome. Puppy has come a long way and certainly offers a lot.

---

