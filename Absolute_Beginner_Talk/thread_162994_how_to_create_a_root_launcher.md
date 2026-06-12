---
title: "how to create a root launcher"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by lreyes6 on 2006-04-20
hello I need to create a launcher for certain application (beep media player for example) but i need to run it as root.. why? because i want to access my mp3 collection on a ntfs partition (i dual boot) and with my regular user that's not possible...

any idea? :confused: 

thanks

---

### Post by trent dillman on 2006-04-20
Well, you could prefix the command with 'gksudo'...

...but you should just mount your ntfs drive as readable for users (or just your user) instead of running programs as root.

---

### Post by OffHand on 2006-04-20
Follow this guide and you will not have to use BMP as a root.

[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by aysiu on 2006-04-20
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If your Windows partition is mounted properly, it will be read-only, and you won't need root to access it.

---

### Post by OffHand on 2006-04-20
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If your Windows partition is mounted properly, it will be read-only, and you won't need root to access it.[/QUOTE]
Are you bean grinding?

---

### Post by aysiu on 2006-04-20
[QUOTE=subsonic_shadow]Are you bean grinding?[/QUOTE] No. I don't really think the EasyLinux instructions are comprehensive enough.

First of all, they assume that /dev/hda1 is the NTFS partition, which it probably is but may not be.

They also assume you're using Gnome, and the *Gedit* command will not work in KDE. In Absolute Beginner, I never assume people are using Gnome.

Finally, they create the mount point in /media, and I've seen several threads where people have had issues with mounting Windows partitions within the /media folder, even if they have the correct parameters in the /etc/fstab.

**Edit**: And one more thing--the instructions ask you to *append* the line. Well, what if the line already exists (in most Breezy installations, it will)? Then, you have two /etc/fstab lines referring to the same /dev location.

P.S. Look at how many beans I have--do you really think I need to grind any more? I actually asked the admin to reset my bean count. Last I heard, they were working on it.

---

### Post by OffHand on 2006-04-20
[QUOTE=aysiu]No. I don't really think the EasyLinux instructions are comprehensive enough.

First of all, they assume that /dev/hda1 is the NTFS partition, which it probably is but may not be.

They also assume you're using Gnome, and the *Gedit* command will not work in KDE. In Absolute Beginner, I never assume people are using Gnome.

Finally, they create the mount point in /media, and I've seen several threads where people have had issues with mounting Windows partitions within the /media folder, even if they have the correct parameters in the /etc/fstab.

P.S. Look at how many beans I have--do you really think I need to grind any more? I actually asked the admin to reset my bean count. Last I heard, they were working on it.[/QUOTE]Fair enough, I apologize.

---

### Post by this213 on 2008-04-11
Funny, nobody responded to the OPs question with a real answer (other than mounting the drive differently) in 2 years.

I came across this because I needed it for Etherape under Fedora. This is what I finally ended up doing (all I did was copy pirut):

as root (or sudo everything since you guys don't believe in the all powerful root)
```
mv /usr/bin/etherape /usr/sbin/etherape

ln -s consolehelper /usr/bin/etherape

cp /etc/pam.d/pirut /etc/pam.d/etherape

sed s/pirut/etherape/ /etc/security/console.apps/pirut > /etc/security/console.apps/etherape
```

Note that this is all under Fedora. Ubuntu likes to deviate from every other distro out there, so the location of your console.apps/ or pam.d/ may differ.

Hopefully now the next person looking to do this won't have to bother with NTFS mount tutorials ;)

---

