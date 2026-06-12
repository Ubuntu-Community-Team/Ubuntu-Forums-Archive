---
title: "[SOLVED] /home and /usr mounted as directories"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by minhamra on 2007-10-15
Hello All, 

Here is the holy grail. I would like to have my base Ubuntu install on one partition and have the following directories in SDA2 (for example)

So /home would be SDA2/home
    /usr would be SDA2/usr

The idea would be that I could back up one partition and get all the changing data and installs. 

So I am guessing that I would have to mount the drive 1st
then mount each directory in that partition.

I have seen directions on how to move /home and /usr to seperate partitions but none on how I could have them both be on a single partition. 

Of course Gutsy is here and I want to move my /home and /usr before I upgrade so that I can keep all the crap I have installed. My crap is stuff, everyone else's stuff is crap. I think George Carlin said that, I paraphrase.

---

### Post by jdfreshwater on 2007-10-15
I think you can only mount 1 partition per directory.  This is because of locking done on writting to that directory.  I believe the only way to do what you want is to use 3 partitions.  one for /home one for /usr and one for / .  I could be wrong though.  If anyone has any contradiction please indicate it.

---

### Post by vikram on 2007-10-15
you could mount only the root to a partition, that way everything under root will be in the same partition. Swap is an exception - it needs to be in its own partition and formatted as swap and not ext3.

having said that I strongly recommend creating home in a seperate partition. that way if you want to reinstall the os, try another distro etc. your data, preferences, favourites etc. are preserved

---

### Post by minhamra on 2007-10-17
I think I have not been clear....By default /home and /user are directories off root (/) I just want to have root on one partition and /home and /user on another (lets say Sda2) so off of /Sda2 I would have /Sda2/home and /Sda2/usr.

---

### Post by Keith_Burton on 2007-10-17
I did this once several years back with /var. 

Mount your 2nd drive. I'll call it /media/drive2 here.
Make sure it's auto-mounting in /etc/fstab before proceeding. Reboot and test it.
Copy your existing data onto drive2: cp -a /home /media/drive2/home
  [check to verify that worked, as sometimes I mess up the exact syntax for copying directories :) ]

Rename the old directories, in-case you need to backout:
mv /home /oldhome

Create symbolic links to the new locations:
ln -s /media/drive2/home /home

and repeat for /usr, if it worked. After you're sure everything's good, delete the /oldhome and /oldusr directories.

Hope this helps!

---

### Post by dwblas on 2007-10-17
You can do that when you install.  If you want to change an existing system, then you want to modify /etc/fstab.  Something along the lines of
/dev/sda2  /home  ext3  defaults  0  2   (although I don't know if sda entries are different)
This will mount the sda2 drive under /home.  If you want both on the same drive, then you will have to create a directory, let's say /sda2, as well as /sda2/home and /sda2/usr, and mount /dev/sda2 at /sda2.  You may or may not have to symlink /sda2/home-->/home, but I would suggest avoiding this by breaking up /dev/sda2 into 2 new partitions and mounting /home on one and /usr on the other.  You can then tar the contents of /home and /usr as backup.  Mount /dev/sda2 at /media/sda2 and cp --preserve -- recursive /home's contents, delete /home's files, and then unmount and mount which will mount the new /home directory that is now on sda2.  Hopefully, this overly long post gives the general idea.

Edit: Of course Google has many entries like [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by minhamra on 2007-10-18
Thank you everyone, this certainly gives me the direction to head in.

---

