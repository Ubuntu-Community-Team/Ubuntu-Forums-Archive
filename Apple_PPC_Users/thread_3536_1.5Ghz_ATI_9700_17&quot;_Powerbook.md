---
title: "1.5Ghz ATI 9700 17&quot; Powerbook"
date: 2004-11-07
forum: Apple PPC Users
---

### Post by taraku on 2004-11-07
Hey

Has anyone had any luck with running Ubuntu (or for that matter, any ppc linux distro) on the 1.5 Ghz 17" Powerbook with the ATI 9700 Mobility graphics card? I can't find this *anywhere.* and subsequently have been waiting for the next release of YDL 4.0 before I can get a fulling working linux install. I would like to bet Ubuntu or Debian going on my system, but this is the limitting factor. Help please!

All the best!

-Tarak Upadhaya

---

### Post by Viro on 2004-11-07
[QUOTE=taraku]Hey

Has anyone had any luck with running Ubuntu (or for that matter, any ppc linux distro) on the 1.5 Ghz 17" Powerbook with the ATI 9700 Mobility graphics card? I can't find this *anywhere.* and subsequently have been waiting for the next release of YDL 4.0 before I can get a fulling working linux install. I would like to bet Ubuntu or Debian going on my system, but this is the limitting factor. Help please!

All the best!

-Tarak Upadhaya[/QUOTE]
 It should work fine. The Powerbook's Radeon card should work with the default radeon drivers (no 3D acceleration, but 2D is fine). Sound, ethernet, dvd read/burn, touchpad should be fine. The only things that don't work are Airport Extreme (extremely annoying), sleep, and 3D acceleration.

Just thought that I'd add, I've installed it on my 1.33 GHz powerbook 12" and it works fine.

---

### Post by monway on 2005-10-12
[QUOTE=taraku]Hey

Has anyone had any luck with running Ubuntu (or for that matter, any ppc linux distro) on the 1.5 Ghz 17" Powerbook with the ATI 9700 Mobility graphics card? I can't find this *anywhere.* and subsequently have been waiting for the next release of YDL 4.0 before I can get a fulling working linux install. I would like to bet Ubuntu or Debian going on my system, but this is the limitting factor. Help please!

All the best!

-Tarak Upadhaya[/QUOTE]


I have an Aluminum Powerbook G4 17" 1.33ghz and Ubuntu/Kubuntu installs fine with no problems at all with graphics or anything just no 3d acceleration. When you boot the install cd and at the boot prompt type ```
install-powerpc
``` there isn't anything else needed to add but if you really want to go for the extra measure at the boot prompt type ```
install-powerpc video=radeonfb nol3
``` (again, it's not necessary but who knows it may vary on different versions of this particular laptop.)
Good luck.
:cool:

---

