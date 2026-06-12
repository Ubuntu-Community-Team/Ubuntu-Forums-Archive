---
title: "Help Dual Boot"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Fala on 2006-09-07
ok I just did a dumb thing and installed Ubuntu from a CD I got from a Linux magazine without doing any research on dual booting.

The install of ubuntu went fine but now I can't seem to get into my XP partition.  If I boot from the CD or the linux partition it boots up ok and I can see the windows partition.  But when I choose the windows partition it just defaults to an IBM Rescue and Recovery program.

Hardware:
IBM T42 laptop
1 HD
XP already installed

chose to resize the partition as suggested by the installer and use some free space.

oh yea and this was my work laptop LOL.  uh pls help

Fala

---

### Post by Fala on 2006-09-07
actually I dont know how to get into the windows partition thru linux either.  I can see the partition but I can't seem to mount it.

---

### Post by elemental666 on 2006-09-07
hmmm, yeah, can you explain in amore step by step way how you installed Ubuntu?
What kind of laptop is this?

Also paste the results of this command in your reply:
```
sudo fdisk -l
```

---

### Post by Fala on 2006-09-07
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4438    35648203+   7  HPFS/NTFS
/dev/hda2            4439        9510    40740840   83  Linux
/dev/hda3            9511        9729     1759117+   5  Extended
/dev/hda5            9511        9729     1759086   82  Linux swap / Solaris

that's what I get when I do a sudo fdisk -l

I wish I could give you a step by step but I did it so fast I wasn't even thinking obviously.  There wasn't a whole lot to choose.  The CD came from a Linux format CD.  I was able to boot to a LIVE ubuntu and dbl click on a install icon on the desktop.  After resizing the partition I only remember it asking about time date user details and not much else.  This happened several hours ago since I was playing with the Ubuntu partition and didn't even realize that I had messed up my windows install.

Any help is greatly appreciated.

Fala

---

### Post by elemental666 on 2006-09-07
ok, you're probably ok, you just need to fix GRUB.  First make sure its really broken, reboot the computer and you should see a countdown at some point, hit esc and you shuld be presented with the Grub menu. Make sure windows is not listed here. Report back.

What is going to get you is that the Windows Bootlader is gone and the only way to get it back is with the windows install media (to the best of my knowledge).  Couple that with the fact that you did this on your work system and that could mean trouble.  Is this a computer that was given to you by your employer? Or is it your personally owned system that you use for work? Is the windows install a corporate image from your employer?

---

### Post by Fala on 2006-09-07
I know for sure that Windows XP/2000 is on that list as the last option but when I boot that's when it comes up to the IBM Rescue and Recover program.  I can get into that program using a pre-designated password.  

The laptop was issued by work.  I figured I had 50Gb left on the disk why not dual boot and see how Ubuntu would work out in a work environment vs. just a home desktop.  So yes my laptop used a corporate image loaded from CDs.

---

### Post by elemental666 on 2006-09-07
ok then, bad news...

IBM doesn't ship recovery discs, instead they have use a partition on the hard drive that contains the recovery files.  I'm guessing you just blew away your corp image and the NTFS partition you see is in fact the recovery partition. If this is the case, then you also lost any work you had saved on that machine.  If this is not the case, then somehow you have damaged the data on the NTFS partition and the recovery program is kicking in to repair it, which will kill unbuntu (which in this case isna't a bad thing). However, the recovery files in that partition are not likely those of your corporate image.

You'll have to contact your deskside support and have them reimage your laptop to get back to where you were.

Important lessons. Don't tinker with your corporate laptop, use it only for the purposes it was designed for. If you do decide to tinker with your corporate laptop, make a full image of every partition on the hard drive before doing so.

Hope you don't get into too much trouble...  good luck.

---

### Post by YeahBuntu on 2006-09-07
Before you take your lappy back to work for the geeks to fix for you ... I would suggest using fdisk or cfdisk and wipe all partitions so you dont get into any hot water... or even grab a copy of gwscan from gateway maybe and write zeros to the drive.  I think there are some other free tools that will destructively wipe the drive too.

Just cant stand seeing someone trying Ubuntu get into trouble from work...

---

