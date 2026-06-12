---
title: "Reloading Ubuntu 7.10 killed my computer - GRUB 18 Error - Please help!!!"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by billnj on 2008-02-09
I loaded Ubuntu 7.10 a couple of weeks ago to salvage my old Gateway 450 computer and to use it as a platform to learn Linux.  I was pretty happy with it until today.  I really need some experienced help this time.

When first loaded Ubuntu it worked very well except for the sound and the video display.  I figured that I would live with the low resolution screen and deal with sound first, so I hit the forums pretty hard.  I could get no sound at all  from my computer at all in spite of some good advice to my inquiries and in spite of using the comprehensive sound guides in the on-line documentation.  At least I was learning something new in the process.

With my patience slightly frayed, I finally decided to reload Ubuntu completely.  I got out the CD and reloaded the whole operating systemt today.  I am using a 160 GB hard drive for Ubuntu and a 13 GB hard drive for Windows XP and it had worked very well up until I reloaded Ubuntu.

Now I can't even boot the computer.  I get a "Grub 18 error" message when I try to boot my computer without the Ubuntu CD.  If I understand the system correctly, isn't Grub the software that allows me to boot either operating system (Ubuntu or Windows XP)?  Why won't it work anymore?

I could probably live without the sound and even with the low resolution screen, but I am now living without my old computer.  I had hoped to leave the Windows Vista machine for my wife and kids to use and I would be happily working in Linux on the old Gateway 450 clunker.  I'm totally lost now.

Please help!!!!!

---

### Post by Tatty on 2008-02-09
Hi billnj

I have never had to mess with the grub myself up till now, so i cant give you any detailed answers.

But it sounds like you simply need to change some settings in your grub.  You need to get a Ubuntu Live cd and boot to that, from here you can access your hard disk and hopefully be able to edit your grub.

[https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29]("https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29") 

And here is another post about a grub 18 error : [http://ubuntuforums.org/showthread.php?t=7051]("http://ubuntuforums.org/showthread.php?t=7051")

This link tells you lots about how the grub works.  It might be a good place to start to try to figure out whats wrong.

Hopefully someone who knows what they are doing might be able to help you, in the meantime ill have a look to see if i can figure anything more

---

### Post by billnj on 2008-02-09
Tatty,

Thanks for the info.  I'll study the links you gave me and see if I can fix my problem.  As you can probably tell, I'm new to Ubuntu and feel hopelessly lost so your help is greatly appreciated.

Thanks,

BillNJ

---

### Post by InfoTech on 2008-02-09
May be this link helps:

[http://wiki.linuxquestions.org/wiki/GRUB#Errors_and_solutions](http://wiki.linuxquestions.org/wiki/GRUB#Errors_and_solutions)

Good luck!

---

### Post by billnj on 2008-02-09
The information in the link that you sent makes sense;  the system is trying to read a block beyond the end of the BIOS.  However, the solution is beyond my meager computer skills.

The link says:  "...just boot with a grub floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match."  It sounds simple enough but I have no idea how to do any of this, or even where to look to find it.

Do I boot from the Ubuntu CD-ROM?  After that, what do I look for?  What should I change?  unfortunately, I don't even know what C/H/S numbers are.  Sorry for my computer illiteracy, but  I'm completely lost.

Thanks,

billnj

---

### Post by InfoTech on 2008-02-10
This might put more light on the issue:
- Creating GRUB floppy
[http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating-a-GRUB-boot-floppy](http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating-a-GRUB-boot-floppy)
- C/H/S numbers:
Cylinder/Head/Sector 
[http://www.win.tue.nl/~aeb/partitions/partition_types-2.html](http://www.win.tue.nl/~aeb/partitions/partition_types-2.html)

Unfortunately (or luckily) I did not had this problem myself, so I can just guess what might caused it. But, as usual, process of solving a problem in Linux makes you learn a lot about it.

Also, possible simple solution is (if you have no important data on them) to format both drives and reinstall operating systems.

---

### Post by billnj on 2008-04-05
Well, I was never able to fix my machine with Ubuntu 7.10 on it.  I tried the suggestions everybody provided and appreciate the help greatly.  Unfortunately, my novice computer skills were a bit lacking and I could never fix the problem.

I suspect that all I had to do is tell Grub where to find the boot information but I could never figure out how to do it.  I'm learning a lot but have a long way to go yet.

I repartitioned my 160 GB Maxtor hard drive into two 80 GB partitions.  I installed Fedora Linux on one of them and have been happily computing since then but I still want to go back to Ubuntu at some point.  I really like the Ubuntu community that I have encountered on the forum.  I may wait until the new long-term support version comes out before I try it again.  

Will I be able to install Ubuntu on my 2nd 80 GB partition and leave Fedora on the 1st one?  I also have Windows XP on a 13 GB hard drive but can't seem to switch to it unless I go into the set-up utilities and change the boot order.   I guess I'm still having some Grub-like difficulties.

Thanks to all who tried to help.

billnj

---

