---
title: "Need help - cannot run 'administrative programs'"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by waggotamp on 2006-07-11
I have Ubuntu running on 3 machines - on my laptop, it has been running well, but now I can not start the 'administrative programs' so I'm un able to upgrade, or change any other items that require this feature. Can any one help???

Any help at all would be most welcome

---

### Post by aysiu on 2006-07-11
Can you post the terminal output of these two commands? ```
sudo aptitude update
gksudo gnome-app-install
```

---

### Post by waggotamp on 2006-07-11
No, I'm unable to start the root terminal.

I'm running 6.06lts on a fastlaptop that was running very nicely. 

I'm not sure what happened. If I do the same on the other ubuntu machine it always asks me for a password, however this machines does not.

Maybe this is the problem?

---

### Post by aysiu on 2006-07-11
You don't need a root terminal. Just any terminal would be fine.

---

### Post by waggotamp on 2006-07-11
Ok, sorry - still very much a beginer

Thisis what happened....

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

tony@Tony Wagner:~$ sudo aptitude update
sudo: unable to lookup Tony Wagner via gethostbyname()
tony@Tony Wagner:~$ gksudo gnome-app-install
sudo: unable to lookup Tony Wagner via gethostbyname()

Any ideas???

---

### Post by annda on 2006-07-11
you might try this thread:

[http://ubuntuforums.org/showthread.php?t=188337](http://ubuntuforums.org/showthread.php?t=188337)

hope it helps.

---

### Post by waggotamp on 2006-07-13
I cannot get this working - any other help?

Have I lost the hostname - even though I still log on to Ubuntu the way I always have done.

Lost...

---

