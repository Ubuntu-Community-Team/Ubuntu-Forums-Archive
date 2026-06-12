---
title: "Need Help Confused About a Few Things"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-04
Alright, I am going to buy another hard drive to go in my computer. I want to install Ubuntu on it and keep Windows XP on the other. I know how to physically install the drive in my computer (i.e. put it in the case) but whats all the stuff I have to do with GRUB? I have no idea what that is.

Also, I don't want my Windows XP drive to see my Ubuntu drive and I don't want my Ubuntu drive to see my Windows drive. Infact, is it possible to have the drive that is not in use totally off and not spinning? Thanks for your help. Its extremely appreciated.

---

### Post by AndyCooll on 2008-01-04
The link in my signature explains everything you need to know about dual booting. 

See here for an explanation of [GRUB]("http://en.wikipedia.org/wiki/GNU_GRUB").   

When you dual-boot you are loading one OS or the other. They live on separate partitions and work completely independent of one another. Only one OS is running at any one-time. 

If Ubuntu is on the second-drive (for instance) then the only time the first hard-drive is likely to spin is on boot up to check the MBR.

:cool:

---

### Post by Crumpets and Jam on 2008-01-04
> **AndyCooll said:**
> The link in my signature explains everything you need to know about dual booting. 

See here for an explanation of [GRUB]("http://en.wikipedia.org/wiki/GNU_GRUB").   

When you dual-boot you are loading one OS or the other. They live on separate partitions and work completely independent of one another. Only one OS is running at any one-time. 

If Ubuntu is on the second-drive (for instance) then the only time the first hard-drive is likely to spin is on boot up to check the MBR.

:cool:

Thanks for the response. I think I get what GRUB is now.

So my Ubuntu and Windows drives won't be able to see each other then? It will be like running two entirely different computers?

---

### Post by AndyCooll on 2008-01-04
Exactly. You start the computer, get a choice of OS and then it boots into the one you choose.

You can of course take various actions enabling you to see the other partitions, but by default they are completely indepedent.

:cool:

---

### Post by kellemes on 2008-01-04
Just another link to study. :)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


By the way, expect to make mistakes so assume you'll loose existing installs (eventhough it'll probably all go fine). ergo.. create backups of your most important data.

---

### Post by Crumpets and Jam on 2008-01-05
Will any viruses be able to get on my Windows drive through my Ubuntu drive? Thanks.

---

### Post by philinux on 2008-01-05
Not unless you put one there yourself.

---

### Post by bumanie on 2008-01-05
It is possible to load each hard drive seperately and choose which one to boot by going into bios and choosing which drive to boot. A bit of a hassle if you are constantly moving between each OS, but if you use one much more than the other, it is an option.
To do this leave xp where it is and when you install the other hard drive, unplug the xp drive and install ubuntu onto the plugged in drive. Replug the xp drive and from then on, choose which hard drive you wish to boot from bios.
(At least I think that's one way to keep both drives/OSes totally separate)

---

### Post by hyper_ch on 2008-01-05
well, a virus on windows could still try and format the linux partition/harddisk... in that case you'd lose the data on it...

---

### Post by Crumpets and Jam on 2008-01-05
> **bumanie said:**
> It is possible to load each hard drive seperately and choose which one to boot by going into bios and choosing which drive to boot. A bit of a hassle if you are constantly moving between each OS, but if you use one much more than the other, it is an option.
To do this leave xp where it is and when you install the other hard drive, unplug the xp drive and install ubuntu onto the plugged in drive. Replug the xp drive and from then on, choose which hard drive you wish to boot from bios.
(At least I think that's one way to keep both drives/OSes totally separate)

So this would eliminate the need for GRUB?

---

### Post by scorp123 on 2008-01-05
> **Crumpets and Jam said:**
> So this would eliminate the need for GRUB? No. Linux still needs a boot loader, e.g. GRUB.

---

