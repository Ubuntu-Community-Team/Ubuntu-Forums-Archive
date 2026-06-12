---
title: "Using Ubuntu as a back up utility"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Efaustus9 on 2006-11-12
I am helping a friend with her computer for this computers Windows XP installation is completely corrupted.I have a Ubuntu 6.06 Live CD and I was wondering if is there a way to access the NTFS formated hardrive using just CD so that she can access and back up the necessary files before I reformat.Thanks for you help.

---

### Post by bodhi.zazen on 2006-11-12
> **Efaustus9 said:**
> I am helping a friend with her computer for this computers Windows XP installation is completely corrupted.I have a Ubuntu 6.06 Live CD and I was wondering if is there a way to access the NTFS formated hardrive using just CD so that she can access and back up the necessary files before I reformat.Thanks for you help.

Yes that should be easy to do. Just boot the Ubuntu CD and you should have access to the ntfs partition.

Be careful you do not "back up" viruses.

---

### Post by Efaustus9 on 2006-11-12
thanks for the response but I belive I have to mount the drive somehow, yet being new to ubuntu I do not know how to do this. Any additional help would be greatly apprechiated.

---

### Post by bodhi.zazen on 2006-11-12
> **Efaustus9 said:**
> thanks for the response but I belive I have to mount the drive somehow, yet being new to ubuntu I do not know how to do this. Any additional help would be greatly apprechiated.

If the drive does not automatically mount:

Where is the windows partition? I assume /dev/hda1.

If you do not know:```
sudo fdisk -l
```Will list your partitions.

Now, assuming /dev/hda1,:```
sudo mkdir /mnt/windows
mount /dev/hda1 /mnt/windows -t ntfs
```And away you go !

---

### Post by Efaustus9 on 2006-11-12
thanks again, when I attemp to browse the drive in ubuntu I get this prompt "You do not have the permissions necessary". When I open the terminal and imput the provided commands I get this prompt "only root can do that". any suggestions?

---

### Post by confused57 on 2006-11-12
Here's how to mount Windows using the Live CD:

[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

---

### Post by Efaustus9 on 2006-11-12
> **confused57 said:**
> Here's how to mount Windows using the Live CD:

[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)
that was quite informative yet when I attempt to mount per the given instructions I get the following promt "according to mtab, /dev/hda1 is mounted on /tmp/disks-conf-hda1". when I navigate to this folder in the GUI I get this promt "the folder contents could not be displayed" .."you do not have permissions necessary to view the contents of "disks-conf-hda1". Any idears as to how to resolve this thanks again for your assistance.

---

### Post by podunk on 2006-11-12
A quick cheat would be 

```
gksu nautilus
```

this will open your file browser in root or super user mode, you'll be able to browse and copy at will.

Any mistakes you make doing this are of the permanent variety though.

---

