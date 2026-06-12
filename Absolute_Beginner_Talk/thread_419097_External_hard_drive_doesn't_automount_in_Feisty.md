---
title: "External hard drive doesn't automount in Feisty"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2007-04-22
Hi guys, I upgraded to feisty and my external hard drive is not auto-mounting anymore.  Does anyone know a fix for this?

---

### Post by mabelrxu on 2007-04-22
what kind of hard drive is it? usb? i'm actually just stalling for time while I try to think up some ideas ... ;) ... :-k

---

### Post by mhansen on 2007-04-23
You're gonna have to edit /etc/fstab.  I just replied to another thread on here somewhere today regarding the same question.  I'd retype it, but frankly I'm exhausted and I know I'd make a mistake.  This link should help: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)  If not, I'll be back in the morning.  Oh, the only thing that article is missing is discussion about UUIDs.  You'll have to google that too....



Regards,
Mike

---

### Post by familyjules74123 on 2007-04-23
> **mabelrxu said:**
> what kind of hard drive is it? usb? i'm actually just stalling for time while I try to think up some ideas ... ;) ... :-k

It is a usb hard drive.  It only automounts if it is plugged in when the computer is started.  If it is plugged in after ubuntu is up and running then it does not detect it.

> You're gonna have to edit /etc/fstab. I just replied to another thread on here somewhere today regarding the same question. I'd retype it, but frankly I'm exhausted and I know I'd make a mistake. This link should help: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) If not, I'll be back in the morning. Oh, the only thing that article is missing is discussion about UUIDs. You'll have to google that too....

Is this a direct feisty fix, or is it a general fix for this?  I am just wondering.  I will try it later on when I am home (in class now).

---

### Post by Hashi on 2007-04-23
Hi,
  I've posted a couple of times about this (won't automount USB drives, iPod etc). What I found, and this is weird, is that when I switched from KDE to GNOME, everything works just fine. My install was originally feisty Kubuntu obviously. I installed gnome-desktop as a last resort, booted into it, and voila! everything works, including my previously not working wireless. Booting back into KDE, the original problems came back. This is a shame, as I much prefer KDE. Hope this helps someone.
Hashi.

---

### Post by sajnikanth on 2007-06-09
To Mount External Drive Manually

1.Connect The drive
2.Make sure it has not been mounted
3.From command line – type pmount /dev/sdb1 (Assuming sdb1 is your drive)
4.To automate this process,  Create or Open .bash_profile in /home/<yourlogin>
5.Add  pmount /dev/sdb1 to the file and save it
6.Next time you restart, the drive (if connected) would be mounted automatically

I am not sure if this is the best method but it has worked for me. Good luck.

Sajnikanth

---

### Post by familyjules74123 on 2007-09-25
> **sajnikanth said:**
> To Mount External Drive Manually

1.Connect The drive
2.Make sure it has not been mounted
3.From command line &#8211; type pmount /dev/sdb1 (Assuming sdb1 is your drive)
4.To automate this process,  Create or Open .bash_profile in /home/<yourlogin>
5.Add  pmount /dev/sdb1 to the file and save it
6.Next time you restart, the drive (if connected) would be mounted automatically

I am not sure if this is the best method but it has worked for me. Good luck.

Sajnikanth

This worked to mount the drive, however the ntfs configuration tool doesnt work still, so I'm not permitted to write to the HD anymore.

---

### Post by sajnikanth on 2008-01-15
This has been fixed on Gusty Gibbon. Open dolphin and uncheck "mount as user" in the disk properties.

---

