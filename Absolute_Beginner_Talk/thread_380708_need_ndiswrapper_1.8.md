---
title: "need ndiswrapper 1.8"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by thejones on 2007-03-10
im trying to install my broadcom wireless card and im looking for a copy of ndiswrapper 1.8.

every search i do for it turns up nothing but post about it and dead links. i read somewhere that it is on the 6.10 disk, but add/remove didnt see it. or am i doing something wronge?

does anyone have a good link so i can download it?

thanks,
jones

---

### Post by honns on 2007-03-10
if ur looking for 1.8, go to System -> Admin -> Synaptic Package Manager. Once you get that open, search for ndiswrapper and install the ones that say 1.8

I would recommend installing 1.38, which is the latest version (I dont know if you need the specific version for the installation)  That version can be found here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

follow the instruction they give and it should work well

I tried to use the 1.8, it has an issue with the version command but other than that seemed to work, but when i installed 1.38 there were no issues

good luck

---

### Post by msak007 on 2007-03-10
> **thejones said:**
> im trying to install my broadcom wireless card and im looking for a copy of ndiswrapper 1.8.

every search i do for it turns up nothing but post about it and dead links. i read somewhere that it is on the 6.10 disk, but add/remove didnt see it. or am i doing something wronge?

does anyone have a good link so i can download it?

thanks,
jones
You shouldn't need to look anywhere external as it is already in the repositories. As honns said, you can use Synaptic to search for and install it. The package name is** ndiswrapper-utils-1.8**. The easiest way would be to type

```
sudo aptitude install ndiswrapper-utils-1.8
``` into a terminal, so whichever method you are comfortable with should work.

EDIT: Sorry, I assumed that since you were online you had some sort of wired connection to get the package online. Follow aysiu's instructions to get the package off the CD.

---

### Post by aysiu on 2007-03-10
It is on the 6.10 disk (on either disk--Alternate CD or Desktop CD).

Type these commands into the terminal: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by thejones on 2007-03-10
thanks guys, ill give it a try.

btw, the only reason im online at the moment is because im dual booting xp untill i get linux nailed down. 

im learning to swim, but i still need the arm-floaties. :D

---

