---
title: "Forgot Username &amp; Password"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-08-13
Hi
 I have been on vacation for two months and I have forgotten my username and password to login to my Ubuntu Operating system on my computer. I remember something about when you boot up you can do something to stop the boot and bypass the username and password and then enter a new user name and password. However I don't remember the steps to do it.
Thanks for any help on this.
Kent41

---

### Post by MaximB on 2006-08-13
you are lucky
just yesterday somone came up with the same question
search the forum

---

### Post by 5-HT on 2006-08-13
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

To find out your username boot into recovery mode (described under the 'standard way' in that wiki page) and have a look at the directories in /home. There should be one named for your user.

To reset the password:```
 passwd your_username 
```

---

### Post by skale on 2006-08-13
insert the CD, get to a shell as root and do a "useradd -m <name>" and a "passwd <name>" to make a new account. 

Or, on the liveCD mount your drive and find the /etc/passwd file, and look for your old user near the bottom. then do the "passwd <user>" as root.

---

### Post by kent41 on 2006-08-13
Thanks I'll give it a try. I have to change disk drives and re--boot

---

### Post by MaximB on 2006-08-13
damn...I thought It should be harder then that...
any one can do it without any discs and nothing...
it drives my back to the linux security isue.
(yeah I know that any OS could be hacked if you have access to the computer - but I thought it was harder then that).

---

