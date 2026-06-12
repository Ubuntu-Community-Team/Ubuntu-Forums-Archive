---
title: "Cannot log in as user or admin- help?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by cautious on 2006-08-08
Hi-

I just installed my Ubuntu today and now I'm unable to login as a username or administrator.

Earlier today that happened, and I was able to boot into recovery mode and entered ls/ home, which gave me "oem" in blue, which I finally realized was my administrative username (I had not been prompted for one during the install).

Now I find myself completely shut out. On the regular login screen I can't log in with either oem or my username.  In the recovery mode I've tried ls /home, but it just comes back as an unrecognized command.

Help!  I'm sending this from (ACK) Windoze!!!!

---

### Post by skirkpatrick on 2006-08-09
Well, you should have been prompted during the install, you just may not have noticed it.  My suggestion, since you can't get into your Ubuntu, is to do a fresh install over the top of it and watch for the prompt.

---

### Post by arjun.shankar on 2006-08-09
I don't know why it is not recognized as a command in recovery mode. But if this one works, it's your best shot:

Type this (as root) in the recovery mode:

**passwd oem**

Enter a new password when prompted to do so. (It won't ask you for the old one)

Use it for logging in. I don't have an OEM installation (which is what it seems you have made), so I'm not sure, but I think you will be able to set things right as "oem" after logging in.

If it won't work, then... well I have no other suggestion.

---

### Post by cautious on 2006-08-09
So far I've installed about four times looking for that prompt to choose a username.  It just does not happen.

I guess my only option is to install yet again and try to keep the "oem" as the username.

I am deeply frustrated.

---

### Post by arjun.shankar on 2006-08-09
Did you try what I asked in the recovery mode?

---

### Post by cautious on 2006-08-09
I had already reinstalled before I got this message.  I may check on that next time I boot up.  Thanks.

---

### Post by skirkpatrick on 2006-08-09
What install disc are you using?  I never heard of it defaulting to "oem".  In fact, my install wouldn't advance until I gave it a username and password

---

### Post by cautious on 2006-08-09
I'm not even sure where I downloaded it from.  I do know that I got a lot of automatic updates today, so it may have been an older version of 6.06.

I was just frantically searching in recovery mode, and typed in ls /shift, and there it was.  That's all I can tell you.

---

### Post by arjun.shankar on 2006-08-10
Well, even if you have the latest CD, you will have a LOT of updates right after install. The latest CD came out on 1st June ;).

Try:
**md5sum filename.iso**
on the iso image of the CD and compare with the final release md5sum.
Did you install from an alternate CD (text mode install with more options) or the regular Live CD that they ship (I've had lots of trouble with that one)

---

### Post by skirkpatrick on 2006-08-10
Hmm, I've used nothing but the live CD and two Internet upgrades.

---

### Post by meatface on 2006-08-10
O.K. I had the exact same problem. I installed 6.06.1 and it does not ask for a username. After reading this thread I tried typing in 'oem' for the username and the password that I supplied and it worked. So give it a try.

Meatface

---

### Post by cautious on 2006-08-10
That's right.  At the risk of repeating myself, I booted into safe mode, and when safe mode stopped and gave a command prompt, I entered ls /home , and oem appeared in blue.

---

