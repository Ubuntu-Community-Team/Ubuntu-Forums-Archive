---
title: "Fresh install, can't login"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by a.Bird on 2006-10-16
Let me preface by saying I'm a noob and am only really used to the Windows interface.  All I want to do is learn how to use Ubuntu, but I can't login.

Downloaded and burnt ubuntu-6.06.1-alternate-i386.iso and loaded it to bring up install menu. Gave me the option of installing with either text mode or oem mode. The first time, I chose oem mode. Everything went great and I remembered what my username (lowercase) and password was. After I installed Ubuntu for about an hour and a half, I came to the Login screen. Wooot! Entered username and password EXACTLY as I had set it up in the installation. "Incorrect username or password." Okay... so I reinstalled in text mode (like it would make any difference) and used the same username and password.  Same message and no login. The user name is simple, it's my first name: zac. The password is one I've used for various accounts for like 10 years. I'm not messing this up. Ubuntu is F**KING WITH ME. :evil: 

Any suggestions??

---

### Post by jordanmthomas on 2006-10-16
I believe that for an OEM install the username is oem

Maybe give that a try?

---

### Post by a.Bird on 2006-10-16
> **jordanmthomas said:**
> I believe that for an OEM install the username is oem

Maybe give that a try?
Well the last install was in text mode but I just tried "oem" with my pass and without it, and still nothing.  I have an x86 Athlon XP 2600+ and I'm not dual booting or anything like that. Did I install the wrong version?

---

### Post by a.Bird on 2006-10-16
OOps sorry.  How do I delete a post?

---

### Post by jordanmthomas on 2006-10-16
oops...didn't see that part.  Sorry.

Reboot and when you see the GRUB menu hit ESC.  Select the recovery mode.  Let it boot up and hit enter to log in as root.

```
cat /etc/passwd | grep zac
```
just to make sure you're a user.

If you're not, do this:
```
adduser zac
```
It will ask you to set up your password and whatnot

If you *did* come up in the list, try setting your password
```
passwd zac
```

reboot and see if you can log in after that.

**I don't think you can delete a post

---

### Post by junglepeanut on 2006-10-16
I have never used the oem install but I have done many of the other installs.

It may be possible that this one has reverted to the no password environment?

i.e. leave the password blank. 

This was the case for some install a long time ago. I have no idea if this has to do with yours, but I hope it helps.

edit: Missed the post above mine, it sounds much more promising.

---

### Post by a.Bird on 2006-10-16
Yup, Jordan's solution worked!  Thank you so much.  My username wasn't listed so I created a new and logged right in.  That was very nifty; it actually makes me more excited to work with this OS.  Thank you again, you're a life saver.  [-o<

---

### Post by jordanmthomas on 2006-10-16
You may have trouble doing things using sudo...I'm not sure if you will or not.  If so, just come back to the forum and someone can help you out with getting them for yourself.

---

### Post by bupkes on 2006-10-17
Installed Dapper via 6.06.1 alternate iso , text
IBM laptop, dual boot with win2k

First boot into Dapper, prompted for username and password.  Entered both, screen went to black and showed:

ubuntu 6.06.1 LTS [hostname] tty1
login:

for about a second.  Screen went back to splash and prompt for username reappeared.

I rebooted into recovery mode, confirmed that my username existed, reset my password. 

Rebooted. Same thing happens.

Help?

---

### Post by a.Bird on 2006-10-17
You should do the same thing Jordan told me to do.
> **jordanmthomas said:**
> Reboot and when you see the GRUB menu hit ESC.  Select the recovery mode.  Let it boot up and hit enter to log in as root.

```
cat /etc/passwd | grep zac
```
just to make sure you're a user.

If you're not, do this:
```
adduser zac
```
It will ask you to set up your password and whatnot

If you *did* come up in the list, try setting your password
```
passwd zac
```

reboot and see if you can log in after that.

---

### Post by velo on 2006-10-17
> **bupkes said:**
> Installed Dapper via 6.06.1 alternate iso , text
IBM laptop, dual boot with win2k

First boot into Dapper, prompted for username and password.  Entered both, screen went to black and showed:

ubuntu 6.06.1 LTS [hostname] tty1
login:

for about a second.  Screen went back to splash and prompt for username reappeared.

I rebooted into recovery mode, confirmed that my username existed, reset my password. 

Rebooted. Same thing happens.

Help?
You have definitly not the same problem a.Bird had.

It seems that somehow your xserver, which is the program driving the graphical interface, just exits right after you log in. What you see before the graphical login-prompt (called gdm) reappears is the bare text-terminal-login.
 
I just searched a little bit and found [this thread]("http://ubuntuforums.org/showthread.php?t=188938") in which someone seemed to have the same problem - unfortunately he only posted *that* he solved it. 
Perhaps you could ask him *how* he did it.

I hope this was helping...

---

