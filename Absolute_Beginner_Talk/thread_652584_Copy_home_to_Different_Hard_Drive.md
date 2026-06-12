---
title: "Copy /home to Different Hard Drive"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by redfish907 on 2007-12-28
Hello.  First, I'm sure this has been covered, but I can not correctly accomplish what I need to based on the posts I've found.  So after two hours, I've given up.

Here's what I need to do:  I installed Ubuntu on a 40GB HD and have been using it for quite a while.  Now I want to install Ubuntu on a bigger HD, but want to copy my /home directory over so I will keep all of my settings.  I'm not worried about the documents... just want the settings the same on the new install so I don't have to go through and configure everything again.

Here's what I did:

I booted off 7.10 LiveCD then opened terminal and did the following:

Old HD = /dev/hda
Old /Home = /dev hda3

New HD = /dev/hdb
New /Home = /dev/hdb3

```

mkdir /oldhome
mkdir /newhome
sudo mount -t ext3 /dev/hda3 /oldhome
sudo mount -t ext3 /dev/hdb3 /newhome
sudo rsync -avP /oldhome/brian /newhome

```

Then I shutdown and boot into the new Ubuntu install on the new HD.  I have documents... but none of my settings.  No Gnome settings, Firefox, etc.

Can someone help me with this?  What am I doing wrong?  I'm sure it's something newbie stupid.

Thanks!

Brian

---

### Post by georider on 2007-12-28
Your commands look right to me . . . . I wonder if you have a different user ID on the new install than the old. Maybe something to check. 

Also, have you compared some of the configurations of the new install to the old? Do they actually differ?

Maybe start with one app and see if you can fix it first and the rest may fall into place.

Hope this helps. Good luck!

-g

---

### Post by redfish907 on 2007-12-29
Thanks for the reply.  I'm not sure what you mean by having a different userid.  None of my configuration settings are on the new hard drive.

I see there is another method of moving your /home directory with the cp command... I'm going to try that and see if it works.

---

### Post by schauerlich on 2007-12-29
Most configuration files are hidden.... maybe rsync skipped over them? I don't know as I've never used it, but, that's what came to mind.

---

### Post by eternicode on 2007-12-29
```

mkdir /oldhome
mkdir /newhome
sudo mount -t ext3 /dev/hda3 /oldhome
sudo mount -t ext3 /dev/hdb3 /newhome
sudo rsync -avP /oldhome/brian /newhome

```

I would think you would want to rsync /oldhome with /newhome, or maybe /oldhome/* with /newhome/

I'm not entirely sure how rsync works, though...

As I mentioned [over here]("http://ubuntuforums.org/showthread.php?t=652743"), while moving my /home from the root partition to its own, new partition, I used

```

cp -aRv /mnt/root/home/* /mnt/home/

```

And it seems to have worked (all my settings were in place, far as I could tell).

So you might try ```
cp -aRv /oldhome/* /newhome/
```

---

### Post by georider on 2007-12-29
Using

```
 rsync -avP /oldhome/brian /newhome 
```

will sync everything including the .config files you are looking for and the "brian" directory to /newhome.

UserID's are simply numbers. When you create usernames, the first username is assigned a userid of 1001. The second, 1002 and so on. If the userids were created in a different order on your new install than they were on the old install they will have different userids. This will cause a permissions issue on your new install because of the -a in the rsync command preserving the userids. 
You can check this by booting into your new install, opening a terminal and typing
```

ls -la

```
and you should see something like
```

drwxr-xr-x 47 brian brian  2152 2007-12-28 16:56 .
drwxr-xr-x 12 root     root       360 2007-10-08 06:47 ..
drwx------  3 brian brian    80 2007-12-27 16:00 .adobe
-rw-r--r--  1 1002 1002  2298 2007-12-21 11:59 .bashrc
drwxr-xr-x  3 brian brian    72 2007-12-26 08:20 .cache
drwxr-xr-x  4 brian brian   168 2007-12-27 20:40 .cddb
drwxr-xr-x  6 1002 1002   248 2007-12-27 18:35 .config
drwx------  3 brian brian    80 2007-12-27 19:38 .dbus

```
The userid shows instead of the username as there is no username associated with the userid. If you see this, you definitely need to chown your files to your new username which will set the userid to your correct userid for this system.

This will show ALL files including any .config files. If you have any numbers listed in the user column, permissions is most likely the culprit. If not, something else is wrong and we can investigate further.

To fix it, simply set all files in your new install as your current username and it will change the userid to match your new username. ```
 sudo chown -R brian /home/brian 
```

You really don't need the Live CD to do this. You can always create a new temporary user on your new install to log into in order to stay away from your real username. This way you don't have to reboot to test. Just log out and log in with your real username.

If you need instructions, let me know. But from the sound of it, your skills are probably strong enough to do it.

Good luck!

-g

---

### Post by redfish907 on 2008-01-09
It's not fun admitting you're dumb... but I'm dumb.  I finally figured out what the problem was.  Thanks georider and eternicode for your help, but as it turns out, no help could have solved my problem.

Here's what happened... Long ago I tried to move my /home to it's own partition.  I copied everything over to the new partition, but something came up and never finished.  So... there was the new "/home" partition and real "/home" directory on the / partition.  All this time I've been rsync'ing and cp'ing the wrong /home.

I decided to fire the computer up today, and try to figure out why this hasn't worked so far.  After a couple of minutes of sitting there looking stupid, the brightest lightbulb turned on.  I remembered trying to move /home before, and I realized I've been copying the wrong "/home" all this time.  I finally copied the correct /home to the new hard drive with "cp -avx /mnt/oldhardrive/home/* /mnt/newhome" and everything worked.

DUH.  Sorry for wasting everyones' time.

---

### Post by jeffus_il on 2008-01-09
> **redfish907 said:**
> It's not fun admitting you're dumb... but I'm dumb.  I finally figured out what the problem was. .

If you're clever enough to know you're dumb then you're NOT DUMB!

---

### Post by georider on 2008-01-09
No waste of time here. There is no problem not worth fixing. :)

Have a better day!

-g

---

