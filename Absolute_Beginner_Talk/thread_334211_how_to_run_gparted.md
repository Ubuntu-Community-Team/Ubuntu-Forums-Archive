---
title: "how to run gparted ???"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-08
I need to run gparted ( or what it's called ) ( the program for managing partrtions ), but i can't find it anywhere. ](*,)

---

### Post by shanepardue on 2007-01-08
It's best to run it from cd. You can install it from ubuntu's livecd or download the gparted livecd from gparted's website.

---

### Post by bodhi.zazen on 2007-01-08
gparted is included on the live CD, but not installed when you install to HD.

I second the advice to run from a live CD and the advice to consider downloading the gparted live CD....

---

### Post by Sasa_Ivanovic on 2007-01-08
you have to insert a cd and restart,  can't you run it from normal session ???

---

### Post by Efwis on 2007-01-08
you can download it from the repos also.

to run it open terminal Applications->Accessories->Terminal and type the following

```
sudo gparted hdb
```

Replace the hdb with the correct setting for your hard drive you are looking for. if it's a single disk and you need just a partion on it, then you would use

```
sudo gparted hdb7
```

These are only examples, please use caution when using this program as you can render your OS inoperable or even completely remove it. This will also remove Windows if you are dual booting and choose the incorrect disk or partition to edit.

I recommend using your /etc/fstab file to determine what disk you want to mess with.

---

### Post by shanepardue on 2007-01-08
You won't want to edit partitions that you are currently using thus a livecd will edit unmounted partitions.

---

### Post by Sasa_Ivanovic on 2007-01-08
thanks everyone.

---

### Post by Kundalinux on 2007-06-12
OK, let's say that I just want to format my memory stick. With the livecd I would have to reboot my machine twice, not very convenient. Basically all I am looking for is a way to format or edit partitions which are not my system.

So first: how do you run gparted in Ubuntu? That was the original questeion....

Second: is there a different way of formatting external drives which is not by using gparted?

---

### Post by bodhi.zazen on 2007-06-12
> **Kundalinux said:**
> OK, let's say that I just want to format my memory stick. With the livecd I would have to reboot my machine twice, not very convenient. Basically all I am looking for is a way to format or edit partitions which are not my system.

Good questions.

> So first: how do you run gparted in Ubuntu? That was the original questeion....

You need to install gparted on your desktop install. Gparted is included on the live CD, but is not installed. Either use add/remove, synaptic, or the command line :```
sudo aptitude install gparted
```

> Second: is there a different way of formatting external drives which is not by using gparted?

Sure, see this link : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Scroll down a little to the bottom of the first post.

---

### Post by Kundalinux on 2007-06-12
> **bodhi.zazen said:**
> Good questions.



You need to install gparted on your desktop install. Gparted is included on the live CD, but is not installed. Either use add/remove, synaptic, or the command line :```
sudo aptitude install gparted
```



Sure, see this link : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Scroll down a little to the bottom of the first post.

bodhi.zazen, many thanks for helping.

I have gparted installed already. My problem is on running the program. I can't see it on my Applicaion menus. Also tried from Terminal with no luck. It gives me a warning telling me Root privilages are required for runningGparter. So, how do I run gparted?

---

### Post by Patrick K on 2007-06-12
"sudo gparted" will do it.

---

### Post by Omnios on 2007-06-12
Gparted is in the Menu _ Applications _ System tools.

 Ubuntu has a lot of hidden menu stuff so you could go into Menu _ System _ Preferences _ and Launch Main Menu, 

 GO to system tools and check mark on gparted so it shows.

 There are also a lot of other hidden menu items there so you might want to have a look through it.


 Word of warning. When using the install disk to resize a partition out of existing partition the size you choose will not make a new partition from it with that size but rather  resize that partition to the size you have chosen.

---

### Post by Kundalinux on 2007-06-12
> **Patrick K said:**
> "sudo gparted" will do it.

Great thanks. It works. :)

How can you make a launcher inside the Applications menu for gparter so that I don't have to use Terminal every time? Anyone knows?

---

### Post by Outrunner on 2007-06-12
If you installed it from the Ubuntu repositories it should have been added automatically. Did you check all the tabs?

---

### Post by Kundalinux on 2007-06-12
> **Omnios said:**
> Gparted is in the Menu _ Applications _ System tools.

 Ubuntu has a lot of hidden menu stuff so you could go into Menu _ System _ Preferences _ and Launch Main Menu, 

 GO to system tools and check mark on gparted so it shows.

 There are also a lot of other hidden menu items there so you might want to have a look through it.


 Word of warning. When using the install disk to resize a partition out of existing partition the size you choose will not make a new partition from it with that size but rather  resize that partition to the size you have chosen.

gparted does not show in under Applications>System Tools or any other manu so I can't check mark it. Strange...

---

### Post by Kundalinux on 2007-06-12
> **Outrunner said:**
> If you installed it from the Ubuntu repositories it should have been added automatically. Did you check all the tabs?

I checked all the tabs. Nothing there :(

---

### Post by Patrick K on 2007-06-13
To add it to the menus, right click on the menus and select "Edit Menus". When the editor opens click on "Administration" in the left panel then the "new item" button.  In the dialog box enter "gksu gparted" for the command, name it what you want, gparted works for me. Close your way out. You may need to restart X to get it to show up. Alt+ctrl+backspace will restart your windows session. Login and check it's there. 
Happy partitioning.

---

### Post by Kundalinux on 2007-06-13
> **Patrick K said:**
> To add it to the menus, right click on the menus and select "Edit Menus". When the editor opens click on "Administration" in the left panel then the "new item" button.  In the dialog box enter "gksu gparted" for the command, name it what you want, gparted works for me. Close your way out. You may need to restart X to get it to show up. Alt+ctrl+backspace will restart your windows session. Login and check it's there. 
Happy partitioning.

Great thanks! Got it :)

---

