---
title: "Stellarium"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by gary0 on 2007-02-27
I have Stellariun installed, but suddenly it won't run from a user account, the screen goes black and there is just a cross cursor. It does however work perfectly when logged on as root.  A similar thing happened with gPredict (satellite tracking), but that wouldn't work at all. I have tried removing said apps from Synaptics, and reinstalling, but they still won't work. Any ideas people?

Gary.

---

### Post by Richard Kut on 2007-02-27
Hello gary0! This is probably a file permission problem on one of the dependent files. Translation: I believe that one of the files may be owned by root when it shouldn't be.

Have a look at the files in question using ls -l to see the ownership and permissions. Try changing files owned by root to be owned by your account. Forexample:

> sudo chown you:you filename


Substitute "you" with your login name. Please update the post with your feedback. Good luck!

---

### Post by gary0 on 2007-02-28
Yep, the executable is owned by root. I am going to change that now, will post update when done. 
Thanks for your help.
Gary

---

### Post by gary0 on 2007-02-28
No, it didn't work so I've just uninstalled it. Can't be bothered to faff around as I'm a very busy man! Got a deadline to meet monday to deliver some software I've written. Will try again after that.

Many thanks for you help.

Gary.

---

### Post by xadder on 2007-03-12
I installed yesterday on edgy (xubuntu base, install with aptitude). Worked great for a few minutes. Then froze completely! I couldn't do anything :-(    

I tried CTRL-ALT-F2, etc.,  to let me close things down, but nothing worked. Had to close down the hard way....

Does anyone have this working? For the few minutes I used this I was really impressed.

---

