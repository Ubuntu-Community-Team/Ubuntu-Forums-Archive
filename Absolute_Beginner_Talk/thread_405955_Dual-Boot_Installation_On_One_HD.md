---
title: "Dual-Boot Installation On One HD"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by ScottyBoyNow on 2007-04-10
I need to know the easiest way to dual-boot XP and Ubuntu on a single hard drive, I don't unfortuatly know what the harddrive is in terms of NTFS or FAT16 or FAT32 (I'm pretty Sure Its 32), but I haven't got my PC yet, could someone give me a few links.

---

### Post by rsambuca on 2007-04-10
This is a pretty good place to start.  [[COLOR="Red"]Link[/COLOR]]("http://www.psychocats.net/ubuntu/index")

---

### Post by jhenager on 2007-04-10
If it comes with Windows preinstalled, you are halfway there. Run the Ubuntu install, and choose the option to resize your Windows partition and install Ubuntu in the free space. You will get a menu when you reboot asking which OS you want to start.

---

### Post by iceraider on 2007-04-10
> **jhenager said:**
> If it comes with Windows preinstalled, you are halfway there. Run the Ubuntu install, and choose the option to resize your Windows partition and install Ubuntu in the free space. You will get a menu when you reboot asking which OS you want to start.

I can't figure out how to run the install.  I've set my computer to boot to the CD with the Ubuntu iso file.  Keeps booting to windows.

Scott

---

### Post by rsambuca on 2007-04-10
> **iceraider said:**
> I can't figure out how to run the install.  I've set my computer to boot to the CD with the Ubuntu iso file.  Keeps booting to windows.

Scott

You need to do one of two things:  either reset your bios to boot from the cd drive first, or check to make sure you burned a cd image, rather than just a regular cd data disk.

---

### Post by dstew on 2007-04-10
How did you obtain the Ubuntu CD? Did you burn it yourself? If so, did you burn it as an image or as a data CD? If you accidently burned it as a data CD, it will not boot. This is a common mistake. Check the CD with Windows Explorer. If you see only one .iso file, then you burned as a data CD. If you see several files and folders, you burned it as an image.

---

### Post by iceraider on 2007-04-10
> **rsambuca said:**
> You need to do one of two things:  either reset your bios to boot from the cd drive first, or check to make sure you burned a cd image, rather than just a regular cd data disk.

Bios is set to boot from CD drive and I can hear it spin up.  Then windows goes on it's merry way.

---

### Post by iceraider on 2007-04-10
> **dstew said:**
> How did you obtain the Ubuntu CD? Did you burn it yourself? If so, did you burn it as an image or as a data CD? If you accidently burned it as a data CD, it will not boot. This is a common mistake. Check the CD with Windows Explorer. If you see only one .iso file, then you burned as a data CD. If you see several files and folders, you burned it as an image.

When I check the CD-RW it shows only the iso file.  When I downloaded the file from the Ubuntu site I didn't see any other files to burn.  What did I miss?

---

### Post by jhenager on 2007-04-10
> **rsambuca said:**
> You need to do one of two things:  either reset your bios to boot from the cd drive first, or check to make sure you burned a cd image, rather than just a regular cd data disk.

Right. It sounds like you have a single file on the CD with an 'iso' extension. If so, you need to re-burn a disk. In most burning software, you will look for the option to burn a disk from a CD image. Then browse to your iso file on the hard disk and select it.

---

### Post by dstew on 2007-04-10
Look over the instructions in this link carefully, and you won't have any problems.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Sigfever on 2007-04-10
ok Ubuntu is great and windows vista is great and seperately both run great but when the boot menu comes up and i am told to select what i want to boot i try to select vista when it says to use the arrows on the keyboard to go up or down that is the part that takes frever or several hundred keysrokes to finally get it to move down the line to be able to select vista that is the only problem i am having seems minor but is anyone having the same problem         let me know thanks

---

### Post by iceraider on 2007-04-10
After running md5, I see my iso files are now larger than 700mb.  How do I get that to fit on a CD now?

Scott


I got it to work fine.  Sorry for bandwidth

---

