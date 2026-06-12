---
title: "Security, packages and performance in Ubuntu"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Peter Mount on 2006-03-12
Hello

I've heard that Ubuntu doesn't have the same setup with Root and User accounts that you find in other Distros (like Fedora). I've heard that Ubuntu doesn't have a proper Root account. Is this true?

I've read that Ubuntu is not as compatible with Debian packages as it used to be. What's the story with this?

I tried Ubuntu 5.10 on my Pentium 2-350 with 448 mg PC100 SDRAM and 64mg video card and it seemed a bit slower than Fedora Core 4 using KDE or Gnome on the same machine. Is there a way of speeding up Ubuntu 5.10 with either Gnome or KDE (I prefer KDE)?

I'm just asking because Fedora Core 4 with KDE now wont start. It appears the /var file system is now read only and fsck only returns the message:

"Warning: Couldn't open /etc/fstab: no such file or directory"

I've got my Ubuntu 5.10 CD's and I'm desperate to get my Linux hard drive up and running again by tomorrow as I've got a client coming around to see his new web site on my PC's Linux hard drive. I'm using XAMPP with PHP and Apache. 

In short, if I can't find a quick solution to my problem with Fedora Core 4 I'm faced with deciding on whether to re-install Fedora Core 4 or just "hang it" and go with Ubuntu 5.10 (and add in KDE). Given the time involved (my client is coming after lunch tomorrow) and the bandwidth I'll use in updating this is a serious decision. So I really need help with this.

Thanks

---

### Post by bjweeks on 2006-03-12
> I've heard that Ubuntu doesn't have the same setup with Root and User accounts that you find in other Distros (like Fedora). I've heard that Ubuntu doesn't have a proper Root account. Is this true?

Yes, it use sudo instead.

> I've read that Ubuntu is not as compatible with Debian packages as it used to be. What's the story with this?


Ubuntu does not matain binary compatibley with debian.

---

### Post by adie273 on 2006-03-12
Ubuntu makes a lot more use of the 'sudo' command and doesn't setup a root account during installation, nor does it allow root to login at GDM.

However, you can go into any user account and give the root account a new password and edit GDM so root can login if you wish, thereby meaning you have the same setup you'd have with fedora core 4.

Plus any files for Debian i've used on Ubuntu have worked flawlessly. That obviously doesn't mean all software for Debian will work perfectly. But from my own experience i've not encountered any problems at all.

As for the speed issue i'm afraid I couldn't give any form of help, i used to use Fedora Core 4 myself before switching to Ubuntu 5.10 and i haven't noticed any speed issues.

Hope this helps in some form tho,
All the best

Adie

---

### Post by Peter Mount on 2006-03-12
Hello

Well for better or for worse I've changed my linux hard drive from Fedora Core 4 to Ubuntu 5.10.

As for the speed it actually seems just as fast as Fedora Core 4 in Gnome. 

Have fun

---

