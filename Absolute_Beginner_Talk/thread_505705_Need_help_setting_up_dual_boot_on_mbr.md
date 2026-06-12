---
title: "Need help setting up dual boot on mbr"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by DogsOfWar on 2007-07-20
I'm trying to set up a dual boot of XP home and ubuntu, each on its own HD.  For some reason, installing GRUB damages my XP installation and I have to reinstall windows to fix it (I'm on my second reinstall, in fact).  I've been trying to set up lilo on my ubuntu installation so I can add it to the windows boot menu, but I've run into problems:

- liloconfig said that my root partition doesn't look right, and that I need to either fix my fstab or write my own lilo.config file.
- I wasn't sure how to fix fstab (or even what needed fixing), so I tried to make my own lilo.config file based on the sample file lilo provides.
- When I tried to put the new lilo.config file in /etc, I got "permission denied".
- When I tried to give myself write permission for /etc, I wasn't able to because "root" was the owner.

At that point, I ran out of ideas.  Anyone want to take a stab at some of these? ;) Any help would be greatly appreciated.

- D.O.W.

---

### Post by Rocket2DMn on 2007-07-20
When you edit system files you need to have superuser privileges, so you need to precede your commands with "sudo" then enter your password when prompted.  Then and only then can you edit such files.
ex:```
sudo gedit filename
```

It works best if you install XP first, then do Ubuntu, here is a nice little guide
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Good luck!

PS: Since Windows XP/Vista uses NTFS (which you should use rather than FAT32), you will need to get ntfs-3g to read/write the Windows drive from Ubuntu - there is documentation to help you with this.  You can also read/write the Ubuntu partition from Windows using an addon driver for Windows - [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by DogsOfWar on 2007-07-20
Yes! I finally got it to dual boot!

Thanks for your help :)

- D.O.W.

---

