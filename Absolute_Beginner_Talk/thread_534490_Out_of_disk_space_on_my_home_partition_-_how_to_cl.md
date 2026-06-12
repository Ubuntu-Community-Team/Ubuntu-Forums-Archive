---
title: "Out of disk space on my home partition - how to clean up???"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by mmathur on 2007-08-25
My root partition ('/') is showing that it is a 100% full.  I have removed the files from the ~/.Trash bin and it is still showing up that it is 100% full:

Filesystem		Size          Used Avail   Use% Mounted on
/dev/sda1             	9.7G        9.6G     0     100% /
varrun                	   471M       276K  471M    1% /var/run
varlock               	   471M             0  471M     0% /var/lock
procbususb             471M       128K  471M     1% /proc/bus/usb
udev                  	   471M       128K  471M     1% /dev
devshm                	 471M            0  471M      0% /dev/shm
lrm                   	      471M        39M  433M      9% /lib/modules/2.6.20-16-generic/volatile
/dev/mapper/HTPC-media	    900G  687G  214G  77% /var/lib

Before I ran into this issue, I copied a large file (7Gigs) into my /var/lib folder and then deleted it using Nautilus (right clicked and deleted the file).  I have ran the following command to clear out the trash:
sudo rm -r ~/.Trash/*

Though the system is still showing up as a 100% full.  Can some one give me some other suggestions on what I can do to get that space back?  At this point, I can't login to my system since GDM doesn't have enough disk space to write to a file.

I am able to connect to my machine via putty and get a terminal.  Any suggestions would be much appreciated.  Thanks.

---

### Post by henriette_holm on 2007-08-25
You'll need to have a look around your disk to see what's taking up all your space. Maybe try using the find command. Use putty to connect to your pc. Make sure your in / and type:

find . -size +1024M

in the terminal. The example will give you all files bigger than 1 Gb. Look here:

[http://dmiessler.com/study/find/](http://dmiessler.com/study/find/)

for more examples.

/Henriette

---

### Post by southernman on 2007-08-25
If you have a livecd handy boot the machine with it. Make a directory for your root partition and mount it. cd to the .Trash folder and remove the file

---

### Post by henriette_holm on 2007-08-25
> **southernman said:**
> If you have a livecd handy boot the machine with it. Make a directory for your root partition and mount it. cd to the .Trash folder and remove the file

He/she already did that.

/Henriette

---

### Post by Dr Small on 2007-08-25
Ubuntu is case-sensitive about it's commands.
You could try running:
```
sudo rm -R ~/.Trash/*
```

Notice the capitalized r.

Dr Small

---

### Post by southernman on 2007-08-25
> **henriette_holm said:**
> He/she already did that.

/HenrietteJust suggesting a different way to do it. ;)

Also try the remove command with the -rf option too instead of just -r... see if that'll help.

---

### Post by mmathur on 2007-08-25
Also, just before I ran into this error, I started a rsync to backup some data, but it failed since I ran out of space.

Does rsync create a temporary folder where it stores the files before copying them?  I know it builds a file list, but I wouldn't imagine the list to be so large that it would be over a few hundred MBs.  Let me know if there is something with rsync that I can delete/remove.  Thanks.

---

### Post by mmathur on 2007-08-25
I solved the issue!!!

in my /etc/fstab file, I map to a NAS.  I commented out the mapping restarted and the system was still not able to login.  I connected via putty and navigated to the mount point where the NAS is usually mounted and I was able to navigate through a folder structure (which didn't match the real folder structure).

Either way, I removed all the files (using sudo rm -r) under that directory and now the system has 6.2Gigs free out of the 9.7!!!

But now, i've got another error...which I think stemmed from me trying to login with other sessions.  I'm getting the following message box when logging in:

"Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean there is an installation problem or that you are out of disk space..."  and the message says something like there may be an installation issue or you may be out of disk space.  Any suggestions on this one??

---

### Post by henriette_holm on 2007-08-27
Try having a look at this:

[http://ubuntuforums.org/showthread.php?t=521803](http://ubuntuforums.org/showthread.php?t=521803)


or do a forum search. This is sort of a know issue (had it myself once) so you should be able to find a way to fix it.

/Henriette

---

