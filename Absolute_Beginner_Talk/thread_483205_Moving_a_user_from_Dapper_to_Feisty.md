---
title: "Moving a user from Dapper to Feisty"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by nick_h on 2007-06-24
I have been using Dapper for some time now.  I have also been evaluating Feisty which I have installed in a separate partition.

What I would like to do now is copy user settings from Dapper to Feisty.

I created a new user in Feisty, and then logged on as the new user in Feisty typed:
```
cd /media/sda3/home/olduser
cp -r . ~
```
Is there a better way to do this?

Now in the new account I can't run Firefox or Thunderbird because the system thinks they are already running. (I would like to import the settings for these)

The Firefox and Help icon in the toolbar now show as a red cross.

Any advice would be appreciated.

Update:  I've found a thread on archiving - i'll try using tar

---

### Post by Bothered on 2007-06-24
The "Firefox/Thunderbird is already running" message tends to pop up if the profile isn't being read correctly. i.e. the data may not have been copied correctly.

Have you tried "sudo nautilus" and copying the files across using that?

---

### Post by nick_h on 2007-06-25
Thanks.  The data probably didn't copy correctly.

I got it working but taring the directory.  The user id was different between the two accounts so I fixed that with a chmod -R.

From what I was reading about archiving, tar will not handle hard links.  Should I expect any problems?  How can a determine if my home directory contains any hard links?

---

