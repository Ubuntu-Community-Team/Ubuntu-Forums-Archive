---
title: "unable to load grub"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by sathya on 2005-12-31
I had Windows XP on my system . I used a Ubuntu install CD and through expert mode tried installing ubuntu, i tried installing ubuntu on the same hard disk . I created three partitions 1. sawp: 2 GB 2. Root 15 GB and 3. Home 3 gb. When I tried to load grub loader it is failing. Now I am nither able to load windows Xp nor Ubuntu.

I quit the ubuntu installation. Again tried the same thing but unable to load grub what should I do ?

---

### Post by piedamaro on 2005-12-31
I created three partitions 1. sawp: 2 GB 2. Root 15 GB and 3. Home 3 gb.
And the one for xp? Xp always want to stay on the first partition to boot properly (note that it may not be the first physical partition on disk, but it has to be te 1st like hda1)

Consider that programs will go in the / (root) dir and personal data in /home. Given that I think your home dir is a bit small.
Also I never seen 2 GB of swap filled up,but it's personal taste.

Grub is failing during he installation or at 1st boot?

---

### Post by sathya on 2005-12-31
thanxs
I tried again and succeeded . Ubuntu loaded. But the boot menu doesn't have XP now.

also there are three options.
1.Ubuntu
2.ubuntu(ecovery mode)
3.ubuntu kernel 

how to edit GRUB ?

---

### Post by vasudevank on 2005-12-31
you would want to login as root (this is just a guess) and type nano -w /boot/grub/grub.conf now you should be able to edit the file and just add windows xp 

title     Windows XP (or what ever version you have)
rootnoverify (hd0, the number of windows partition is on -1 (so if /dev/hda2 it would look like (hd0,1))
savedefault
makeactive
chainloader +1

(this should be at the end of the grub.conf, where it says Other OS's)

Hope this helps

---

### Post by sathya on 2006-01-01
At the terminal : When i write root it says
                        bad command.
when i type sudo
sathya@ubuntu:~$ sudo
sudo: unable to lookup ubuntu via gethostbyname()
postdrop: warning: unable to look up public/pickup: No such file or directory
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
sathya@ubuntu:~$ sudo -p
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
what should i do ?

---

### Post by steve.horsley on 2006-01-01
The sudo commadn should be followed by the command you want to execute. If you want to edit the grub menu file:
```
sudo nano /boot/grub/menu.lst
```
If your GUI is working, you may prefer gedit to nano as an editor.

---

