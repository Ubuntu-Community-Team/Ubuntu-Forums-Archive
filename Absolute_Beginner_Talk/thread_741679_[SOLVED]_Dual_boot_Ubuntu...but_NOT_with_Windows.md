---
title: "[SOLVED] Dual boot Ubuntu...but NOT with Windows"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by SaddleTramp on 2008-04-01
Howdy Ya'll, I'm back again.  Thought I'd post a new thread since I got some things figured out from my other one.

FYI...Have seen others on here that couldn't get Vista partitions to shrink for Ubuntu install...News Flash...Vista won't.  At least on most proprietary systems such as HP and apparently most that come with OEM "you have to create recovery CD".  I was referenced to look in BIOS for a setting that dealt with this problem.  I've been working with hardware over 30 years. I'm familiar with most BIOS (i.e. Award, AMI, and on and on). I've yet to see anything in there that has anything to do with it.  My best guess (or opinion) is that they've embedded the chipset somewhere with that feature.  I slicked Vista from my HP Pavilion a1700n desktop, repartitioned the Samsung 250Gb HDD removing the recover partition so I have the whole partition back. On bootup, I STILL get the HP screen with all the options (i.e. Boot sequence, setup, recover).  Only other option left for me was to get a 2nd HDD to install Ubuntu to to run both Vista and Ubuntu. However, after thinking about this for a while it got me aggrevated enough to decide to slick Vista and go with Ubuntu all the way.  BTW, I tried every way mentioned on here and a few other forum sites to shrink Vista's partition with no joy. So there ya go. Hope to save some of the rest of ya from wastin' your time.

My proplem now is that I need to know how to set up my partitions to dual Ubuntu 8.04 64 bit and Ubuntu Ultimate 1.7 32 bit.  As I said, I installed a 2nd HDD, so now I have a Samsung SATA 250Gb (came with computer) and an added WD SATA 320Gb.  I know this sounds like it ought to be easy, and I could prolly handle it with just what I've read on here had I kept Vista.  What I can't quite wrap my mind around is how to install the 2nd Ubuntu as far as the Mount Points go. 

Ex.  Ubuntu Hardy:
dev/sda:      (Samsung 250Gb)
dev/sda1          '/'
dev/sda2         /home
dev/sda3         /swap

dev/sdb:      (WD 320Gb)
dev/sdb1         ??
dev/sdb2         ??
dev/sdb3         ??

where would I put Ultimate??  what would the mount points be ??  and would it be better to use a /boot ??

Thanks for takin' the time to read this and all assistance/advice offered,
S'Tramp



Update:  I stand corrected.  I've just been informed that there is a setting in the BIOS of some Acer & Dell computers that controls the partition shrinking capabilities.  Individual has an HP identical to mine at his office he is going to check tomorrow since he's familiar with this particular setting to let me know it's there and if there, I just didn't recognize it.  Will update when he gets back with me.

---

### Post by zvacet on 2008-04-01
Ultimate 1.7 is unofficial release based on Gutsy (more apps added),so I think(and I can be wrong) you should install it as any Ubuntu release.Basicly partition your second drive as you do with first one.

---

### Post by SaddleTramp on 2008-04-01
> **zvacet said:**
> Ultimate 1.7 is unofficial release based on Gutsy (more apps added),so I think(and I can be wrong) you should install it as any Ubuntu release.Basicly partition your second drive as you do with first one.
So you think putting Hardy on one drive and Ultimate on the other would work then?  Will try that and see what happens.
Thanks zvacet.
S'Tramp

---

### Post by northern lights on 2008-04-01
> **SaddleTramp said:**
> So you think putting Hardy on one drive and Ultimate on the other would work then?

Will work out of the box. Simply run one setup after the other, the second will alter GRUB, but not delete the existing entries. This is only not the case if you were to install Windows (XP or Vista, or any other for that matter) on a machine with an existing Ubuntu installation...

---

### Post by SaddleTramp on 2008-04-01
> **northern lights said:**
> Will work out of the box. Simply run one setup after the other, the second will alter GRUB, but not delete the existing entries. This is only not the case if you were to install Windows (XP or Vista, or any other for that matter) on a machine with an existing Ubuntu installation...
Thanks Northern, but I tried that (although there is the strong possibility I did something wrong :-k) ) What's throwing me off is the mounting points (to use to windows and labeled drives as C: D: E: etc. And extended partitions were no problem for me in Windows.)
So if I install, let's say Ubuntu 8.04 Hardy **64bit,** as:

dev/sda                     (Samsung 250gb SATA)
dev/sda1        '/'          (10gb partition for Hardy system)
dev/sda2        /home
dev/sda3        /backup
dev/sda4        swap

then when I install Ultimate 1.7 **32bit**, upon getting to gParted, it would take me thru the same procedure as it did with the Hardy install & I would still have to assign the mounting points as I did in Hardy ?? and would it let me then install Ultimate in a 15gb partition behind Hardy ??

If I can get Ultimate installed after Hardy, I was going to partition my 2nd drive this way:

dev/sdb                   (WD 320gb SATA)
dev/sdb1      /games
dev/sdb2      /movies
dev/sdb3      /backup
dev/sdb4      swap

Keep in mind that I'm installing  64bit & 32bit versions of Ubuntu. So, if they won't work properly on the same drive, I can install each on a different drive (which may be a good idea anyway and if I have a drive crash I already have a setup on the other to fall back on and recover.

I appreciate ya'lls time on this very much.  But I pretty much need step-by-step directions for the way I need to do this.  All the reading I've been able to find on dual booting all refer to Windows/Ubuntu installs.  Couldn't find anything to install 2 Linux OS's.

Thanks again,
S'Tramp

---

### Post by zvacet on 2008-04-01
Yes you need to assign mountpoints,and you can install Ultimate on same drive with Hardy.Systems will not interact with each other like they don´t when you dual boot with windows.If you choose to install that way you can dedicate your second drive to your files.

---

### Post by SaddleTramp on 2008-04-01
> **zvacet said:**
> Yes you need to assign mountpoints,and you can install Ultimate on same drive with Hardy.Systems will not interact with each other like they don´t when you dual boot with windows.If you choose to install that way you can dedicate your second drive to your files.
Thanks much zvacet...What I ended up doing just to get things going while at the same time trying to shorten the learning curve, was installl each to a drive, which worked out well.  After thinking about it, I kinda figured if I had a drive crash, then I'm already set up to recover from the other drive as I have the backups for each drive on the opposite drive (i.e. Hardy backup stored on Ultimate Drive).  However, after successfully getting thru current installation, it became a little clearer how the installation routine goes. So I had the thought that this was the same way you would do it installing both on the same drive and that Grub would handle the mounting points properly.  Your statement above confirms my thinking is going to right way about all this.
Appreciate your responding and looking forward to learning more about Linux thru Ubuntu.

Ya'll take care and Thanks again,
SaddleTramp

---

