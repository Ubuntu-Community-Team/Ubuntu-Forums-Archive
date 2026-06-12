---
title: "Cant watch DVD Movies"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by pakora on 2007-08-25
My dvd rom drive doesnt work. When I went to system and then computer i clicked on my drive and it says

Unable to mount the volume. How do I fix this problem? Thank you

:KS

---

### Post by Happy_Man on 2007-08-25
Can we see the result of the command ```
cat /etc/fstab
``` please?

---

### Post by pakora on 2007-08-25
pakora@pakora-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=db42c6a3-508f-4233-a3e3-16cb320e15bd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b48dc015-8109-4cfc-aa84-557800925f11 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
pakora@pakora-laptop:~$

---

### Post by uclalinux on 2007-08-25
you need to install the dvd player file, 

in the terminal type the following:  aptitude install libdvdcss2 libdvdread3 libdvdnav4 vlc

if you are new to linux here is a good place for many of your questions you will have.  

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by pakora on 2007-08-25
> **uclalinux said:**
> you need to install the dvd player file, 

in the terminal type the following:  aptitude install libdvdcss2 libdvdread3 libdvdnav4 vlc

if you are new to linux here is a good place for many of your questions you will have.  

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)


When I tried that this is what response I got

pakora@pakora-laptop:~$ aptitude install libdvdcs2 libdvdread3 libdvdnav4 vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
pakora@pakora-laptop:~$

---

### Post by Dr Small on 2007-08-25
Run:
```
sudo aptitude install libdvdcs2 libdvdread3 libdvdnav4 vlc
```

---

### Post by ritterrav on 2007-08-25
aptitude install libdvdcs2 libdvdread3 libdvdnav4 vlc

I think you need to throw a 'sudo' with out the '' before the code, and you will have to enter the pass then it will install.

---

### Post by pakora on 2007-08-25
Still doesnt work

Now says 

Unable to mount the selected volume

---

### Post by Dr Small on 2007-08-25
Do you have the DVD in the DVD rom drive?
If not, put it in, and then go to /media (if the DVD doesn't auto-play) and go into cdrom or cdrom0 and see if that works.

Dr Small

---

### Post by pakora on 2007-08-25
Im a noob with Linux.... do what!?

---

### Post by nonewmsgs on 2007-08-25
now on your desktop do you get a cd picture with the name of the dvd?  it should also be under places.  is it there?  (thats what he asked)

in movieplayer it should be there under file.  if it gives an error tell us or tell us what isnt working.

---

### Post by thefowlstar on 2007-08-25
Dr Small means for you to put a DVD in the drive, and then, using the GUI, go to /media/ . You do this by opening your Home Folder using the Places menu, then pressing Ctrl+L, and then typing in /media/ . In that folder, look for a folder called either cdrom, cdrom0, or something similar and try to open it.

lol. It's okay. we were all a noob once. :]

---

### Post by pakora on 2007-08-25
It shows folders in /media/

but nothing inside the folders.


still says my drive is not mounted how do I mount it!?

---

### Post by thefowlstar on 2007-08-25
Okay here are the instructions to mount it.

Make a new folder in /mnt/ called cdrom. You can do this using the command line by typing```
cd /mnt/
sudo mkdir cdrom
```

Then type this is to the terminal:
```
sudo mount -t iso9660 -o ro /dev/cdrom /mnt/cdrom
```

If it was successful, nothing will be returned to the terminal. You can then use whatever media player you use to open the DVD drive and hopefully it will work.

If it doesn't work, please post the error the terminal returns.

---

### Post by pakora on 2007-08-26
It gave me this error :(

pakora@pakora-laptop:~$ cd /mnt/
pakora@pakora-laptop:/mnt$ sudo mkdir cdrom
Password:
pakora@pakora-laptop:/mnt$ sudo mount -t iso9660 -o ro /dev/cdrom /mnt/cdrom
**mount: special device /dev/cdrom does not exist**
pakora@pakora-laptop:/mn

---

### Post by schorsch on 2007-08-26
According to the output of your fstab you gave a page ago:
"/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0"
you should try:
```
sudo mount -t iso9660 -o ro /dev/scd0 /mnt/cdrom
or
sudo mount -t udf -o ro /dev/scd0 /mnt/cdrom
```
Which command to use depends on the type of the disc.

---

### Post by Happy_Man on 2007-08-26
Instead of /dev/cdrom, use /dev/scd0.

---

### Post by pakora on 2007-08-26
pakora@pakora-laptop:/mnt$ sudo mount -t iso9660 -o ro /dev/scd0 /mnt/cdrom
mount: special device /dev/scd0 does not exist
pakora@pakora-laptop:/mnt$ sudo mount -t udf -o ro /dev/scd0 /mnt/cdrom
mount: special device /dev/scd0 does not exist
pakora@pakora-laptop:/mnt$

---

### Post by schorsch on 2007-08-26
What is the output of
```
lshw -C disk
```

---

### Post by pakora on 2007-08-26
when I ran lshw -C disk 

i was told I should run the program as a superuser

---

### Post by schorsch on 2007-08-26
```
sudo lshw -C disk
```
... but that is weird ... it should run without sudo ....

---

### Post by Happy_Man on 2007-08-26
It does, but the output is unreadable without sudo. :confused:

---

### Post by pakora on 2007-08-26
pakora@pakora-laptop:/mnt$ sudo lshw -C disk
Password:
  *-disk                  
       description: SCSI Disk
       product: HTS421240H9AT00
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: HACO
       serial: HKA070AHH1EHZG
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 35GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          size: 1608MB
          capacity: 1608MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 1608MB
             capabilities: nofs
pakora@pakora-laptop:/mnt$

---

### Post by pakora on 2007-08-27
Help Please :(

---

### Post by Happy_Man on 2007-08-27
Are you sure that /dev/scd0 isn't there? Go look in your /dev/ folder manually and find the proper name for it, whether it be cdrom, cdrom0, scd0, or whatever. Then use that.

---

### Post by pakora on 2007-08-27
couldnt find anything resembling that in the /dev/ folder

---

### Post by Kenobi on 2007-08-27
On ubuntu 6 there was a partition manager in the system tools menu that displayed every device and gave the option to mount it. I don't know how it was called... Maybe you should try to download any of these programs that do the stuff for you. It worked on my place.

---

