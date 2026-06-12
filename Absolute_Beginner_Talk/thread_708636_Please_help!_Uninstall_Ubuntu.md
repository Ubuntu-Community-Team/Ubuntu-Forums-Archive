---
title: "Please help! Uninstall Ubuntu"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by CJWild8 on 2008-02-26
Okay so I'm sick and tired of not knowing how to do anything with a Linux OS (Ubuntu Gutsy Gibbon 7.10) so I want to do a complete uninstall so I can put Windows back on my PC.

Can somebody please tell me how to do this?

Assume that I know nothing about Ubuntu (truth)

---

### Post by benfindlay on 2008-02-26
Sorry to hear you are having problems. The simplest thing to do is put the windows CD in the computer and reboot. Install windows from it and just get rid of the ubuntu partitions when you get the choice for partitioning.

---

### Post by CJWild8 on 2008-02-26
I've tried doing that but I get some error saying that there isn't enough system space? I thought maybe this was because Ubuntu was still installed? Is there anyway I can Uninstall it first before I re-install Windows?

---

### Post by louieb on 2008-02-26
[Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")

---

### Post by benfindlay on 2008-02-26
You need to remove the ubuntu partitions before going onto install windows. This is done by Deleting the partitions so that you get un-partitioned space. Then you create new partitions again and windows is installed onto the computer in the new partitions, which will be totally free of anything.

---

### Post by jhenager on 2008-02-26
> **CJWild8 said:**
> I've tried doing that but I get some error saying that there isn't enough system space? I thought maybe this was because Ubuntu was still installed? Is there anyway I can Uninstall it first before I re-install Windows?

Windows gives you the option to delete existing partitions. I believe the option is D, and then L to confirm.
Then you press C to create a new partition.

---

### Post by bodhi.zazen on 2008-02-26
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by HermanAB on 2008-02-26
Windows is too dumb to understand Linux file systems.

You have to boot with a Linux live CD (Knoppix or Ubuntu), then run Partimage and repartition and format the whole disk with VFAT.  After that, Windows will install again.

BTW, Ubuntu is not the easiest Linux.  Ubuntu is sort of intermediate difficult.  The easiest Linux is PuppyOS and second to that would be Mandriva (or PCLOS).  So if you wish to give Linux another spin one day, try one of those.  Another way, is to buy a pre-installed machine such as the Eee PC which only costs $400.

Cheers,

Herman

---

### Post by t0p on 2008-02-26
> **HermanAB said:**
> ...Ubuntu is not the easiest Linux.  Ubuntu is sort of intermediate difficult.
Sez you.  Me, I think otherwise.

---

### Post by CJWild8 on 2008-02-26
Guys, I know this may be easy for some of you but I am NOOOOB. I don't know what to do step-by-step to try any of the things you suggested. And I don't want to render this computer useless in between steps or I will have no way of knowing what to do next.....

Someone shoot me.....

---

### Post by bodhi.zazen on 2008-02-26
The link I posted goes over how to do this step by step in detail :twisted:

---

### Post by Paqman on 2008-02-26
> **CJWild8 said:**
> I don't know what to do step-by-step

Put your Ubuntu LiveCD in the drive and reboot. Once the LiveCD session is up and running you want to open up Gparted (I forget which menu it's in)

In Gparted click on every partition and select it for deletion. Hit apply. You'll be left with a drive consisting eintirely of "unpartitioned space". If you want you can format the whole drive to NTFS, or you can let Windows do this during installation.

Exit Gparted and shutdown the PC. Boot up with your Windows install CD in the drive and go to the "recovery console". Type in:
```

fixmbr

```

Your drive is now 100% Ubuntu-free!

---

### Post by UFRaymond on 2008-02-26
[HowTo: Remove Ubuntu (& Restore Windows - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=508927")

---

