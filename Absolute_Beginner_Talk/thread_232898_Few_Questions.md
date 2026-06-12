---
title: "Few Questions"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Tamil on 2006-08-09
:?: What is equivalent in Ubuntu to Windows task manager?

:?: How can I prevent changes in guest account?

:?: I reinstalled Windows and it shows Windows only during booting. Is it possible to get back Ubuntu options?

---

### Post by drtvasudevan on 2006-08-09
first get your ubuntu back by installing grub.
look at this.
[http://ubuntuguide.org/wiki/Dapper#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/wiki/Dapper#restoregrubmenuafterwindowsinstallation)
it will solve most of your problems

---

### Post by kb3hkg on 2006-08-09
1. by command line there is ps, a gui would be the gnome System Monitor

2. what changes do you mean?

3. If you install Windows after linux it has this nasty tendancy to overwrite the MBR, getting rid of your bootloader, this is why for any dual boot setup you always install windows first. It is painful to get back to where you were usually.

---

### Post by Ivaldi on 2006-08-09
1. System -> Administration -> System Monitor
2. Don't know, sorry.
3. Yes. Here's how: [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Good luck :)

---

### Post by Tamil on 2006-08-10
Thanks.

Can I change the location of home to another partition? Currently it is in root.

---

### Post by drtvasudevan on 2006-08-10
you mean you want to dedicate a separate partition to ubuntu home?
it may be a bit difficult.
if you have not done much already better to reinstall.
perhaps easier.that will also reinstall your grub

---

### Post by Gustav on 2006-08-10
It's not that hard to move /home to a different partition.

Step 1. Make the partition with your favourite patitioning program

Step 2. Mount the partition somewhere ('sudo mount -t /dev/hda2 /mnt/newhome' (if the new partition is hda2 and you have a /mnt/newhome folder))

Step 3. Copy the stuff from your /home to the new partition ('sudo cp -a /home/* /mnt/newhome' (don't forget the -a switch!))

Step 4. Add a appropriete line in /etc/fstab (I don't know exactly how it should look but you can copy the /-line and change it as appropriete (I'm not at home with my linux-box at the moment))

Step 5. Reboot and pray to god (if you don't have that much confident in prayers you might want to make a backup of your /home as well)

---

### Post by drtvasudevan on 2006-08-10
hi gustav!
this person seems to be a total noob.
and has lost his grub.
simplest is reinstall.
such reinstalls gave me confidence to deal with other distros!

anyway noted your instructions for future use.thanks.

---

### Post by Tamil on 2006-08-10
Reinstalled and works fine. Thanks Gustav & drtvasudevan.

---

### Post by memos on 2006-08-10
Hi all.I download the k3d 0.5.16.o-src.tar.gz package and I would want to make install but I do not know how him I make.Please if it becomes step-step because I am newbes.:cry: :cry: :cry:

---

### Post by drtvasudevan on 2006-08-11
better go through the synaptic application.
open synaptic.
hit search
enter k3d
when done click on the box saying k3d. you can read the description of that file in the lower box.
click apply
it will get downloaded and installed automatically unless you have network problems.

pl post messages relevant to the thread only.
if you have a question click on new thread in the top left of the forum page and enter text in the box that will appear

---

### Post by Tamil on 2006-08-15
I tried to install flash player but it installed only for me. How can I install for all?

---

### Post by drtvasudevan on 2006-08-15
what you install as sudo must be available to all! that is my understanding. is it otherwise?

---

### Post by Tamil on 2006-08-15
Installed. Thanks once again.

---

### Post by Tamil on 2006-09-13
:confused:

---

### Post by Tamil on 2006-09-14
I got answer from [http://ubuntuforums.org/showthread.php?t=215627](http://ubuntuforums.org/showthread.php?t=215627)

---

