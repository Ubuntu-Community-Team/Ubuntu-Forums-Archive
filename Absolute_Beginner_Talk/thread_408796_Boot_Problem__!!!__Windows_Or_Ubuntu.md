---
title: "Boot Problem  !!!  Windows Or Ubuntu??"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by sebdj on 2007-04-13
Hi!

Two days ago, for the first time I have installed Ubuntu. I had at the same time windows XP

I put the cd on at the startup Choose install Ubuntu after it load by itself.

Then I click on install on the desktop and I select to not Format but second choice

I did exactly at this tutorial :
[http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/#more-83]("http://fosswire.com/2007/01/12/giving-linux-for-a-spin-the-first-time-part-3/#more-83")

(Begin to the install of Ubuntu not before)

Then I was suposed to see Windows and Ubuntu logo so I can choose one of them.

But now my computer just don't boot at all. (It just boot the initial boot with the click DEL to acces the bios, click F12 to have the Boot Menu , clcik F8 for the Network Menu. )

IT SAID : 

NTLDR is Missing
Press any key to restart


1. I have try Super Grub

2. I have try to boot by the Windows XP Boot Cd and the recovery file and the FIXMBR

3. I have try to reinstall XP (but they don't let me the choose (I'm obligated to format)

4. I have try the sudo fdisk -l n the Ubuntu command. 

I can only access ubuntu from the Ubuntu Cd I burn. 

Now I just really need my files back...

Please help this is very urgent!

---

### Post by steve.horsley on 2007-04-13
I saw a post from someone a couple of days ago who got this NTLDR missing message. He eventually discovered there was a floppy in the drive and the PC was trying to boot that. It's worth checking.

---

### Post by Seisen on 2007-04-13
It sounds to me that grub didn't even install, which would be what your problem is. You can try reinstall Ubuntu and this time make sure to check if grub installs.

---

### Post by seshomaru samma on 2007-04-13
Seisen is probably right. Reinstalling Ubuntu is a good idea , but this will not solve the Windows problem .
It seems like sebdj wants to save his (/her?) Windows files first
Initially I suggested Knoppix ,but when I saw the output of fdisk -l sebdj posted [here]("http://suprfile.com/get.php?id=6rm7mm4"), I changed my mind, it looks like thre is some serious problem there. 
In order to save the files in the Windows partition, I suggest the following steps:
1. Run XP in rescue mode , follow the instruction [here]("http://www.windowsforum.org/forums/index.php?showtopic=10455") - this will reinstall Windows while keeping your data (this is not the same as fixmbr)
if it doesn't work then:
2. Run Test Disc as suggested by Sef in your other thread,
3. Run Knoppix to save your files, instructions [here ]("http://lifehacker.com/software/disk-recovery/geek-to-live--rescue-files-with-a-boot-cd-192982.php")


If one of these doesn't work - please supply details on how it doesn't work and what kind of errors do you get.

---

