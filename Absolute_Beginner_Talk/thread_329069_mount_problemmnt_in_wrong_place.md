---
title: "mount problem/mnt in wrong place?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-12-31
i am running dapper on hda,and edgy on hdb
now i was mnt the volumes /partitions and i mnt'd hda1 as / and hdb1 as /home, i think that is where i goofed.

so now i cant access my home folder or file system,cant even go to applications> disk to undo what i did .
terminal wont open,in fact not much i can access,

i figure i can load the live disk and mnt that to undo what i did ,i just dont know how to mnt the live disk.

 hope i can do this without shutting down the computer as i am 27% through a 700 meg download,lol

i am now going out the back to beat some sense into my self,](*,) 

thanks and happy new year

---

### Post by dlehman on 2006-12-31
First of all when you say mnt'd are you saying mounted or did you mount some to the /mnt folder
Second I think it would be helpful to post your /etc/fstab file

also the umount command will umount a device

good luck

---

### Post by STREETURCHINE on 2006-12-31
i mounted the file systems 
on hda1 /
hda2 extend 
hda3 ext3
hda4 fat32
hda5 fat16
hda6 swap
i think that is how it goes!
hdb1 /home (i mounted this from hda1 and think that setting the mnt point for home was wrong)
hdb2 extend
hdb3 ext3
hdb4 fat 32
hdb5 swap
 i cant open terminal or most outher programs from hda since i did this ,so i cant access fstab or get you any more information ,
that is why i need the command to use the live disk to mount hda1 and undo what i did .

so i hope this is understandable as i am not to savvy with terminoligy for computers.

---

### Post by STREETURCHINE on 2007-01-01
ok i seem to have blundered into the solution for this ,dont know what i did to fix it .
it could have been the reboot but i doubt it.

       so it might have been 

   ctrl+alt+backspace  (restartx)
   then(dont sign in just hit)
   ctrl+alt+F1              (tty1)
   then
   log in with user name and password.
   then type in.
   sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

  and then restart computer

  (ps .i have not worked out how to shut the computer down fron there so i just hit the reset button on my tower.)  :D

---

### Post by dlehman on 2007-01-01
glad you got it working I forgot to mention ctl+alt+F 1-6 get you tty 1-6 
and to reboot from terminal it would be

```
sudo shutdown -r now
```

---

