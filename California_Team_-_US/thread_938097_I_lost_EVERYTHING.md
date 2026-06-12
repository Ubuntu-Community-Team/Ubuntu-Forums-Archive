---
title: "I lost EVERYTHING"
date: 2008-10-04
forum: California Team - US
---

### Post by brenbren on 2008-10-04
In an attempt to due a clean install of Hardy and back up my data, I lost all my data. Although the clean install took and Hardy works very nicely. I only know enough to get me into trouble, as is evident now, so is there any where in the Orange County area where an expert could look at my computer and see if anything I lost is still there somewhere?

---

### Post by christianvaldes on 2008-10-04
How many hard drives on your system?

I usally have all my data on another drive and then mount it after a fresh install.  But I feel your pain.

---

### Post by howefield on 2008-10-04
Sorry to hear about our data, anything not overwritten by your clean install has a decent chance of being recovered.

There are many software programs that will scan your disk and give you an idea of what can be retrieved. The important issue is not to use the disk in the meantime as you run the risk of over writing more files.

To get this done professionally can be pretty expensive. Good Luck.

---

### Post by Zimmer on 2008-10-04
[http://www.psychocats.net/ubuntucat/photorec-saves-the-day-again/](http://www.psychocats.net/ubuntucat/photorec-saves-the-day-again/)
photorec
Not familiar with its use personally but it may be worth investigating further .

---

### Post by brenbren on 2008-10-06
okay. Got photorec, and it looks very promising; got an external drive a 500 GB Freeagent. Now all I need is to get the freeagent to be have read and write permissions so I can access it as where I want the recovered files to go. I've already used gparted to format the drive to ext3. Command df -h output: Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              37G   36G     0 100% /
varrun                502M  104K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   60K  501M   1% /dev
devshm                502M   48K  501M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M   96K  928K  10% /tmp
gvfs-fuse-daemon       37G   36G     0 100% /home/brenbren/.gvfs
/dev/sdb1             463G  199M  439G   1% /media/disk
 but when in photorec /media/disk is not an option. 
Please help, I am so close!!!

---

### Post by aysiu on 2008-10-06
This is a step-by-step on Photorec (with screenshots):
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

It's targeted to Windows, but it'll work for Ubuntu as well (just make sure to select Ext3 instead of NTFS).

---

### Post by brenbren on 2008-10-06
I love the psychocats guide, it's just that when I get to the part where I need to pick a place to put the recovered files, my external drive under /media is not there as an option. The drive is there when I check via terminal. But not in photorec. Any theories?

---

### Post by Zimmer on 2008-10-06
Best guess....
Check you have mounted the external drive. Look on the desktop, is there an icon for it?
Yes?
right click on the icon and click on the <volume> tab and that will show you the address of the mount point address.

---

### Post by brenbren on 2008-10-07
right clicking the icon does give me options, none about volume though. Except unmouting volume. which elicited this warning:

---

### Post by Zimmer on 2008-10-07
You need to check the permissions of the drive! I will dive off and look for a proper method for you to unlock the drive from root...  (the quick and naughty way to do it is to 
gksudo nautilus 
in a terminal and browse the drive as root and create a folder on it and give users read/write permissions to the folder .) I'll be back..

and here again..

sudo chmod 777 was what I was looking for.   (in your case it looks like   sudo chmod 777 -R /media/extra     would be right)

This should give any user permission to read/write to the drive location  /media/extra

---

### Post by brenbren on 2008-10-07
I ran that command, and it took a second and though about it so it looked like it worked. So I ran photorec but /media is still not an option.
Also an error message comes up when I tried to unmount the external drive 

umount: /media/extra is not in the fstab (and you are not root)

what's up with this wacky thing?

---

### Post by brenbren on 2008-10-07
O frabjous day! I found it! Zimmer you were right on the money. Photorec is running and saving files to the external hard drive.
:D

---

### Post by Zimmer on 2008-10-08
Phew!  :)
Glad you will be able to recover something!

There are better/more elegant and useful ways to assign the permissions to a drive.
The use of a group and granting permissions to the group and making the appropriate users members of that group would be considered better practice.

---

