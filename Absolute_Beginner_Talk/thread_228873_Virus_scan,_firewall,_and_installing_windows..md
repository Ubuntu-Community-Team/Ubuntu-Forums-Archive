---
title: "Virus scan, firewall, and installing windows."
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by lifesalongsong on 2006-08-03
Hey, I was just wondering if it is smart to install a firewall and virus scan on Ubuntu. If so which one would you reccomend (freeware plz). Also how do I install Windows after I have installed Ubuntu. Ubuntu is already installed on my laptop, and i was sure to leave a 15g partition for windows, I just dont know if the windows install will mess up GRUB and if so how would I fix it. Thanks in advance.

---

### Post by neilp85 on 2006-08-03
Firewall, yes, iptables is the linux firewall but isn't the easiest thing to learn. Virus scanner, no, linux is a secure operating system.

---

### Post by az on 2006-08-03
> **lifesalongsong said:**
> Hey, I was just wondering if it is smart to install a firewall and virus scan on Ubuntu. If so which one would you reccomend (freeware plz). Also how do I install Windows after I have installed Ubuntu. Ubuntu is already installed on my laptop, and i was sure to leave a 15g partition for windows, I just dont know if the windows install will mess up GRUB and if so how would I fix it. Thanks in advance.

Freeware?

Freeware is still proprietary.  Ubuntu is free-libre open source.

Anyway, you don't need any of that.  Just keep up-to-date with security updates.

---

### Post by user1397 on 2006-08-03
To my knowledge, it is always better to install ubuntu *after* you've installed windows.  I think there's a way to do it, but it would be really easy just to delete ubuntu, install windows, and then install ubuntu.  (remember to back up anything important)

---

### Post by deadgobby on 2006-08-03
Yes, you will need to install windoz first. Windows does not like to share with other o/s. I feel windoz does not play nice with other distros. 
Enjoy

---

### Post by ewl1217 on 2006-08-03
If you want to install a GUI frontend to Ubuntu's firewall, iptables, (I know it isn't really needed, but if you're like me, you'll want one just to have a little more control over your system.) then try Firestarter for Ubuntu or Guard Dog for Kubuntu. Both work well and give you an easier way to control the firewall.

---

### Post by lifesalongsong on 2006-08-03
Thanks alot for the info, firestarter is awesome!!:D

---

### Post by confused57 on 2006-08-03
Here's a thread with someone who has had success installing Windows after Ubuntu:

[http://www.ubuntuforums.org/showthread.php?t=225583&page=2](http://www.ubuntuforums.org/showthread.php?t=225583&page=2)

---

### Post by anaconda on 2006-08-03
Installing windows after linux Windows ALWAYS owerwrites your grub, so know how to restore your grub, and add windows to your grub (menu.lst -file)

And I have heard a rumour, that some new wersion of windows will write something to the beginning of the first partition if windows is installed to some other partition.. so it would (propably) make the os in 1.st partition unusable..   Dont know if this rumour is true....

---

### Post by anaconda on 2006-08-03
And if you install windows, it might be a good idea to install virus scanner to your linux, so  that you could scan your windows drive... :D

---

