---
title: "DVD R/RW won't work in Ubuntu AND Windows"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by sanjay135 on 2008-04-12
I'm not sure if this is just the device not working and a coincidence, or if I somehow corrupted a driver file or something. But ever since I installed Ubuntu 7.10 on a partition on my harddrive (dual-boot with XP), the DVD drive hasn't been working. 

I insert a DVD, push the tray back in, and I hear it starting up followed by some repeating startup noises and sometimes something I can only describe as knocking. This has happened in the past before, but it always somehow resolved itself in the end. But it hasn't this time, as well as the past few times I've tried watching a movie. 

The part that makes me think it's an issue with the hardware itself is that it won't work in either OS, Ubuntu or Windows XP. But I thought I'd try and see if anyone had heard of this before over here before calling Dell for a replacement (it's a Dell e1705 laptop bought in March of 2006) disk drive.

---

### Post by em3raldxiii on 2008-04-12
That *definitely* sounds like a hardware failure issue.  But, if you wanna just make sure about things, you could try installing an updated firmware for your drive.  Unfortunately, many firmware updates require a running Windows environment (ugh).  This might change something and make it work.  It's a pretty long shot, but  ...

The only reason why something like an Ubuntu install would "cause" this problem with your drive is that if the drive already had a hardware problem, the extended use of the drive during the Ubuntu install might have knocked something loose, so-to-speak.

Keep us apprised of your progress :D

---

### Post by prshah on 2008-04-12
> **sanjay135 said:**
> 
I insert a DVD, push the tray back in, and I hear it starting up followed by some repeating startup noises and sometimes something I can only describe as knocking. This has happened in the past 


A look at ```
dmesg | tail -20
``` will give us a clue; do this command immeidately AFTER inserting a CD/DVD and the knocking noises stop.

---

### Post by sanjay135 on 2008-04-13
@prshah
Well here's the output.

[   29.700000] [fglrx] total      GART = 130023424
[   29.700000] [fglrx] free       GART = 114032640
[   29.700000] [fglrx] max single GART = 114032640
[   29.700000] [fglrx] total      LFB  = 134086656
[   29.700000] [fglrx] free       LFB  = 104214528
[   29.700000] [fglrx] max single LFB  = 104214528
[   29.700000] [fglrx] total      Inv  = 0
[   29.700000] [fglrx] free       Inv  = 0
[   29.700000] [fglrx] max single Inv  = 0
[   29.700000] [fglrx] total      TIM  = 0
[   55.296000] NET: Registered protocol family 17
[   55.784000] SoftMAC: Open Authentication completed with 00:14:6c:d5:7a:1a
[   55.796000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   56.284000] ieee80211_crypt: registered algorithm 'TKIP'
[   63.248000] FAT: Filesystem panic (dev sdb1)
[   63.248000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   63.248000]     File system has been set read-only
[   63.432000] FAT: Filesystem panic (dev sdb1)
[   63.432000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   76.956000] eth1: no IPv6 routers present

I waited for the knocking noises to stop like you said before pushing Enter.

---

### Post by joshrobinson on 2008-04-13
the knocking noise must be the laser trying over and over to read the disc, if it doesnt work in either operating system, i would say the drive died

have you checked the bios of your computer to see if its still recognized?

---

### Post by prshah on 2008-04-13
> **sanjay135 said:**
> 
[   63.248000] FAT: Filesystem panic (dev sdb1)
[   63.248000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   63.248000]     File system has been set read-only
[   63.432000] FAT: Filesystem panic (dev sdb1)
[   63.432000]     fat_get_cluster: invalid cluster chain (i_pos 0)


Assuming that /dev/sdb is your SATA CD/DVD drive: 

Are you by any chance trying to use a DirectCD (or packet writing format) disk? Typically, you would have installed Nero InCD, or Roxio's DirectCD in Windows. This allows you to write over and over again on a CD, making the use rather like a large floppy disk.

What they don't tell you is that eventually, the CD will fail. To me, the above errors suggest that situation. 

Do you get such errors only with a particular CD/DVD, or all CDs/DVDs? How about playback, is it OK?

---

### Post by sanjay135 on 2008-04-14
No it's just a movie DVD. I've only experienced this with DVDs and CDs and haven't really tried anything else. They just won't play. In linux, I've almost gotten it to play soon after first setting up, but it malfunctioned somehow. In windows, it just says there isn't a disk in the disk drive. It doesn't recognize that it's there.

---

### Post by SpiceWeasel on 2008-04-14
I'd like to know how this works out as i seem to be getting a similar problem with my HP laptop. The disk drive will read most DVDs and CDs that i put into it in windows but some it wont recognize the format. In Ubuntu it reads all the disks but i cant get it to play my movies on VLC for some reason. 

To be specific i can take a band of brothers disk that has no scratch or smudge that plays perfect in a DVD player and it wont be recognized by windows 50% of the time but linux will pick it up but not let me play it. I can hear the drive running and it doesn't make any noise out of the ordinary but still no dice most of the time.

I have a sneaking suspicion if id just defrag my windows partition it would clear up on there but im still moving things from it to my Ubuntu partition, which sadly is taking forever since my fat32 partition is 2 gigs and my removable hard drive refuses to mount properly in this new release of Ubuntu. But thats for another post ](*,)

Anyways i don't mean to in any way jack your post but i also don't want to get on a moderator's bad side for making another post about the same problem. Even though in my gamer days i used to count that as half the fun of posting in forums :biggrin:

---

