---
title: "Macbook Pro Live CD problem!"
date: 2013-03-02
forum: Apple Hardware Users
---

### Post by 77broncodriver on 2013-03-02
I have been trying to make a live cd of 12.10 for the past 2 days, i have downloaded the 32bit, 64bit, and the mac64bit versions and everytime my computer tells me the there is not mountable file. so i burned some anyways through diskutility and nothing comes up on refit other than my mac partition. 

I have dualbooted osx and ubuntu before but its been a couple years but im just at the downloading the cd part and i already having problems! 

Ive been searching for the past 6 hours and havent found any sloved threads on the internet. 

Should i just pay the $20 bucks and wait for a desktop cd strait from ubuntu or is there a simple solution that im just missing here?

Thanks in advance, Evan

---

### Post by GreatDanton on 2013-03-02
Before you order a CD I would try either this: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) , or making [live usb ]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick"). First that come to my mind is that you made data cd instead of burning iso file as image cd.

---

### Post by 77broncodriver on 2013-03-02
I looked at that, I download the .iso, I load it in disk utility, then burn to DVD. Then my computer just says this computer can't read this disk. I've also tried converting to .img. Why can't my computer mount the iso? It seems like a lot of people are having this problem

---

### Post by 77broncodriver on 2013-03-04
alright i dont know how people on these newer macs are getting ubuntu to work? ive tried ever .iso form of 12.04 and 12.10 on ubuntus website and none of them will "mount". I try and burn them on a dvd anyways through disk utility, puting the .iso on the left side then buring it onto a dvd. I know thats the right way of doing it, but the problems before that, the .iso just isnt working, its not readable by my computer. i have a newer macbook pro, its version 9,1 running 10.8.2 someone on here must have some info on this. i see it all over the internet that people have this problem but non of them are solved. im about to give up, i dont want to spend the money on a live cd from ubuntu.

---

### Post by 77broncodriver on 2013-03-04
[IMG]http://i777.photobucket.com/albums/yy55/dirtbiker77/ScreenShot2013-03-04at12203AM.png[/IMG]



[IMG]http://i777.photobucket.com/albums/yy55/dirtbiker77/ScreenShot2013-03-04at12236AM.png[/IMG]

---

### Post by 77broncodriver on 2013-03-04
here is what shows up when i click on the .iso and also when i put the cd in after i burn it. also refit doesnt recognize it either

---

### Post by AestheticArson on 2013-03-05
**[COLOR=#000000][77broncodriver]("http://ubuntuforums.org/member.php?u=1794842"), have you tried rebooting your Macbook with any of the burned Live CD's you created and holding down the "option" key while your Macbook is booting up?[/COLOR]**

---

### Post by montgomeryj on 2013-03-06
I have a macbook pro and had some difficulty burning live CD's before.  The hack that I found to get around that was to create an Ubuntu virtual machine (using either virtual box or VMware), mounting the DVD drive to the virtual machine and then burning the live DVD that way.  It is a little bit of a work around, but I've been easily able to create live DVD/CD's.  When you create the live CD/DVD just make sure that you have the ISO file that you want to turn into a live CD/DVD on the virtual machine, otherwise you can only create a live CD/DVD of the version of Linux that your virtual machine was created from.

---

