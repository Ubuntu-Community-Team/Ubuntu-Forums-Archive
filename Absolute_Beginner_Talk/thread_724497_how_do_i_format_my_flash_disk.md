---
title: "how do i format my flash disk"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by nnamdi on 2008-03-14
please i have a flash disk (kingston) and i would like to format it
anytime i want to format i usually do that with a windows system


and also i want to give my ubuntu a nice look 'n' feel 

thanks for your urgent reply

---

### Post by Rocket2DMn on 2008-03-14
You can download and install gparted from the repos (it's on the LiveCD already, but it's annoying to boot into that just to format a flash drive).  
```
sudo apt-get install gparted
```
System->Administration->Partition Editor
Format from there.

---

### Post by Ardrias on 2008-03-14
```

sudo apt-get install gparted
sudo gparted

```

Choose the flash drive, format to desired format. As for looks... [Gnome-look]("http://www.gnome-look.org/") should get you started.

---

### Post by joshrobinson on 2008-03-14
just a normal usb flash drive?

```
sudo apt-get install gparted
```
then
```
sudo gparted
```

insert the drive
in the top right corner you will see a dropdown menu, click that and select the one that is your flash drive, "say its 256mb look for the one thats that size"
right click on the used/free line in the bottom white box, click unmount, right click it again then go to format to: and select what filesystem you want

---

### Post by nnamdi on 2008-03-14
thank you how do pimp my ubuntu look 'n' feel

---

### Post by joshrobinson on 2008-03-14
check out
[http://www.gnome-look.org]("http://www.gnome-look.org")

look for a nice GTK2.0 theme, some new icons or wallpapers, whatever you like from that site
you can also get new GDM themes (login screen)

really neat stuff there

---

### Post by nnamdi on 2008-03-14
thanks once again for the sharp response

---

### Post by souneedalink on 2008-03-14
> **nnamdi said:**
> please i have a flash disk (kingston) and i would like to format it
anytime i want to format i usually do that with a windows system


make a filesystem on it....
open a console and type sudo mkfs and hit tab a couple times and it will present you the different type of filesystems you can use to format it

then use mkfs.whatever on the device name /dev/XYZ1

---

