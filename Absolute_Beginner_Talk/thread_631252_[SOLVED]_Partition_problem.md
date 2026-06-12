---
title: "[SOLVED] Partition problem"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by nomemory on 2007-12-04
I cannot write data on one of my partitions.
I've installed Ubuntu few days ago. I've customized my partitions by 
- creating one parition for system files: 30 GB
- allocation 60 gb to home
and another 60 gb to a place called: "Warezhouse" (a place for storing miscellaneous downloads & stuff).

The problem is that I cannot write anything on /warezhouse. I can't modify anything:
"You are not the owner, so you can't change these permissions."

Any ideas how to acces that place ?

---

### Post by Znort_Ubern00b on 2007-12-04
> **nomemory said:**
> I cannot write data on one of my partitions.
I've installed Ubuntu few days ago. I've customized my partitions by 
- creating one parition for system files: 30 GB
- allocation 60 gb to home
and another 60 gb to a place called: "Warezhouse" (a place for storing miscellaneous downloads & stuff).

The problem is that I cannot write anything on /warezhouse. I can't modify anything:
"You are not the owner, so you can't change these permissions."

Any ideas how to acces that place ?

try typing in terminal

sudo chgrp groupname /media/drivename

where groupname is the name of group of people you want to be able to write to that drive(my one is called stdusers and includes everyone) and /media/drivename is something like hda1 or sdb1 you should have those details.

check groups in system-admin - users and groups

---

### Post by banewman on 2007-12-04
in a terminal type - 
sudo chown -v you:you /path/to/file
where you is your login name and group and /path/to/file is where the partition is mounted in the file /etc/fstab
Open the file   /etc/fsab   and look for what the partition is mounted under   e.g.  /dev/sda3
If it is a ntfs partition ( windows ) then you need to install    ntfs-3g    from synaptic
Feel free to ask for more help :)

---

### Post by nomemory on 2007-12-04
[IMG]http://farm3.static.flickr.com/2091/2085982707_67f9ceaedf.jpg[/IMG]
The owner is still root...
Even after:

> andrei@andrei-desktop:~$ sudo chown -v andrei:andrei /dev/sda3
ownership of `/dev/sda3' retained as andrei:andrei
andrei@andrei-desktop:~$ 
I need to change the privileges of andrei to more than access files...

Any other ideas ?

---

### Post by Znort_Ubern00b on 2007-12-04
try sudo chgrp one that i suggested...eg sudo chgrp mygroup /dev/sda3

this will change group ownership of the drive to whichever group you chose.

---

### Post by nomemory on 2007-12-04
> andrei@andrei-desktop:~$ sudo chgrp andrei /dev/sda3
andrei@andrei-desktop:~$

nothing happened.

---

### Post by Znort_Ubern00b on 2007-12-04
is andrei the name of a group in your users and groups menu???

check
system - admin - users and groups 
you should be admin group if so try 

sudo chgrp admin /dev/sda3

---

### Post by banewman on 2007-12-04
The   -v   option is always handy  :)

---

### Post by nomemory on 2007-12-04
> andrei@andrei-desktop:~$ sudo chgrp -v  andrei /dev/sda3
group of `/dev/sda3' retained as andrei
andrei@andrei-desktop:~

The owner is still root not andrei :(

---

### Post by Znort_Ubern00b on 2007-12-04
> **nomemory said:**
> The owner is still root not andrei :(

is andrei a group on your system?

system - admin - users and groupsif andrei isn't a group it will not transfer ownership. you need to use an actual group on your system

---

### Post by nomemory on 2007-12-04
> Group name: andrei
Group id: 1000
Group members:
root
mihai
andrei
Saboyan user

Yes it's a group.
andrei is also my default name when i've installed ubuntu.

---

### Post by timcredible on 2007-12-04
what filesystem type is it?

---

### Post by nomemory on 2007-12-04
ext3

---

### Post by nomemory on 2007-12-04
How can I make my user andrei root by default so I can be the owner of that partition ?

---

### Post by nomemory on 2007-12-04
Ok.
Here is what i did:
1. Opened the terminal
2. Entered gksudo nautilus
3. Changed the permissions from gui
4. Not it works
5. Thanks for your help.

---

### Post by Znort_Ubern00b on 2007-12-04
you can but it is very dangerous to do so, the reason you are not root is so that to install things you have to put in password as root you can install anything (including detrimental stuff - a la windoze)

anyone would tell you that they would not recommend it.

---

