---
title: "umount problem"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by bks on 2007-03-06
I have had some trouble unmounting my fd0.  I use 'pmount /dev/fd0' and it successfully mounts to '/media/fd0'.  However, when I wish to write the files and remove the disk I type 'umount /dev/fd0' and it returns an error saying I'm not root.  So I type 'su' and my password, but it keeps saying 'Authentication Failed'. I know it is the right password and I type it carefully, but I cannot successfully unmount the drive via the terminal.

---

### Post by mikewhatever on 2007-03-06
Just a guess, but try sudo unmount /dev/fd0

---

### Post by dstew on 2007-03-06
I believe the correct command would umount /media/fd0, and not umount /dev/fd0. See the umount man page.

---

### Post by bks on 2007-03-06
What is 'sudo' for?

---

### Post by bks on 2007-03-06
> **dstew said:**
> I believe the correct command would umount /media/fd0, and not umount /dev/fd0. See the umount man page.

I think I tried that, but I will try it again, thanks.

---

### Post by bks on 2007-03-06
> **mikewhatever said:**
> Just a guess, but try sudo unmount /dev/fd0

Thanks it worked perfect!

---

### Post by maniacmusician on 2007-03-06
> **bks said:**
> What is 'sudo' for?
sudo gives administrative rights to a command. It's saying "hey, run this following command as an administrator!"

For graphical applications in Gnome, you should use "gksudo" instead of "sudo", and if you're using KDE, you should use "kdesu" for graphical applications.

---

