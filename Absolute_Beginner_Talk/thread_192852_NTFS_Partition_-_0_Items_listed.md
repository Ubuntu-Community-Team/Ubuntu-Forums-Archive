---
title: "NTFS Partition - 0 Items listed"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by maxtrix on 2006-06-09
Hey all.. finally dumped the XP and went totally Ubuntu... liking it so far.

I backed up MP3's and other files on an NTFS partition prior to wiping out XP.  I have successfully mounted that partition and have permissions to access the Part.

When I go into the partition, it lists zero items on the partition.  Yet it displays that there is only 6GB left on the 66GB partition.

Any ideas?

---

### Post by steve.horsley on 2006-06-09
Odd. Are you sure it's mounted OK? Can you post the output from these commands?

df -h
mount

Then change to the directory it's mounted at and try the command:

du -h

---

### Post by maxtrix on 2006-06-09
I'm not sure it's mounted ok... lol... I think I did everything right.

df -h Command
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             6.8G  2.1G  4.4G  32% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-23-386/volatile
/dev/hda5              67G   61G  5.7G  92% /windows

Mount Command
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/hda5 on /windows type ntfs (rw)

When I try to CD to the windows dir (when not root) I don't have the proper permissions to do so.  I know that is the issue because when I browse the Windows dir as root... I can see all files (this is through terminal).

Any ideas?

---

### Post by steve.horsley on 2006-06-10
Oh right - this was a cunningly disguised FAQ.

This web page probably says it all for you:
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#Windows](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#Windows)

Your windows partition is /dev/hda5
You probably need to add **umask=000** to that line in /etc/fstab, like this:
/dev/hda5       /windows     ntfs    nls=utf8,umask=000 0       0

---

### Post by witchdoctor on 2006-06-10
Just like above, this may help you 

[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

That's perm question, i think. But i did't know is that **umask 000** would be able to write ntfs format. Because MS didn't release all technical details about NTFS, thus there could be some danger for give the perm of umask 000.
But i didn't try it anyway :)

---

### Post by fireshell on 2006-06-10
I think by default once you mount an ntfs partition only root has access to the files. This is what I found in the gui in any case. What I did was once it was mounted I used the run feature in the main menu and ran the file manager under root. Once I found the mount point (/media/hda1) I used a right click -> properties -> permissions and set the owner of the folder to my own user name.

Please note that this is under Kubuntu though I think it is a similar procedure under Ubuntu. I dont know enough about the console to be able to provide console instructions

---

### Post by fireshell on 2006-06-10
Just a quick note... hda1 is my Windows partition and folowing that procedure I have full access to all files. The mount point syntax follows like so...

hd (a,b,c etc for drive 1, 2, 3) (1, 2, 3 etc for partition number)

hda1 is the first harddrive on my laptop and the first partition on that drive. aka Windows XP. I find that a useful idea to keep in mind when trying to work out mount points

---

