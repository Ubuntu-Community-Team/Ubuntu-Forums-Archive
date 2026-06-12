---
title: "Moving to Ubuntu - some questions"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by R00tKid on 2008-02-13
Hi, new to Linux and Ubuntu but learning rapidly... have read No Starch Press Ubuntu for Non-Geeks and Ubuntu Hacks.  Some things I still don't get or understand - 

- I have a DLink DNS323 NAS on my network (@home).  How do I get my PC to connect to it both when logging on or after logging on (I want to mount one directory at logon and another only when I need to access it infrequently).  The NAS is set up with different privileges/directories for the users - how can I 'link' the user to the directories?

- I have an AMD64 machine and the forums here suggest that this may require some 'special' attention to get it working with the 64-bit distro.  However, most of the messages were dated over 12-14 months ago.  Is this still the case now?

- I plan to set up a dual-boot initially so that I continue to have access to my real work.  If at some point, I decide to take out either Ubuntu or WinXP completely, how difficult is it to do it without having to backup all the data or wiping out data/configurations?

Thanks

---

### Post by dca on 2008-02-13
If you're talking about auto-mounting a volume on start-up you can look into the contents of the /etc/fstab file on any Linux distro.  Learn what each switch and toggle does...  This kinda' explains some.
 
[http://www.newlinuxuser.com/explanation-the-fstab-file/](http://www.newlinuxuser.com/explanation-the-fstab-file/)

---

### Post by lamego on 2008-02-13
"- I have an AMD64 machine and the forums here suggest that this may require some 'special' attention to get it working with the 64-bit distro. However, most of the messages were dated over 12-14 months ago. Is this still the case now?"
There are no special considerations specific to AMD64, there maybe considerations related to your mother board chip set and for some (non open) applications witch do not provide 64 bits binaries.

---

### Post by alenis on 2008-02-13
The DNS323 uses Samba to share its files, so you need to install this protocol on your machine. Then you should edit your /etc/fstab file inserting a line similar to this one:

//192.168.0.32/data /media/nas/data cifs credentials=/home/username/.smbpasswd,uid=username,gid=username 0 0

where 192.168.0.32 is the (default) address of the NAS, data the samba share and /media/nas/data the mount point. credentials specifies the userid and the password needed by user 'user' to access the share on the NAS.
.smbpasswd is a simple text file containing:
username=name
password=xxxxxxxxx

Now you should be able to see the NAS at boot time and to mount it with 
sudo mount /media/nas/data

---

### Post by R00tKid on 2008-02-14
Thanks everyone, for the responses.  I took the plunge yesterday and installed Ubuntu AM64 in a dual boot mode.  When I first did that, it would boot right into Windows.  Finally I deleted the linux partition using Acronis Disk Director, installed Acronis OS Selector, then re-installed Ubuntu.  Now it provides me the option of selecting the OS I want to boot into. I wish I could do without the OS Selector but for now, I am okay.

For some reason, it detected the NAS (under Network in Nautilus) and I was able to mount/access it.  Quick question, is it okay to write into the Windows NTFS partition or are those meant for read only?  I have read about the NTFS Partition Write Support utility and was wondering if without it, I am not allowed to write there.

WOW!!!  This thing is sexy!!  I turned on all the visual effects and the experience is mid-blowing. I have 4 GB of RAM and with the full visual effects on, it is still way way faster than my performance-tweaked/no visual effects Win XP - apps start up almost instantenously.

Other issues - can I burn an Audio CD from Rhythym Box or do I have to use  the Serpentine tool to do that?  I was trying Serpentine last night and for some reason, it would not accept any of my MP3 files - does it not reencode into WAV automatically or is accessing the MP3 from NAS an issue?  I could not drag and drop the songs from Rhythym Box into Serpentine either....

---

### Post by Mad_Dawg on 2008-02-14
> **R00tKid said:**
>   If at some point, I decide to take out either Ubuntu or WinXP completely, how difficult is it to do it without having to backup all the data or wiping out data/configurations?

ALWAYS back up your data when doing something like this. Just in case.

---

### Post by Alex_Fingers on 2008-02-15
"- I have an AMD64 machine and the forums here suggest that this may require some 'special' attention to get it working with the 64-bit distro. However, most of the messages were dated over 12-14 months ago. Is this still the case now?"

I have an AMD64 and the only problems I've had relate to installing Flash plugin and programs that run in the Java Runtime Environment - you need 32-bit work-arounds for these. I didn't find it very hard to solve these problems - just persistence in following the right instructions on ubuntuforums.. Good luck !

---

