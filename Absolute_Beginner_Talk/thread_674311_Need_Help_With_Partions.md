---
title: "Need Help With Partions"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by aztecnk on 2008-01-21
i have a dell with 2 40gb hardrives. i have windows xp on one hard drive and want to install ubuntu 7.10 on the other drive using only 10 gb. the problem that i have is that i try to install ubuntu it gives me error message "no root file is defined". im at step 4 of 7 in the installation process. i want to be able to use both os and if possible, be able to access files from ubuntu with windos xp. also im not shure wat these mean:     /dev/sdb1 ext 
               /media/sda2
                ext2
                reiserfs
               jfs      xfs        swap
also im given the options of mount point:
            /            /boot       /home      /tmp     /usr      /var       /srv      /opt
                     /usr/local

id appreciate it if someone can help me with the meaning of these and what their purpose is.

---

### Post by cyclefiend2000 on 2008-01-21
"/" is the root mount point. you need to assign "/" to one of your partitions. 

take a look at this walk-through...
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

edit: this link describes the linux file structure in pretty good detail....
[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

---

### Post by njparton on 2008-01-21
I would go for the following:

**/swap** at 1GB
**/** at 10GB
**/home** the remainder

Use ext3 for greatest compatibility for the last 2.

---

### Post by thelatinist on 2008-01-21
I would not create a separate home partition.  I would create a separate *data* partition to store music, documents, etc., but I would not save my /home folder to it.  It just creates a false sense of security and is likely to cause more headaches than not if you ever have to reinstall.

You can easily symlink your Document, Music, and Videos folders to folders on your data partition.

So I would create the partitions njparton suggests, all of them ext3, but I would not the third as my /home.

---

### Post by vikram on 2008-01-21
I would create both a data partition and a seperate home partition.

In case you had to do a reinstall the seperate data partition will protect your media files. 

If you kept your home directory you can preserve desktop customization on a reinstall. I dont know if I do a lot of desktop customization becasue I use KDE or chose KDE because I like to completely customize my desktop and I'd hate to loose them :-)

---

### Post by thelatinist on 2008-01-21
> **vikram said:**
> If you kept your home directory you can preserve desktop customization on a reinstall.

That's what regular backups are for. ;-)

---

### Post by njparton on 2008-01-22
> **thelatinist said:**
> I would not create a separate home partition.  I would create a separate *data* partition to store music, documents, etc., but I would not save my /home folder to it.  It just creates a false sense of security and is likely to cause more headaches than not if you ever have to reinstall.

You can easily symlink your Document, Music, and Videos folders to folders on your data partition.

So I would create the partitions njparton suggests, all of them ext3, but I would not the third as my /home.

Not as straight forward for a newbie though.  Keep it simple. Home partitions have always worked for me, even after upgrades and reinstalls between distros.

---

### Post by housam on 2008-01-22
> **aztecnk said:**
> i have a dell with 2 40gb hardrives. i have windows xp on one hard drive and want to install ubuntu 7.10 on the other drive using only 10 gb. the problem that i have is that i try to install ubuntu it gives me error message "no root file is defined". im at step 4 of 7 in the installation process. i want to be able to use both os and if possible, be able to access files from ubuntu with windos xp. also im not shure wat these mean:     /dev/sdb1 ext 
               /media/sda2
                ext2
                reiserfs
               jfs      xfs        swap
also im given the options of mount point:
            /            /boot       /home      /tmp     /usr      /var       /srv      /opt
                     /usr/local

id appreciate it if someone can help me with the meaning of these and what their purpose is.

Re arrange your partitions first through Gparted ( a partionner on the live CD ) . You have to create at least 2 partions : ( / ) for the root  about 10 GB and a swap partition about 1 GB. During installation , when it comes to the partition choices , choose the manual one and assign them for installation.

You can also make your XP recognizing ubuntu drives if you install the fs-driver from [COLOR="Red"][[COLOR="Red"]this link [/COLOR]]("http://www.fs-driver.org/")[/COLOR].

---

### Post by starfry on 2008-01-22
Interesting discussion, and one I've been wondering about.

Does anyone partition off things like /tmp, /var, /srv, /home ... ?

The advantage of having separate partitions is that you minimise the risk of filling up your root partition which is most likely to cause your system to have problems.

The disadvantage is it is harder to set up and you can potentially waste space by allocating too much to a partition (and, converseley, run out of space by not allocating enough to a partition).

I compromise by having multiple big partitions (actually on different disks) that I "move" parts of the filesystem to and then reference them via symlinks.

My scheme has one big partition for / but parts of it are symlinked onto other big partitions disk on other disks:

/home -> /media/hdb1/home
/srv/www -> /media/hdc1/srv/www
/srv/transfer -> /media/hdb1/srv/transfer
/var -> /media/hdb1/var

and so on. I have a script to make my links after a re-install.

---

