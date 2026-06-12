---
title: "2 problems.."
date: 2007-10-07
forum: Apple Intel Users
---

### Post by ikker666 on 2007-10-07
hi..
yesterday i've installed mac os x tiger...
now..its a triple-boot with ubuntu and xp..
i can go on the os x BEFORE i installed ubuntu and xp.. now on my bootscreen the os x is gone..
thats my first prob. ...

my second is ... i can't g oon the internet when is was on os x... 
(btw. on my ubuntu i can... but not on xp and os x)

i think i havent got drivers.. :s

please help..

greadz kristof):P

---

### Post by ikker666 on 2007-10-07
btw... i'm on a notebook (toshiba satellite) i its wireless...

---

### Post by pxwpxw on 2007-10-07
> **ikker666 said:**
> btw... i'm on a notebook (toshiba satellite) i its wireless...

What is your computer?

---

### Post by ikker666 on 2007-10-07
toshiba satelite 1.6ghz i think... 512ram 80g HD...
intel... thats all i know..

---

### Post by dmber on 2007-10-07
you're booting os x on a toshiba?

---

### Post by cyberdork33 on 2007-10-08
This is not that crazy guys.... We probably cannot help you here, as this is a support forum for Apple Intel Hardware with Ubuntu. Try going to the Hackintosh forums or InsanelyMac.

---

### Post by ikker666 on 2007-10-09
hey guys..

i finaly had my triple-boot.. :D:D jeej..!!
but still no internet...
 for the people ho wanna know how...

in a terminal(ubuntu):
sudo gedit /boot/grub/menu.lst
 add... below..

title MacOS 10.4.8
rootnoverify (hd0,4)
makeactive
chainloader +1

the (hd0,4)
stands for..

the "0" is the HD..
the "4" is the partision..

just a know how for you ;)..

but no internet.. :s someone??...

---

### Post by cyberdork33 on 2007-10-09
> **ikker666 said:**
> but no internet.. :s someone??...
This is likely hardware dependent...

---

### Post by ikker666 on 2007-10-09
but i installed os x INTEL.. :s

---

### Post by cyberdork33 on 2007-10-09
> **ikker666 said:**
> but i installed os x INTEL.. :sThat is not the issue, the issue that the Intel version of OSX does not support your hardware. Checkout the forums I mentioned. They are much better equipped to handle the questions you are asking.

---

### Post by ikker666 on 2007-10-10
k.. thx..

---

### Post by ikker666 on 2007-10-10
hackingtosh sucks... you mean hackingtosh.org hé?? their are a cople of 10 posts.. :s

---

### Post by cyberdork33 on 2007-10-10
[http://www.hackint0sh.org](http://www.hackint0sh.org)
[http://www.osx86project.org/](http://www.osx86project.org/)

---

