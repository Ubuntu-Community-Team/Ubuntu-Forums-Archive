---
title: "[SOLVED] Grub Won't Set up"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by uclalinux on 2007-11-17
I reinstalled Vista and I have to fix grub, I have done this before but this time I keep getting an error. I am putting in a 7.10 livecd and this is the order I type the commands. 

```
sudo grub
root (hd0,0)
setup (hd0)
```

Then I just reboot and grub should work. But when I am trying to do this grub is giving me this error when I try to run setup. 

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
grub> 
```

Any Ideas ? 
Thanks

---

### Post by Sephyth on 2007-11-17
try messing around in the grub with the partition location

when in the grub i think you hit esc when it gives you the error
then "e" to edit

then try changeing the partitition location from 0,0 to 0,1 or 1,0 ect
change it go back then press b to boot from the newly specified location

try that untill you get a real answer from some one that knows what there doing

---

### Post by uclalinux on 2007-11-17
I can't even get into grub yet, I have to use a liveCD, or I will boot directly to Vista

---

### Post by Sephyth on 2007-11-17
what kind of setup are you running?
mutiple hardrives with seperate partitions?
or just the one with vista and ubuntu on diffrent partitions but sharing the one HD?

---

### Post by uclalinux on 2007-11-17
Solved..

Ok, I am a bone head
I  was running the wrong partition,  it was not (hd0,0), it should have been (hd0,4). 

Sorry for taking up everyones time, 

Thanks for your help.

---

