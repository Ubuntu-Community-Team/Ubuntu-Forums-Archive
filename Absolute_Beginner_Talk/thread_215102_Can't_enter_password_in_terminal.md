---
title: "Can't enter password in terminal"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by cheerstix on 2006-07-13
I installed ubuntu 2 days ago without any problems dual booting after reading through these forums for a couple of days and getting plenty of good advice - Thank you!

I'm now trying to use sudo to access the root account but when asked for login password no characters display in the terminal when I enter install username - just blank and login failure. I've read numerous threads and I can't find any with similar problem. For now I'm just trying to set my resolution, which I think I can do if I could login. 

Any help to get me past this sticking point appreciated - Thanks!

---

### Post by invalid on 2006-07-13
The characters do not show up on purpose, this is a security feature. They are, however, being received by the system.

The password should be the same one you use to log in with. If you are sure this is the password you are using, we might can start in a different direction.

---

### Post by devpatel on 2006-07-13
just type your password in and press enter..

what you type is still being entered but it doesnt show up...probably for security reasons

---

### Post by T700 on 2006-07-13
Always good to check the simple first:

1.   Caplock on?
2.   Does your password have numbers in it?  If so, and you are using the number pad, is the Num Lock on (it should be).
3.   Try writing the password down on a sheet of paper and typing it one character at a time.

Paul

---

### Post by cheerstix on 2006-07-13
WOW! Didn't expect a response this quick.
I've checked cap lock, num lock etc and is OK. I did read an article that said characters are hidden but still nothing. I click applications > accessories > terminal and get my details displayed, I then type sudo followed by a command and get the password prompt. I enter my install password (no character is displayed) and hit enter, then I get: Sorry, try again.

---

### Post by Brunellus on 2006-07-13
just to confirm:  you're typing your user password, right?  The one that you typed to log onto the system to begin with?

BTW, don't expect *all* threads to be responded to this quickly... but generally, on ubuntuforums, you can expect very prompt responses on common issues if you ask the question in a way that's easily understandable

---

### Post by cheerstix on 2006-07-13
> **Brunellus said:**
> just to confirm:  you're typing your user password, right?  The one that you typed to log onto the system to begin with?

Yes, and I've rebooted and entered same password to check once more. I also entered my password at initial command prompt just to double check caps lock and num lock are OK - then backspaced to remove.

---

### Post by Brunellus on 2006-07-13
if you're backspacing, that's going to come up as an error.

---

### Post by T700 on 2006-07-13
[This thread]("http://www.ubuntuforums.org/showthread.php?t=214323") may give you so help in resetting the password.

Paul

---

### Post by steve.horsley on 2006-07-13
Are there more than one user configured on the system? Only the first one you entered during install is allowed to use the sudo command, though you can fix this later.

---

### Post by invalid on 2006-07-13
Try running a command using the Alt-F2 prompt. For example ```
gksudo synaptic
```.
You have asteriks in this box, to affirm you are typing it in. If you know you have the right password here as well, there is a problem with the password itself somewhere.

---

### Post by cheerstix on 2006-07-14
Part of my password used keys in the number pad and I'm guessing somewhere in the installation that the pad wasn't active. I've re-installed and set my resolution via the terminal - no probs. I'm hooked on Linux already and its only been 5 days!

Thanks for the help

---

### Post by invalid on 2006-07-14
> **cheerstix said:**
> Part of my password used keys in the number pad and I'm guessing somewhere in the installation that the pad wasn't active. I've re-installed and set my resolution via the terminal - no probs. I'm hooked on Linux already and its only been 5 days!

Thanks for the help
Cheers!

---

