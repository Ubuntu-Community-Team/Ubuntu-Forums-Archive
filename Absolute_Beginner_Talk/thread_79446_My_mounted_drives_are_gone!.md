---
title: "My mounted drives are gone!"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by clueo8 on 2005-10-20
The only storage media that I have is my floppy driver... I have a linux drive and 2 windows partitions mounted!  When I restarted the computer a few times, I notice these disapeared.  I used the Disk & Filesystem in the system settings of kde to ad my drives at startup (im running kubuntu, breezy)  Now when I go back in there, all the options are greyed out, even after I click administrator mode and enter the root password, it still has them greyed out...  HELP!  I can't even access the linux partition!

---

### Post by onesojourner on 2005-10-20
look at the instructions in the ubuntu guide. this was the first thing I tackled with ubuntu. the guide shows you how to temp mount the drives and to mount them so they are there everytime you start your computer. just do an advanced search with my user name and you will find all the stuff i did.

---

### Post by clueo8 on 2005-10-20
Not only cannot I not access administrator mode in the drives section, but I cannot access anything with administrator mode in the system settings.  I'm entering the right root password, im sure, cause su works fine in a terminal.  Is there any way around this or a way of gettings administrator mode button to actually put me in admin mode for these settings?

---

### Post by rubycon on 2005-10-20
Are you absolutely sure your using the right password? Because when programs ask for root access they usually do it with sudo, asking for your user password rather than the root password. Anyway, couldn't you just edit the /etc/fstab and add the filesystems you want mounted on startup there manually?

---

### Post by clueo8 on 2005-10-20
i ended up reinstalling... I heard that there is no root password for kubuntu installed, just the password of the main user created during the install... I was doing a terminal command to create a password on the root account, maybe thats a no no.

---

### Post by onesojourner on 2005-10-21
ya stay out of the root user as much as possible. you can do almost everything you need with the first user account. use that password when it asks for one.

---

