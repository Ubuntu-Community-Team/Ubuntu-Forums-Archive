---
title: "mounting 2nd HDD"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by guilly on 2007-08-19
Alright this problem is driving me absolutely nuts.... im trying to mount a second hard drive on my Server running fiesty server edition. The only way i can get it to mount is with root priveledges which does not allow me to write to the disk without root power. I've tried motifying the fstab and still no luck it does not evn auto mount i have no idea what else could possibly be the problem here is my fstab entry!!! any hep with this would be really really appreciated

# /dev/hda1
/dev/hda1    /media/ftp    ext3    auto rw,user,exec     0    1

I've also tried this 

# /dev/hda1
/dev/hda1    /media/ftp    ext3    defaults,uid=1000,guid=1000     0    1

uid and guid match up with the user that i use regularly.

my goal for this second hard drive is to use for my ftp server incase that matters.

thanks again

---

### Post by Jimmyfj on 2007-08-19
Don't know if this will do the trick, but it's worth a shot:

chown -R USERNAME:USERNAME /media/ftp

---

### Post by Steve1961 on 2007-08-19
try changing the ownership of the mount point:

sudo chown username:username /media/ftp

Insert your own username in the above

---

### Post by guilly on 2007-08-19
thanks for the reply,

i can get chown to work if the media is already mounted and then i do the chown command then i have full access with my user name

as soon as the system reboots the media does not get mounted again, however once it's mounted i regain ownership

my fstab config is set as follows : 
# /dev/hda1
/dev/hda1 /media/ftp ext3 auto rw,user,exec 0 1

---

