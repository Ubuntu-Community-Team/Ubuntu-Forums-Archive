---
title: "Problem with DVD Disc"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by snake444 on 2007-07-28
I bought today dvd writer to the computer and connected it
and the ubuntu in my computer i saw the new device
and i burned disc with K3b with the name of FIlmi and he was 4.1gb
then i wanted to watch the movies on the dvd and when i tryed to run the dvd from my computer
i got this error:
[http://img267.imageshack.us/img267/7707/screenshotwq9.png](http://img267.imageshack.us/img267/7707/screenshotwq9.png)
and i cant watch it from the totem and other players
and when i do properties for the disc i see that he has label filmi and he is 4.1gb size so i dont think that the problem is in the disc
so how to fix that problem?

---

### Post by mikeyphi on 2007-07-28
DVD films are often 'copy protected' so that even if you manage to burn a copy you will be unable to play it without using the original disk.

---

### Post by snake444 on 2007-07-28
if its copy protected why i have mount problem and not drm or something?
i can see the movie from the computer but cant from dvd disc?

---

### Post by snake444 on 2007-07-28
anybody???? i just need to solve that mount problem because it doesnt mounts the dvds

---

### Post by Mornedhel on 2007-07-28
From the "no newline" problem, I'd say maybe your /etc/fstab needs fixing. Could you post its contents here ? (The file is /etc/fstab, you may view its contents by typing at a terminal gksudo gedit /etc/fstab, it will ask for your password.)

---

### Post by snake444 on 2007-07-28
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8329c5df-4390-45e6-af17-1510e26ee0f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=522ae50a-e0cc-42ce-b290-4a85cf4d7161 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

btw what is the gk before the sudo means?

---

### Post by NutrOn on 2007-07-28
I have a dvdrom cdrw drive with the no mount problem and here are the results of a few commands for any one interested. PS I am on fiesty
mount: block device /dev/hdc is write-protected, mounting read-only
lewis@ubuntu:~$ mouont
bash: mouont: command not found
lewis@ubuntu:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev)
lewis@ubuntu:~$ mount /media/cdrom0
mount: must be superuser to use mount
lewis@ubuntu:~$ sudo mount /media/cdrom0
mount: block device /dev/hdc is write-protected, mounting read-only
mount: /dev/hdc already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0

---

### Post by snake444 on 2007-07-28
nobody have a solution??:confused::mad:

---

### Post by Mornedhel on 2007-07-28
snake444, did you try mounting from the CD-ROM one ? I take from your screenshot that you've been trying to mount from CD-RW. Now the weird thing is that, according to your fstab, you only have one CD drive, is this true or is the fstab wrong ?

NutrOn, I suppose you cannot access the contents of your CD either. The automount may have mounted it before you tried, so if just inserting a CD is not enough for you to browse its contents, then we do have a problem. As for its being read-only, that's pretty normal considering it's a CD, not an HD. When you type "mount", it lists what devices are actually mounted, so if you see /media/cdrom0 there, it's mounted already. Could you confirm that you actually cannot see the contents after having mount return an entry under /media/cdrom0 ?

---

### Post by snake444 on 2007-07-28
i got  1 cd rom and 1 dvdrw rom
the cdrom works good and the dvdrom i bought today and only plugged to the computer
without any drivers\configs\settings
and then i burned one dvd disc with 4 files
and i the cdrom cant read dvds and the dvdrom gives the error like in the screenshot
maybe i need to install\config something? because as you said on the fsab theres only the cdrom
so how can i do that there will be the dvdrom too? 
btw the burn process was good and i think the dvd disc is good but i didnt checked him coz the only dvd i have is that dvdrom..

---

### Post by snake444 on 2007-07-28
i tryed to put in the dvdrom a regular cd and it mounted it
so why doesnt it mountes the dvd i burned with k3b?

---

### Post by mgmiller on 2007-07-28
Your fstab only shows one optical disk.  Did you install the new DVD writer on the same data cable as the CD rom drive?  If you did, you need to check the jumper settings on both drives.  One needs to be master and the other needs to be slave.  If the CD rom and DVD burner are on separate cables, then both need to be set as master.  Usually, burners work more reliably when they are master.  Often new drives come with the jumper set to CS which means cable select.  This often gives very weird behavior.  Take a look on the top or back of the drive, there will be a little diagram somewhere that shows the correct jumper settings.  Make sure the machine is turned off before you poke around or try to change the jumpers.

---

### Post by anewguy on 2007-07-28
Is this an external write?  If so, you may have to mess around with the USB stuff in fstab.:)

---

### Post by mgmiller on 2007-07-28
> Is this an external write? If so, you may have to mess around with the USB stuff in fstab

I disagree, external USB drives are not mounted in fstab.  If they don't auto mount on powering on the external device you would use the pmount command to get them to mount.

Here is how it's done:

First, you need to figure out where it is being seen in /dev
so run the command:
```
sudo fdisk -l
```

and look for the entry for the drive.  You may need to unplug and replug the USB cable for it to appear.

Once you know the device name use the pmount command to mount it.

If the fdisk command showd you the drive is /dev/sdg and you want to mount it as "backup"
enter the command:
```
pmount /dev/sdg1 backup
```

Look in /media and you will see a new folder called backup.  

To unmount the drive, use the command pumount with the name of the mount point.
For our example:
```
pumount backup
```
and the entry should dissapear from /media

You can now make buttons for your panel to mount and unmount and save a bookmark in nautilus for the mounted location to semi automate the whole thing.  

I didn't get the feeling the OP was using an external drive though.  :popcorn:

---

### Post by anewguy on 2007-07-28
Having no experience at it (USB external drive), I was just going on what I've read on a couple of other posts - something about mounting a USB file system in fstab.  I guess those things must either be wrong or apply to something else.  At any rate, thanks for providing info on using a USB external device!:)   I'll book mark this page, as I do plan on getting an external DVD/RW next year for use on my laptop.

---

### Post by mgmiller on 2007-07-28
> At any rate, thanks for providing info on using a USB external device! I'll book mark this page, as I do plan on getting an external DVD/RW next year for use on my laptop.

You're welcome.

The instructions I posted only apply if you plug in the external USB drive and it doesn't automount when you power it up. Most of them will.  I needed to use this info when I ran across a USB harddrive that would not auto mount.  I never tried it with a burner, but I don't see why it wouldn't work.  

To head off any potential problems ](*,), try googling the brand you are interested in getting to see if there are any Linux compatibility problems.  You're always best off getting hardware that is Linux friendly and "just works".  Newegg.com is a good place to look for user reviews.

---

### Post by snake444 on 2007-07-29
i switched the jumper to slave and now the dvdrom doesnt appear on My Computer
but when i click on the eject button physsicly it ejects the cd

---

### Post by mgmiller on 2007-07-29
> i switched the jumper to slave and now the dvdrom doesnt appear on My Computer

Please answer each of the following questions. 

1) Which jumper did you change?  
2) What are the jumper settings for each of the 2 drives?  
3) Are they on the same or separate cables?
4) My Computer is a reference to Windows.  Are you dual booting?  
5) Does the drive show up in Places > Computer?


> when i click on the eject button physsicly it ejects the cd

What eject button?  On the drive? 

Please tell me if you have changed anything in your /etc/fstab, or if the one you posted earlier is still correct.

Let's get the hardware sorted first, then we can work on getting your etc/fstab to correctly list everything.

---

### Post by snake444 on 2007-07-29
1) I changet the jumper of the dvdrom it was master now its slave
2) dvdom is slave, cdrom i dont know but i think that master ill check in few mins
3) same
4) i have only ubuntu installed on the pc and i added my computer icon to the desktop (location is computer:///)
5) the drive was showen there when the jumper of the dvdrom was at master, now when its slave it doesnt shown
6) yes the one on the drive

and i didnt changed anything in fsab

---

### Post by mgmiller on 2007-07-30
ok, here is what I would like you to try.

Please read everything before doing anything.

1st make a backup of your fstab:
```
sudo cp /etc/fstab fstab.backup
```

I made 2 changes to your fstab file.  the first adds a line for the DVD burner and the second changes the line for the cdrom to reflect its new position in the IDE chain.

Next you are going to edit your fstab file  by running:
```

gksudo gedit /etc/fstab
```

erase the entire contents of the file and paste in the following:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=8329c5df-4390-45e6-af17-1510e26ee0f7 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=522ae50a-e0cc-42ce-b290-4a85cf4d7161 none swap sw 0 0
/dev/hda   /media/cdrom0  udf,iso9660  ro,user,noauto    0  0
/dev/cdrom /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```

Save the file and turn off the computer.

Change the jumpers so the jumper on the DVD burner is master and the jumper on the CD rom is slave.  make sure their cable is plugged into the primary IDE controller port on your motherboard, if there is a choice.  Some mobos only have 1 IDE controller port, others have 2.  The primary port is often blue, while the secondary is black.  There will probably be tiny writing silk screened onto the mobo to identify which is which.

Close it up and reboot.

Everything should now work.  :popcorn:

---

### Post by snake444 on 2007-07-31
i did it now there is more one cd rom drive
look at this screen :
[http://img160.imageshack.us/my.php?image=screenshotga6.png](http://img160.imageshack.us/my.php?image=screenshotga6.png)
the "CD-ROM1" is the new one that gives the left error in the next screen
the "CD-ROM Driver" is the cdrom drve in the computer
and the CD-RW/DVD±RW Drive is the one that doesnt mounting, and the error is still continiues showing every time
[http://img505.imageshack.us/my.php?image=screenshot1ho0.png](http://img505.imageshack.us/my.php?image=screenshot1ho0.png)

---

### Post by snake444 on 2007-07-31
whoohoo upgrading to gusty solved the problem :D
i upgradet with [http://ubuntuforums.org/showthread.php?t=501893](http://ubuntuforums.org/showthread.php?t=501893) :)

---

### Post by mgmiller on 2007-08-01
> whoohoo upgrading to gusty solved the problem 
:lolflag:
OK then....  Once the hardware was sorted out, the OS upgrade fixed it for you.  
Good luck with Gutsy...It's a little too premature for me to make that move.

That's a really nice looking desktop, by the way.  What are your Theme settings?
I especially like your window borders.  I am currently running Compiz, I see you are running Beryl.  Hopefully I can use the same window border you have.

---

### Post by snake444 on 2007-08-01
theme is here [http://www.gnome-look.org/content/show.php/Vista-Linux?content=42875](http://www.gnome-look.org/content/show.php/Vista-Linux?content=42875)
the wallpaper is from wincustomize.com its called fell the fire skully
i downloaded it like 2 years ago so if it doesnt exists send pm ill upload it to you

---

### Post by mgmiller on 2007-08-02
Thank You.

---

