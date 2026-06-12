---
title: "File permissions. (or partition)  Easy fix?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by skydivingbiker on 2006-11-13
Hi,
This might be an easy one for you guys.

I have a partition hda3 on the dev/media/hda3

I want to change those permissions.  There are 3 of us users:p :p :p , with different logins.  I want to change that partions or file path, so that we all can read, write, execute, or whatever floats our boat. 

I have an Ubuntu book, but... ](*,) 

my plan is to keep the partition hda3 or dev/media/hda3 open for all of us to share :-\" music:-({|= , or funny videos, or whatevers clever.  It will be the bulk of our storage. :idea:  

But I can't get the permissions to work, so all the users can read, write.. and.....

So now I'm ready to screw around with some sudo commands \\:D/

---

### Post by taurus on 2006-11-13
Is /media/hda3 a NTFS, fat32, or ext3?

---

### Post by skydivingbiker on 2006-11-13
> **taurus said:**
> Is /media/hda3 a NTFS, fat32, or ext3?

Ext3

Hey man, whatcha doin here?  you replied to my post in a cigarette's time.

You must be devoded to the ubuntu...... Idea?

---

### Post by taurus on 2006-11-13
Since it's a ext3, you can change the permissions with chmod command.  Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo chmod -R 777 /media/hda3
```

p.s.  Is it /dev/media/hda3 or /media/hda3?  You can know for sure which one it is by looking at the output of this command!

```
df -h
```

p.s.s.  No smoking around here!!!  ;)

---

### Post by skydivingbiker on 2006-11-13
> **taurus said:**
> Since it's a ext3, you can change the permissions with chmod command.  Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo chmod -R 777 /media/hda3
```

p.s.  Is it /dev/media/hda3 or /media/hda3?  You can know for sure which one it is by looking at the output of this command!

```
df -h
```

p.s.s.  No smoking around here!!!  ;)

Okey doke.  So I typed in the code, put in the root password, but when I go to the hda3, I dont have the option to create a folder in the natalauis GUI.

Oh hey, long as im here.  My experience in compuers have been OS/390, ZOS, (mainframe) and a little bit of AS/400.  Lately at work I've been wondering how well Linux works.  Just started using Unix at my new job.  Anyway, thats the reason I abandoned microsoft and started loving Ubuntu linux.

I can't wait to dig in and screw around with everytyhing! Wait.. headbanging smiley.. scroll down window imported smileys... hmm.. 

Ps.. there's plenty of smoking around here \\:D/ 

Oh hey, should I log out and log back in?  or is that a windows thing?

---

### Post by taurus on 2006-11-13
Is that /dev/media/hda3 or /media/hda3?  What is the output of this command from a terminal then?

```
ls -la /dev/media
-or-
ls -la /media
```

---

### Post by skydivingbiker on 2006-11-13
jason@monstermachine:/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              30G   22G  6.4G  78% /
varrun                237M   84K  237M   1% /var/run
varlock               237M  4.0K  237M   1% /var/lock
udev                  237M  112K  237M   1% /dev
devshm                237M     0  237M   0% /dev/shm
lrm                   237M   19M  218M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hda1              15G   15G     0 100% /media/hda1
/dev/hda3              59G   19G   39G  33% /media/hda3
jason@monstermachine:/media$ sudo chmod -R 777 /media/hda3
Password:
jason@monstermachine:/media$

I don't mind leaving in monstermachine, I doubt anyone here has any ill intent.

So comon man, whatcha do for a living?  are you at work right now slacking?:twisted: 

So after I executed the above, I went to Places > Home, then switched to hda3 on the side bar "places"

When i right click in open space, the option to create a folder is greyed out?  I want to create a folder to move all of our shared data too.

Oh, and by the way, you rock. =D>

---

### Post by skydivingbiker on 2006-11-13
oops.. I think I screwed it up! ](*,)

---

### Post by taurus on 2006-11-13
What is the output of these two commands then?

```
ls -la /media
ls -la /media/hda3
```
p.s.  About to grab something to eat before I go to work.  Working late tonight...

---

### Post by skydivingbiker on 2006-11-13
drwxr-xr-x  5 root root 4096 2006-11-13 07:32 .
drwxr-xr-x 21 root root 4096 2006-10-27 03:38 ..
lrwxrwxrwx  1 root root    6 2006-10-27 02:48 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-10-27 02:48 cdrom0
drwxr-xr-x 21 root root 4096 2006-09-29 15:06 hda1
drwxrwxrwx  5 root root 4096 2006-11-13 13:38 hda3
jason@monstermachine:/media$ ls -la /media/hda3
total 20
drwxrwxrwx  5 root  root  4096 2006-11-13 13:38 .
drwxr-xr-x  5 root  root  4096 2006-11-13 07:32 ..
drwxrwxrwx 39  1003 hda3  4096 2006-10-26 14:55 bambi
drwxrwxrwx 23 john  john  4096 2006-10-03 16:36 casey
drwxrwxrwx 35 jason jason 4096 2006-11-13 13:20 john
jason@monstermachine:/media$

---

### Post by taurus on 2006-11-13
```
cd /mnt/hda3
sudo chmod 777 .
mkdir /media/hda3/test
```

---

