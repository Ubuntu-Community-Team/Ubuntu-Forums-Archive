---
title: "Installation problem.... Please help."
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Newman05 on 2006-05-14
Hi Gys,

I'm tried to install Ubuntu on my laptop several times. I have currently Windows 2000 on it and I'm trying to make a daul boot. For some reason it gives me an error during installing the base system. At 68% it gives me an error message "Unable to install initrd-tools check /target/var/log/bootstrap.log for details". 

At this point I'm hopeless and I can't do anything but trying to delete the partition and the swamp and try to re-install. Off course I will be unable to have the option of accessing Windows 2000. ](*,) 

The laptop is an old Sony. with 64 MB RAM, 12 GB HDD, trying to install Ubuntu on 4 GB.

Thank you very much in advace for your help. :(

---

### Post by catlett on 2006-05-14
It should install on that size partition. You might want to try Xubuntu though it runs on less ram  [http://www.xubuntu.org/](http://www.xubuntu.org/)
If you have a windows install disc or a rescue disk from your computer maker you can access windows again. Boot into the disk and enter recovery mode. In recovery you can get a command line enter ```
fixmbr
``` That will rewrite your windows bootloader to the mbr. At least you can get into windows until you straighten out Ubuntu.

---

### Post by Sef on 2006-05-15
> The laptop is an old Sony. with 64 MB RAM, 12 GB HDD, trying to install Ubuntu on 4 GB.

Since you only have 64 ram and 4 GB HD, I would look to install Xubuntu.  It is a lightweight window manager.  Will run faster than Gnome or KDE.

---

### Post by Newman05 on 2006-05-15
Thanks catlett, thanks Sef. I will give it a shot and I will let you know.

Regards.

---

### Post by izvie on 2006-05-15
I had the exact same error come up while I was installing on *my* old Sony laptop. It was also a dual boot I was setting up, but with XP instead of 2000. 

I got around the error by clicking "go back" or whatever it said, and I was presented with a list of what the install had done already.  I skipped the step that didn't work and went onto the next step, (I believe the step that wasn't working was "installing base packages").  

Oddly enough, the whole install finished after that with no errors.  I have loaded it three times now for practice and each time the same error popped up and each time this workaround fixed it.  Hope this helps and good luck.

Oh, and that fixmbr command Catlett mentioned?  It works like a charm.  It'll bring your Windows 2000 machine back to normal in about 30 seconds.

[QUOTE=Newman05]Hi Gys,

I'm tried to install Ubuntu on my laptop several times. I have currently Windows 2000 on it and I'm trying to make a daul boot. For some reason it gives me an error during installing the base system. At 68% it gives me an error message "Unable to install initrd-tools check /target/var/log/bootstrap.log for details". 

At this point I'm hopeless and I can't do anything but trying to delete the partition and the swamp and try to re-install. Off course I will be unable to have the option of accessing Windows 2000. ](*,) 

The laptop is an old Sony. with 64 MB RAM, 12 GB HDD, trying to install Ubuntu on 4 GB.

Thank you very much in advace for your help. :([/QUOTE]

---

