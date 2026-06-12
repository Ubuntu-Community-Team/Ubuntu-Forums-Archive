---
title: "Root password unknown, at the worst timing possible..."
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by redkover on 2006-11-17
I recently changed my root password in Ubuntu,(my brother was messing around with some things). Later, when I rebooted, I have totally forgotten my root password, and during start up, it gave the 'Has not checked hdb1 after 30 bootups, check forced.' message. It failed, and it asked for root password. I was frustrated, typing every password I know, but nothing came up. I tried safe mode, but it didn't work.  I'd like to know if there is any way I can get back, without cracking, and reinstalling(It will take ages to get it back)... I looked all over Google, but everything I see requires you to log in, or go in safe mode. Thanks in advance!

---

### Post by 23meg on 2006-11-17
Are you sure it was your root password, and not user password that you changed? To change the root password, you need to have enabled logging in with the root account and set up a root password in the first place, because it's disabled by default. Did you do that? How exactly does recovery mode fail?

---

### Post by redkover on 2006-11-17
Well, I did 'sudo passwd' and it accepted that. And, recovery mode failed because of the 'Check forced' message. So long story short, I need to get my root password without logging into Ubuntu, or Ubuntu Recovery Mode.

---

### Post by bodhi.zazen on 2006-11-17
```
sudo passwd
```

Enter your log-in password, change root.

---

### Post by chriscando on 2006-11-17
Right, if you have sudo privilages you can switch to root without the password
```
sudo su
```

---

### Post by dmizer on 2006-11-17
if the check force fixed problems ... what problems did it find?  didn't happen to be in /etc/pam.d did it?  if so, you might want to take a look at this thread for how i solved the same problem: [http://www.ubuntuforums.org/showthread.php?t=296129](http://www.ubuntuforums.org/showthread.php?t=296129)

---

### Post by yota on 2006-11-17
In a worst case scenario you can:
[LIST]
[*]Boot from live cd and repair your root fs (sudo fsck -fp /dev/*rootFsPartition*)
[*]Mount your root fs
[*]chroot into it
[*]change root pwd in the chrooted env
[/LIST]

Probably just the first step will enable you to boot your real system again and change the root password from there.

Hope this helps.

---

### Post by anaconda on 2006-11-17
You can also boot with liveCD and edit the file 
/etc/shadow

Just delete the encrypted password and you wont need password after that. Just remember to set a new password next time you log in..

More info of shadow -file:
[http://db.assam-glug.org/documentations/Linux-admin-made-easy/shadow-file-formats.html](http://db.assam-glug.org/documentations/Linux-admin-made-easy/shadow-file-formats.html)

---

### Post by bodhi.zazen on 2006-11-17
> **anaconda said:**
> [http://db.assam-glug.org/documentations/Linux-admin-made-easy/shadow-file-formats.html](http://db.assam-glug.org/documentations/Linux-admin-made-easy/shadow-file-formats.html)

Nice link. Thank you.

---

