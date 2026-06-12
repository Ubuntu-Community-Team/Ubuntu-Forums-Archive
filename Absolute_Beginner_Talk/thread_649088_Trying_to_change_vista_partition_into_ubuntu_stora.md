---
title: "Trying to change vista partition into ubuntu storage"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by h-town on 2007-12-24
Hey guys, 

Microsoft is Dunzo, so I'm trying to convert my Dual boot ubuntu/vista laptop into a ubuntu/ubuntu storage kind of configuration if you know what I mean. 

And.. I've already used gparted to unmount the vista partition, format it into ext3, and now I don't know what to do. When I try to browse the partition all I can see is this Lost and Found Folder with an X and I can't access it or create new folders, it says I don't have permission to access it. 

what can I do? thanks in advance.

---

### Post by Duck2006 on 2007-12-24
You need to mount the partition.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

This may help.

---

### Post by h-town on 2007-12-24
thanks for the link, i'm sure it will help, but, i'm not exactly an old hand at using terminal. so in this tutorial,  when he says:

Then I'll edit my /etc/fstab file:
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab

does that mean that I type the first sudo code, enter, and then type the second line and then enter, or do i copy and paste both and enter them simultaneously? 

haha, yea i'm new at this :lolflag:

---

### Post by Duck2006 on 2007-12-24
> **h-town said:**
> thanks for the link, i'm sure it will help, but, i'm not exactly an old hand at using terminal. so in this tutorial,  when he says:

Then I'll edit my /etc/fstab file:
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab

does that mean that I type the first sudo code, enter, and then type the second line and then enter, or do i copy and paste both and enter them simultaneously? 

haha, yea i'm new at this :lolflag:

No one line at a time.
ie sudo cp /etc/fstab /etc/fstab_backup        "then press enter"
then sudo nano /etc/fstab                              "then press enter"

---

### Post by h-town on 2007-12-24
ok, i'm following the tutorial and i'm at this point in it:


sudo nano /etc/fstab

and when i do that this crazy (to me) fstab dos-y menu comes up. Now, do i just add the line like it says in the next step, or do I do something about some UUID header that is before each line.

Im not sure what to do.

---

### Post by h-town on 2007-12-24
well.. i went ahead and did it and this happens after I save the changes to fstab and exit and then enter this code: 

harrison@The-Zone:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
harrison@The-Zone:~$ 


i take it that's not suppose to happen.

---

### Post by h-town on 2007-12-24
here's a screenshot of my fstab.

[http://img525.imageshack.us/my.php?image=screenshotuj2.jpg](http://img525.imageshack.us/my.php?image=screenshotuj2.jpg)

someone take a stab at my fstab.. i'm corny and in need of assistance!!

---

### Post by h-town on 2007-12-24
hey you know what (anyone that's interested) 

I FIXED IT MYSELF!

 :guitar:

thanks for pointing me in the right direction, i was able to successfully mount my partition and it works fine. I'm so proud of myself.

---

