---
title: "Can't Write on Any Directories - Access denied"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by pcbianchijr on 2008-01-19
I'm having trouble writing to my linux partition. It seems like I can't write to any other directories, other than the desktop. It's in ext3 format. Access denied, but I'm logged in as an administrator.

---

### Post by Dr Small on 2008-01-19
Your user account can not write to other directories without root, or usage of sudo, because they are owned by root.

If your user account is an administrator, then you should be able to write to it, with the usage of sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Dr Small

---

### Post by Twizzle on 2008-01-19
I had a similar problem at first. It was because of the permissions of the folders. I think, other than your user folder (including desktop), they all belong to root. You need to change the permission to allow you to write to them.

I used 'gksudo nautilus', then went to the folder I wanted to be able to write to, right click and choose options and then set the permissions.

By the way, I think Ubunu is set so you can't be logged in as an administrator (root) - you need to tell it when you want to run something as root.

---

### Post by Dr Small on 2008-01-19
> **Twizzle said:**
> I had a similar problem at first. It was because of the permissions of the folders. I think, other than your user folder (including desktop), they all belong to root. You need to change the permission to allow you to write to them.

I used 'gksudo nautilus', then went to the folder I wanted to be able to write to, right click and choose options and then set the permissions.

By the way, I think Ubunu is set so you can't be logged in as an administrator (root) - you need to tell it when you want to run something as root.
Don't change permissions on the folders!
They are setup like that for a reason, and not writeable by regular user (without sudo) for your protection and security.

Dr Small

---

### Post by pcbianchijr on 2008-01-19
Hmm, I see... I'm treating my linux as it was windows... I have a lot of reaqding to so...
thanks guys

---

### Post by Michl on 2008-01-19
Sure, you can change permissions.  Just be careful where you change
permissions.

---

### Post by fatality_uk on 2008-01-19
I would suggest NOT changing permissions without a very good reason. As the good Dr. above said, the Linux file system is designed to actively prevent usage in certain folders without having root priv.

What are you trying to write there and why? There may be another way to do this without needing to change permissions.

---

### Post by pcbianchijr on 2008-01-19
I ham trying to copy the flash 9 .so to the firefox folder, and changing menu.lst for booting windows first, as I'm the only user of this pc who will use linux... But it can't save any changes on the file, neither copy the .so to the firefox plugins folder.

---

### Post by mcduck on 2008-01-19
> **Michl said:**
> Sure, you can change permissions.  Just be careful where you change
permissions.

Changing permissions of system directories/files is not smart because of security reasons, and in case of some files can also break your system into unbootable state.

If you need to work with system directories you should always just leave the permissions the way they are  and use 'sudo'. Or, if you want a GUI way, just run 'gksudo nautilus' to open the file manager as root user.

---

### Post by fatality_uk on 2008-01-19
> **pcbianchijr said:**
> I ham trying to copy the flash 9 .so to the firefox folder, and changing menu.lst for booting windows first, as I'm the only user of this pc who will use linux... But it can't save any changes on the file, neither copy the .so to the firefox plugins folder.

Ok. If you want to change GRUB to ensure that Windows boots first, try this:
In a terminal type:
```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
This backs up your copy of GRUB. If anything goes wrong

Now enter GRUB like this:
```
sudo gedit /boot/grub/menu.lst
```

In GRUB you will se a line at about line 14
```
default		0
```

This is the default OS that grub will boot into

The entries in GRUB start at 0. So if the first two entries are Ubuntu and the third entry is for Windows.., you need to change this value from 0 to 2

Now just file->save and that should change your default OS to Windows.

Now why are you trying to copy that folder?

---

### Post by Christmas on 2008-01-19
Write all what you need in your home directory, that is /home/your_user. Don't change permissions for other directories like /bin, /usr etc. They are used to keep the software which you install via 'sudo' command, documentation, configuration files. Keep all your personal files in /home/your_user or create a separate partition and mount it somewhere and put your files there. For example i have /floyda and /floydb, two partitions in which I keep my data. Since a normal user cannot write to directories like /bin /usr etc, this is more secure so if you run the wrong script or command as user you can't mess the system, only the files you have access to.

---

### Post by oldos2er on 2008-01-19
> **pcbianchijr said:**
> I ham trying to copy the flash 9 .so to the firefox folder, and changing menu.lst for booting windows first, as I'm the only user of this pc who will use linux... But it can't save any changes on the file, neither copy the .so to the firefox plugins folder.

 "sudo cp /old/file/ /new/file/" will allow you to copy your Firefox plugins.

 To run a graphical program like gedit with su privileges, run "gksudo gedit /boot/grub/menu.lst"

 You might want to go to [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) and read the sections on file permissions and security on Ubuntu.

---

### Post by The Cog on 2008-01-19
It's also worth remembering **gksudo nautilus** to launch a file manager with full root rights.

---

