---
title: "Log-in Fails"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by af4k on 2006-08-31
Hi - I just installed UBUNTU on a computer, and it starts up fine.
I am not connected to the internet with it yet. However, I cannot LOG-IN at all.
It rejects my user name and password. ANy idea what I cna do to start over?

Thanks - af4k

---

### Post by jordanmthomas on 2006-08-31
Did you do an OEM install or a normal one?

In the off chance you accidentally did an OEM install, try logging in as 'oem' with whatever password you gave.

Also, if you boot into single user mode (it's on the grub screen when you first boot your computer) you should be able to log on as root and add a user.  I can help you do that (I think) if logging in as oem doesn't work.

---

### Post by jordanmthomas on 2006-08-31
After reading one of your posts in another thread, I guess you think I am trying to show off or something. [(here)]("http://www.ubuntuforums.org/showthread.php?t=240093")  Sooo, I will just go ahead and tell you what to do in case an oem login doesn't work.

You will need to write this down or print it or something.

1.  Reboot
2.  Right as it starts up, hit the ESC key until you see a menu.
3.  Look on the menu  for an item labeled '(recovery mode)' and select it.
4.  When you go to log in, don't put any password.  Just hit return.
5.  After logging in, if you want to see if your user exists, type this:
```
cat /etc/passwd | grep *username*
```
6.  If you see anything output from this command, go to step 7.  Otherwise, go to step 9:
7.  ```
passwd *username*
```
8.  Then you just enter your new password and type 'reboot' when you're done.
9.  Only do this if you skipped steps 7 & 8.
```
adduser *username*
```
10.  Reboot and you should be able to log in next time (after choosing the kernel at the top of the GRUB menu)

If you have any questions, feel free to ask.

---

