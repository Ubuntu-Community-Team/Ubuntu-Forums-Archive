---
title: "Out of disk space"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by rhynes1 on 2007-01-06
Ok, so I'm new to Ubuntu and I installed one too many packages...now I'm out of disk space and I can't even log in to gnome. I'm running a dual boot of XP and Edgy, I have about a 15GB drive split between the two OS's.

My last install was KDE and it ran out of space before it finished...how do I uninstall KDE without being able to login to the GUI to see Synaptic and do it? 

I've tried to mess with aptitude, but I apparently need to login as root. What commands do I use in aptitude to login as root so I can uninstall KDE?? I'm stumped at this point.](*,)

---

### Post by quartzy on 2007-01-06
```
sudo aptitude
```

Use your user password when it asks

---

### Post by deadgobby on 2007-01-06
For one of lack of is HD space. You may need to inquire to obtain a larger HD to be able to do what you want. For dual booting is at least 40g HD is required. So you may have to go the light side of things. That would may be KUbuntu. I know Earth money can be tight thing for many, but a 40 gig HD can be less than you think. If that is out of the question. Then maybe Kubuntu is the best route to go.
Gobby

---

### Post by aysiu on 2007-01-06
Boot into recovery mode.

Then try ```
sudo aptitude remove kubuntu-desktop
sudo aptitude clean
reboot
``` See if that helps.

---

### Post by mcduck on 2007-01-06
You can select the safe mode option from Grub menu to boot into command line as root (so you don't need to use sudo in safe mode). That should let you log in because 5% of your disk space is reserved for root and is most likely still free.

Then you can clean some disk space and after that normal login should work again..

---

### Post by Jason Weiss on 2007-02-17
I cant believe this I have an 80 g drive with only ubuntu installed on it. 

and it is full does this sound right the install is only a few weeks old, and I have been like a kid in a candy shop with the synaptic but I only get 12 g per month download with my braod band account so I do not know how I got up to 80g?

Does this sound right?

---

### Post by bulldog on 2007-02-17
Nope it doesn't.
Did you make a separate home partition?

---

### Post by highneko on 2007-02-17
What I usually do is:
```
sudo du -ch --max-depth=0 /*
```
Hope it helps. I'm sure you'll fix it. Good luck, have fun.

---

### Post by Jason Weiss on 2007-02-17
> **bulldog said:**
> Nope it doesn't.
Did you make a separate home partition?

Was that one of the options when I installed ubuntu?

Is there a way that I can see my free space?

---

### Post by Jason Weiss on 2007-02-17
> **highneko said:**
> What I usually do is:
```
sudo du -ch --max-depth=0 /*
```
Hope it helps. I'm sure you'll fix it. Good luck, have fun.

I just ran this and I got the results below. 

Have I fixed anything?

```
4.8M    /bin
8.4M    /boot
0       /cdrom
148K    /dev
14M     /etc
4.9G    /home
4.0K    /initrd
0       /initrd.img
108M    /lib
48K     /lost+found
4.3G    /media
4.0K    /mnt
4.0K    /opt
900M    /proc
1015M   /root
6.3M    /sbin
4.0K    /srv
0       /sys
39M     /tmp
2.6G    /usr
52G     /var
0       /vmlinuz
65G     total
```

---

### Post by taurus on 2007-02-17
```
sudo df -h /var
```

---

### Post by Jason Weiss on 2007-02-18
> **taurus said:**
> ```
sudo df -h /var
```


Ok I did this. 

and I got this 

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              71G   60G  7.9G  89% /


```

Is there something I should delete in var to free up some space. 

By the way this is a fault of linux for providing so much high quality software for free (as in speech):)

---

### Post by taurus on 2007-02-18
```
sudo du -h /var
```

---

