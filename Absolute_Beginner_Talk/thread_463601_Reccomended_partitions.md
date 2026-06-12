---
title: "Reccomended partitions?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-03
I have read guides that say just make a / and a swap, and others that say also make a /home, and still others that reccoment a /usr and /boot. Is there an atvantage to setting up all these extra ones, and if so, how is this accomplished?

---

### Post by drs305 on 2007-06-03
Here is a pretty good introduction to the considerations of how to partition your drive:

[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by southernman on 2007-06-03
The minimum you'll need to install is:

/ 
swap

The only additional partition that'll be handy for future upgrades, system crashing is a seperate /home

Psychocats (aka aysui) does a nice job of breaking it down for you.

---

### Post by ahaurw01 on 2007-06-03
the advantage to having a /home partition is that you can do a reinstall of your distro without wiping your personal files and things. (ie if you had dapper and now want to install feisty you could totally wipe your / partition and do a complete new install of feisty, keeping your settings and data instead of doing a potentially messy upgrade.)
haven't heard good arguments for creating a /usr and /boot partition for the average user. 
how to set it up? just use the advanced track when installing and create/edit partitions as needed and then click edit partition and select in the drop down menu how you want to mount it- / , /home , /boot, swap... etc. 
It is no big deal if you want to just use the default / and swap partitions- everything should go fine with the install 
have fun!

---

### Post by drs305 on 2007-06-03
As was stated, all you really need are swap and /  . If you decide to go that way there are instructions or links  on this site which can tell  you how to move your home directory ( /home ) to a new partition. I did that and it was fairly easy to do. However, if I had to start all over again I would have made a separate /home folder and have done so on all subsequent ubuntu installations.

---

### Post by FleetAdmiral74 on 2007-06-03
The /home partition looked like a good idea. Found a guide at [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I got to:
find . -depth -print0 | cpio &#8211;null &#8211;sparse -pvd /mnt/newhome/

but terminal gives me 
cpio: You must specify one of -oipt optionme/

Is there a more recent guide, or is this just up to date and I missed something.

---

### Post by drs305 on 2007-06-03
I looked at the site you mentioned. There is a problem with the way word processors handle the script. The correct script at that point should have double dashes in front of null, sparse and preserve.  Lots of programs convert a double dash into a sinlge long one which screws up code.

```
find . -depth -print0 | cpio --null --sparse --preserve-modification-time -pvd /mnt/newhome/
```

Note: If the command doesn't work you may have permission issues and will have to use sudo or change folder permissions to get it to copy correctly.

---

### Post by southernman on 2007-06-03
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Just stick with ^that^ one.

---

