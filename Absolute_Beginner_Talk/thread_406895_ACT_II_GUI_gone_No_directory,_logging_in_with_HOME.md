---
title: "ACT II: GUI gone: No directory, logging in with HOME=/"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Ian-on-the-Trent on 2007-04-11
Solar George has been helping me but we seem to have hit a wall.  This is the link to our previous posts: [http://ubuntuforums.org/showthread.php?t=405942](http://ubuntuforums.org/showthread.php?t=405942)

Somehow, some way, and totally beyond my comprehension, my GUI disappeared.  Not only that, my command line access is restricted to going through GRUB and the recovery mode.

When I boot, Ubuntu appears to load normally up until the time bar is filled at the "Ubuntu logo on a black background" point.  Then instead of loading the tan, default Ubuntu graphics and such, it goes to a CLI.

[B]Starting up ...
Ubuntu 6.10 MYCOMPUTER tty1
MYCOMPUTER login:[/B]

When I try to login I get the following (I have tried all accounts including SU):

**Last Login: Tue Apr 10 10:51:43 2007 on tty1 ** (note: this date/time does change)
[B]Linux MYCOMPUTER 2.6.17-11-generic #2 SMP Thur Feb 1 19:52:28 UTC 2007 i686

...standard UBUNTU legal stuff is here...

No directory, logging in with HOME=/
Cannot execute /bin/bash: Permission Denied[/B]

To make matters even more interesting, when I boot in the Recovery mode I get to a root prompt:
**root@MYCOMPUTER:/#**     *(Maybe this is normal?)*

While I thought I installed my ***/home/*** on its own partition, I can't be sure.  Nonetheless, while my ***/home/*** directory does not appear when I enter ***ls -l***, my ***/home/*** directory is accessible when I enter ***cd home***.

[COLOR="Green"]***I want my GUI back?***[/COLOR]  ](*,)

Any ideas?


[COLOR="DarkRed"]Just added: I typed*** cfdisk ***at the prompt and saw that I had ***hda1*** (boot, primary) and ***hda5*** (swap).  I guess I don't have a separate /home/ partition.[/COLOR]

---

### Post by zvacet on 2007-04-11
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

Because you boot in recovery mode make you root so you don´t have to write **sudo** in command you willl find on this page.

---

### Post by Ian-on-the-Trent on 2007-04-12
errant post.

---

