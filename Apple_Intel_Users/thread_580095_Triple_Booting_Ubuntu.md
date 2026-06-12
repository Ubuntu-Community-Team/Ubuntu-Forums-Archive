---
title: "Triple Booting Ubuntu"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by malikk on 2007-10-18
Hello,
I am trying to triple boot ubuntu.
I os x and rEFIt boot loader.  Then i installed xp and left 5 gigs for Ubuntu.
I then put in the live CD (6.06 i think) and follolwed the steps at the wiki.onmac.net for ubuntu and i got to lilo and i got that and installed it and kept following the steps but when i went to teyp lilo into the terminal i believe it said there was a descrepancy like it said there migh be so i reboote  and synced the GPT and MBR (i think it's GPT) with the rEFIt partition tools and restarted and apparently now i should be able to boot into linux.... but i can't.

Can anybody help me try to figure this out?? I don't really know what kind of information you would want me to give you so maybe if you can respond with what you need to help me i can get it for you...Thanks everyone who helps!

---

### Post by ward83 on 2007-10-18
I wound up using Boot Camp instead of rEFIt to partition my hard drive, it was easier to use. However, I don't use any special boot loader, just the mac one. I'm not sure if it will work for triple booting though.

---

### Post by Hatfield on 2007-10-18
Here's my triple-boot using Boot Camp to partition for MacOSx and Vista and GParted to partition for Vista and Ubuntu and using the Grub loader(Boot Camp Menu>"Windows">Grub(Ubuntu or Vista)).  Read all the way through the thread for all my trials and tribulations.  I got an error message that I had to repair.  The outcome is post #23.
[http://ubuntuforums.org/showthread.php?t=571507](http://ubuntuforums.org/showthread.php?t=571507)

And here's a very similar triple-boot that I found only after finishing mine up.  But this guy used the GParted on the LiveCD and I used the separate GParted LiveCD....and I also had to repair my Vista installation.
[http://ubuntuforums.org/showthread.php?t=501832](http://ubuntuforums.org/showthread.php?t=501832)

---

### Post by ivesjd on 2007-10-18
I used rEFIt, which is just an EFI bootloader. What I did though, is installed grub (I think you could do the same with lilo) to my ubuntu partition. And then let windows have the MBR. So now I get the nice gui based boot loader for all three. selecting OSX boots it. Selecting windows boots it. and selecting linux goes to grub so you can select which kernel you want to boot.

---

### Post by malikk on 2007-10-19
well that is what iam trying to do ivesjd but
.... i install lilo and try to set it up but idk it's not showing up in rEfIt and i was wondering if anyone could give me insight on setting it up so rEFIt notices it..... becuase linux is installed it's just lilo isn't pointing to rEFIt and idk why not....

---

### Post by malikk on 2007-10-19
Hatfield i liked your second link except i already have os x and windows installed with rESIt and i'd rather get linux to displa yon that one as well.... 

I have linux installed with a swapfile created... i just need to get lilo point to rESFit and i can't figure it out.... nobody knows a tutorial for that or anything or talk me through it when itell them what i did etc?

---

### Post by cyberdork33 on 2007-10-19
firstly,support for Macs in 6.06 is poor. Try the new gutsy release. The partition sync issues have been solved in feisty onward.

You do not need to install lilo special (unless that is just what you want), the default grub works fine.

IDK what you have done with lilo, but if rEFIt is not seeing it, then something is wrong (obviously). Lilo doesn't point to rEFIt, rEFIt just scans for bootable partitions, and it is not seeing yours for some reason.

---

### Post by malikk on 2007-10-19
I know it is not seeing it Cyber but i am not sure why... i was hopign someone here would have thoughts... i'm not very knowledgable on messing with boot loaders and all.

---

### Post by cyberdork33 on 2007-10-19
> **malikk said:**
> I know it is not seeing it Cyber but i am not sure why... i was hopign someone here would have thoughts... i'm not very knowledgable on messing with boot loaders and all.Try starting over with Gutsy... I think you will have less problems.

---

### Post by malikk on 2007-10-20
Is that the newest release?? and what wiki should i follow then to triple boot (what instructions)

---

### Post by eodchop on 2007-10-20
> **malikk said:**
> Is that the newest release?? and what wiki should i follow then to triple boot (what instructions)

Malik if you have 6.06 that is Dapper Drake. It was released in June of 2006 ie 6.06. Please try using 7.10 which was release in 10/2007. Its name is Gutsy Gibbon.

---

### Post by malikk on 2007-10-22
i wil give it a try... but why would gusty make a difference... is there a specific reason... and should i use the same faq that was made for the 6.06 one?

---

### Post by cyberdork33 on 2007-10-22
> **malikk said:**
> i wil give it a try... but why would gusty make a difference... is there a specific reason... and should i use the same faq that was made for the 6.06 one?
It makes a difference because most of the issues that you have to work around in 6.06 are fixed in 7.10.

you should not need a tutorial. You need to make a partition for Ubuntu. You can do this with Bootcamp, the OSX commandline utility 'diskutil resizeVolume' or you can use gparted. Once you have made space, you can boot the Ubuntu CD, and install to the free space. It sounds like you already left space on your disk anyway (although I might have left more than 5GB).

There may be other issues after installing (such as the Wi-Fi not working out-of-the-box), but there is plenty of information in the forum to get it working. (madwifi, ndiswrapper). I could link you to the appropriate wiki page for your hardware, but you have as of yet not told us what you are trying to install on. A good place to start is the FAQ thread in this forum.
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

---

### Post by malikk on 2007-10-23
my apologies i thought i had already told you what i was installing it on... i'm isntalling on a macbook pro... i have rEFIt on there with mac os x and windows xp already installed, just trying to get linux to install.

---

### Post by cyberdork33 on 2007-10-23
[https://wiki.ubuntu.com/MacBookProGutsy](https://wiki.ubuntu.com/MacBookProGutsy)

There are also various variations of the Macbook Pro (Santa Rosa?) that requires some special attention.

---

### Post by malikk on 2007-10-23
at the moment i jut want it installed then i will worry about the problems.

---

### Post by LeopoldBloom on 2007-10-24
hey malikk,
i don't have much experience with linux, though i was able to triple-boot with 6.06 last year. i just installed 7.10 this afternoon and it was amazingly easy compared to 6.06. listen to these guys and just get your hands on a copy of 7.10 (gutsy gibbon) and you will save yourself a lot of headaches. the only thing i changed during the install process was to have grub installed on the linux partition. i don't know if that's necessary, but the guide i followed did that. i have had no problems with any of my other partitions. good luck!

---

### Post by malikk on 2007-10-24
Hey, 
What guide did you use to install 7.10 ... i have a copy of it...?

---

### Post by cyberdork33 on 2007-10-24
> **malikk said:**
> Hey, 
What guide did you use to install 7.10 ... i have a copy of it...?
I think you are missing the point... there is no guide. Put the Live cd in your machine and boot it... then install it to your partitioned space.

---

### Post by malikk on 2007-10-25
... but i have rESFIt and that won't see linux i hear... and  i did that nad lilo didn't isntall right.. i'm going to try i just don't understand how installing linux... then grub/lilo will then magicaly have linux appear in rESFit

---

### Post by cyberdork33 on 2007-10-25
> **malikk said:**
> ... but i have rESFIt and that won't see linux i hear... and  i did that nad lilo didn't isntall right.. i'm going to try i just don't understand how installing linux... then grub/lilo will then magicaly have linux appear in rESFit
Use Gutsy, 7.10. There is no need for lilo anymore. installing normally will cause an icon to appear in rEFIt with no configuration required. In fact, the linux cd should make an icon appear in rEFIt if it is in the drive when you turn the computer on.

---

### Post by malikk on 2007-10-25
Thanks guys! Triple booting now :)
I did not know the new version 7.10 did away with the need for lilo for triple booting..  Can i ask why it did this (how)?

---

### Post by cyberdork33 on 2007-10-25
> **malikk said:**
> Thanks guys! Triple booting now :)
I did not know the new version 7.10 did away with the need for lilo for triple booting..  Can i ask why it did this (how)? They fixed the bugs that prevented Grub from working.

---

