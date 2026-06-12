---
title: "rhythmbox error !"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by medya on 2007-05-06
I cant run it, I run it and it quits the program after 10 seconds , here is the error which I get in the terminal

> shewdiz@shewdiz-pc:~$ rhythmbox
main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory
main.c: WARNING: called SUID root, but not in group 'pulse-rt'.

RhythmDB-ERROR **: file rhythmdb.c: line 2098 (queue_stat_uri): assertion failed: (uri && *uri)
aborting...
Aborted (core dumped)

---

### Post by felicity on 2007-05-06
Have you tried uninstalling / reinstalling it? 

Did you change any settings, add any files, or plug ins right before this occurred?

---

### Post by medya on 2007-05-06
yep I tred it ...

---

### Post by Cappy on 2007-05-06
Try ..
```

usermod -G pulse-rt yourusername

```

---

### Post by medya on 2007-05-06
hey I did that and still I have my problem with rhythmbox
> shewdiz@shewdiz-pc:~$ usermod -G pulse-rt shewdiz
usermod: unable to lock password file
shewdiz@shewdiz-pc:~$ sudo usermod -G pulse-rt shewdiz
Password:
shewdiz@shewdiz-pc:~$ 



---

### Post by aysiu on 2007-05-06
Only clue I found from your error is this:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/83137](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/83137)

---

### Post by medya on 2007-05-06
> **Cappy said:**
> Try ..
```

usermod -G pulse-rt yourusername

```

hey I did 
sudo usermod -G pulse-rt shewdiz

and it msssed up my system , now I cant do anything, it says I dont have right to do that !!!
for example  I can use my sound card or I cant run synaptic ...

how I can undo 
the 
usermod -G pulse-rt shewdiz ?

---

### Post by medya on 2007-05-06
bump

---

### Post by omicist on 2008-07-18
Sorry to resurrect this thread, but I had been suffering from a similar problem.  The command listed above should actually read > [FONT="Lucida Console"]usermod -**a**G pulse-rt [username][/FONT] Without the 'a' (append) option, your previous group memberships will be obliterated, and there is no trivial way to recover them!

Although you've probably done something about that by now, if anyone else has made this mistake they might find some love [here](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/#comment-37611/).

---

