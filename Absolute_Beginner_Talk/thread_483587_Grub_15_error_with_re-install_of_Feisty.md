---
title: "Grub 15 error with re-install of Feisty"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by BIZKeT on 2007-06-24
So I dumped Windows and installed Feisty. It went seamlessly. I was _really_ happy. Then came trying to get City of Heroes to run in Cedega. I had installed the restricted ATI drivers, got Cedega installed and started getting weird problems. I opted to wipe it all and re-install Feisty and go from scratch to test an idea for my CoH woes.

Then I rebooted.

Grub Error 15. I did some research and found a lot of stuff that confused me a bit, most of it dealing with the master boot record. My biggest hope seems to be a cd image that I can burn and boot from that has some kind of Grub software. Problem is, the only burner that I have is the cd drive in the laptop I am installing Feisty on, and I am booting into a live cd at the moment so that burner is unavailable.

My computer is an Acer Ferrari 3200, and my live cd is the latest (grabbed it yesterday) Feisty live cd (not the dvd). Are there any tools on the install disk that I can use to look at the MBR and make changes? Gparted shows /dev/hda1 is ext3 with 107.45 total space, /dev/hda2 is locked and extended with 4.34 gig and /dev/hda5 is locked and linux-swap, 4.34 gig and inside of /dev/hda2.

Thanks in advance for any help you guys can give me.

---

### Post by Happy_Man on 2007-06-24
Mm..... try reinstalling again. This seems like a fluke GRUB problem... just reinstall and it's likely it will be fixed again, since Feisty worked before.

---

### Post by alienexplorers on 2007-06-24
Try booting your live-cd.  Eneter terminal and enter sudo grub.
Enter
> find /boot/grub/stage1
You will get a message like (hd#,#) where they are your disk and partition numbers.
enter 
> root (hd#,#)
enter
> setup (hd#)
remember to leave off the partition number.
exit grub
reboot

---

### Post by K.B. on 2007-06-24
I'm replying to this thread about the Grub ERROR 15 instead of the other threads that touch on this since this is the most recent one ----


I've been running Ubuntu on my laptop in a dual boot (the other is XP) set-up for at least 6-8 months with a single problem. Upgraded to Feisty Fawn with no major problems and have been living the good life--- till today.

Today I rebooted my laptop and got the dreaded message:
GRUB 1.5 
ERROR 15...

and it hangs.

I booted with my 6.10 CD and tried *grub> find /boot/grub/stage1* but it comes back and tells me that it can't find the file.

I tried the suggestions about mounting the drive first and none of them worked either. With everything it tells me that it can't find the file. 

I found a suggestion on how to get the installer on the disk to skip to the part about installing GRUB without re-formatting my drive and resinstalling Ubuntu but I can't get the installer to do anything unless I tell it to reformat part of the drive.

I **_REALLY_** don't want to have to format this drive, lose everything and re-install the works.. but I am not finding any new suggestions in my searches.  

 I'm hoping someone has a suggestion for me.   thanks

as a bit of information, this is what I get back from *_sudo fdisk -l_*
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1029     8265411    7  HPFS/NTFS
/dev/hda2            1030        2240     9727357+  83  Linux
/dev/hda3            2241        2373     1068322+  82  Linux swap / Solaris
/dev/hda4            2374        3648    10241437+  83  Linux


---

### Post by confused57 on 2007-06-24
You both might want to try burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD is only a 5-7 Mb download...it may not work, but it would be worth attempting to boot Ubuntu with SGD.

---

### Post by alienexplorers on 2007-06-24
Load your windows disk and goto recovery mode. Enter fixmbr.  Then try running the grub fix I listed above.

---

### Post by K.B. on 2007-06-24
> Load your windows disk and goto recovery mode. Enter fixmbr. Then try running the grub fix I listed above.

I fired up the XP install disk... went into recovery mode and did the *fixmbr* -- restarted with my Ubuntu disk and am still getting the ***"Error 15: file not found" ***

now it bypasses the GRUB start up completelyand goes straight for the XP side if I don't tell it to boot from the CD.

---

### Post by K.B. on 2007-06-25
I tried all the same suggestions again this evening and I'm still getting "FILE NOT FOUND" errors and the laptop will boot straight into XP. 

Any other suggestions or ideas???

---

### Post by BIZKeT on 2007-06-26
> **Happy_Man said:**
> Mm..... try reinstalling again. This seems like a fluke GRUB problem... just reinstall and it's likely it will be fixed again, since Feisty worked before.


Reinstall fixed it. Thanks! Now to just get City of Heroes running in Cedega...[-o<

---

