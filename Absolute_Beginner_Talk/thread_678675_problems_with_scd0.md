---
title: "problems with scd0"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by kywillia on 2008-01-26
Hey guys, pretty new to linux but i love it so far.  Anyway. . . I have been having problems whenever i try to burn a cd or dvd.  I have tried the cd/dvd creator, k3b, and dvdauthor.  when i put mount in the terminal this is what i get:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
     I really have no clue what any of this means i got to this point looking at the other posts in the forums.  i do not even see my cd/dvd+r drive? is this my problem or could it be something else? any help would be appreciated :)

---

### Post by Xell Strider on 2008-01-26
Well, maybe you need to explain what do tou really want to do.
Do you want to see the blank cd-r's or see what is in it after burnt them?
If you want to see if there is a cd in the drive when is it blank use the cd info option in any of the burning programs to see if it is blank or the space, because as far as i know you can't mount a blank cd or dvd.
Hope it helps.

---

