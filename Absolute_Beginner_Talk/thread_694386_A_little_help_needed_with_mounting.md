---
title: "A little help needed with mounting"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by UBeavUNTU on 2008-02-12
Hey everyone, Great Forum! I've never seen such a helpful community! :-D

I've been installing and uninstalling different linux distros for the past few weeks and it finally looks like ive found one that i'll keep, Ubuntu is fantastic! Ive run into a few niggles though :( It managed to pick up 4 out of 5 of my USB drives (the last one comes up whith the following error when i double click on it to view files:

 $LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdc1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have windows then disconnect the external devices by	clicking on the 'Safely Remove Hardware' icon in the Windows		taskbar then shutdown Windows cleanly. Choice 2: If you don't have windows then you can use the 'force' option for 	your own responsability. For example type on the command line:	mount -t ntfs-3g/dev/sdc1 /media/60GB HDD -o force	Or add the option to the relevant row in the /etc/fstab file:		/dev/sdc1/media/60GB HDD ntfs-3g defaults,force 0 0

Any ideas? :confused:

Also, it picked up my SATA drive but does not mount this for me, is there any way i can get it to mount on start up? and in fact how do i get programs/deamons to load on start up too?

Thanks to everyone who takes the time to read my ramblings and try and help me!! :mrgreen:

---

### Post by Jive Turkey on 2008-02-12
The fstab method with the force option should mount on startup.  In a terminal type ```
sudo gedit /etc/fstab
```
then add or edit the appropriate line for the device, save and close.  then back to your terminal, type:
```
sudo mount -a
```
and you should be good to go, hope it works for you.

---

### Post by UBeavUNTU on 2008-02-12
Ok 2 problems fixed, I went back in to windows (i couldnt find a tool to do the following in ubuntu) and renamed the unmountable HDD partition as i noticed it had a space in it... success, it now mounts fine

I also added the line:
/dev/sda1	/media/160GbSATA ntfs	rw,user,	0	0
to my /etc/fstab and it now mounts at startup :-D

Thanks for your help JiveTurkey!!

Ive also sorted my hotmail email through evolution using freePOPs to download the emails, then using filters in evolution its auto sorted into seperate folders/accounts and archived/backed up by an IMAP account on googlemail, all in all im happy with how it works. 

I still dont know how to get evolution to start at startup tho and also, is there a way to get it to minimize to the system tray? 

Any help would be great, Thanks! :)

---

