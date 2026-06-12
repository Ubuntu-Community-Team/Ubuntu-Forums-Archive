---
title: "unknown username and password"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by vinnyv99 on 2006-04-11
hello, brand new to the forum and to Ubuntu.  A computer was given to me by a person who I no longer have contact with.  I booted up the computer and found that it has the Ubuntu OS installed in which I have no experience and which brings me to this forum.  Figured this is a good time to start learning this new os.  Anyway the problem is that it boots up to a username/password in which I do not know.  Is there anyway to get around this initial login?  The computer came with the CD distribution and various other file installs so I imagine I can reload and start fresh but that would be a pain.  Can I boot off the cd and change the username/password?

tks

---

### Post by halitech on 2006-04-11
You can check this thread for more info:

[here]("http://ubuntuforums.org/showthread.php?t=98535&highlight=forgotten+username+password")

***I really need to check how forums use attachments before I post them :(

---

### Post by dcstar on 2006-04-11
[QUOTE=vinnyv99]hello, brand new to the forum and to Ubuntu.  A computer was given to me by a person who I no longer have contact with.  I booted up the computer and found that it has the Ubuntu OS installed in which I have no experience and which brings me to this forum.  Figured this is a good time to start learning this new os.  Anyway the problem is that it boots up to a username/password in which I do not know.  Is there anyway to get around this initial login?  The computer came with the CD distribution and various other file installs so I imagine I can reload and start fresh but that would be a pain.  Can I boot off the cd and change the username/password?

tks[/QUOTE]
Try this:

[http://ubuntuforums.org/showthread.php?t=3609](http://ubuntuforums.org/showthread.php?t=3609)

---

### Post by steve.horsley on 2006-04-12
Originally by jdong:
> 1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.
---- If that doesn't fix your problem, do the steps below...
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.
Now, there's a trick I didn't know!

You can find the usernames configured on the system by listing the folders in the home directory with the command:
**ls /home**
Imagine you see s folder called **steve**. You can set steves password with the command:
**passwd steve**

Better, you can find which username has admin rights with the command:
**grep ^admin: /etc/group**
 and you will get a line someting like:
admin:x:106:steve
You can change this users password (as above) then reboot with Alt-Ctrl-Del. You should be able to log in as that user now.

---

### Post by Iowan on 2006-04-12
Will **/etc/sudoers** need to be edited?

---

### Post by steve.horsley on 2006-04-12
[QUOTE=Iowan]Will **/etc/sudoers** need to be edited?[/QUOTE]
I don't see why, if all he is doing is using the existing admin account and changing the password to one he knows. Even if he adds a new user for himself, he can just put himself in the admin group - no need to edit sudoers.

---

