---
title: "Please a simple guide"
date: 2005-06-02
forum: Absolute Beginner Talk
---

### Post by ajsadler on 2005-06-02
I'm still having trouble installing Ubuntu on my PC can someone please just give me a simple set by set guide explaining clearly what to do from Downloading the software to First loading up Ubuntu. Thanks


-AJ

---

### Post by DrMoxie on 2005-06-02
Are you experiencing problems on a particular stage such as hardware detection? Essentially, you just need to download the ISO from [the download area](http://www.ubuntulinux.org/download/).  The installer will do a decent job walking you through the steps to set up the installation (timezone, keyboard layout, etc).  Once it is installed you can visit [The Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/) for further information about fine tuning the installation.  :smile:

---

### Post by pdk001 on 2005-06-02
go to download ubuntu CD's here [http://us.releases.ubuntu.com/releases/5.04/](http://us.releases.ubuntu.com/releases/5.04/)
which one choose either install CD or live CD
and inset void CD in the cd-rom to burn CD you downloaded

---

### Post by ajsadler on 2005-06-02
How would I go about creating a dual-boot with WindowsXP?

I have all my data backed-up, 2 CDs (one with LiveCD version of Ubuntu and one with Install version of Ubuntu).

I want to be able to get to a screen during the bootup stage where I can choose which O/S to load. Thanks


-AJ

---

### Post by Technoviking on 2005-06-02
Here is a good starting point:
[http://www.ubuntulinux.org/wiki/InstallationHowToI386](http://www.ubuntulinux.org/wiki/InstallationHowToI386)

If you are brand new to Linux, and want a dual boot system, I would installing a second harddrive. It make partition easier and gives you plenty of room to play with linux.

Mike

---

### Post by henriette_holm on 2005-06-02
You can also take a look at this page:

[http://mrbass.org/linux/ubuntu/install/](http://mrbass.org/linux/ubuntu/install/)

Please note that following this guide for partitioning your drive will **DELETE** your windows partition.

-Henriette

---

### Post by ajsadler on 2005-06-02
Hmm thanks for that info Mike but currently I just want to 'trial' Ubuntu for a while because I do not want to jump from W*nd*ws XP to Ubuntu as I have little idea of how it works, what you can do on it, and possibly most importantly ... all those command lines I keep seeing everyone throw about and I think that would really confuse me. I am very able at using computers and a lot of commands but my knowledge is limitted to W*nd*ws. Suggestions? Thanks


-AJ

[Edit in reply to henriette_holm]
Thanks for that guide and I have reached the first screenshot with the Ubuntu install load screen with my Install version of Ubuntu and pressed Enter to which I got this error (vague memory - possible wording errors. Can rectify if needed)

"uncompressing linux

crc error

system halted"
[/Edit]

[Edit to add information]
Just remembered that my current W*nd*ws XP partition takes up (virtually) all of the available space on my hard drive.
[/Edit]

---

### Post by az on 2005-06-02
Partitioning a single hard drive for both operating systems is not hard:  You get the boot menu by default when grub is installed and grub is installed at the last step of the installation...

see:
[http://test.wiki.ubuntu.com/forum/installation/Partitioning](http://test.wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by couchwarrior on 2005-06-02
i just did this myself on my laptop, as a noob i found it was simpler to resize my xp partition with partition manager and just leave 20gb of unallocated space , booted the ubuntu disc and when prompted to installed into the unallocated space 
if you want rid at a later date then boot into windows,  fixmbr will kill grub, and then delete the linux partition

---

### Post by ajsadler on 2005-06-02
I've just reformatted my hard drive and created 2 partitions, my second going to be used to boot Ubuntu and contains approx. 35Gb of storage and also about 1Gb or spare storage space. I'm on a different computer now, as you can guess, downloading Nero to try writing the Install Ubuntu version to a new CD as I believe the old one may be corrupted.

What do the terms fixmbr & grub mean? Thanks


-AJ

---

### Post by couchwarrior on 2005-06-02
fixmbr is a winxp command to repair the master boot record , basically wipes out grub which is the linux boot manager

---

### Post by ajsadler on 2005-06-02
When inserting my Install disc I get that error that occured before:

"Uncompressing linux

crc error

--System halted"

---

### Post by Jussi Kukkonen on 2005-06-02
crc error means that verifying the data failed. If I've understood correctly the check is done on data on the hard disk -- if this is correct, it implies there's something wrong with your disk.

If you have another linux machine you can plug the disk into, you could run *badblocks* on it...

---

### Post by ajsadler on 2005-06-02
It's OK now thankyou I've solved this problem. Please see my new thread regarding a new problem  ](*,)

---

