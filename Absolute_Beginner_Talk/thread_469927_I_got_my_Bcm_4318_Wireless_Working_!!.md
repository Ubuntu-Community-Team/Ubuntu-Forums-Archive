---
title: "I got my Bcm 4318 Wireless Working !!"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-10
I should apologize upfront for posting this shameless post of self-congratulatory glee.  But I couldn't believe it.  I explain how I did it below, in hopes that it may help another beginner. 

I've been in Ubuntu 3 weeks maybe? Anyways, let me expound from a beginner's point of view how confusing this can be. I may have literally lucked out in getting this right. 

On one hand, there are several ways put before you to download a package that has the driver(s); then the point of WPA-Supplicant jumps out at you - "Do I need that?" "How would I install THAT?" 

Different choices of terminal scripts get dangled in front of you...then the statement always arrives on time: "But if you want the easier way, just use Ndiswrapper".  Your head is spinning at this point. 

And in this case today, as it shows up in many given online directions, there's that loooong string of a complicated procedure with explanations followed at the bottom by: "Or you can just run this command line"

It's just funny how complex it can seem at times. So now I'll show what worked in case it helps someone. 

Here goes: I was here at the Ubuntu tutorial:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty) 

First let me point out how important it was that I read the introduction at the top for the different choices offered and why.  It jumped out at me when it explained this: If you get an error called 43xx_microcode on reboots before the X server starts, then installing the native driver will work for you and will correct this error. (I'm paraphrasing) THAT gave the confidence to install the native driver and not feel that I needed to lean on Ndiswrapper.  So here's what I did:

1) I downloaded this to my desktop, although I think the third step did this again automatically:
[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)

2) I ran this command: sudo apt-get install bcm43xx-fwcutter

3) Then I ran this: sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

That's it!! I used Network Manager (already defaulted in Feisty) and clicked on the network I wanted and it connected !!!

Also, I have WPA Personal encryption and it went through with no problem; No WPA supplicant was necessary to install. 

Many Thanks and I hope this helps someone,....Frank B.

---

### Post by johnny4north on 2007-06-10
congratulations, thanks 4 sharing your progress with us:).  its nice to share:D

---

### Post by Mazza558 on 2007-06-10
Did you try the deb file that is suggested in a big HOWTO thread? Because that method is WAY easier :D

---

### Post by Brightbelt on 2007-06-10
Thanks for that tip.... 
Can you link me to that thread ? I've looked but can't find it. 

Thanks, Frank B.

---

### Post by Baelfael on 2007-06-10
Hey, congratulations! I have a BCM4318 card as well, (or something close to that) and it took me ages to get it to work. I was so happy when I got it to work.

---

### Post by Brightbelt on 2007-06-10
Btw, I think I had tried installing a Bcm43xxFirmware.tar.gz file earlier today and it didn't get me connected, but it perhaps put something in the right place for what I did just now.

Thanks, Frank B.

---

### Post by Brightbelt on 2007-06-10
Thanks for all the support! It's really nice to have here,....Frank B.

---

### Post by borimrr on 2007-06-29
Same here. Got it working on my Compaq v2000 in like 3 steps. It was a pain when I didn't know how to do it. Know I might go and try it with Gentoo.

---

