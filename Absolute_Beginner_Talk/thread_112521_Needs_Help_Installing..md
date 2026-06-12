---
title: "Needs Help Installing."
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by ItalianSidedish on 2006-01-04
Ok right now I'm on my windows xp service pack 2.  I want to make a parition to my hard drive so I can have ubuntu on here as well.  I have partition magic 8 along with boot magic.  I'm just not sure and I'm a bit frightened on how to do this.  Can anybody tell me how to make a partition, right size and everything?  This is my first time ever with linux but I'm not exactally new to computers.  I've used windows for the last 10 years of my life and I'm ready to try this out.  Please help me, even if it requires me to download a different partition program or anything.

I do have Ubuntu on a disc ready for installation, I already downloaded the iso and I burned it with some iso burning program, I just need help on getting ubuntu on here without erasing windows.

Remember, I still want windows on here, but I also would like ubuntu as a secondary OS I guess.

Thanks in advance. :D

---

### Post by hod139 on 2006-01-04
The ubuntu wiki has a lot of information on how to install ubuntu.  [https://wiki.ubuntu.com/Installation]("https://wiki.ubuntu.com/Installation")

For setting up the dual boot, see [https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")

---

### Post by ItalianSidedish on 2006-01-04
Ok, so exactally how much is a good amount for a partition?  10 gigs?  I have 200 gigs on my hard drive.

---

### Post by Raybuntu on 2006-01-04
I have just finished doing that. You need to free up some space for Ubuntu on your hard drive. You can do that with Partition magic. I made 20GB, but you only need about 2GB for the basic. Leave the free space unassigned. Then boot from the Linux CD. Ubuntu will install on the free space and set up GRUB as the boot manager. Ubuntu will be the default boot when you reboot, but it will give you 30 seconds to choose windows if you want to. Hope that helps. It worked for me.

---

### Post by ItalianSidedish on 2006-01-04
do I chose before C or after C when using partition magic to make a new partition?   Or does it even matter?

---

### Post by Raybuntu on 2006-01-04
You dont need a new partition, just free up some space and Ubuntu will install there and make the partitions. Leave the space as unasigned.

---

### Post by byen on 2006-01-04
Yes. you would have to create a seperate drive..doesnt matter if you name it D or E.. just create one..and use that drive during ubuntu install to format into ext3-file type and install ubuntu with "/" as the mount point.

Now a suggestion:
If you are planning to stick with ubuntu and would like to use windows and ubuntu side by side..you might wanna have another third drive (FAT) which can be used as a common storage point for ubuntu as well as Windows.As you cannot write from ubuntu to Windows(NTFS) and from Windows to Ubuntu(ext3).

Since you have 200Gb. i would say a safe bet would be 10gb ubuntu and FAT(depending on your req.)
Hope that helps. goodluck.

---

### Post by ItalianSidedish on 2006-01-04
Ok so I tried installing linux and failed.  I let it check for everything and everything checked out.  Then I chose to free up some space.  It said you need at least 11 percent, so I chose 50 gigs to free up (too much?) Then I waited like 10 minutes and I was on this blue screen with a white line under it and I got scared and ctrl alt deleted it.  I'm on windows now and I am determined to get this to work so can somebody puh leease help?:confused:

---

### Post by Lord Illidan on 2006-01-04
Hmm, you needn't have done that. Resizing takes time, especially on a large harddisk. You might have had the risk of losing your data.
Did you defragment your harddisk?

---

### Post by ItalianSidedish on 2006-01-04
no I didn't, but everything appears to be working so nothing has been lost.  I'm going to defragment right now and instead of 50 I'll use 25 gigs.

Now WTF is FAT?

---

### Post by byen on 2006-01-04
FAT is a type of file system.
Now Windows used to use FAT as its file system but in Xp it uses a different type of file system called "NTfs". linux on the other hand uses ext3 (among others). So since Xp and Ubuntu use different file systems... you cannot wite from one to the other.. like say while running windows you cannot write files into the linux drive(ext3) or from linux to windows(ntfs). Hence i suggested that you create a common file system (FAT) where both the Operating Systems can read and write. Trust me you will find having a seperate fat drive once you get your system installed and running.
Goodluck

---

### Post by jimrz on 2006-01-04
look [**[COLOR="Sienna"]here[/COLOR]**]("http://users.bigpond.net.au/hermanzone/") for a really good guide to doing a dual boot install.

Welcome and good luck

---

