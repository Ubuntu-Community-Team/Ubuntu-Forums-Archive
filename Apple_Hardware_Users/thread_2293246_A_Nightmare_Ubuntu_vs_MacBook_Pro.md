---
title: "A Nightmare: Ubuntu vs MacBook Pro"
date: 2015-09-03
forum: Apple Hardware Users
---

### Post by bartatubuntu on 2015-09-03
I want to start with Linux for a year now, and really willing to do some computer work. 
But i still need MacOS for one application, MaxMSPJitter. 
I am a computer user and programmer for 16 years now. 
Trying to install and get MacOS and Ubuntu dual boot running on a MacBook Pro 5,1. 


After many threads, tutorials, reviews, ..., now following AGAIN this one: 
[http://ubuntuforums.org/newthread.php?do=newthread&f=328](http://ubuntuforums.org/newthread.php?do=newthread&f=328)

But no way to get Ubuntu running and or installing. 
This after 17 different configurations of bootable life DVD's and 4 different configurations of bootable life USB keys. 

No luck at all!  
My view on Ubuntu (Linux) is becoming black like the screen that i have looked to for hours and hours. 

Can somebody lighten a light? 

specifications:

MacBook Pro 5,1
[FONT=Lucida Grande]2,6 GHz Intel Core i7
[/FONT][FONT=Lucida Grande]8 GB 1600 MHz DDR3
[/FONT][FONT=Lucida Grande]Intel HD Graphics 4000 1024 M
[/FONT][FONT=Lucida Grande]NVIDIA GeForce GT 650M 1024 MB[/FONT]
MacOS Mavericks [FONT=Lucida Grande]10.9.5
[/FONT]
tried to dual boot install: 
Ubuntu 11.04 
now trying my luck with 
Linux Mint 17.2

---

### Post by mystics on 2015-09-03
Did you really try with Ubuntu 11.04 or is that a typo?

Edit: Also, your link is taking me to create a new thread rather than an tutorial.

---

### Post by bartatubuntu on 2015-09-04
No typo, it's 11.04, with live DVD and live USB. 
Also with [COLOR=#333333][FONT=Ubuntu]rEFITt 0.14 i wasn't seeing the Ubuntu boot at all, with [/FONT][/COLOR]refind 0.9.0 i see the [COLOR=#333333][FONT=Ubuntu]Ubuntu boot at least but after that there isn't happening nothing. 
[/FONT][/COLOR]I have tried [COLOR=#333333][FONT=monospace]nouveau.noaccel=1[/FONT][/COLOR][COLOR=#333333][FONT=monospace] [/FONT][/COLOR]and [COLOR=#333333][FONT=Ubuntu]nomodeset and a lot more without any succes. [/FONT][/COLOR]
Mistake in the link, it's this one: [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty)

---

### Post by mystics on 2015-09-04
11.04 has reached end of life, so there's no point in trying to install it. The three currently supported versions, both long term (LTS) and standard, are:

12.04 (LTS): Will reach end of life in 2017
14.04 (LTS): Will reach end of life in 2019
15.04 (standard): Will reach end of life in a few months

So before anything else, you should make a live USB of one of those versions and try that out. Which one you choose is up to you. I personally would go with 14.04 since it will reach end of life last.

---

### Post by bartatubuntu on 2015-09-04
Why is there then no wiki, no review or tutorial that explains how to install 14.04 on a MacBook Pro 5,1? 
And no mentioned of it in the compatibility lists? 
Like: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
The reason why i choose for 11.04 is that it's the only Ubuntu wiki that exist and shows that all features are supported for MacBook Pro 5,1.


Best way to make a live USB on a Mac and for dual boot MacOS Mavericks and Ubuntu on a MacBook Pro 5,1?
I ask this because there are 100 ways on the internet, but non of them that i have tried have worked properly for me. 
For sure the one explained on the Ubuntu site doesn't work at all. 

Thanks.

---

### Post by mystics on 2015-09-04
> **bartatubuntu said:**
> Why is there then no wiki, no review or tutorial that explains how to install 14.04 on a MacBook Pro 5,1? 
And no mentioned of it in the compatibility lists? 
Like: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
The reason why i choose for 11.04 is that it's the only Ubuntu wiki that exist and shows that all features are supported for MacBook Pro 5,1.

I'm sorry. I should have linked to the tutorial: [https://help.ubuntu.com/community/MacBook5-1/Trusty](https://help.ubuntu.com/community/MacBook5-1/Trusty)

It is still a little bit dated (e.g. you should use rEFInd instead of rEFIt). There are other tutorials around the Internet that give some really good advice. 

Here's how to make a live USB on Mac and get to it: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

And here's a tutorial that helped me install things: [http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)

However, I will advise that you should try out the live USB for a little bit before partitioning your hard drive, just to make sure you're willing to make the shift and that it is reasonably compatible with hardware.

> Best way to make a live USB on a Mac and for dual boot MacOS Mavericks and Ubuntu on a MacBook Pro 5,1?
I ask this because there are 100 ways on the internet, but non of them that i have tried have worked properly for me. 
For sure the one explained on the Ubuntu site doesn't work at all.

The link I mentioned above about creating a live USB should work. If it doesn't, then the problem likely exists with the file you downloaded.

Have you checked the MD5Sum? This site has both the ISO file for 14.04.03 (be sure to get the desktop one) along with a file that contains the MD5Sums: [http://releases.ubuntu.com/14.04.3/](http://releases.ubuntu.com/14.04.3/)

Try downloading the 14.04.03 ISO. Once you get it downloaded, be sure to check the MD5SSUMS file and compare it to your result. To get the MD5sum of your ISO, navigate to where it is located in a terminal and type:

```
md5sum "file name"
```

replacing "file name" with the name of the ISO file (don't include the quotes). If there isn't an exact match, then the download didn't work properly. Chances are, if they aren't exact, the difference will be great enough to see right away.

---

### Post by este.el.paz on 2015-09-04
@Bartat:

I have triple boot set up on my 09 MBPro 5,4 . . . now running in the linux partition Rebecca 17.2???  MATE flavor.  I concur with Mystic that 11.04 is "too old" . . . but it's odd that you can't boot a live DVD of anything???  And, then, if you can't boot the Live DVD how are "installing" or trying to install?  I have done a bunch of installs of various linux mint flavors and xubuntu/lubuntu and for the most part had no problem booting a live session.  

There are some details on the install that might require some thinking, but, as Mystic says, first thing is to boot a live session--of course that means you have to have downloaded the "live" iso????

e.e.p.

---

### Post by bartatubuntu on 2015-09-04
@este.el.paz: That's not helping me a lot. I have tested 17 different configurations of bootable iso life DVD's and 4 different configurations of bootable iso life USB keys. 
@mystics: Is there no difference in the wiki's for MacBook or MacBook Pro?  
I have the desktop 14.04.1 ISO file already laying around and will put it now on a USB key with the Ubuntu instruction. 
It's the desktop version "ubuntu-14.04.1-desktop-amd64.iso". I don't see a Mac version at all, like mentioned in the instructions at howtogeek? 


I have never checked the MD5Sum, will do that also. Was never thinking that a fast internet connection could do something wrong with a downloaded file. 

Because never had that problem with downloaded MacOS or iOS system installers. 
Plus it should be very strange that all 21 downloaded iso files, that i already have, are corrupt. 

And i will follow the instructions that you mentioned after testing the live USB: 
[http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)

Keep fingers crossed. :-)

---

### Post by mystics on 2015-09-04
> **bartatubuntu said:**
> @mystics: Is there no difference in the wiki's for MacBook or MacBook Pro?

I'm not sure it will make much of a difference, at least not for machines that old.
  
> I don't see a Mac version at all, like mentioned in the instructions at howtogeek?

Based on my experience, looking for a specific Mac version of the ISO is unnecessary. I've gotten the basic ones for most Ubuntu flavors to work reasonably well on my own computer. 

> I have never checked the MD5Sum, will do that also. Was never thinking that a fast internet connection could do something wrong with a downloaded file.

A vast majority of the time, there shouldn't be a problem on a good high-speed connection. However, there will occasionally be moments. But...

> Plus it should be very strange that all 21 downloaded iso files, that i already have, are corrupt.

*That* is strange.

Still, try out Ubuntu 14.04 and see if it works better, or has that already failed for you?

---

### Post by este.el.paz on 2015-09-04
> **bartatubuntu said:**
> @este.el.paz: That's not helping me a lot. I have tested 17 different configurations of bootable iso life DVD's and 4 different configurations of bootable iso life USB keys. 
@mystics: Is there no difference in the wiki's for MacBook or MacBook Pro?  
I have the desktop 14.04.1 ISO file already laying around and will put it now on a USB key with the Ubuntu instruction. 
It's the desktop version "ubuntu-14.04.1-desktop-amd64.iso". I don't see a Mac version at all, like mentioned in the instructions at howtogeek? 

I have never checked the MD5Sum, will do that also. Was never thinking that a fast internet connection could do something wrong with a downloaded file. 
[http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)

Keep fingers crossed. :-)

@bartat:

Glad I could be of assistance . . . .  You probably don't know how many people I've posted to on threads asking your exact same problem "dual boot on MBPro" and many don't reply at all when I provide detailed instructions to them.  It's not rocket science to get linux running on an Intel Apple, and from my point of view you aren't providing much detail on what you have done to try to "boot" or "install" your 17 - 20 isos . . . .  The more detail the better you could be helped; it's usually something that the operator is doing wrong that causes their problem, it's hard to know what that is sitting 10K miles away.  On my MBPro and on PPC installs I find it "better" to try to boot a DVD, but if USB drive works for you then do that.  It should be that your MBPro is 64 bit, so yes the "amd64" version should work.  I just downloaded Lubuntu 14.04.3 the other day so your version is already "old" and there may be bugs that have been fixed since 14.04.1 came out . . . awhile back.

In terms of "not checking the md5sum" number, it could be possible that your "mirror" is messed up and in the old days like LM 13 you could have a "corrupted" file but it would still install and run fine--that is no longer the case, if the md5 number is off there are "problems" . . . so it is important to check that number before trying to install.

Also, I did read through the "how-togeek" instructions that Mystic linked and they are possibly OK . . . it's showing you how to do "automatic" install, and if it works and installs the system, but doesn't boot it, then you need to do "something else."  But, first thing is, "why is linux not booting live session disk"??

e..

---

### Post by bapoumba on 2015-09-06
If you still need MacOS, why not install VirtualBox and run Linux as a host ? This is what I do.

---

### Post by bartatubuntu on 2015-09-06
Don't like [COLOR=#000000]VirtualBox[/COLOR] and don't need it anymore. 
Ubuntu 14.04.1 is up and running in dual boot. No more ubuntu nightmare! 
Now busy to optimise the Ubuntu system but it's already running smooth. 
@mystics: THANKS to explain clear and well that it is beter to install 14.04.3 then to suffer on older versions. 


And THANKS to show this tutorial: [http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)
Now i will update to 14.04.3 and try out Ubuntu in deep and try to install also Linux Mint to test. 
The one i like the most will become my new Os.  
And when it will be Ubuntu then i buy a Ubuntu phone compatible phone to install that. 

@UBUNTU and Canonical: 
Please clean up the many (not working) wiki's and put CLEAR on your website how to install properly the latest Ubuntu on a MacBook (Pro). 
It's unbelievable how many day's i, and i think many people, have put trying to install Ubuntu while it is possible in 1 hour. 
All the wiki's let people think that on older MacBook (Pro) computers you need to put that particular older Ubuntu system. 

Also one of my mistakes was because this unclear document: 
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

> Convert the .iso file to .img using the convert option of hdiutil e.g.,


hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso
Note: OS X tends to put the .dmg ending on the output file automatically.


I was always taking out the .dmg because how it is described it seams an error from MacOS X that it put the .dmg. 
With keeping the .dmg my Live USB works like a charm. 

Thanks!

---

### Post by PaulW2U on 2015-09-06
> **bartatubuntu said:**
> @UBUNTU and Canonical: 
Please clean up the many (not working) wiki's and put CLEAR on your website how to install properly the latest Ubuntu on a MacBook (Pro). 
It's unbelievable how many day's i, and i think many people, have put trying to install Ubuntu while it is possible in 1 hour. 
All the wiki's let people think that on older MacBook (Pro) computers you need to put that particular older Ubuntu system. 

bartaubuntu, these forums are for users, you won't find Ubuntu/Canonical developers here.

Wiki's can be updated/corrected by anyone with a [Launchpad]("http://launchpad.net") id. Please feel free to make those updates yourself and in doing so help other users.

---

### Post by bartatubuntu on 2015-09-06
Ok, i will check the Wiki's plus Launchpad and see what i can do. 
But it's the honour of mystics and howtogeek.com. 
[http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)

---

### Post by bapoumba on 2015-09-06
> **bartatubuntu said:**
> Ok, i will check the Wiki's plus Launchpad and see what i can do. 
But it's the honour of mystics and howtogeek.com. 
[http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)

There is a contact us link on howtogeek, this site is independent.

---

