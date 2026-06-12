---
title: "Error message when Gnome desktop has loaded: &quot;Failed to initialize HAL&quot;"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by patslap on 2006-09-25
Hi 

Gnome boots up at normal speed, but when my desktop appears i get a "Failed to initialize HAL" message.

I've looked at lots of threads to try and fix this myself, but I just don;t understand the posts (they mention smb, smbfs, samba, etc/fstab, and it's all a bit beyond my level of knowledge), hence my post here in noob section.

I'm using 64-bit Dapper, and my system is running as normal apart from this error message, which I'd like to fix.

Can anyone help?

Thanks

patslap

---

### Post by drtpw on 2006-11-19
I know that this is very late.  I have gotten that message too.  It happens whenever I boot up and I've got a memory card or compact flash card - some type of removable drive - in my machine.  If I remove those and boot with empty slots I do not get the error message.  Hope that this helps.

---

### Post by jgcamp99 on 2006-11-21
> **drtpw said:**
> I know that this is very late.  I have gotten that message too.  It happens whenever I boot up and I've got a memory card or compact flash card - some type of removable drive - in my machine.  If I remove those and boot with empty slots I do not get the error message.  Hope that this helps.

Try disabling the autologin user feature or change/enable it as a timed autologin user instead. The time it takes for you to enter userid and password or the @ minimum 5 second delay to autologin on a timed basis as the user is enough time for HAL to initialize properly. At least it is for a 32 bit Ubuntu version/system ?

---

### Post by Hwoarang on 2006-12-09
> **jgcamp99 said:**
> Try disabling the autologin user feature or change/enable it as a timed autologin user instead. The time it takes for you to enter userid and password or the @ minimum 5 second delay to autologin on a timed basis as the user is enough time for HAL to initialize properly. At least it is for a 32 bit Ubuntu version/system ?


In my case this problem Occured when I was automounting Drives over Samba. Try disable automount

---

### Post by cstudent on 2006-12-09
> **Hwoarang said:**
> In my case this problem Occured when I was automounting Drives over Samba. Try disable automount

The problem popped up on me a couple of weeks ago. I'm running Edgy on my main desktop with two drives that auto mount from my server running Dapper. I had my fstab entries mounting the drives with smbfs as the file type. I changed them to use cifs and changed dmask and fmask to dir_mode=0777 and file_mode=0777. That seemed to solve my problem, but I don't know why it all of a sudden popped up to begin with. It was working fine the other way.

These are the fstab lines currently:
```

//192.168.1.11/ServerDrive /media/FSdrive cifs credentials=/root/.smbcredentials,dir_mode=0777,file_mode=0777	0 0

//192.168.1.11/LinuxDrive /media/BUdrive cifs credentials=/root/.smbcredentials,dir_mode=0777,file_mode=0777	0 0

```

---

### Post by Hwoarang on 2006-12-12
Yeah thats mine fstab too. When I automounted using smbfs instead of cifs I got the error. Now everything is ok :)

---

### Post by Jakanori on 2007-01-02
I found that disabling autologin as suggested above removed this problem for me :rolleyes:

---

### Post by mrpot6469 on 2007-01-13
Hello !

I've watched this thread for a little while and am having the same problem, but I found the solution a little different, here goes.

I'm running Ubuntu 6.10 amd64, and I upgraded the kernel for k8-smp as I have a Althon X2.
After upgrading is when I noticed the Hal error, so from reading other forums I upgraded DBUS, and re-installed HAL and all assosiated libraries.  This stopped the hal error on log in, but another problem occurred, the desktop took forever to load, and trying to access anything in the /media directory was impossible, including the dvd player.
I noticed two CD-Roms with the same name, hmmm.  Now from digging through synaptic I found a automount program which is already installed, that automatically mounts cd-roms/dvd's as a regular user.  Remembering this I checked fstab and found an entry for a cdrom ??? Now just wait, if there already is a program that mounts it, maybe this entry was added during a package install or upgrade. Under "sudo gedit /etc/fstab" and commenting out the CD-ROM entry, and then rebooting, whola, no more hal error, or delay in desktop comming up.

I hope all this info helps !

Mike Potapoff

---

### Post by Buck2348 on 2007-01-13
> I noticed two CD-Roms with the same name, hmmm.Where?--In the /media directory, the /dev directory, on the desktop?. . . .

---

### Post by mrpot6469 on 2007-01-13
Further update...

Sorry guys, it shows up on the desktop twice, (I saw it because the icon's were not exactly on top of each other). 
I was diggin a little further, let me explain a little deeper. It seems that when a CD is inserted, it is mount as /media/cdrom0 with a soft link /media/cdrom, I have a dvd recorder (and this may happen with a cdrw as well), that is mounts is as well into /media/dvdrecorder, which doesn't exist unless there is a disc in the drive (Remove the disc, the directory disappears).  This most likely causes a problem with HAL, as well as when you try to view the directory either thru a file manager or thru a console window.  The fstab on my machine shows as thus:

/dev/hda     /media/cdrom0 udf,iso9660 user,noauto     0       0

what I did was comment it out with a # at the beginning, or simply just delete it, save the file (oh, you need to edit the file as sudo). Once that is done, reboot the machine.  After getting back up, go into the console, go to the /media directory and run:

sudo rm cdrom
sudo mkdir dvdrecorder
sudo ln -s dvdrecorder cdrom

Now when I insert the disk, all is ok.
Please note this is how it worked on my machine, you may need to change the "dvdrecorder" to what ever shows up in the /media folder when a disc is inserted.

Mike

---

### Post by mrpot6469 on 2007-01-13
Hey again :)

One more discovery.  Now when I boot my computer with a CDROM in the drive, nothing shows at all in the desktop unless I open and close the door.  Another solution is to not delete the entry in fstab (/dev/hda /media/cdrom0 ...) and change the cdrom0 to, in my case dvdrecorder.  This will allow a disc that is inserted on boot to show up correctly, and not cause any conflicts with a device mounted in two seperate directories in the /media folder.

here is what my fstab entry looks like now :

/dev/hda        /media/dvdrecorder   udf,iso9660 user,noauto     0       0

Mike.

---

### Post by mrpot6469 on 2007-01-14
Hello again.

One more update on the issue from my end.  Tried having the entry for the DVD in fstab, but eventually, the problem with the two mounted CD's showing on the desktop happened again. So removing the entry all together seems to be the best solution.

Good luck !!

Mike

---

### Post by mrpot6469 on 2007-03-16
If anyone is still following this tread, try uninstalling the gnome-volume-manager, this will remove the issue for sure as it is the service generating the problem anyway.  It's function is to poll dbus for changes in such things as a inserted cd or dvd, usb flash drive etc.  The only problem with uninstalling the volume manager is those things won't get automatically mounted, meaning you'll have to do it the old fashioned way or use a script, and an desktop icon link to it.

Any who, I'm not having the problems anymore.

Mike.

---

### Post by jbayone on 2007-03-16
I re-installed HAL via synaptec whenever I was having this issue.  Also, my cd and dvd drives would not open while they were mounted.  After reinstalling HAL and rebooting, everything worked fine.

---

### Post by Jaak on 2007-03-19
> **jgcamp99 said:**
> Try disabling the autologin user feature or change/enable it as a timed autologin user instead. 

This worked for me! I had autologin "on" i turned it off, rebooted, logged in manually, problem solved, turned autologin back on. Problem still solved.

---

