---
title: "Cannot Log on to Dapper"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by adam s on 2006-06-19
Hi,


I have been using Dapper for about two weeks on my spare PC and I tried to log on yesterday and could not manage it. I do not get an incorrect password/username error.

The screen goes to a command line terminal (full page no GNOME screen at all) and indicates that it is logging into my computer and then goes back to the log on screen with no errors showing.

I cannot even log on using the terminal only option.

I would like to copy off some files from this PC and I was wondering if any one has any ideas. I have tried logging on to the LIVE CD and then reading the files there - but I cannot see them ther either through the terminal or Nautilus.

Any ideas will be much appreciated.

Thanks in advance,

Adam.

---

### Post by anaconda on 2006-06-19
You can boot with a live CD, and copy all the files you need to another partition or wherever..

Did you mount your linux partition.. (sorry haven't used ubuntu liveCD) Knoppix liveCD mounts all partitions automatically.. I suppose ubuntus liveCD does also? But if it doesn't you must mount the partition before you can access it.

If you have forgotten your password.. have you tried logging in as "single" (boot option (in Grub)) Again I am not sure if booting as single is supported in ubuntu.. never tried it. (My bacround is from other linux distributions..)
But usually booting with single lets you boot to terminal with root priviledges..  (worth a try)

---

### Post by halfvolle melk on 2006-06-19
From the live CD you can go System > Administration > Disks. You may be able to access your data from there.
You could also try to boot into the fail safe kernel; somewhere at boot time press Esc(I think) and select the right kernel. If this allows you to log in, maybe can try to fix whatever is broken.

---

### Post by adam s on 2006-06-19
Thanks guys,

I have now managed to get to my files - by mounting the hard drive through System > Administration > Disks.

I just have to work out how to record this stuff to CD as Nautilus doesn't allow me to and I do not know the Linix commands for this :-) Time for the rest of the web.....

I have found that if I use the command sudo su root from a terminal I can do anything I want to with my hard drive files. Surely this is a major security risk (although useful to me at the moment? 

Should I mention this to anyone in particular? or will someone appropriate pick it up from this forum?

Thanks in advance again,

Adam.

---

### Post by anaconda on 2006-06-19
I tried it, and booting as single works in ubuntu (at least in 5.10) it booted to a terminal with root rights. If your problem was that you had forgotten your password, then you could log as single, and type:

adduser

and then answer the guestions.. eg, new username, password, name etc..  And then boot and log as the new user which you just created....

> 
have found that if I use the command sudo su root from a terminal I can do anything I want to with my hard drive files. Surely this is a major security risk (although useful to me at the moment?
 

That is the purpose of "sudo su" eg to give the user root rights, so that you can do administrative operations, without ANY restrictions. If you boot from hard-disk, then it asks for the password, before you get root rights. And if you boot with liveCD you can get full rights to the hard-disks in that computer. 

Security is considered to mean: Secure from attacs from the net. If someone gets physical access to your computer, then he/she can do what he wants. Unless if you have encrypted your hard-disk, and prevent booting from CD/USB/floppy from bios and disaple unauthorizes access to bios..  Even then the intruder can steal your hard-disk, and try to crack your encryption...

---

### Post by adam s on 2006-06-19
Thanks for the info,

I have the same problem now when I log in as a single or through the live CD.
When logged in as root, when I type in the command :

cdrecord -scanbus

I receive a long story about known issues in version 2.5 and newer .... but the main issue is the error :

No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.

Does anyone know another way that I will be able to offload 300Meg of data off this hard drive.

I do not get the same error that one does when you type in a correct password. I also created a new user just in case and I could still not get into GNOME.

Thanks,

Adam

---

