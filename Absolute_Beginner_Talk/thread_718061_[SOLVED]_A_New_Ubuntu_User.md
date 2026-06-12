---
title: "[SOLVED] A New Ubuntu User"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Johnathannn on 2008-03-07
HI! Well, I've recently installed Ubuntu and it's pretty nice on my laptop... I don't really like that I can't use programs like Nero 8, PowerISO, ETC... however, Ubuntu is a REALLY fast and secure OS. I'm completely new to Linux, and I've gotten it to install properly on my Acer Aspire 500 computer, but I have absolutley not clue on how to get connected to the internet!!! I'm pretty sure that Ubuntu can't find the ethernet card that's included in my laptop, but I don't know how to get the OS to find it, or how to install it! I'm so confused, but if anyone has an Aser Aspire 500 Laptop with an AMD 64 processor, 448 mb of RAM and an SIS video card, can anybody tell me how to get wireless connection to the internet? Thanks a bunch for anyone's response! Also, since you can't use programs like Nero 8, is there any other programs such as CD/DVD burning that is compatible for linux...>? So basicly my question is... how can I get a wireless connection to my internet, on my acer apsire 500 laptop!?

Johnathannn

---

### Post by PinkFloyd102489 on 2008-03-07
Ubuntu does CD/DVD burning by default. Under Places => CD/DVD Creator.

---

### Post by JoshuaRL on 2008-03-07
I would suggest either K3b for CDs, and K9 for DVDs.  Those both work well.

An alternate for K3b is Brasero.

---

### Post by kwacka on 2008-03-07
CD/DVD burning try brasero or K3B

PowerISO - use acetone2iso, or gmount iso or just type "sudo mount -o loop disk1.iso /mnt/iso"  (you'll need to create the directory /mnt/iso first).

For other alternatives see:  [http://www.linuxalt.com/](http://www.linuxalt.com/)   or [http://www.osalt.com/](http://www.osalt.com/)   gives open-source alternatives for linux, windows and mac.


For wifi type 'lspci' and you'll find a list of cards installed. Search here for advice on your particular card.

Unfortunately many manufacturers don't want linux users to use their cards so if you're unfortunate to have one of these you've got 2 choices - use ndiswrapper which cobbles the windows drivers, or buy the driverloader from [www.linuxant.com](www.linuxant.com).

---

### Post by Daveth on 2008-03-07
in the immediate absense of any kindly Aser uses posting, check out

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

for a bit of step by step trouble-shooting

---

### Post by Johnathannn on 2008-03-07
Hey everyone! Well, I just googled what to do for a few minutes, it brought me back to this site and I didn't use ndiswrapper, but I used something that was on a forum... forget which one, but it was a package and worked fine! THANKS ANYWAY! :) And thanks for the cd/dvd tools HAHA!

Johnathannn

---

### Post by ugm6hr on 2008-03-07
Regarding wifi...

Post the output from the following (NB case sensitive!)
```
lshw -C network
lspci
```

What encryption do you use on wifi network?
Do you have wired (i.e. ethernet) network connection available for now?

---

### Post by steveneddy on 2008-03-07
> **Johnathannn said:**
> Hey everyone! Well, I just googled what to do for a few minutes, it brought me back to this site and I didn't use ndiswrapper, but I used something that was on a forum... forget which one, but it was a package and worked fine! THANKS ANYWAY! :) And thanks for the cd/dvd tools HAHA!

Johnathannn

So, what did you do to fix this? We all share issues and problems and how to fix them.

So what was your fix?

---

### Post by x05 on 2008-03-07
> **Johnathannn said:**
> Hey everyone! Well, I just googled what to do for a few minutes, it brought me back to this site and I didn't use ndiswrapper, but I used something that was on a forum... forget which one, but it was a package and worked fine! THANKS ANYWAY! :) And thanks for the cd/dvd tools HAHA!

Johnathannn

Yeah seriously, share. I'd like to know how you got it working. Teach and learn.

---

### Post by Johnathannn on 2008-03-08
Hey everyone! Well I have wireless internet working perfectly, and I just looked on this sticky... [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)... I used the directions that he said for this option..." Use the native bcm43xx driver. This driver is open source and included with the kernel. It can not run at any speed higher then 11mbps, is some what flaky, and supports promiscuous mode. Requires user to be somewhat close to the access point. Is a bit easier to install.". After I downloaded that file (Check the forum for the link) I just double clicked it, installed it and I had my wireless access points detected, just like that! I'm pretty sure it sais something about the speed of my internet connection being lower, but I haven't noticed any difference! Hope that helped everyone! Thanks Guys!:)

Johnathannn

---

### Post by Forrest Gumpp on 2008-03-08
You read a Sticky?

What a good boy!

Don't you dare tell those other bad boys which Sticky it was.  Make them search for themselves!:)

---

### Post by Johnathannn on 2008-03-08
Well... it's not too hard to read things on this forum lol... Don't congradulate me, I'm pretty sure everyone knows how to read stickys hahaha!

Johnathannn

---

