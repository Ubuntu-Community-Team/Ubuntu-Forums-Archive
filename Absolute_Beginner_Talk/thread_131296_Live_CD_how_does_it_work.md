---
title: "Live CD? how does it work"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by Donderwolkje on 2006-02-16
Hey hello,

I just got this neat looking two cd package with an install and a liv ubuntu cd. but it doesn't come with any findable documentation.

just configure your mac to boot of the cd-drive!! hey what? please tell me how.

ok after calling half an hour browsing the ubuntu site, if figured it out: hold "C" while booting. why keep this info a secret.

ok so ubuntu boots, and i see a black screen that looks like a dos-shell with some text and the whole thing waits. i press enter ->error. then i dunno why, just guessing i typed live at the command line, and woeps... its started again.
AGAIN my question is WHY keep this info a secret? why not put a txt file or whatever on the disk on the site explaiing this to dummies. that would be nice.

so then the installation goes along clicking through options... wait installation... i thought this wasn't going to install anything. and yes ofcourse: it can't find the cd drive...? what? This program is obviously running from a cd-in the cd drive in my powerbook saying it can't find the cd drive??? talk about existential problems there. i tried all options available (none/cdrom and yes/no), but to no avail.

so far ubuntu, i can't say this impresses me.

I followed a little Unix training at work, and really liked it, like the idea of an open source free platform, but why can't it be simple, 

sorry just ranting here, i was just shocked to find out it.

please feel free to point me out what i did wrong, i want to learn and am eager to try this out.

---

### Post by SMF on 2006-02-16
lol

I hear you and I too am a new kid on the block.
I also tried a live DVD of Linux XP Desktop 2006 and I only was able to get it to run once and then when I rebooted it hung on the grub and I was unable to do anything more with that but I did not like Linux XP it was too slugish but I got bit by Linux none the less and I wanted more so after doing a lot of reading and just comparing and hearing what others had to say they suggested kaponix something like that also they suggested Mandriva and SUSE but I did an online test and in those suggestion was to get a copy of ubuntu and I felt that ubuntu looked right for me and it was. I said the hell with the liveDVD. I want the installation CD! I want to install Linux on my computer NOW! and so I did and so here I am and I am so happy. I am adicted and very excited. Its like a new little world. Sure I was scared but I have messed up my computer before. I never back up nothing :p 
Again I hear you and I know where you are comming from. Before I finaly got enough courage to install the ubuntu box on my system I did a google and had about 25 different pages open and was reading here and there and anywhere and then when I thought I was ready, I dove right in. I honestly hope you get feeling I have of joy and satisfaction I have right now. I am bit of lamer at best but I try to learn what I can.

God bless and good luck. Do not get discouraged. There are many people here who are more than willing to help.

Peace and I welcome you from one n00b to another:mrgreen:

---

### Post by AndyCooll on 2006-02-16
Difficult to know exactly why the errors are occurring for you. What specifications are your laptop?


Since I'm not using a MAC I can only relate my pc experience. I had call to use the Live CD for the first time last night in order to repair a faulty boot-up process. My pc has the CD drive as it's first boot option and when I installed the CD it duly found the drive and kicked into action, asked me a few questions and pretty soon I had a working Ubuntu desktop. I must admit my pc's specifications are not top of the range (though it is less than a year old)

From there I was able to mount my faulty drive, make some changes to config files and resolve the problems.

---

### Post by Donderwolkje on 2006-02-16
well, it's just an out of the box 15 inch powerbook, 1.67gh, 3 months old, hires, superdrive.

i really like to give this a try so i took the live disk to work, and tried it again with some real nerds watching over my shoulder. Luckily this proved i'm not THAT stupid. hehehe it stalled at exactly the same place: Cannot recognise your cd-rom drive: this from a program running from the cd/dvd drive.

so i'm guessing this is not going to work.

---

### Post by Donderwolkje on 2006-02-16
but where are my manners, 

thanks for the replies

---

### Post by linear on 2006-02-16
Have a look at this:
 
[http://ubuntuforums.org/showthread.php?t=84403](http://ubuntuforums.org/showthread.php?t=84403)
 
People have reported success with the installer on DVD, bug supposedly fixed in Dapper.

---

### Post by alfonz on 2006-02-16
> ok after calling half an hour browsing the ubuntu site, if figured it out: hold "C" while booting. why keep this info a secret.

Thats how your system boots from CD rather than an HDD, it is an Apple proprietary architecture and has nothing to do with Ubuntu's live CD.

If I am wrong then pls correct me :)

---

### Post by Donderwolkje on 2006-02-17
hey linear, 

thanks,

too bad there isn't any solution.

---

### Post by aysiu on 2006-02-17
[QUOTE=Donderwolkje]
just configure your mac to boot of the cd-drive!! hey what? please tell me how.

ok after calling half an hour browsing the ubuntu site, if figured it out: hold "C" while booting. why keep this info a secret.[/quote] It's not Ubuntu. It's Mac. Why does *Apple* keep it a secret? There's nothing special on the Ubuntu CD that requires you to hold down **C** while booting. In fact, I use a natively Windows PC, so I *don't* hold down **C**--I just configure my BIOS to boot from CD-ROM.

See the attached screenshot for more details. It's an Apple thing, not a Ubuntu thing.

> 
ok so ubuntu boots, and i see a black screen that looks like a dos-shell with some text and the whole thing waits. i press enter ->error. then i dunno why, just guessing i typed live at the command line, and woeps... its started again. Sounds as if you got a bum CD. This you can blame Ubuntu on.

> 
so then the installation goes along clicking through options... wait installation... i thought this wasn't going to install anything. and yes ofcourse: it can't find the cd drive...? what? This program is obviously running from a cd-in the cd drive in my powerbook saying it can't find the cd drive??? talk about existential problems there. i tried all options available (none/cdrom and yes/no), but to no avail.

so far ubuntu, i can't say this impresses me. A bad CD. That's what I think. Even though [the vote seems to be against me](http://www.ubuntuforums.org/showthread.php?t=113925), I'm still convinced Ubuntu tends to have more badly burned CDs or corrupted ISO images than other Linux distributions--yes, even the "official" ones sent from Canonical can be bad.

The operating system isn't bad. I've used it on my wife's Powerbook--it's excellent.

The problem you had was a combination of:

1. Apple not making it obvious how to boot from CD
2. Canonical shipping you badly burned CDs.

---

