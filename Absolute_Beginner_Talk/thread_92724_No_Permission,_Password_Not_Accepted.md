---
title: "No Permission, Password Not Accepted"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Boca on 2005-11-20
Had no problem yesterday viewing folders and files on FAT partitions that XP and Ubuntu shares but today can't view any folders in one and can't access any files in the folders in the other. Here's what I get...........

[B]boca@linubuntu:~$ su
Password:
su: Authentication failure[/B]

[[img=http://img499.imageshack.us/img499/7362/screenshot1jz.th.png]](http://img499.imageshack.us/my.php?image=screenshot1jz.png)

I haven't changed my password so I don't know what's going on.

---

### Post by nsa_767 on 2005-11-20
Hi, this is going to sound strange, but... I have had no success using **su**. Wit su, it rejects my password the whole time, but with sudo it doesn't.

Try and use **sudo** or open a root terminal.

---

### Post by steve.horsley on 2005-11-20
You won't be able to use **su** unless you have a root password configured. Try using **sudo bash** instead if you really want a root command prompt.

As for your disk access problem, can you post the output from the commands **mount** and **cat /etc/fstab**? VFAT doesn't store file permissions, so it's the way that it's mounted that controls access.

---

### Post by Boca on 2005-11-20
Never mind :mad:

I went [here]("http://tinyurl.com/dz6o8") looking for a way to gain permission and didn't read it correctly (used the command that was posted **sudo rm -rf /**) and disintegrated Ubuntu.

2 days work gone apparently :(
Oh well, if I get some more time someday maybe I'll try this again.

Thx anyway!

---

### Post by nsa_767 on 2005-11-20
I'm so sorry about that... I feel guilty now... :-( But **rm** is the remove command, so technically what you did worked. Again, I am so sorry.

---

### Post by Boca on 2005-11-20
[QUOTE=nsa_767]I'm so sorry about that... I feel guilty now... :-( But **rm** is the remove command, so technically what you did worked. Again, I am so sorry.[/QUOTE]

Oh it surely wasn't your fault. Mine for not knowing what I was doing :)

---

