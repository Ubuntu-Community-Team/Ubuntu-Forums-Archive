---
title: "Drives and Folders"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-03
Hi all
I have two Q re folders and drives.

Based on info fro this forum, I went with a dual drive install for Ubuntu - which worked perfectly.

Qustion 1
When I boot to Ubuntu I can see the Windows NTFS drive, labeled as "228.1GB Volume", but when I try to open it, I get an error
"Unable to mount the selected volume."

Is there any way to be able to see the contents of this drive? - That will make migration of my files a lot easier


Question 2
I will be setting up 3 other Linux users - all of whom are non-tech (my family) and I want to replicate the concept of "Shared Documents" in the other OS - Thats where we keep music files, family photo's etc.

What would be the best way to acieve this?
My current plan would be a new folder /home/shared and then somehow add a link to that folder in everyones home folder - is this the best way and if so - how would I create that link?


Mods - if these needs to be 2 seperate treads - let me know and I will split it.


Thanks

---

### Post by taurus on 2006-12-03
1.  Read this...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

2.  Create a /home/share and change the permission so everyone can read and write to it...

```
sudo chmod -R 777 /home/share
ln -s /home/share  ~/share
```

---

### Post by dkenny on 2006-12-03
Taurus
Thanks for the both of those - they both worked perfectly.

---

### Post by taurus on 2006-12-03
> **dkenny said:**
> Taurus
Thanks for the both of those - they both worked perfectly.
You're welcome.

---

### Post by CatKiller on 2006-12-03
If you haven't yet created those users, putting a link in /etc/skel will make it automagically appear in the home folder of each of the new users. Like so, I think:

```
sudo ln -s /home/share /etc/skel/share
```

(Because you can't write outside of your Home folder by default, you need to use sudo to write in /etc. It will ask for a password - this is the password you logged in with.)

---

