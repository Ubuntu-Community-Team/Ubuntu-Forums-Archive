---
title: "VMware using Physical IDE:ErrorMsg : Grub - Error 17  - HELP- !!"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-02
VMware: boot Physical IDE but gives Grub - Error 17 
________________________________________

I am doing VMware with my physical harddisk of winnt 2000

but unfortunatly, it's not working ... 
when i start the VMware, it says : 
(black screen)
 
Grub loader 1.5
  
Error 17
 
Is there a genius who could help me for my big problem to run VMware ??

Thank you very very much !!

Pat'

---

### Post by mlomker on 2005-10-03
What is the output of **sudo fdisk -l** and what partition did you specify in your virtual machine?  

If you use your main boot disk then it isn't going to work.  You shouldn't see anything about grub when booting Windows.

---

### Post by patrick295767 on 2005-10-03
[QUOTE=mlomker]What is the output of **sudo fdisk -l** and what partition did you specify in your virtual machine?  
If you use your main boot disk then it isn't going to work.  You shouldn't see anything about grub when booting Windows.[/QUOTE]

First, thank you for your reply 

v. fast ...:
my /dev/hda is as follows:

partition 1: 100Mb  hd0 (bootable) with a boot.ini

partition 2: 10GB   WINNT2000 Operating system NTFS

partition 3: 50GB   NTFS  Data

partition 4: the rest of GB for Linux UBUNTU


(since installation of linux, i still have to review the partitions to make my swap, but linux ubuntu is installed still rather experimentally )

the vmware is set up with for the two partitions boot 100mb part1 and partition2

I also tried the MSDOS (from my boot.ini) of the partition1:
result : same message ERROR 17
this means that the ERROR 17 is independant of the partition
it shoudl certainly be due to the Grub located in the MBR

(the rest of my reply in few hours with cmd fdisk ... )
see ya

---

### Post by patrick295767 on 2005-10-03
Hi, 

I found this web page concerning vmware ...

I set up my vmware with 2 partitions (not whole disk).

----
pat'

---

### Post by patrick295767 on 2005-10-03
[http://forums.gentoo.org/viewtopic-t-246371-highlight-ntfs%20vmware.html](http://forums.gentoo.org/viewtopic-t-246371-highlight-ntfs%20vmware.html)

---

### Post by patrick295767 on 2005-10-03
after [http://www.vmware.com/community/thread.jspa?messageID=80274&#80274](http://www.vmware.com/community/thread.jspa?messageID=80274&#80274)

I have feelings that I can give up 

I lost hopes after reading in forums ...

---

### Post by mlomker on 2005-10-03
[QUOTE=patrick295767][http://forums.gentoo.org/viewtopic-t-246371-highlight-ntfs%20vmware.html](http://forums.gentoo.org/viewtopic-t-246371-highlight-ntfs%20vmware.html)[/QUOTE]

That is an interesting post.  I don't have a dual boot machine (I run Windows in a VM), so I don't have any suggestions.

---

### Post by patrick295767 on 2005-10-03
[QUOTE=mlomker]That is an interesting post.  I don't have a dual boot machine (I run Windows in a VM), so I don't have any suggestions.[/QUOTE]
   
   
   
   
That's it !!!! :-)
Great !!! 
So, the trick is as follows : 
         In order to enjoy the fully Linux world at 100% and also using the fast vmware (i am very impressed), 
         and your physical partitions (windows nt or xp), the thing is that it should be set up not only one or two partitions but the whole hdd ( /dev/hda ) !!
   
     So, then, the vmware is booting first on the grub, then u can select windows or linux, then, it's passing via the boot.ini, your select the OS you wanna work with and that's it !!!
Windows Onto Linux !!
 
I hope that it will help some people who have some 'error 17' problems too !!
     
 Thank you for your advices mlonker again !

Patrick.

---

### Post by dkavraal on 2007-07-22
Hi,
It's weird that I could not get it working as you have done, patrick.
In fact, I was getting error 17, as I was choosing partition mode. When I have choosen entire disk, and on boot selected "windows", I get a new error:
"Starting up ...
A disk read error occurred
Press Ctrl+Alt+Del to restart"

I am now unable to start windows.

Any suggestions?

---

### Post by perfran on 2008-06-20
Thanks a lot patrick29...
I've had this error since a long time now it's solved :)

I've still a problem: I can't boot from a CD , it boots directly grub of this HD and does not boot on the ISO image I mounted in the cd drive of vmware :(

---

