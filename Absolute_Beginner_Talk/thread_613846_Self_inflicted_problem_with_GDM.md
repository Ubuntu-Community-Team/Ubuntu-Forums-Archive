---
title: "Self inflicted problem with GDM"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by stjoenewt on 2007-11-15
Hi all. Being a noob to Linux, I was hosing around with directory groups and permissions, attempting to allow access to partitions. I altered the group for /var, and in the process pretty much hosed things up. 

I now get an error message when I boot, telling me that the /var/lib/gdm directory does not exist and to correct the configuration. If I respond OK, to the error, I can then log onto Linux and can perform an STARTX command, which gets an error indicating it cannot start HAL. If I ignore this, I can use the desktop, although with limited functionality. I know that /var/lib/gdm exists, so it must be an access privileges problem. 

I submitted posts in the desktop forum, and received proper settings for the /var directory, however after correcting them, still get the ServAuthDir error. Currently, the directory characteristics are as follow; 

drwxrw-rw- 16 root root 4096 2007-04-15 08:01 var 
drwxr-xr-x 45 root root 4096 2007-10-28 07:45 lib 
drwxrwx--T 3 root gdm 4096 2007-11-11 17:32 gdm 

In trying different things, I have found that if I change the GDM configuration to use another directory on another volume, which I have created with the same owner and group as /var, that GDM will start. It does have a different look, the sign on screen is blue with a yellow flower, but it does start. 

I also tried to remove and reinstall GDM (sudo apt-get remove gdm & sudo apt-get install gdm) and reconfiguring GDM (sudo dpkg-reconfigure gdm) with no success. I had seen other threads that made me think that might be a remedy. 

It seems to me, at this point, that GDM, or Linux, is remembering the earlier group/access settings, thus preventing it from seeing the /var directories. 

I also posted in the GNOME forums, and received a reply indicating that I should revert the changes.  How would I do that?   I am not very familiar with Linux commands, is there a series I would execute to back off changes I made?  Or, does anyone know what I must reset to cause GDM, or UBUNTU to not remember prior settings? 

Thanks in advance for any assistance.

---

### Post by Hospadar on 2007-11-15
why not just change var back to the correct permissions?

my var permissions (from "ls -o" are ```
drwxr-xr-x  15 root  4096 2007-10-15 19:31 var
```try doing ```
chmod 755 /var
``` to restore normal permissions.  you might also need to alter permissions inside /var if you originally changed them recursively.

ls -o /var gives me this:```
drwxr-xr-x  2 root 4096 2007-11-15 07:36 backups
drwxr-xr-x 17 root 4096 2007-10-29 16:59 cache
drwxrwxrwt  2 root 4096 2007-11-15 12:12 crash
drwxr-xr-x  2 root 4096 2007-10-15 19:31 games
drwxr-xr-x 55 root 4096 2007-10-29 16:49 lib
drwxrwsr-x  2 root 4096 2007-10-08 06:47 local
drwxrwxrwt  2 root   60 2007-11-14 10:05 lock
drwxr-xr-x 14 root 4096 2007-11-15 07:40 log
drwxrwsr-x  2 root 4096 2007-10-15 19:17 mail
drwxr-xr-x  2 root 4096 2007-10-15 19:17 opt
drwxr-xr-x 14 root  620 2007-11-15 08:32 run
drwxr-xr-x  7 root 4096 2007-10-15 19:22 spool
drwxrwxrwt  3 root 4096 2007-11-15 12:16 tmp

```And in the future, don't monkey about with permissions on system files! it never ends well =)

If you arn't familiar with "chmod" (which changes permissions), try doing "man chmod" or look it up on the internet.

also note that re-installing gdm wouldn't affect this, as the permissions on /var are totally seperate from the gdm package.  I'd guess what you did was to alter permissions so that gdm no longer had execute permissions on what it was looking for.

---

### Post by stjoenewt on 2007-11-15
Thanks for the quick reply Hospadar.

I had attempted to change back everything I had touched.  I went back and reset owner and group of directories and subdirectories, as well as permissions.  I had however missed the /var setting of r-x and had it as rw- instead.  Don't know where I got that, probably from one of the many threads I read in various forums.   

But in any case, I have learned a little more about Linux, which is a good thing, even though it was somewhat painful.   And your reply, with the correct settings for the directories, was a vital tip.  

Thanks again.

---

