---
title: "Upgrading from Hoary to Breezy"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by zaxer on 2005-12-14
Hi guys:

(Hope this hasnt been asked before)

Im still a Hoary user, but today I received my Breezy cds and I want to update to without risking any of my data.

What do you guys think is the best option to upgrade.

[LIST=1]
[*]Live from synaptic.
[*]Updating through official cds.
[*]Making a new install.
[/LIST]

Thanks for you help guys!

---

### Post by NotJustANewbie on 2005-12-14
I'd go with the CD option myself, but I have never done an update (Breezy was my first Ubuntu install). Just boot up with the CD and it should just prompt you to update.

By making a new install you would have to back up all your valuable data to a storage device anyway and since your breezy discs have arrived, why not give it a shot? :p

---

### Post by zaxer on 2005-12-14
[QUOTE=NotJustANewbie]I'd go with the CD option myself, but I have never done an update (Breezy was my first Ubuntu install). Just boot up with the CD and it should just prompt you to update.
[/QUOTE]

I think I have not explained correctly. 

Whith "updating through official cds" I meant, through Synaptic adding the cd  following these steps:

   1.Open up Synaptic Package Manager
   2.Click on "Edit/Add CD-ROM"
   3.Click on "Mark All Upgrades"
   4.Click on "Apply"
   5.See the additional notes below
   6.Note that you need to add the cdrom again with Synaptic "Edit/Add CD-ROM" after the first reboot,this is needed because of new package authentication feature

---

### Post by NotJustANewbie on 2005-12-14
I didn't know about that after reboot...:confused: 

I think its possible to do it how I stated above, I haven't tried it though.

---

### Post by thezerogroup on 2005-12-14
The apt-get method did not work for me, in fact it created a ton of problems, which I was able to remedy, but having done it both ways I would recommend downloading the new iso image.

---

### Post by NotJustANewbie on 2005-12-14
I've read loads about the internet update creates lots of problems.  The developers should hopefully have solved this problem by the time dapper comes out as stable. :rolleyes:

---

### Post by Mustard on 2005-12-14
Try reading over this guide..
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

I notice you seem to have cut and pasted those instructions from this guide, so I guess you have seen it already.  I would think the synaptic method is good if you have a good internet connection.  If you don't then the CD method would be fine.

The third option clean install is a different kettle of fish. Obviously a clean install will wipe your system clean and you will lose your personal configurations.  The only way to avoid this is to either backup your $HOME directories and restore them afterwards or if you have your /home on a seperate partition, you can choose to not format that when you come to the partitioning part of the install process.

If you follow the pre-upgrade instructions at the top of the guide, then you shouldn't have any issues.  Most issues to do with upgrading via synaptic would have occured because people had inadvertantly uninstalled ubuntu-desktop metapackage (or whatever other flavour of ubuntu they were using) and without this package installed, certain parts of the upgrade process did not complete properly.

---

### Post by zaxer on 2005-12-16
Hi guys!

Ive completed the update without problems! I chose the cd-upgrade option and everything went right (I think).

The only issue I have to ask you guys (again) is where is the great new graphical mode grub??

When I start my system the old grub loads, no changes there. Is that right?

Thanks for your support guys!

---

### Post by Mustard on 2005-12-16
[QUOTE=zaxer]Hi guys!

Ive completed the update without problems! I chose the cd-upgrade option and everything went right (I think).

The only issue I have to ask you guys (again) is where is the great new graphical mode grub??

When I start my system the old grub loads, no changes there. Is that right?

Thanks for your support guys![/QUOTE]

I think you might be talking about the usplash screen that breezy uses rather then the straight text output it normally shows as the kernel is starting up.  It might be a case of usplash not working for you after the upgrade if that is the case.

Grub is just the same as ever.  A text menu offering you a choice of boot options, recovery mode and a memtest.

---

### Post by zaxer on 2005-12-17
[QUOTE=Mustard]I think you might be talking about the usplash screen that breezy uses rather then the straight text output it normally shows as the kernel is starting up.  It might be a case of usplash not working for you after the upgrade if that is the case.

Grub is just the same as ever.  A text menu offering you a choice of boot options, recovery mode and a memtest.[/QUOTE]

Yay thats right, thats what I meant, the new usplash isnt working. What am I doing wrong?


Thanks!

---

### Post by bscbrit on 2005-12-17
zaxer - what do you see when the system is booting up.  Do you see the old style black and white terminal with each action being shown followed by [OK] or is the first thing you see the login screen ?

---

### Post by zaxer on 2005-12-17
[QUOTE=bscbrit]zaxer - what do you see when the system is booting up.  Do you see the old style black and white terminal with each action being shown followed by [OK] or is the first thing you see the login screen ?[/QUOTE]

Grub --> Old style black and white terminal --> login screen

---

