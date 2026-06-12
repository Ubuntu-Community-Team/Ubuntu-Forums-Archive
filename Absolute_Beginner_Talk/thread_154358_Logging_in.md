---
title: "Logging in?"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by prpandey on 2006-04-02
I installed Ubuntu 5.1

I installed all the packages as well.

It asks me to login. I put in the information (username/pass). Then I am redirected to a prompt. I type "help" and I can't get much info.

The prompt is something like "username:ubuntu:" I don't remember exactly. How do I just get to the desktop?

---

### Post by halitech on 2006-04-02
you can try Startx or sudo /etc/init.d/gdm restart

---

### Post by prpandey on 2006-04-02
[QUOTE=halitech]you can try Startx or sudo /etc/init.d/gdm restart[/QUOTE]


Hi, thanks for the help. However, that still hasn't fixed it. I tried to do startx. Apparently I have some sort of problem with X. It asks me if I want to diagnose the problem. My screen goes blank a few times, then it wont work. I get prompted again back to my username@ubuntu:

Any ideas?__

---

### Post by halitech on 2006-04-02
[QUOTE=prpandey]Hi, thanks for the help. However, that still hasn't fixed it. I tried to do startx. Apparently I have some sort of problem with X. It asks me if I want to diagnose the problem. My screen goes blank a few times, then it wont work. I get prompted again back to my username@ubuntu:

Any ideas?__[/QUOTE]


try running

sudo dpkg-reconfigure xserver-xorg

and see if you can get X server to configure and allow you to login

---

### Post by prpandey on 2006-04-03
[QUOTE=halitech]try running

sudo dpkg-reconfigure xserver-xorg

and see if you can get X server to configure and allow you to login[/QUOTE]


I did that and tried to reconfigure everything to the best of my ability and it still wont work. i get some problem with a framebuffer device. I'm on a ATI Radeon x200 (laptop vid card). I am on a AMD Athlon.

---

