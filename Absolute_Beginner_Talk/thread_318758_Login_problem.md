---
title: "Login problem"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by cosworthgizmo on 2006-12-14
Hey

I have some problems with my login, because it's say's my password is wrong, or incorrect.. 

what do i do ??

i can't loging.. 

anywone that can help me ??

---

### Post by Duck2006 on 2006-12-14
Can you login as in recovery mode

---

### Post by cosworthgizmo on 2006-12-14
> **Duck2006 said:**
> Can you login as in recovery mode

nope

when i start it, after i have installed it with the alternative install cd, and i have created a user : klaus and a passwd : xxxx

and then i would like to login, but it just says the user or passwd is incorrect..

how can i get in or fix this ??

---

### Post by Nopposan on 2006-12-14
O.K., I'm going to assume you're supposed to be logging in and not just trying to get around security.  Right?

Alright, if you're computer's basic input/output system (BIOS) is configured to boot from cdrom/dvdrom (which it probably is if you just installed Ubuntu) then I think all you need to do is change the root password by editing the right file via a Live Linux CD that allows you to write to the hard drive.  'Sorry, I'm not holding out on details but I just don't remember them right now.  I'll get back to you if no one else has an answer for you before I get the chance.  For now, just know that there's a solution and keep the faith.

Cheers.

---

### Post by Nopposan on 2006-12-14
Oh yeah, did you use numbers in your password?  If so, then make sure your numbers on your kepad are locked.  Similarly, make sure that the CapsLock key hasn't been accidentally depressed.  This solves most password issues, in my experience.

---

### Post by Nopposan on 2006-12-14
One of the answers in the thread whose url I pasted below should be helpful.  I'm particularly interested in that grub boot option as it doesn't require having access to a cdrom.  However, 'could be a security problem for some folks.

[http://www.ubuntuforums.org/showthread.php?t=317923&highlight=forgot+my+password+login](http://www.ubuntuforums.org/showthread.php?t=317923&highlight=forgot+my+password+login)

Good luck.  I hope that helps you.

---

### Post by civic_si on 2006-12-14
at the grub bootup screen select recovery mode. this will get you to a root prompt then just typ the username in 

passwd klaus

hit enter then it will ask you for a new password. then just type 

init 6

this will reboot the machine and try the new password at the login screen. this is assuming that you have installed Ubuntu this wont work off the live CD.

---

