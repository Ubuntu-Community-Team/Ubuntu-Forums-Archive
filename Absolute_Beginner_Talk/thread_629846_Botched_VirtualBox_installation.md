---
title: "Botched VirtualBox installation"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by mubelhor on 2007-12-02
I keep failing at my attempts to install Windows XP on a virtual disk in Virtualbox.

If I do manage to get a virtual disk created, then my whole system freezes up when the Windows XP installation CD gets to the step of formatting the disk.

I tried:

sudo dpkg -r VirtualBox

and then reiinstalled the package, but I still can't make much progress.  I'm wondering if I need to somehow purge my computer of all Virtualbox traces before reinstalling.

This is maybe a different problem, but if I opt to log off, I catch a brief glimpse of an error message.  I think it's something about "insmod", but I don't know how to pause that screen.

If I do make it to the point of setting up a virtual disk, here's a common result after setting up the virtual disk:

---

### Post by Threbus5 on 2007-12-03
Plan "A" consists of continuing to attack the problem until finding a solution.

But consider plan "B" -
I experienced similar problems with virtualbox and decided to use (Free) VMware server instead. It seems to work OK - mostly.

In my instance the VMware server fails to recognize external usb drives. However, by enabling sharing in the Windows XP that runs in the virtual server and selecting Samba share in Ubuntu it is easy to select the Windows XP IP and open a server connection to the shared files. File transfer from Ubuntu to the virtual server works around the usb issue.

Good luck.

---

### Post by FakeOutdoorsman on 2007-12-03
Try finding .Virtualbox folder in your home folder and renaming it (you might have to hit ctrl + h in Nautilus to show hidden files or open a terminal and type "ls -al ~/").  This folder contains most of the preferences and renaming it will make Virtualbox start fresh.  Then proceed with the XP install.  If that fails then you can try with the reinstallation.

How did you install VirtualBox and which version did you install?  You can either use the free but proprietary Virtualbox binary or the Virtualbox Open Source Edition (OSE).  If you installed via Synaptic (System -> Administration -> Synaptic), right click Virtualbox and choose "Mark for Complete Removal" to get rid of all Virtualbox files.  Then check your home folder for a .Virtualbox folder.  If it still exists rename or delete it before trying a new installation.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by mubelhor on 2007-12-03
FakeOutdoorsman:
> Try finding .Virtualbox folder in your home folder and renaming it (you might have to hit ctrl + h in Nautilus to show hidden files or open a terminal and type "ls -al ~/"). This folder contains most of the preferences and renaming it will make Virtualbox start fresh. Then proceed with the XP install. If that fails then you can try with the reinstallation.

I'll try that when I get off work this evening. 

I used the proprietary binary and - for most attempts - let the firefox gdeb (?) plugin install it.  One time I opened a terminal and copied the installation command that's listed in the Virtualbox users' guide ( I'm not on that machine right now and don't remember the actual command).

Threbus5:
> But consider plan "B" -
I experienced similar problems with virtualbox and decided to use (Free) VMware server instead. It seems to work OK - mostly.

In my instance the VMware server fails to recognize external usb drives. However, by enabling sharing in the Windows XP that runs in the virtual server and selecting Samba share in Ubuntu it is easy to select the Windows XP IP and open a server connection to the shared files. File transfer from Ubuntu to the virtual server works around the usb issue.

I'll definitely pursue that plan if I can't get Virtualbox to work.  Thanks.

---

