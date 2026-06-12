---
title: "[SOLVED] Ubuntu not booting correctly...methinks"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by pika2 on 2008-01-19
Well, it's been fine for me for a while, but now when i boot, it'll show a splash screen, and go to a command prompt.  What do I do now?

---

### Post by eapache on 2008-01-19
Does it show an error, a login prompt, or just "username@computer-name:~$"

What you need to do depends on which it shows.

And did you change any hardware recently?

---

### Post by pika2 on 2008-01-19
In a texty whatever you call it (i am such a n00b) it asked for my username then password.  then it showed "username@computer-name:~$"

---

### Post by eapache on 2008-01-19
Alright, try```
startx
```after you log in and see what happens. If that works, then go to System>Administration>Services and make sure GDM is enabled.

And it's called a command line :P

---

### Post by Dr Small on 2008-01-19
Could possibly be that Xog is not starting. Have you tried starting x?
```
startx
```

Or, it could be that you are booting into recovery mode (which doesn't sound logical), if your prompt says "root@computer-name:~#"

Dr Small

---

### Post by pika2 on 2008-01-19
I'm in recovery mode right now, when i tried normal it just showed some green screen.

---

### Post by eapache on 2008-01-19
Can you describe the green screen?

In recovery mode, try```
sudo dpkg-reconfigure -phigh xserver-xorg
```then restart into normal mode.

---

### Post by pika2 on 2008-01-19
It's uhh...green?

i'll try that

---

### Post by pika2 on 2008-01-19
omg whatever that was worked

thanks so much

---

### Post by eapache on 2008-01-20
Something you did (possibly changing your video card) meant that whatever driver it had recorded was wrong, and was failing to start your graphics. The command simply ran an auto-detect and auto-configure. Apparently it corrected whatever the issue was.

You can now mark this thread as 'solved' using the thread tools at the top of the page. This makes it easier for people browsing to find unsolved problems.

---

