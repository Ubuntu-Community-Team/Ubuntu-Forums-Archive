---
title: "Duel-Boot, Error Logging in"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by sirgogo on 2008-01-27
Hello all:

I recently duel-booted my laptop with Windows XP Pro and 7.10. Everything was going fine. But then...

I wanted to set my home dir to /media/disk/Documents and Settings/Abhejit Rajagopal/My Documents
I set this using the GUI from System-->Administration-->User and Groups, so there wasn't any problem with the spacing/

So now, I restarted to see if the changes would take effect. Unfortunately they didn't, but placed me with an error that said I couldn't log in. So I changed to the terminal screen and started looking around.

I checked the /etc/passwd file:
```
sudo nano /etc/passwd
```
but everything showed up just as I had set it.

Then I suspected that it could be that the partition was not mounted.
So I poked around.:
```
abhe@abhe-laptop:/$ cd /
abhe@abhe-laptop:/$ cd media
abhe@abhe-laptop:/media$ ls
cdrom  cdrom0
abhe@abhe-laptop:/media$ cd ..
abhe@abhe-laptop:/$ cd mnt
abhe@abhe-laptop:/mnt$ ls
abhe@abhe-laptop:/mnt$ 
```.

I know I can fix the login by changing the /etc/passwd file, but I wanted to figure this out!

Any ideas on how to auto/manually mount the windows partition, even though its not recognized in the media folder?

Thanks.

---

### Post by gerscht on 2008-01-27
what does ```
df -h
``` say? 
(It will list all mounted file systems.)

---

### Post by mikewhatever on 2008-01-27
Hi, I had no idea it was possible to change you home the way you did. Anyway, here is a very similar thing done successfully, the only difference that may cause problems is ntfs file system in your case. [http://ubuntuforums.org/showthread.php?t=676018](http://ubuntuforums.org/showthread.php?t=676018)

---

### Post by sirgogo on 2008-01-27
Hey,

The output was as follows:

```
abhe@abhe-laptop:~$ df -h
Filesystem            Size    Used Avail Use% Mounted on
/dev/sda2             392G   3.1G   34G   9% /
varrun                   346M   96K  346M   1% /var/run
varlock                 346M        0  346M   0% /var/lock
udev                     346M    60K  346M   1% /dev
devshm                346M     0      346M   0% /dev/shm
lrm                   346M         64M  313M   10% /lib/modules/2.6.22-14-generic/volatile
abhe@abhe-laptop:~$ 

```
Ah, that took a while to type.

Yeah, but I can't find my 15 GB partition! I Well, first of all, when I was duel-booting, I made it 53% of 57 gb hard drive, but then when I logged in a "15 G.B." disk was mounted. Kinda weird, but it was okay because the Ubuntu partition accounted for the rest, so maybe I accidentally made it more than 53%. Thats not a big issue though....

Where is my partition!?!

Edit: Mike, thanks for the link. I looked through the thread, but the problem I'm having is that my partition has "disappeared" (as seen above), or it is not detected. Hmm...
Perhaps there is a way to auto-mount all devices before the gdm login?

Thanks for your help.

---

### Post by sirgogo on 2008-01-27
Hoold on!

I found it. I tried mounting sda1, and it worked:

```
mount /dev/sda1/ /media/windows
```
(this is after I created a folder in /media/ called "windows")

Aiite, cool, now I just need to get it to auto-mount. I think I'll try and use that fstab stuff.

Thanks guys.

---

### Post by sirgogo on 2008-01-28
Ahh!

This is being painful now! Okay so this is the status:
-found out that /dev/sda1 is my windows partition
-added a fstab line that looks like this:```
/dev/sda1 /media/windows  ntfs defaults,errors=remount-ro 0 1 
```
-made sure my /etc/passwd file said:```
/media/windows/Documents and Settings/Abhejit Rajagopal/My Documents/:bin/bash
```
- tried ```
chmod 600 ~/.dmrc
```, didn't work.
-used ```

sudo chown -R abhe /media/windows/Documents and Settings/Abhejit Rajagopal/My Documents
sudo chgrp -R abhe /media/windows/Documents and Settings/Abhejit Rajagopal/My Documents
sudo chmod -R 755 /media/windows/Documents and Settings/Abhejit Rajagopal/My Documents
sudo chmod 644 $HOME/.dmrc
```
And I get an error on the last line. It tells me that
```
chmod: invalid mode: '/media/windows/Documents'
Try 'chmod --help' for more information,
```


ALSO: When I attempt to login, it tells me that the $HOME/.dmrc is being ignored and to make sure it has 644 privileges or something.


Any ideas guys? :(

---

