---
title: "Ubuntu Live CD"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by divi on 2007-02-26
Hello,
I have a fake copy of XP which I know one day will stop working ,I didn't buy a fake copy I just bougt, the computer that way,so I thought I would give Ubunta Live CD ago,and it works and it feels good to use something different from XP.
I have looked in google and other forums on how to install Ubunta and people are saying you need two disks a XP and Ubunta ,I only have the Ubunta and I don't wont to ruin XP ,So what would happen in I went ahead and Installed the Ubunta Live CD?

---

### Post by antoz on 2007-02-26
Just play around with the live Cd to gain a bit of confidence before you install it. You don't need a separate HD provided there is enough free space on the one you have.
Check this link it has all the help you need to get you started
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

have fun,A

---

### Post by divi on 2007-02-26
Thanks , I have played around with it and even though people have said the live CD will be slower, it seemed to work faster than my firefox browser,I liked using it because so many people I think just throw  computers away because they don't have no intallation disks, when things go wrong.

---

### Post by Kateikyoushi on 2007-02-26
It is easier to restore booting to XP if you have a windows CD but can do without.

---

### Post by Aurora Borealis on 2007-02-26
> **divi said:**
> Thanks , I have played around with it and even though people have said the live CD will be slower, it seemed to work faster than my firefox browser,I liked using it because so many people I think just throw  computers away because they don't have no intallation disks, when things go wrong.
 Ubuntu gives out free CDs. It's usually of the prior distribution, but new releases are only about 4 months old anyway. A good bet if ever you find you need a new CD. It could save you a lot of money over buying a new computer. But if the computer you have has a CD burner, you may want to look into downloading distributions. Once you learn how, you can use whatever you want and save yourself a lot of time and trouble.

Best wishes to you.

---

### Post by divi on 2007-02-26
Thanks I have five new copies of ubuntu sent to my door, free of charge, going to give friends copies as a few of them have deleted something off their computer and don't have intallation disks like me.
Infact some people I know think XP is a computer not a OS, I only heard about linux four months ago,

---

### Post by antoz on 2007-02-27
Like I said earlier use the live CD for a while before you rush into installing it, while it is not too hard to install you CAN mess things up and could loose XP.
A good idea would be to back up everything including your MBR there should be information on the link I sent you I remember reading about it on HERMANZONE I think it was on the uninstall ubuntu page.

---

### Post by divi on 2007-02-27
Thanks I am using the live cd now. have read your links about intalling the cd and it all looks pretty harmless if you choose opition 1 and not opition 2 or 3. The link says its 99.9% sure, surely I could not be in the 0.01% ?
What is MBR ? By the way I have two harddrives one has windows on and is 40g with about 60% of free space and the other has windows on and is 80g but with this harddrive windows is broken although it's still on there.
My plan now is to...

1) Use the 80g hardrive as master and load up ubuntu
2) Connect working 40g windows harddrive as slave
3)Reboot and hope the computer gives me the opition to choose between XP and Ubuntu

---

### Post by antoz on 2007-02-27
The MBR is your "master boot record" if for some reason or an other after installing Ubuntu you decided to uninstall it you would not be able to boot into Windows anymore without restoring the MBR. If you had the original Widows disk this would not be a problem but since you haven't got it just back up the MBR on a floppy in case you need it some time in the future.

---

### Post by Scarlett on 2007-02-27
MBR is the master boot record.  It's where your computer looks to load up an OS.

It's always a good idea to back up any files you can't live without, but Ubuntu should create a separate partition and install Grub which will allow you to dual boot while leaving all your Windows and NTFS stuff intact.  It's also a good idea to defrag your Windows drive if you're installing on the same HD.

---

### Post by divi on 2007-02-27
> **antoz said:**
> The MBR is your "master boot record" if for some reason or an other after installing Ubuntu you decided to uninstall it you would not be able to boot into Windows anymore without restoring the MBR. If you had the original Widows disk this would not be a problem but since you haven't got it just back up the MBR on a floppy in case you need it some time in the future.

Thanks , I do have a HP floppy disk ,I could connect the the second harddrive and put all my files on there.

---

### Post by antoz on 2007-02-27
Since you have 2 hardrives you could partition the larger drive and create a FAT32 partition in that case you can share files between the 2 operating systems.
Also if you are worried about Windows there is software available to create a mirror image of your drive one of them is "Acronis" but there are others.
If you have windows on a separate drive though I can't see how you could mess it up but I think you will need to edit your Grub to be able to boot into windows I am not really experienced enough to help you there but I have seen it on the one of the pages of the link.

---

### Post by divi on 2007-02-27
Thanks...

---

### Post by Kateikyoushi on 2007-02-27
You could read files from your linux ext partitions with this driver. [LINK]("http://www.fs-driver.org/") NTFS can be mounted linux and read only is safe.

---

### Post by webofunni on 2007-02-27
I think using ntfs-3g you can give ntfs drives write access in ubuntu. I had done it but doesn't gave a problem still now

---

### Post by divi on 2007-02-27
thanks

---

### Post by divi on 2007-02-27
Thanks for the Acronis advice....I am going to ..
1)back up the 80G harddrive and use that one as the master
2)he working harddrive that I use now,I'm going to tuck in bed
and hey bingo it should work....

---

### Post by Aurora Borealis on 2007-02-28
> **divi said:**
> Thanks I have five new copies of ubuntu sent to my door, free of charge, going to give friends copies as a few of them have deleted something off their computer and don't have intallation disks like me.
Infact some people I know think XP is a computer not a OS, I only heard about linux four months ago,

I'm glad to hear it. It makes life so much easier. I'm new to linux myself.

---

