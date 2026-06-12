---
title: "Looking for Ubuntu for PowerPC"
date: 2014-07-05
forum: Apple Hardware Users
---

### Post by jacatone on 2014-07-05
I have an older MacOSX 10.5 Leopard Powerbook. Is there a Ubuntu version that'll work with this thing. I'd like to use XFCE or LXDE if possible. Thanks.

---

### Post by Farinet on 2014-07-05
Yes. lubuntu 14.04 installs fine. There might be a problem with sound. You could ask help to lubuntuusers mailing list too. As for me i resolved,  for a pb 17", by keeping lubuntu 14.04 but downgrading the kernel to 3.2-4 or something like that. It's not really elegant, but it works - for the moment (the reason for the sound problem is an inherited bug from the debian kernels > 3.2) And i get also all upgrades ...  May be there will be video problems which you can resolve using specific settings either on the fly for the live-cd like as well for yaboot in the final installation. As for me i've:     video=radeonfb:1440x900-32  But that depends on the graphic card of your machine, obviously.  Good luck.

---

### Post by bapoumba on 2014-07-05
*Thread moved to **Apple Users**.*

---

### Post by frank18 on 2014-07-05
> **jacatone said:**
> I have an older MacOSX 10.5 Leopard Powerbook. Is there a Ubuntu version that'll work with this thing. I'd like to use XFCE or LXDE if possible. Thanks.

If i were you would  forget any Ubuntu distro for aple PPC ,install debian wheezy ppc  unless you want to pull your hair and get bold faster.

---

### Post by Farinet on 2014-07-06
> **frank18 said:**
> If i were you would  forget any Ubuntu distro for aple PPC ,install debian wheezy ppc  unless you want to pull your hair and get bold faster.  +1  Some remarks:   - Even there you have the sound problem. - If you do it, install also the sid repositories. - Mint-PPC is wheezy based (but contains some few ppc specific tweakings).  ---  Personally, i tweaked my original lubuntu installation to get as close as possible to crunchbang (which as a distro does not exist for ppc).

---

