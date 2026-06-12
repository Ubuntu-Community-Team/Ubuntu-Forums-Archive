---
title: "what would be the easiest method of transfering"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by redhue on 2007-12-30
I,ve just upgraded my PC with a 120GB hard drive from a 40GB.I was trying out ubuntu and am very happy with it.My problem is that I,m not sure about the best way to move all of the desktops and other folders and files to the new hard drive from the old one.I,ve loaded ubuntu on to my new drive.So now when I start my PC up I,m given the option of either Ubuntu on my old drive or ubuntu on my new one.So is there a way of transferring or merging the two drives to where I am just running one OS with everything accessible.My wife is not very happy with "my making things so complicated and that she is going to loose her desktop that she just got done  decorating just the way she wanted it"PLEASE HELP QUICK ! in the interest of domestic harmony.THANX

---

### Post by ^rooker on 2007-12-30
All your per-user settings (Desktop, preferences, etc...) are stored in subfolders and files in that user's home directory.

So if you simply copy /home/* to the new drive you're *almost* done. Now you have 2 options:

1) If you want to completely replace your 40GB hdd you must copy the whole system - more complicated. I'll help you through this on demand.

2) If you're just adding the 120 GB to the 40 GB, move /home/* to the new drive and either:
a) symlink /home on the old drive to point to the new location of home - e.g. 
ln -s /media/120GB/home /home
b) mount the new drive directly as /home in /etc/fstab.


Sorry, but you didn't mention your experience level, so if the above sounds like gibberish, I'll give you more GUI-focused infos.   :)

---

### Post by redhue on 2007-12-30
> **^rooker said:**
> All your per-user settings (Desktop, preferences, etc...) are stored in subfolders and files in that user's home directory.

So if you simply copy /home/* to the new drive you're *almost* done. Now you have 2 options:

1) If you want to completely replace your 40GB hdd you must copy the whole system - more complicated. I'll help you through this on demand.

2) If you're just adding the 120 GB to the 40 GB, move /home/* to the new drive and either:
a) symlink /home on the old drive to point to the new location of home - e.g. 
ln -s /media/120GB/home /home
b) mount the new drive directly as /home in /etc/fstab.


Sorry, but you didn't mention your experience level, so if the above sounds like gibberish, I'll give you more GUI-focused infos.   :)

OK my experience is pretty minimal so yeah if you could kind of walk me through it I won't become the heel of the household and I'll be able to at least appear to be a technical wiz and save face. I hope you don't mind.

---

### Post by ^rooker on 2007-12-30
I'll do my best, but first please tell me which harddisk(s) should finally stay in the system, and if you can already see/access the new 120GB disk.

---

### Post by jken146 on 2007-12-30
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Is that what you want?

---

### Post by Paqman on 2007-12-30
Can you browse the old drive when you're logged into the copy of Ubuntu on the new drive? If so, just copy the respective home folders for the users on the old system over to the new one. You'll need root privileges for that. You can fire up Nautilus as root by using:
```

gksudo nautilus

```
Remember to close this Nautilus session after you've copied the files!

You may strike problems with permissions. Make sure that the user accounts on both systems are identical to avoid this. Check the user id numbers in each user's account (System > Administration > Users and Groups)

---

### Post by redhue on 2007-12-30
sorry I got pulled away. OK My intent is to just have the 120 if possible. Unless it is easier or necessary to keep both. but as it stands I have the 120 as the master and the 40 as the slave.And am working of the 120 right now.

---

### Post by redhue on 2007-12-30
> **^rooker said:**
> I'll do my best, but first please tell me which harddisk(s) should finally stay in the system, and if you can already see/access the new 120GB disk.

sorry I got pulled away. OK My intent is to just have the 120 if possible. Unless it is easier or necessary to keep both. but as it stands I have the 120 as the master and the 40 as the slave.And am working off of the 120 right now__________________

---

### Post by ^rooker on 2007-12-31
no prob. I also got pulled away (sleep).   :)

I've looked at the link suggested by jken146 and there are some things in there I think are not necessary, so I'll still explain how you could do it (looks more complicated than it actually is, don't worry):
([COLOR="Red"]Warning:[/COLOR] Close all applications, unless the ones that are necessary, because they *might* lock/write/modify files in your /home while you're copying it)

1) Boot the "Old" ubuntu installation. 
2) Make sure that you can access the 200GB drive with your new installation on it somehow (e.g. as /media/200GB)
3) You have to be root to completely copy /home - so (as Paqman said), run Nautilus as root:
"gksu nautilus"
4) Rename /home on your *new* drive to something else. e.g. "xxx_home"
5) Copy /home from your *old* system to the new drive as /home, too.

Now all you have to do is change the ownership of that home-copy to the right users of your new system (they might have different user-ids now).
You could check if that step is necessary by comparing your old and your new /etc/passwd. 

Look for lines with the usernames that have their home in /home. It will look somewhat like this:

```
user1:x:**1000:1000**::/home/user1:/bin/sh
user2:x:1001:1001::/home/user2:/bin/sh
...
```

If the IDs (here bold) match on both systems, you're done. If not, you must change the *new* home folders to belong to the right users. I'm sorry, I don't know how to do that with Nautilus ("right click/permissions/change owner" I guess?).

Here's how to do it in the shell
```
chown -R NEWUSERID1:NEWUSERGROUP1 /home/user1
chown -R NEWUSERID2:NEWUSERGROUP2 /home/user2
```

...where "NEWUSERID" and "NEWUSERGROUP" are the IDs taken from your *new* setup's /etc/passwd.


Actually, that's it. In case that rebooting to your new system chokes on these new home folders, due to some error, reboot your old system and swap the copied /home with the backed up "xxx_home".


Good luck!

---

