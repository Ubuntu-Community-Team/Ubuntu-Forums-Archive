---
title: "Automount a hard drive at startup?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Cuzit on 2008-04-17
Is it possible?  I assume so.  Google mentioned it, but all the results were "resolved" issues, and no guides, explanations, etc.  So I'm in the dark here.

My Windows installation hogged all of my hard drive except 6GB for Ubuntu (which is weird, I gave 70% of my hard drive to Ubuntu when running the partitioner), so I'm trying to put all my files on the Windows drive.  Speaking of, is there a way to separate the partition so that Ubuntu, Windows, and my files are all on a separate partition, without losing any of my current files?

Any help is appreciated. :D

---

### Post by northern lights on 2008-04-17
Doesn't your system do that out of the box?

What sort of device is it? External? Some wicked RAID, or what?

What filesystem is is formatted as?

---

### Post by bodhi.zazen on 2008-04-17
> **Cuzit said:**
> Is it possible?  I assume so.  Google mentioned it, but all the results were "resolved" issues, and no guides, explanations, etc.  So I'm in the dark here.

My Windows installation hogged all of my hard drive except 6GB for Ubuntu (which is weird, I gave 70% of my hard drive to Ubuntu when running the partitioner), so I'm trying to put all my files on the Windows drive.  Speaking of, is there a way to separate the partition so that Ubuntu, Windows, and my files are all on a separate partition, without losing any of my current files?

Any help is appreciated. :D

For a partition to automount there needs to be an entry in fstab. Usually the installer will do this for you, but if not you will need to edit /etc/fstab ...

Here is a tutorial on how to do that :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

=============

What I advise is you make a shared data partition, and mount it on both Windows and Ubuntu. There is no need to do this as you can access your windows files from Ubuntu.

If you want to move files, if you have the hard drive space, make a partition and move the data to it. Can be done from either Windows or Ubuntu.

If you do not have the space, move the files to CD/ DVD. Make sure they are intact, delete them off the hard drive, and then resize your partitions to make a data partition.

You have many options depending on what exactly you want to do and your hard drive space.

HTH

---

### Post by Cuzit on 2008-04-17
Formatted as ext3, internal hard drive.  The automatic partitioner made a partition for Ubuntu with 6GB, and the rest of my hard drive went to Windows.  It shows up under Computer as, basically, two seperate hard drives.  I click into the Windows drive and I have to enter a password to mount it.  I want that drive mounted automatically at startup, as all my files will go there.

Also, something else I need help with - I'll ask here instead of making a new topic (unless necessary).  How do I give myself root permissions to tamper with the filesystem files?  A lot of my programs, such as Azureus, can't update because I don't have admin permission.  I went into the Users and Groups manager, but no matter what I choose, I can't give myself permission to alter those files.  There's my username and a "root" username (with a random password that I don't have access to) that was auto-created.  I believe root has access to those files, but I don't.  And no matter what I choose as my group (admin, root, etc.) I still don't have permission.  Help there, too?  Thanks.

---

### Post by northern lights on 2008-04-17
You need to run those apps/commands with "sudo" or "gksu" (for graphical apps). To manually (not that I'd advise you to) tamper with system files open the file browser like so: ```
gksu nautilus
```

Ubuntu's concept is such that you can't log on as a permanent "root" user. "sudo" let's you run a command as a temporary root, though.

The closest you can get to a permanent root (again, not that I'd advise you to) is to run a terminal like so:```
gksu gnome-terminal
```

---

### Post by bodhi.zazen on 2008-04-17
Check the link on fstab I gave you for auto mounting the windows drive. If you need help, post the output of ```
sudo cat /etc/fstab
```

==========

For root access, use sudo.

sudo <command>

sudo -i #for a root log in

gksu for graphical applications.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jamesxross on 2008-04-18
actually, it is possible to login as root.

I'm sure I hardly need to say this, but this gives you the potential to do some pretty serious damage.

System->Administration->Login Screen

go to the Security tab
tick the box next to Allow local system administrator login
hit close

you should then go to System->Administration->Users and Groups

click on root
click Properties
click the radio button next to Set password by hand, and set the password to whatever you like
click OK
click close on the Users and Groups window

TADA!!! you can now login as root from your login screen (i've found this invaluable when i'm making changes to some files. it's quite irksome to have to do sudo or gksu and enter your password every time :-P)

Again, be careful when logged in as root. Bad stuff can happen if you accidentally delete or alter something.

---

### Post by sam_delta on 2008-04-18
have you considered resizing current partitions?
you can resize partitions if you like to
 just install gparted from synaptic, it is a graphical partitioner editor

sam

---

### Post by bodhi.zazen on 2008-04-19
> **jamesxross said:**
> actually, it is possible to login as root.

I'm sure I hardly need to say this, but this gives you the potential to do some pretty serious damage.

System->Administration->Login Screen

go to the Security tab
tick the box next to Allow local system administrator login
hit close

you should then go to System->Administration->Users and Groups

click on root
click Properties
click the radio button next to Set password by hand, and set the password to whatever you like
click OK
click close on the Users and Groups window

TADA!!! you can now login as root from your login screen (i've found this invaluable when i'm making changes to some files. it's quite irksome to have to do sudo or gksu and enter your password every time :-P)

Again, be careful when logged in as root. Bad stuff can happen if you accidentally delete or alter something.

Yes, I understand this sentiment. However, for a root terminal you can :

```
sudo -i
```

You can also lock your root account again with :

```
sudo passwd root -l
```

---

### Post by erlyrisa on 2008-04-19
man mount

man fstab

--- I have all my netwroked drives mounting as "MINE" ---ie you need to set the permissions on the mount ....

specifically guid=1000 , and uid=1000

eg,

/mnt/mymounty user=me,password=hello -o uid=1000,guid=1000,rw


you won't have to worry about nautilus again.

---

