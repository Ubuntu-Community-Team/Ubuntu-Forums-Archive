---
title: "Lost my Home File"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by jgeeting on 2006-09-09
I added a second hard drive to my system.
Used the disk untility that is included to format it to fat 32.
Then I changed the access path to /home
Now I can't get to the old home, it was a mistake, for sure,
I wasn't thinking. Of course nothng works...
Is there a command line to use to change the access path back 
to the old home folder?

---

### Post by jorn on 2006-09-09
Did you cange it in /etc/fstab?
Then just reverse the change.
Set your /home folder to the old drive again.
And mount the fat on a new directory that you have to create. Confused?

---

### Post by taurus on 2006-09-09
You are NOT supposed to make your /home to be fat32!!!  If you want to share files between Linux and Windowx, create a seperate partition and make it fat32.  That's how people would do it.  do you still have your old /home?

---

### Post by jgeeting on 2006-09-09
Yeah... the drive was supposed to be shared between the one of the windows machines on the network and the box itself. At least that was my thought.
As far as I know I deleted nothing. My old home should still be there.

---

### Post by jgeeting on 2006-09-09
/etc/fstab   - is this the utility that allows you examine the dicks on the system. Found at  - system > admiministration > disks on teh task bar.

and do I just acesss it from the termainal - say in failsafe terminal session?

---

### Post by insane_alien on 2006-09-09
ok if you want to share files use ext3 and get some driver for windows so it can see the files. unmount the drive and you should see your old files.cut those files and then remount the drive. paste the files and everything should be fine and dandy

---

### Post by taurus on 2006-09-09
Boot your machine into recovery mode from GRUB and edit your /etc/fstab.  Change the line for /home to whatever the original partition for /home...  Save it and reboot!

```
nano /etc/fstab
```

---

### Post by jgeeting on 2006-09-09
that was a fix... 

Thanks for your help!

---

