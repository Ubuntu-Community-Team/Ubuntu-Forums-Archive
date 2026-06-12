---
title: "HOME/ being ignored"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by rafkin on 2008-01-20
Whenever I log into my Ubuntu, after my login and password I get a error message that reads: $HOME/.dmrc being file being ignored. HOME directory must be owned by user & not writable by other users. This never happened until I did an update that needed a restart.

---

### Post by gsiliceo on 2008-01-20
sudo chown *******YOURUSERNAME******* /home

---

### Post by rafkin on 2008-01-20
appreciate the reply but I think I might be doing something wrong.

greg@greglinux:~$ sudo chown greg/home
chown: missing operand after `greg/home'
Try `chown --help' for more information.

---

### Post by rafkin on 2008-01-20
doesn't seem to work, unless I am doing something wrong.

---

### Post by steveneddy on 2008-01-20
From[ this thread]("http://ubuntuforums.org/showthread.php?t=371052&highlight=%24HOME%2F.dmrc"):

```

sudo chmod 644 /home/**your_login**/.dmrc
sudo chown** your_login** /home/**your_login**/.dmrc
sudo chmod -R 700 /home/**your_login**
sudo chown -R **your_login** /home/**your_login**

```

Of course, changing every instance of  **your_login** with your own login name.

Good luck.

:popcorn:

---

### Post by rafkin on 2008-01-20
Once again the forum has saved me from a migraine headache. Used your fix and everything is working fine now. Not sure where I would be without this forum, probably just another windows user beating his head against his monitor.   LOl  thanks again

---

