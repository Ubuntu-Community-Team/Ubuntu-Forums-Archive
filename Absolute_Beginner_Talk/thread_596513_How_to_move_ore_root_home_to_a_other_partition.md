---
title: "How to move ore root /home to a other partition?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Chris11 on 2007-10-29
I think this was asked before but I can't find any post - probably my search terms are incorrect..
so how can I have my personal folder ion a other disk ore on a other partition? 

Chris

---

### Post by llamakc on 2007-10-29
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by nest on 2007-10-29
sudo nautilus

copy & paste it :)

edit: think i missunderstood the question. sorry.

---

### Post by Chris11 on 2007-10-31
ok.. I followed the steps in the  link but I have no success,

I copied the home folder with the given command to the new partition (former mounted to media/30MB), and changed the permissions from "root" the "user".

in fstab I # the former mounting point and added the new line

> 
# /dev/hda1 media/30MB ext3 user,auto 0 2
/dev/hda1 /home ext3  nodev,nosuid 0 2


at boot I get a error message that /home is not found respect. configuration not found, and the desktop start up with different settings (screen resolution, etc...). Once started up I can see home and open my folder, in gparted the partition is mounted at /home. 

any ideas were I'm doing something wrong?

Chris

---

### Post by volksman on 2007-10-31
Did you empty or move the existing /home before the reboot?  In order for the mount to work there needs to be an empty /home directory waiting for it.

Also you don't need to reboot.....A sudo mount -a should do the trick....

---

### Post by Chris11 on 2007-10-31
I don't understand exactly what you mean. I copied the home folder to the new partition, but it is not empty, all my personal program data are there, i.e. several GB of amule files, thunderbird files etc, etc... The old home folder is still in place were it was before - should I move it to a other place?

Chris

---

### Post by volksman on 2007-10-31
hrm...hard to explain in text... :)

What you start with:

```
/home
     /username1 - bunch of data in the dir
     /username2 - bunch of data in the dir
```

What you do to move it:

move the CONTENTS of the /home directory to the new drive (so from your fstab it WAS /media/30MB)

What you end up with:

```
/home - empty
/media/30MB
             /username1
             /username2
```

(Notice that there is no home directory on /media/30MB, the home part is where you mount the info into.  Otherwise you end up with /home/home/username1)

Then modify your fstab to mount /dev/hda1 /home

Then run 'sudo mount -a'

What you should end up with is /home/username1 again....if you run the mount command you should see that /dev/hda1 is mounted to /home.

This can all be done without a reboot.

---

### Post by statikeffeck on 2007-10-31
You could also move all the data within /home to your preferred partition which is probably mounted under /media/something (type mount to find mounted directories).
Then, you can create a symbolic link so /home points to something else (this is probably not recommended, but it is a nice feature of symbolic links).

---

### Post by volksman on 2007-10-31
I would highly recommend you DON'T go that route....It works but some shell functions get messed up as your real home is /media/somedir/home/user instead of just /home/user.

Like I said it works and I did that when I first started playing with linux but it does have some weird side effects...

---

### Post by Chris11 on 2007-10-31
thanks I got it working now.. the problem was copied home/user to the new partiion instead of just /user...

I think it would be a nice feature of the  Ubuntu 8.04 if it is possible to move personal folders to other disks ore partition in a easier way...

Chris

---

