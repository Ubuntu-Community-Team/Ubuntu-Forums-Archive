---
title: "Reinstall XP while Ubuntu is on my HDD"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-09-06
Could someone walk me through a reinstall of WinXP? -I currently have XP and Ubuntu 6.06 installed on this HDD and I've heard that Windows will overwrite Grub's boot loader: so how do I reinstall XP without loosing the bootloader and Ubuntu? My current setup is:
OS:  Ubuntu 6.06/WinXP Pro SP2
CPU: Pentium 4E 3400 MHz (4.25 x 800)
Chipset: Intel Grantsdale i915
BIOS: AMI (09/24/04)
RAM: 1024 MB
Video: RADEON X800 PCIe
Audio: Creative Audigy Platinum
HDD: WD 250G (WDC WD2500JD-22HBB0)
Partitions: 1. 10G ext3 (Ubuntu 6.06)
            2. 104G NTFS (WinXP Pro SP2) 
            3. 1G Swap
            4. 112G ext3 (/home)
Optical: LITE-ON DVDRW SOHW-832S
Optical: SAMSUNG DVD-ROM SD-616E 

Can I reinstall XP easilly without loosing Ubuntu? -if so how?
If you could explain how to do this as if I were an idiot I would appreciate it -New to Dual booting, new to Linux.
Thanks for your time,
522.
(edit spacing etc.)

---

### Post by LeslieL on 2006-09-06
I've reinstalled Windows while Xandros was installed. Windows allows you to choose the partition to install in - just make sure you don't touch your Ubuntu one:) . But Windows overwrites the boot record, I believe, so it looks like you've lost Ubuntu. In Xandros you have to use the restore or repair option on the installation disk to recreate the boot record. I'm curious to know how you do this in Ubuntu.

I do know it's easier to install Linux after Windows than the other way around.

---

### Post by Drakkor on 2006-09-06
Yes,when you install Windows it will overwrite the mbr(master boot record),
but as long as you reinstall windowss on the same partition it was on, Ubuntu on another partition is fine,you just have to reinstall grub to be able to boot from either OS

---

### Post by dannyboy79 on 2006-09-06
i haven't done it but I can tell that I have read somewhat about it, as long as you chose which partition you want to install xp on you won't overwrite your ubuntu os but then the boot record gets written over like LeslieL stated. So you just need to redo your grub setup. I have Googled "restore grub after winxp install" and found you a perfect link with plenty of peoples response's that has restored their grub and back to a working dual boot machine, here it is, [http://www.linuxquestions.org/questions/showthread.php?t=446952As](http://www.linuxquestions.org/questions/showthread.php?t=446952As) the above person stated, it is way easier to install ubuntu after windows. Windows sucks because it wants to be the only os on the computer so it takes over grub. FYI, whenever you want to find something out just google a short summary or phrase and most of the time you can find it pretty quickly and most of the time get your answer quicker than having to wait for people in these forums to respond but it's obviously up to you. I know that I have posted plenty of questions that I can't find in google or that would take way to much reading to figure it out and I have a few answered and a few unanswered. I can honestly say that I often just read through the forum subject and if I know the answer I'll open her up and post the answer just like I have done with this one! Good luck!

---

### Post by Drakkor on 2006-09-06
Just found my notes on how to reinstall grub
OK,boot to the live Ubuntu CD
Open terminal type **sudo grub**
At **grub>**prompt enter these commands
**find /boot/grub/stage1**
This will return a location like **(hd0,1)**
still in terminal type
**root (hd?,?) ** use the values from the find command
Next enter the command to install grub to the mbr 
**setup (hd0)**
Enter **quit**
reboot to the hard drive

I have done this and it works ! :D

---

### Post by rudlavibizon on 2006-09-07
Thanx Drakkor, worked for me too. :p

---

### Post by fiver22 on 2006-09-08
Thanks for all the replies and helpfull comments -I appreciate it. Question answered.

---

