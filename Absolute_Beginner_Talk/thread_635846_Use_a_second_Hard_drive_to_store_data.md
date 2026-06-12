---
title: "Use a second Hard drive to store data"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by 2much4u on 2007-12-09
Hello!

I'w a newbie with Ubuntu but I love it, I need to use a second hard drive to store downloads :).

I've connected the drive, I've made the partitons with Gparted and everything goes well but...

1) How can I point, if possible, my /home/$user/Downloads folder to this new drive?
2) How can I mount this drive automatically at system startup?
3) How can I rename this drive?

Thanks in advance!

---

### Post by Ub1476 on 2007-12-09
1) Check out sbackup, it's in the repos I think. After it's installed go to System>Administration>Simple backup config, and change the folders to backup and where to backup, how often to backup and so on..

2) My drive get mounted automatically (shows an icon on Desktop), doesn't yours?

3) I'm not sure what you mean, doesn't it work to right click and rename?

---

### Post by 2much4u on 2007-12-09
1) What I mean is that how can I tell to Ubuntu that /home/$user/Downloads it's my new hard drive.
2) No it doesn't just after I mount it manually
3) No, it doesn't work.

---

### Post by HereInOz on 2007-12-09
Here is a good article on the use of fstab to mount your drives:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Also check out this:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

to see how to make a /home partition on the drive.

Hope this helps

---

### Post by insane_alien on 2007-12-09
you'll need to add a line to fstab to mount it on boot. are you sure you wouldn't rather put it in a non user part of the directory(/download instead of /home/username/download) so all can do it.

otherwise you will need to put a few lines in fstab to mount it in every user who will use the drive.

or if you are the only user on the computer you can leave it there.

---

### Post by 2much4u on 2007-12-09
Thanks I'll try it

---

