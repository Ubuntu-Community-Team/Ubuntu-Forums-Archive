---
title: "ipw2200 install for begginers to linux"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by AsburyPark on 2005-07-03
How can I get my wifi to work?  I need a beginners explination, I looked at the post in tips & tricks, but I got lost after "hello"  Where do I download the drivers, what is the proper way, how to install, ect.... ](*,)

---

### Post by Agamemnon on 2005-07-03
[QUOTE=AsburyPark]How can I get my wifi to work?  I need a beginners explination, I looked at the post in tips & tricks, but I got lost after "hello"  Where do I download the drivers, what is the proper way, how to install, ect.... ](*,)[/QUOTE]

Where is that post?

---

### Post by AsburyPark on 2005-07-03
[QUOTE=Agamemnon]Where is that post?[/QUOTE]

[HERE](http://www.ubuntuforums.org/showthread.php?t=26623) 

If you figure it out, let me know the trick!

Good luck!

---

### Post by mohaham on 2005-07-03
ipw2200 works out of the box in Ubuntu Hoary, 
u dont have to install any additional stuff to get it to work..
Only if you need wpa support then you have to install additional packages..

---

### Post by AsburyPark on 2005-07-03
[QUOTE=mohaham]ipw2200 works out of the box in Ubuntu Hoary, 
u dont have to install any additional stuff to get it to work..
Only if you need wpa support then you have to install additional packages..[/QUOTE]

how would I go about installing additional packages?  What packages would i need to install? I actually have a ipw2915, and it did't work after install, or after I upgraded the kernel.   :?

---

### Post by poofyhairguy on 2005-07-03
[QUOTE=AsburyPark]how would I go about installing additional packages?  What packages would i need to install? I actually have a ipw2915, and it did't work after install, or after I upgraded the kernel.   :?[/QUOTE]


As a general rule...if a wireless device doesn't work out of the box with Ubuntu...its needs ndiswrapper. Currently this is not easy to do....but is possible:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

[https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29)

---

### Post by mohaham on 2005-07-04
there are 2 ways to install this..
using ndiswrapper as poofyhairguy suggested
(or)
using the open source firmware as explained in this HOWTO
[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=2200](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=2200)

if you dont need wpa u can stop at the "Now we have to download and install the wpa_supplicant package" step in the above HOWTO

---

