---
title: "mouting hdd"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by aran384 on 2005-08-02
Ineed to know how to mount my second hdd that is installed to /home so i have loads of space.......

i know this is possiable cos i did it in mandrake awhile back ....

i have partitioned the drive into ext3 if this is wrong i got Gparted so i can easily change it 

so how can i mount this drive ???  :???:

---

### Post by super on 2005-08-02
[FONT=Courier New]sudo mount /dev/hdxx /home -t ext3[/FONT]

to do this at boot all you gotta do is add your drive info to the filesystem table.
[FONT=Courier New]sudo gedit /etc/fstab[/FONT]
> /dev/hdxx       /home             ext3    defaults,errors=remount-ro        0       1

of course the xx should be the path to your drive.

---

### Post by Zelut on 2005-08-02
let me take a quick look at my /etc/fstab because I just did the same thing with an extra 13G (I know, it isn't much but its an old box!)

/dev/hdXX    /*where*    ext3    defaults, errors=remount-ro   0     1

Give that a try.

---

### Post by aran384 on 2005-08-02
when i do sudo thing my gnome panel closes ???:s

---

### Post by aran384 on 2005-08-02
when i did that and rebooted it fucked it up big time nearly shit my self as well......

but i remembered how i added it......

---

