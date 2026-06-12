---
title: "correct way to mount a hard drive ?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-01-07
ok i have reinstalled dapper so before i procceed and stuff up my system again,here is how i mounted my hard drives in the past..

gksudo gedit /etc/fstab ...>
and added 
/devhdb1    /media/shared      ext3      defaults 0   1

saved and made a new mount point

sudo mkdir /media/shared
sudo mount -a
sudo chmod -R 777 /media/shared

then did the same on the outher hard drive changing hdb1 for hda1

in the past this has messed up permissions on hda1
cant use any thing and when i sign in got a error message 

user's home folder being ignored ,home folder must be owned by user and not writeable by outher .(so on and so forth)

so i ask what are the correct commands to do this as i dont want to go through it again.

thanks for your help.  :D

---

### Post by aysiu on 2007-01-07
Those are the correct commands, and changing permissions on /media/shared (/dev/hdb1) shouldn't in any way affect /dev/hda1.

---

### Post by quartzy on 2007-01-07
Meh Ignore me :\

---

### Post by STREETURCHINE on 2007-01-07
yes i know but this is the third time i have had to reinstall(only because i cant work out how to fix it) dependig on which one i mount first ,if i mount hda1 first i lose permissions on hdb1 or visa- versa that is why i thought i may hav got it wrong.ok i will go again .

hope i dont break it again..lol

---

### Post by aysiu on 2007-01-07
How is /dev/hda1 mounted?

---

### Post by quartzy on 2007-01-07
You should note that the syntax for mounting a ntfs/fat partition is different to that of mounting a ext3.  Ext3 already has file permissions therefore it's easy but with a NTFS / fat filesystem it's best to define the permissions at mount time. IE chmod 777 won't work (at all?) very well.

See [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

---

### Post by STREETURCHINE on 2007-01-07
Filesystem            Size Used Avail Use% Mounted on
/dev/hda1             181G  2.3G  170G   2% /
varrun                506M   92K  505M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  124K  505M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  488M   4% /lib/modules/2.6.15-27-686/volatile

is this what you were looking for.
if not ,i only let the live cd do all the partitions itself so it would be the defaults.

---

### Post by aysiu on 2007-01-07
Hm. So /dev/hda1 is your root partition.

Then I'm totally baffled.

As I said before, the permissions on /media/shared shouldn't affect the permissions of /dev/hda1

---

### Post by STREETURCHINE on 2007-01-07
yesss. ! well i shall do it again shortly before i reinstall to much stuff and see what happens
will report back

thanks aysiu.

---

### Post by STREETURCHINE on 2007-01-07
ok i did it ,,just to be differant i used gksudo instead of sudo

            gksudo gedit /etc/fstab
add

            /dev/hdb1    /media/shared    ext3   defaults   0   1
saved

            gksudo mkdir /media/shared
            gksudo mount -a
            gksudo chmod -R 777 /media/shared
            df -h   (to see if it is mounted in dev/media/shared)

i dont know if gksudo was required but it did work for me .as i have not lost permissions ,
and i have rebooted several times between harddrives just to make sure..crossing my fingers now..lol

---

