---
title: "bin and other permissions"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-05-18
Edit: Now I can't access the recovery mode either since I'm not root. Looks like it is reinstall time...

Accidentally changed permissions of /bin, possibly /usr/bin and /usr/bin/sudoers and need to reset them. I think I can reset them from the recovery mode. What chmod numbers do I use?

Background: I lost my network connection and then noticed I also couldn't use sudo. In attempting to correct them via posts on this forum, I screwed up the permissions of several important folders  (my fault, not the instructions in the posts). Now I can't boot into Ubuntu due to lots of permissions denied - I think because the permissions are set incorrectly. I know I screwed up the /usr/bin and /bin permissions and possibly others... Oops.

---

### Post by kebes on 2007-05-18
Well on my systems all the files in "/bin" and "/usr/bin" have permissions like:
-rwxr-xr-x 

So you could manually fix them by going:
```

cd /bin/
sudo chmod 766 * -R
cd /usr/bin
sudo chmod 766 * -R

```

Of course since you can't boot, you'll have to boot into a LiveCD, mount your hard drive, and go to the proper directory (e.g. "cd /media/hda/bin/").


Hopefully that's the only thing that has been changed...

---

### Post by kebes on 2007-05-18
> **drs305 said:**
> Edit: Now I can't access the recovery mode either since I'm not root. Looks like it is reinstall time...

Like I said, instead of using the recovery mode, you can boot into an Ubuntu LiveCD, and make the changes from there. Just boot into it the LiveCD, mount the hard-drive, and make the required changes. To mount a hard drive partition you would use a command like:

cd /media/
sudo mkdir drive
sudo mount /dev/hda drive

---

### Post by drs305 on 2007-05-18
I think I edited my original post before seeing your post. I'll try booting the live CD - I have always used the alternate CD for installations - and see if I can get the permissions fixed. It would certainly be easier than reinstalling even though I have a separate /home folder.

Thanks for the assistance.

---

### Post by drs305 on 2007-05-18
I reset the /bin and /usr/bin permissions but when I rebooted I saw a bunch of 'permission denied' lines flash by and it ended with 'failed to start the X server. It is likely it is not set up correctly'.

The only permission I did not change this time was the /etc/sudoers file but it had the same properties as the file on this working computer (root:root read only, others none).

---

### Post by taurus on 2007-05-18
> **kebes said:**
> 
```

cd /bin/
sudo chmod 766 * -R
cd /usr/bin
sudo chmod 766 * -R

```


If you run those commands, you will never be able to use your machine as a regular user again since you don't have executable permissions to run anything in /usr & /usr/bin.

It should be

```
cd /bin
sudo chmod -R 7**[COLOR="Blue"]55[/COLOR]**
cd /usr/bin
sudo chmod -R 7**[COLOR="Blue"]55[/COLOR]**
```

---

### Post by drs305 on 2007-05-18
Okay, thanks guys. I've started to reinstall the system so that should fix things.

---

