---
title: "Working with the command line"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Darkness on 2006-03-27
Hello all.  

Thank you for all your work on this project.  I have yet to actually enjoy gnome in Breezy, but from what I have seen, it is quite nice. 

I installed Breezy on my Inspiron 5150 and have been reading and searching, but have not had success yet.  The problem is with my ATI card, and I have found the .deb file needed to fix me up (or I hope).  

Anyway, the real problem is that I do not have networking on the machine needing the .deb.  Therefore, I have to login to this computer and search for the files and help I need, then I have to return to the other computer and try to fix it.

When I installed Breezy, I reformatted my HD and made four partitions for windows and let the rest for Ubuntu (it was having problems with all of the junkware that Dell installs - which I subsequently uninstalled, apparently incorrectly at times). 

When I made the partitions for windows XP, I left one as fat32 (this required formatting with a windows 98 boot disk) so that I would have an easy repository on my own machine to move files back and forth on.

Anyway, when i downloaded the .deb I needed, I used my thumbdrive to transfer it to the other machine (logged into windows) and placed it on the drive I made for that purpose.

Then, I tried to log back into Breezy at the command line and cp the file from the other HD.  The problem is, that I am having problems 'seeing' the windows drive.  

The .deb is on /dev/sda6.  Do I need to modify fstab in order to mount this drive?  I tried sudo mount /dev/sda6 and this didn't work.  When I finally do get this drive mounted, where exactly should I cp the .deb to in order to extract it.  Are there any dependencies I should be aware of?  If so, it would be nice to hunt down those files first. 

FWIW, I am not new to the command line.  I learned almost all I know about computers from DOS 3.1 :).  However, this exercise is testing my patience and resolve ;-)  

Anyway, I _am_ new to linux though and just need a little push to get me rolling.  Thanks in advance for any help.

---

### Post by Darkness on 2006-03-27
Hmmm.  

Also, when I less fstab, it prints the contents and then stops with "(END)".  How do I break from this?  My computer just beeps at me no matter what I try.

TIA

---

### Post by akiro.yamamoto on 2006-03-27
This entry on the Ubuntu Official Wiki should get you where you need to go.
[** Windows Partitions**](https://wiki.ubuntu.com/MountingWindowsPartitions)

The wiki and these forums are great sources of info...
Also check my Sig ... ;)

---

### Post by Sutekh on 2006-03-27
[QUOTE=Darkness]
The .deb is on /dev/sda6.  Do I need to modify fstab in order to mount this drive?  I tried sudo mount /dev/sda6 and this didn't work.  When I finally do get this drive mounted, where exactly should I cp the .deb to in order to extract it.  Are there any dependencies I should be aware of?  If so, it would be nice to hunt down those files first. [/QUOTE]
OK you are kind of in between two methods of mounting

```
sudo mount /dev/hda6
```assumes there is an entry in the /etc/fstab and will try to mount /dev/hda6 according to this line.  If such a line doesn't exist, then you get an error.


If you want to mount the partition, you can either use
```
sudo mkdir /media/hda6
sudo mount /devhda6 /media/hda6 -t vfat -o iocharset=utf8,umask=000
```
This will mount the partition to the folder /media/hda6, which must be created prior.  The -t vfat lets mount know that the filesystem is FAT, and the -o iocharset=utf8,umask=000 allows reading of special characters and allows full access to the partition.


OR if you wished to make the mounting of /dev/hda6 permanant then you should consider editing the /etc/fstab
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```and adding this line in
```
/dev/hda6 /media/hda6 vfat iocharset=utf8,umask=000 0 0
```
Then refresh the mounted partitions using (no reboot necessary)
```
sudo mount -a
```


When you copy the .deb over, you can copy it anywhere you like.  You can then install it using
```
sudo dpkg -i <packagename>.deb
```

Unfortuntely you will have to fix dependencies yourself.  What is the package you wwant to install and where did you get it from?

---

### Post by akiro.yamamoto on 2006-03-27
Don't use less....
```
 sudo nano /etc/fstab 
```
To modify your fstab when you cant access it from the GUI...
Hope this info helps ;)

---

### Post by Wolki on 2006-03-27
[QUOTE=Darkness]Also, when I less fstab, it prints the contents and then stops with "(END)".  How do I break from this?  My computer just beeps at me no matter what I try.
[/QUOTE]

Use "q" to exit less.

Not really sure about your other problem. Try mounting the partititon to a certain place, like "sudo mount /dev/sda6 /media/sda6". You'll need to create /media/sda6 before that with a command like "sudo mkdir /media/sda6". If the mounting still doesn't work, try adding the filesystem type option, for fat32 something like this:
"sudo mount -t vfat /dev/sda6 /media/sda6". If that works, you can put the filesystem info into the /etc/fstab so the partition will be mounted automatically. Take a look at the wiki page for more info: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

I don't know if you need any more depeendencies. If its a deb you downloaded from ubuntu repositories, you can use packages.ubuntu.com to list dependencies. Use "apt-cache policy <packagename>" to see what version of a certain package you have installed, use the exact names from packages.ubuntu.com for this. And yes, manually resolving dependencies sucks, but there's stuff in the works to fix that.

After you have access to the .deb, install it with "sudo dpkg -i <filename>". You can autocomplete filenames with the tab key, pressing it once when only one filename is possible it will autocomplete, pressing it twice when there are severeal options it will display all of them. This is handy, not only will it save you a lot of typing, you'll also have less mistakes from mistyped filenames. :) 
dpkg will also complain if you lack some dependencies, so you can use this instead of manually checking everything.

---

### Post by Darkness on 2006-03-27
[QUOTE=Sutekh]What is the package you wwant to install and where did you get it from?[/QUOTE]

xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11.1_i386.deb

Can't recall from where I got it, but I followed a link from here.

I am not able to start X because of problems with my ATI 600x video card (or I am pretty sure that's the problem.  It seems to be the case because I am having the same problems as others.

Thanks for the responses so far.  I gave up the last two days because I didn't want to get frustrated.  

Can anyone help be break from the less command.  It is still stuck at "(end)".  This is where I gave up last night.

---

### Post by Darkness on 2006-03-27
[QUOTE=Wolki]Use "q" to exit less.[/QUOTE]

Thanks so much.  I tried many combinations of keys.  Don't know why this escaped me.

I also have the book "Linux in a Nutshell" but, it seems to be geared more for people with experience.

Thanks again.

---

### Post by Sutekh on 2006-03-27
[QUOTE=Darkness]xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11.1_i386.deb

Can't recall from where I got it, but I followed a link from here.

I am not able to start X because of problems with my ATI 600x video card (or I am pretty sure that's the problem.  It seems to be the case because I am having the same problems as others.

Thanks for the responses so far.  I gave up the last two days because I didn't want to get frustrated.  

Can anyone help be break from the less command.  It is still stuck at "(end)".  This is where I gave up last night.[/QUOTE]
Okay I can fix the ATI problem too.  This is only a quick fix, but will get X working until you can sort out the ATI drivers, through mounting, dpkg etc.

Okay you need to change the driver that X is currently using.

First backup and edit the X configuration file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```
 - When prompted for a password use your user's password

 - Those commands are case sensitive so make sure its X11 not x11 (or just copy and paste the commands)


When the file opens move down until you reach the section entitled
```
Section "Device"
```
Change the line that contains
```
Driver "ati"
```or whatever it may be to```
Driver "vesa"
```

Save the file (Ctrl+O) and exit (Ctrl+X).

Then restart X using Ctrl+Alt+Backspace (not Delete, this doesn't restart the PC, just the X server)


If you get into Ubuntu, then you are halfway there.  Those "vesa" drivers are just the quick fix.  You can try this HOWTO

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)

It will be difficult because you are offline, but you can download the packages and their dependancies and install them using dpkg

---

