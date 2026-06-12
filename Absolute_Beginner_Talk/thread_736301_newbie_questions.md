---
title: "newbie questions"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Zedzero on 2008-03-26
i'm a total newbie to linux, and i'm confused.

- i'm trying to customize ubuntu to my liking. but i'm really confused. can someone please explain these, in respect to others? (like: while x is responsible for this and that, you should customize y for this thing), desktop environment, window manager, x, gtk, gdm, x11,

- everytime i need to run gdmsetup, i run it from terminal. where is it located in system menu? (yes i can just add it, but i know it should be somewhere already)

- where can i add commands to run at boot time?

- how can i not have x at boot?

- i need my other partition to get mounted at boottime. how can i do this?

- somehow i installed a login manager and i need to click on my name and then enter password everytime. how can i set it up so i should enter my username like default?

- i tried some themes, windows managers, etc, but almost all of them look like giant candies. i just want a nice basic but pixel perfect theme. no round edges, no gradients. (i used xfce before and loved it). are all the themes for gnome like that? art.gnome.org and gnome-look are the sites i checked. any other sites?

- if i select "lots of effects and bla bla", it enables compiz fusion, but i can't find where to set it up.

- after disabling compiz fusion and resetting to basic no-effects thing, i still have some effects. why? (like borders minimizing to taskbar when minimizing, etc.)

thanks...

---

### Post by rudihawk on 2008-03-26
For your compiz question, you can install the "advanced desktop effects manager"

For your autologin problem - there is an option like that in the login window, look under the  security tab.

---

### Post by drs305 on 2008-03-26
> **Zedzero said:**
> 
- where can i add commands to run at boot time?


Unless you mean before ubuntu actually loads, you can add apps or scripts to run at start up by going to System, Preferences, Sessions, Startup Programs and selecting Add. 

For more complex operations you can search for 'startup' and ' /etc/init.d '  to run scripts during boot.

---

### Post by Zedzero on 2008-03-26
thanks i will try these. any suggestion for other problems?

---

### Post by drs305 on 2008-03-26
> **Zedzero said:**
> 
- i need my other partition to get mounted at boottime. how can i do this?



Partitions can usually be mounted automatically from a line in your /etc/fstab file. Before doing anything else, make a backup!
```
sudo cp /etc/fstab /etc/fstab.backup
```

You can do a search for how to make entries in fstab. Typically you will need to know the type and location of the partition (hda2, sdb1; ntfs, ext3, etc) and the location of the partition (dev/sda1, dev/hda2, etc).  If you don't know what the partition is, run 
```
sudo fdisk -l
```

Once you know the partition info, do a search using, for instance, "fstab" "ext3" (for an Linux ext3-formatted partition)  "defaults" and you will probably find a good example of a line to copy.

One method to edit your fstab file:
```
gksu gedit /etc/fstab
```


Here's one link for understanding fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

