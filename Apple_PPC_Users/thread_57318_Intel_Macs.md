---
title: "Intel Macs"
date: 2005-08-16
forum: Apple PPC Users
---

### Post by spaceballl on 2005-08-16
I was just thinking how nice it will be when we have Intel macs as far as dual booting linux goes... Can't wait.

---

### Post by DJ_Max on 2005-08-16
Not really the case with me, I already dual boot OS X & Ubuntu. Besides, I would have rather them moved to AMD.

---

### Post by Freddie on 2005-08-17
Ubuntu (Debian) users currently do quite well on PPC (mac) CPU's. We get around 15,000 packages which is almost as many as the x86 lot get. Since you can get the source for most apps as well we probably do just as well as the x86 users. But we do miss out on things like a decent java distro and some other closed source applications.

---

### Post by Ptero-4 on 2005-08-18
[QUOTE=Freddie]Ubuntu (Debian) users currently do quite well on PPC (mac) CPU's. We get around 15,000 packages which is almost as many as the x86 lot get. Since you can get the source for most apps as well we probably do just as well as the x86 users. But we do miss out on things like a decent java distro and some other closed source applications.[/QUOTE]
 Also kubuntu users on PPC (and those running KDE on a ubuntu install) tend to have issues with some kde styles, window decorations and applets b/c qt have some big bugs that affect big endian systems (like the PowerPC based Macs), but doesn't affect little endian ones (Wintels and Mactels).

---

### Post by Freddie on 2005-08-19
Isn't the Mac (PPC) bi-endian? I am sure that there is an option in Open Firmware to change it. Still I think that little-endian is quite dumb, why store the least significant byte first?

---

### Post by DJ_Max on 2005-08-19
[QUOTE=Freddie]Isn't the Mac (PPC) bi-endian? I am sure that there is an option in Open Firmware to change it. Still I think that little-endian is quite dumb, why store the least significant byte first?[/QUOTE]
 Yes, the PPC architecture is big-endian, but I don't think you can change it, because thats how the processors works.

---

### Post by Ptero-4 on 2005-08-19
[QUOTE=Freddie]Isn't the Mac (PPC) bi-endian? I am sure that there is an option in Open Firmware to change it. Still I think that little-endian is quite dumb, why store the least significant byte first?[/QUOTE]
 Yes, the PPC is big-endian and that's what makes the PPC choke so bad with some of the QT/KDE functions/features/plugins/applets. It seems that some parts of the QT/KDE API are designed for little-endian CPUs and have endianess issues in big-endian CPUs.

P.d: if you want to see a somewhat annoying but harmless example of this incompatibilities download any version prior to 0.6 of the baghira KDE style/kwindeco combo, install it and use both parts of this theme, you'll see the titlebar buttons washed off and the combo boxes and other controls aren't transparent.

---

