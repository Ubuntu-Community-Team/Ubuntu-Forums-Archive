---
title: "Help installing program in (Kubuntu)"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Otto-C on 2007-02-08
I downloaded the snapshot of 'program-version' to the /tmp directory
and did a tar xzvf /tmp/program-version.tar.gz. The program tar worked
correctly.

I followed further install instruction and cd' to the 'program' directory
and began the install instructions. I was interupted and had to quit.

The next day upon resuming I did a: 
cd program and got the message:
bash: cd: program: No such file or directory.

I tried to do a locate, find, whereis etc and the directory is gone.

I then tried to do: 
$ tar xzvf /tmp/program-version.tar.gz
tar: /tmp/program-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
$

How to recover from from this problem.

tia
otto-c

---

### Post by Brunellus on 2007-02-08
1) what package are you trying to install, and why?

For general installation help, see

[http://help.ubuntu.com/community/InstallingSoftware](http://help.ubuntu.com/community/InstallingSoftware)

---

### Post by nereid on 2007-02-08
The whole problem is that you tried to do everything in the /tmp folder. This is just a temporary folder and all content will be deleted on reboot. So, get your application archive again and instead on extracting it into the /tmp folder use a folder in your home directory, for example ~/sandbox or something like that.

---

