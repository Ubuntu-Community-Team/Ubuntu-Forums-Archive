---
title: "window HD not mounted"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Tiamats_Chosen on 2008-02-21
just installed 6.06 at work on a separate HD(120gb volume)  and teh windows HD(80gb volume) is detected but when i try to read it i get the unable to  mount selected volume error wiht this in details: error: 
                               "device /dev/sda1 is not removable

                                error: could not execute pmount"  

how do i fix this so i can read the files on there without having to reinstall again(did 3 times already) 
 
see attachment for properties

sorrt if this has been asked before i looked through 16 pages of searching befoer i posted and couldnt find anything that helped me

thanks

nuubuntu

---

### Post by taurus on 2008-02-21
What happens if you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1
df -h
```

---

### Post by Tiamats_Chosen on 2008-02-21
this is what i get

oops its a "one"not an "l"
it created a folder in file system/media  that i do not have access too
 and it doesnt show up in computer any more as a separate drive

---

### Post by oedha on 2008-02-21
from your second attachement....
it supposed to be :==> sudo mount /dev/sda1 /media/sdal
( because you have made /media/sdal ( with lower "L" ) but /dev...it has to be /dev/sda1 ( one aka "1" )

---

### Post by Tiamats_Chosen on 2008-02-22
i did it with the one and it created a folder in media and its blocked from reading

i would prefer it to be read as a harddrive named "Windows" instead of a folder

---

### Post by Tiamats_Chosen on 2008-02-22
here is properties of that folder

---

### Post by Duck2006 on 2008-02-22
May be this will help.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Tiamats_Chosen on 2008-02-22
when i get ot the fstab this is waht it gives me

and my windows is on a separate physical hard drive

whats that error on /dev/hdb1 mean too?

---

### Post by Duck2006 on 2008-02-22
Have you tried unmounting the drive and editing your fstab and then remounting the drive?

Edit using the link in my last post to umount the drive and then remount.

---

### Post by Tiamats_Chosen on 2008-02-22
thats how i got to where im at 
 that is the fstab that i have to edit
the windows drive is not on there

---

