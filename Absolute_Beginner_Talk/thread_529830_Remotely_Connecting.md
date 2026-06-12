---
title: "Remotely Connecting"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Raptor45 on 2007-08-19
I'd like to be able to access a home computer from college over the internet. I have used Remote Desktop fine in the past, but unless I'm mistaken this requires a user to be logged in. Is there any way to set it up so that as long as the computer is turned on I can access it? Logging in via command line at first would be okay, but I'd want to be able to start the GUI to use certain programs.

What is the best way to go about setting up remote access like this?

---

### Post by HermanAB on 2007-08-19
If the target is Windows, use 'rdesktop'.  If the target is Linux, use ssh.  For rdesktop, you need to forward port 3389 in the home router to the PC and for Linux, you have to forward port 22 and you have to have sshd running of course.

However, once you do that, you are bound to get automated brute forcers knocking on the door, so you have to ensure that the machine has a very long password.  For Windows, a password should be 15 characters or more and for Linux, 9 characters or more. (The reason is a bug in the Windows Lanman password system).

Hope that helps!

Herman

---

### Post by Raptor45 on 2007-08-19
How can I access the GUI via SSH?

Is there some way perhaps, to let Ubuntu automatically login... thus enabling the standard Remote Access without needing to do anything?

---

### Post by nitro_n2o on 2007-08-19
you need to get something like Xwin32 to forward X over ssh... this will also require you opening port 6000 in your system, but it's generally slow
to automatically login to ubuntu (without username, passwd) go to System->Administration->Login screen->Security and do what ever you want..

---

### Post by Paul133 on 2007-08-19
Would VNC work, or is that only if you're targeting a UNIX-like system (not Windows)?

---

