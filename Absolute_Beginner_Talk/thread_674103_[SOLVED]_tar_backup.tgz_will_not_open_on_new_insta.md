---
title: "[SOLVED] tar backup.tgz will not open on new install"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2008-01-21
I was going to do something risky with my HD and made a tar backup of my system first. I have used this method of backup before and it has restored properly, so I felt safe.

My experiment with windows did not word out so I decided to reinstall 7.10 and let it use the entire drive. The install is fine and boots OK but the restore command will not open the file:
```
peter@ubuntu_7_10:~$ sudo su
root@ubuntu_7_10:/home/peter# cd /
root@ubuntu_7_10:/# tar xvpzf backup.tgz -C /
tar: backup.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@ubuntu_7_10:/# 

```Can someone pleas help me out.

The backup process I used[ is here]("http://http://ubuntuforums.org/showthread.php?t=35087&highlight=tar+backup")

---

### Post by stump138 on 2008-01-21
did you bring the file over from the dvd or cd you saved it to?

---

### Post by bodhi.zazen on 2008-01-21
first, it looks like the backup.tgz is not in /

second I would do that from a live cd, mount your ubuntu root in say /media/ubuntu, and extract the tar to /media/ubuntu rather then /

---

### Post by kindafunnylookin on 2008-01-21
> **stump138 said:**
> did you bring the file over from the dvd or cd you saved it to?
Yes I brought it over and it is in /var where it belongs. I also have a copy of it in /root.

---

### Post by kindafunnylookin on 2008-01-21
> **bodhi.zazen said:**
> first, it looks like the backup.tgz is not in /

second I would do that from a live cd, mount your ubuntu root in say /media/ubuntu, and extract the tar to /media/ubuntu rather then /

It is in both / and /var where it is normally stored. Is it OK to use a live 7.04 cd to do this ???

---

### Post by oodledoodle on 2008-01-21
are you sure you didn't type it incorrectly? it's ".tar.gz" normally.

---

### Post by kindafunnylookin on 2008-01-21
> **oodledoodle said:**
> are you sure you didn't type it incorrectly? it's ".tar.gz" normally.
No, for this project the code is correct but thanks for the reply

---

### Post by bodhi.zazen on 2008-01-21
Try ./backup.tgz

---

### Post by kindafunnylookin on 2008-01-21
> **bodhi.zazen said:**
> Try ./backup.tgz
[COLOR=Red]Progress,  [COLOR=Black]something different has turned up.
[/COLOR][/COLOR]```
peter@ubuntu_7_10:~$ ./backup.tgz
bash: ./backup.tgz: No such file or directory
peter@ubuntu_7_10:~$ sudo su
[sudo] password for peter:
root@ubuntu_7_10:/home/peter# cd
root@ubuntu_7_10:~# ./backup.tgz
bash: ./backup.tgz: File too large
root@ubuntu_7_10:~# /backup.tgz
bash: /backup.tgz: No such file or directory
root@ubuntu_7_10:~# 
```

---

### Post by mcduck on 2008-01-21
Try running these commands to find if the file even exists (and where it is):

```
sudo updatedb
locate backup.tgz
```

---

### Post by kindafunnylookin on 2008-01-21
[quote=mcduck;4180592]Try running these commands to find if the file even exists (and where it is):

I ran that code and got:
```

peter@ubuntu_7_10:~$ sudo updatedb
[sudo] password for peter:
peter@ubuntu_7_10:~$ locate backup.tgz
peter@ubuntu_7_10:~$ sudo locate backup.tgz
peter@ubuntu_7_10:~$ 
```

That is pretty discouraging as I can see the file in both / and /var I have even experimented with changing the permissions. I'm stumped here in stumptown.

---

