---
title: "&quot;unable to mount volume&quot;"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by boxxy27 on 2008-02-02
Alright im in some serious help as i have my 320GB external hard drive useless right now to me and its full of stuff that I really need...

Ok anyway when Ubuntu tries to mount the volume i get this error:

Record 5 has no FILE magic: Input/output error Failed to mount '/dev/sdb1': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g./dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details...

So what iv done is booted into windows...but windows can see the hard drive but it cant run chkdsk as it says the volume is corrupted or something through command promt...

I tried to recover the hard drive and the programs in windows can see all the files...its readable and i can re-format it but i dont want to as i dont want to lose any of the information stored on the hard drive...

I heard something about ntfsprogs....which i downloaded but i dont know what to do with it...

please help me if you can thanks

---

### Post by dstew on 2008-02-02
What kind of external drive is it? A USB drive? Can you read files on the external drive? Can you copy the files to your internal hard disk? It seems that both Windows and the Linux NTFS programs are saying the same thing: The disk seems to be corrupted. So it seems best to try to get the files off it, and repair it if possible.

---

### Post by Desperate on 2008-02-02
Check before you follow my advice, but I came three weeks ago to Ubuntu to rescue my wrecked XP ATA RAID hard disks.
I used the Ubuntu life CD and loaded/installed DMraid. Actually you can see it all here and that saves me the typing :)

[http://ubuntuforums.org/showthread.php?t=682096](http://ubuntuforums.org/showthread.php?t=682096)

No warantee, but somewhere in that line should the solution be.
I'm now running XP again and looking for a solution to install Ubuntu without reinstalling XP.

Good Luck and if.. drop me a note here or pm me.

---

### Post by boxxy27 on 2008-02-02
no...i can only see the files if i use a recovery program which im not use to and the ones that i found were not free......

OH yeah and its usb

Linux recognizes the hard drive as the name "External" which i named it, and it also recognizes the NTFS partition, windows doesnt...just says its raw data until i use some program

---

### Post by boxxy27 on 2008-02-02
im not quite sure how to do this...

After loading/installing DMRAID I opened a terminal to type:
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_bccebhcagd_RAID0" already active
RAID set "isw_bccebhcagd_RAID01" already active
ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo gedit /etc/fstab
** and added the line:
** /dev/mapper/isw_bccebhcagd_RAID01 /media/windows ntfs-3g defaults,force 0 0
** and saved it of course
ubuntu@ubuntu:~$ sudo mount -av /dev/mapper/isw_bccebhcagd_RAID01
ubuntu@ubuntu:~$ 


that and i dont know what DMRAID is....

---

### Post by Desperate on 2008-02-02
Google or read
DMraid will make a ATA RAID Volume acceptable for Ubuntu.

dmraid or sudo dmraid will activate those but to see for yourself type dmraid -h in a terminal and that will partly explain it.

the option -ay = activate yes
Now Gparted will recognize it as a possible volume, but it will not load/mount it as it is (a bit) corrupted. Like me you still have all your files when you check with ntfs4dos or something like it.
The right name you'll find in /dev/mapper/  and after clicking on properties you can copy it to you terminal (I'm very lazy and don't type much)

I tried to use the Check option in Gparted, but I could only do that with the wrong "name"  isw_bccebhcagd_RAID0 and gparted chrashed
I never tried it with that RAID01 volume as gparted wouldn't even mention it as NTFS.

Then I ran in to the *sudo mount -av* option that will tell you what's wrong and what you should do to make it right. Add a line to /etc/fstab   with *sudo gedit /etc/fstab*, make a place to mount it  *sudo mkdir /media/windows*  and try it again and suddenly I had a drive called windows on my desktop :)
I don't know if we have the same problem or what will happen on your machine when you follow it, but I was hoping that some of the Linux Guru's would see the thread and comment with possible help and/or warnings.
Once I had my drive in Ubuntu I made backup dvd's to save my 15.8 gig of needed data. Then I rebooted the machine and tried the windows option and everything was there :)


Edit : some links with info
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by DO55 on 2008-03-12
i have same problem with my external HDD  
the HDD was work ok but now it is not work 
please help

---

### Post by DO55 on 2008-03-13
help

---

### Post by DO55 on 2008-03-13
help

i cant use the HDD

---

### Post by DO55 on 2008-03-14
help

---

### Post by DO55 on 2008-03-14
help

---

### Post by Berean on 2008-03-14
Hi, I've had problems mounting an external hard drive and ended up performing the following;
sudo /etc/init.d/hal restart (obviously in the terminal).  This enabled me to see the contents of the drive, but - unclear on why it keeps stopping hal - have to type the command each time I want to mount the drive. My external drive is USB connected. This may work for you - I hope so - but being relatively new myself, I can't guarantee anything.  Good luck!

---

### Post by DO55 on 2008-03-14
also it dose not work 

thank

---

### Post by DO55 on 2008-03-15
help

---

### Post by DO55 on 2008-03-16
help

---

### Post by Berean on 2008-03-16
DO55, might I suggest that as you've posted a few times in this thread already (and not got an answer) that you start a new thread in Absolute Beginner Talk?  Someone, I'm sure, will help you, if not an administrator.  Unfortunately, your problem is beyond me, but I wish you good luck and God speed.  Regards.

---

### Post by DO55 on 2008-03-17
thanks :)

good idea

---

