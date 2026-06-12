---
title: "Strange Error Message at bootup"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Frank Golden on 2006-05-29
Hi All,
    I am all of a sudden getting a strange message at boot up right before the desktop below is a word for word copy of message.

users $HOME/.dmrc file is being ignored. This prevents the default session and
language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable
by other users.

What in the name of God is this all about, Where is the $HOME/.dmrc file located 
and how can I fix it?

It doesn't appear to cause any harm but I have to click ok on message to continue
boot. This is on a new install of Dapper Drake the latest RC.

Please help!

---

### Post by cskeide on 2006-05-29
Check if your home directory, and the .dmrc file are owned by your user:
```
ls -al /home
ls -al ~/.dmrc
```
For example, on my computer, the output of these commands are as follows:```
drwxr-xr-x 61 cskeide cskeide  4096 2006-05-29 18:27 cskeide
-rw------- 1 cskeide cskeide 26 2006-04-16 13:11 /home/cskeide/.dmrc
```
You can see that my home directory as well as the .dmrc file are owned by my user.

If this is not the case for you, try the following commands (replace cskeide with your username):
```
sudo chown cskeide:cskeide ~
sudo chown cskeide:cskeide ~/.dmrc
sudo chmod 644 ~/.dmrc
```

Hope this solves your problem

---

### Post by Frank Golden on 2006-05-29
Hi cskeide,
    Well I tried your code, that and manually changing the group of my /home and
/home/frankgolden directories to frankgolden seems to have fixed the problem.
Don't know how or why this happened or anything about what I just did to fix it. Thanks. Below is output of ls -al /home etc commands.


frankgolden@frankgolden-laptop:~$ ls -al /home
total 12
drwxr-xr-x  3 frankgolden frankgolden 4096 2006-05-28 20:18 .
drwxr-xr-x 22 root        root        4096 2006-05-28 22:30 ..
drwxr-xr-- 34 frankgolden frankgolden 4096 2006-05-29 06:43 frankgolden
frankgolden@frankgolden-laptop:~$ ls -al ~/.dmrc
-rw-r--r-- 1 frankgolden frankgolden 26 2006-05-28 20:24 /home/frankgolden/.dmrc
frankgolden@frankgolden-laptop:~$

Again I don't have a clue what I'm looking at but the problem seems to be fixed.
Again Thanks.

---

### Post by cskeide on 2006-05-29
You're welcome. I had the same problem a few weeks ago. I never really understood why it happened either...

---

