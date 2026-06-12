---
title: "sudo chmod og+w /mnt/media &lt;-Failing..why?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Lor Boo on 2006-08-05
I cannot seam to get write rights to a folder for my user (me!) :confused: 

**_History:_**
Harddrive partitioned:
[COLOR="DarkGreen"]HDA1 - 20 gigs - vfat - no os installed.
HDA2 - 35 gigs - ext3, Ubuntu
Swap - 1.4g gigs

[COLOR="Black"]HDA1 mounted with command:[/COLOR]
drinky@drinky:/$ mount -t vfat /dev/hda1 /mnt/media

[COLOR="Black"]Then made directory:[/COLOR]
drinky@drinky:/mnt$ mkdir /mnt/mp3
mkdir: cannot create directory `/mnt/mp3': Permission denied
drinky@drinky:/mnt$ sudo mkdir /mnt/media/mp3
drinky@drinky:/mnt$ ls
media

[COLOR="Black"]Current folder rights:[/COLOR]
drwxr-xr-x 3 root root 16384 2006-08-05 15:27 media
drwxr-xr-x 2 root root 16384 2006-08-05 15:27 mp3[/COLOR]

And now I'm stuck.  I cannot get write access to either folder media or mp3.  I've tried a few things including:
[COLOR="Navy"]drinky@drinky:~$ sudo chown drinky:users /mnt/media/mp3
Password:
chown: changing ownership of `/mnt/media/mp3': Operation not permitted
drinky@drinky:~$ sudo chmod a+rw /mnt/media/mp3
drinky@drinky:~$ ls -l /mnt/media
total 16
drwxr-xr-x 2 root root 16384 2006-08-05 15:27 mp3
drinky@drinky:~$ sudo chmod a+rw /mnt/media
drinky@drinky:~$ ls -l /mnt
total 16
drwxr-xr-x 3 root root 16384 2006-08-05 15:27 media
drinky@drinky:~$ sudo chown drinky:users /mnt/media
chown: changing ownership of `/mnt/media': Operation not permitted
drinky@drinky:~$ sudo chmod 777 /mnt/media/mp3
Password:
drinky@drinky:~$ ls -l /mnt/media
total 16
drwxr-xr-x 2 root root 16384 2006-08-05 15:27 mp3
drinky@drinky:~$ sudo chmod g+w /mnt/media/mp3
drinky@drinky:~$ ls -l /mnt/media
total 16
drwxr-xr-x 2 root root 16384 2006-08-05 15:27 mp3
drinky@drinky:~$ sudo chmod g+w /mnt/media
drinky@drinky:~$ ls -l /mnt
total 16
drwxr-xr-x 3 root root 16384 2006-08-05 15:27 media
drinky@drinky:~$

[/COLOR]

I've tried other things too and read around.. that's where the chmod a+rw /mnt/media came from..I'm not familar with "a" as a flag.. I thought it was ugo? with either rwxX or 3 numbers such as 777 or 770 etc...

I didn't think I'd have to post for help with chmod...but here I am..
Thanks for any help.

[COLOR="DimGray"]Last note: orginally I created the hda1 partition from win2k.  The ubuntu 'system / administrator / disks' gui could not access it.  So I formated selecting vfat in case that makes a difference?[/COLOR]

---

### Post by taurus on 2006-08-05
You need to set the permission in /etc/fstab since changing it from a command line won't work for vfat!!!  Just add this line to your /etc/fstab...

```

/dev/hda1   /mnt/media   vfat   defaults,umask=0000   0   0

```
Then, unmount /dev/hda1 first and mount it again with

```

sudo umount /dev/hda1
sudo mount -a

```

---

### Post by Lor Boo on 2006-08-05
Thank you much Sir.
I'm up and running.

I feel a sence of satisfaction at least in the knowleage that I would
not have figured this out on my own very easily.

Also, you know, i've played with linux before, Red Hat 8.  Mandrake 9 and 10.....I never really got a lot of support outside IRC...and IRC was very hit or miss with many many misses.
This time I'm hoping to keep with it.

Thanks again.
Lor Boo.

---

### Post by taurus on 2006-08-05
Glad to hear that you can read/write to your vfat now.  Just stick around here and you might learn more and if you run into something that you don't know, try to see if you can figure it out first (that's how you learn) and if not, just post it here with much details as you can.  Then, I bet somebody will get back to you real fast...  ;)

---

### Post by Lor Boo on 2006-08-05
That's the plan.
3 weeks soly in ubuntu...and this was my first posting.
Thanks again.

---

