---
title: "Windows crapping out, data in jeopardy"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by ernie.bornheimer on 2008-02-16
Forgive me for my absolute beginner status.

Apparently my Windows box is going bye bye. Tried to start today, got "non system disk or disk error." Recovery console sees no disks, can't recover. Corrupt boot sector? Probably not malware. Now many hours later, trying to figure this out, here's the short version:

Booted with Ubuntu LiveCD (6.06, I think). It can see the Windows disks (one physical disk, partitioned into 3 logical), but won't let me open them, "You do not have the permissions necessary to view the contents of "disks-conf-sda1"

Under Ubuntu, I created a new user with admin privileges (or so I thought), logged in as that user, same result. I think I don't understand users and permissions. When I get that understanding, I can burn my data to CD, and get a new hard drive.

What am I doing wrong, how can I see into my Windows partitions?

Thank you!

Ernie

---

### Post by ugm6hr on 2008-02-16
I thought the LiveCD logged you in as "root" (the administrative superuser).  Therefore, you should have access to all your data if you are booting from the LiveCD.

Just in case I'm wrong - try this:
```
gksudo nautilus
```
Then try again to see whether you get the same error.

The more likely problem is that your HD partitions are not mounted.  Perhaps 6.06 doesn't mount when you double-click in nautilus (the file browser)?

Easiest way to try and mount with a GUI is with GParted (Labelled as Partition Editor in the menus). Just right-click on each partition, and it should have the option to mount.  You should then be able to access all the files in Computer -> / -> media -> disk (or whatever it is called)

I actually used PuppyLinux to save my data when my HD started to die a year ago - and now I'm a full-time Linux user.  Try and resist the temptation to repeatedly reboot - it will just jeopardise your data further.

---

### Post by stalkingwolf on 2008-02-16
try right clicking on a file and selecting properties.  then reset the permissions.

---

### Post by ernie.bornheimer on 2008-02-16
Can't reset permissions because I am not root. Can't log in as root, that's why I tried to create another user with admin rights. 

Volumes are mounted (well, not at first, but I can mount them), the issue is with permissions. Not sure if it's Linux or Windows permissions.

Thanks!

Ernie

---

### Post by ashmew2 on 2008-02-16
Well do you have your precious data only on the Windows partition ? Even if you can manage 2 gb of space , you can install Ubuntu and burn your data from the windows partition by running the installed Ubuntu. You can think about everything else later once your data is safe.

---

### Post by ernie.bornheimer on 2008-02-16
Ashmew2

Last night, I walked through the process of installing Ubuntu, until I got to a screen that warned me about losing data on partitions that Ubuntu will use. Since I am completely new, I wasn't 100% sure I understood the process, so I backed out. Also not sure the permissions issue wouldn't be the same running Ubuntu from the hard drive.

Found a possible solution here: 

How to fix your Windows MBR with an Ubuntu liveCD
[http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)

sounded promising, but got stuck where it said:
"Once Ubuntu starts up, go to System -> Administration -> Software Sources and enable (by checking it off) the Universal repository." Under Administration, I don't see software sources. Tried like hell to find and install ms-sys, but no go. Then I tried to download the latest version of Ubunto (I'm using 6.06), but "not enough space on the disc." So now am back to square one.

Right now I'm logged in under the user I created, I just checked Users and Groups again, and saw that it contains a user called ubuntu, and the User details says: Ubuntu LiveCD user, so that must be who is logged in by default. I should mention that last night I also tried to log in as root (after changing the password), but got a message that that user can't log in using that screen.

Looks like the user ubuntu already has admin perms, so it must be an issue of *ownership,* rather than permissions per se?

I will keep trying to figure this out. In the meantime, I'm open to suggestions.

Thanks!

Ernie

P.S.

How do I check what user is currently logged in?

---

### Post by jrothwell97 on 2008-02-16
As I understand it, a temporary user is set up on the Live CD which doesn't have root priveliges, except for writing new partitions to the HD.

Just a bit of advice: try checking the cables inside the computer to your HD. I've had problems before which have been rectified by securing the power and IDE/SATA cables in the machine.

---

### Post by louieb on 2008-02-16
The 6.06 CD won't auto mount your hard drive partitions. 
Run this in a terminal window and you may be able to read your windows data for the 6.06 live CD. Just use the file manager to browse to /windows 
create a different directory and mount it for each of your /windows partitions. 
BTW -t ntfs ix for XP -  if win98 can't remember but belive the type is fat32.
```

sudo mkdir /windows
sudo mount -t ntfs /dev/hda1 /windows

```

Gutsy 7.10 one will mount them after you click on the drive in the places menu. 

The easiest Live CD I've found to use is  [Knoppix Linux]("http://www.knoppix.net/") .  That and the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") is what I use when I need to recover data. 

Another good one thats a smaller download as ugm6hr said he used is [Puppy Linux ]("http://www.puppylinux.org/user/viewpage.php?page_id=1")

---

### Post by ashmew2 on 2008-02-16
I thought he already mounted the partitions. But still try what louieb suggested. Sounds reliable.

---

### Post by ernie.bornheimer on 2008-02-16
Yes, volumes are mounted. I'll try Knoppix and the System Rescue CD.

Thanks!

Ernie

---

