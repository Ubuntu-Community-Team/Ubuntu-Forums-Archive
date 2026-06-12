---
title: "ibook G3 700Mhz dual usb Install issues"
date: 2015-05-02
forum: Apple Hardware Users
---

### Post by Steven_Stroud on 2015-05-02
Hey all Linux newb here.... fair warning lol.

I read an article about linux on old macs that inspired me to dig out my old ibook G3. I'll be honest here the only distro I've had install and function was Mint 11. I played around with it and got my old Airport card up and going and was fairly pleased with its performance... *fairly*. But me being the tinkerer I am wanted to try other distros and see what kind of trouble I could get into lol (plenty of course). I read another article on Ubuntu MATE, so I downloaded a few different flavors (Ubuntu MATE 14.04.2 and 15.04, Lubuntu 14.04.2 and straight up Debian 8.0.0)

So I started with 14.04.2 and booted and was greeted with a black screen *RAWR* So I booted with yaboot parameter video=radeonfb:1024x768-32 and it worked. Installed like normal and then rebooted and of course greeted with the same "black screen of death". Tried booting with the same yaboot parameter and that didn't work. Tried a few other parameters as well (video=ofonly, radeon.agpmode=-1,  Linux 1 video=ofonly nosplash, radeon.modeset=0, video=radeonfb:1024x768-32@60) and a combo of all those with no "love".

So I went ahead and tried Lubuntu and same results... So lastly I saw another cool article here 
[http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-i.html](http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-i.html) 
which seemed nice because it was a tutorial on how to do it and would be using "Openbox" which seemed pretty nice imo (lightweight etc). I went thru the install and everything went well until the reboot... You guessed it BLACK SCREEN... sorry didn't mean to yell lol.

I like to learn on my own I'm just wired that way lol. But I'm afraid I'm at my wits end here. I've read so much that I can't remember what I've even read anymore... thank god for bookmarks and notes.... haha that sarcasm, at least the notes part... I have plenty of bookmarks lol.

I think the main problem I have here is the dreaded "black screen of death" So if anyone out there could give me a clue as to what to do about that, that would be nice and you would be my new best friend forever lol. Ohhh yeah the other annoyance is how long it takes to boot from DVD... omg it takes FOREVER... so long that I sometimes forget what I had booted into the live cd for, for example. Tho it wouldn't be big deal if I didn't have to boot from a DVD so much (no this poor old laptop wont boot from USB grrr). It maybe because I'm using Dual Layer DVDs to burn these distros (all I have on me atm) I know it's kind of a waste :/ I guess I've ranted long enough lol. So in closing, here is my hardware info

ibook G3 700Mhz Dual USB, 256MB RAM, DVD Combo drive, and 30GB HDD
[http://www.everymac.com/systems/apple/ibook/specs/ibook_700_14.html](http://www.everymac.com/systems/apple/ibook/specs/ibook_700_14.html)



Many, MANY thanks in advanced,
Steven

---

### Post by dand1972 on 2015-05-03
radeon.modeset=0 should've worked to give you a screen.  The parameter "nomodeset" achieves the same thing, so type in "Linux nomodeset" with no other parameters and see what happens.

BTW, my bug report for the black screen on your identical machine is here:

[https://bugs.freedesktop.org/show_bug.cgi?id=90220](https://bugs.freedesktop.org/show_bug.cgi?id=90220)

---

### Post by Steven_Stroud on 2015-05-03
Thanks for the tips dand1972! I'll make sure and check out that big report.
I'll give it a shot when I get home and report back my findings either tonight or tomorrow.
Honestly I may or may not of used that parameter. I can barely remember. This time around I'm going to actually note every step I take so if I need the info I don't have to hunt for it and if anything I can help others with the same issue(s)

---

### Post by rsavage on 2015-05-04
> **Steven_Stroud said:**
> 
So I started with 14.04.2 and booted and was greeted with a black screen *RAWR* So I booted with yaboot parameter video=radeonfb:1024x768-32 and it worked. Installed like normal and then rebooted and of course greeted with the same "black screen of death". Tried booting with the same yaboot parameter and that didn't work. Tried a few other parameters as well (video=ofonly, radeon.agpmode=-1,  Linux 1 video=ofonly nosplash, radeon.modeset=0, video=radeonfb:1024x768-32@60) and a combo of all those with no "love".

You shouldn't of had a black screen with the live ISO... are you sure you had this?

There are two black screen problems, dan is describing one that seems to occur with your model of ibook under kms. I think maybe there is a problem with phantom outputs or the wrong connector table or something like that... there are options you could try to disable stuff to try and fix it, but the simpler thing is to use 12.04 until you find your feet in Linux.


> 

I think the main problem I have here is the dreaded "black screen of death" So if anyone out there could give me a clue as to what to do about that, that would be nice and you would be my new best friend forever lol. Ohhh yeah the other annoyance is how long it takes to boot from DVD... omg it takes FOREVER... so long that I sometimes forget what I had booted into the live cd for, for example. Tho it wouldn't be big deal if I didn't have to boot from a DVD so much (no this poor old laptop wont boot from USB grrr). It maybe because I'm using Dual Layer DVDs to burn these distros (all I have on me atm) I know it's kind of a waste :/ I guess I've ranted long enough lol. So in closing, here is my hardware info

ibook G3 700Mhz Dual USB, 256MB RAM, DVD Combo drive, and 30GB HDD
[http://www.everymac.com/systems/apple/ibook/specs/ibook_700_14.html](http://www.everymac.com/systems/apple/ibook/specs/ibook_700_14.html)


You can boot from USB, but that ram is not a lot for a live ISO....I didn't think it would work with so little.

---

### Post by Steven_Stroud on 2015-05-04
I think you are right about about the black screen. It wasn't until post install that I received the black screen under 14.04 if memory serves me right. I also think you're right about getting more "familiar" with Linux in general before I venture to far. I get MintPPC 11 to work without a problem, which like 12.04 is just another Wheezy based distro.. I could be wrong. I'll just keep messing with it until I get it right, being as this is just a play toy (the ibook G3) and not worried about getting it up and running full-time in any hurry. Thanks a bunch for help and input. I will get this... it's only a matter of time :)

---

### Post by rsavage on 2015-05-04
The card seems to have been having problems for years ([http://ubuntuforums.org/showthread.php?t=1539615](http://ubuntuforums.org/showthread.php?t=1539615) ) - what I don't understand is why kms has to be disabled (modeset=0) since it should already be due to other reasons....

---

### Post by rsavage on 2015-05-04
....and other people seem to be able to use KMS with, i think, with the same machine - [https://bugs.freedesktop.org/show_bug.cgi?id=55745](https://bugs.freedesktop.org/show_bug.cgi?id=55745)

So what causes the error 

[drm:drm_calc_timestamping_constants] *ERROR* crtc 14: Can't calculate constants, dotclock = 0!

which is presumably the problem?

---

### Post by rsavage on 2015-05-04
Similar [https://forums.gentoo.org/viewtopic-p-7128758.html](https://forums.gentoo.org/viewtopic-p-7128758.html)

---

