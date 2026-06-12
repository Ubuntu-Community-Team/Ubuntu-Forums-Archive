---
title: "Can't enter Ubuntu - password inccorrect"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-18
So I just installed Ubuntu, and now I can't enter the OS.  Is there any way to fix this without reinstalling?  I figure I'll end up at this point again anyway.

What I find odd is that I had to password protect a username but not the root/administrator...

Anyway, any help is appreciated.  If I go to recovery mode I get the prompt root@Myusername-Ubuntu:~#  (oddly my username is capitalized - it made my uncapitalize it originally).

I have no idea what to do to reset the username password or whatever I'll need to do to enter my newly installed OS.  

Consider me a newbie (I know its the newbie forum but some people respond with answers for intermediates or better anyway).

K

---

### Post by localzuk on 2006-03-18
When you set up Ubuntu, it asks you for a password for your user - this user is the admin account and has access to 'sudo' to allow it to run root tasks without using root directly.

If you go into recovery mode again, try typing 'passwd Myusername' at the shell. It will then ask you for a new password...

Also, the 'Myusername-Ubuntu' is the name of the machine as far as I am aware. The user that is being used is 'root'.

---

### Post by stuporglue on 2006-03-18
When starting to boot, hit "Escape" to enter the grub menu. There should be a recovery option, I think. Enter that, then let it continue booting. 

Hopefully you'll end up at a prompt. At the prompt, type:

passwd YOUR_USER_NAME

That will prompt you for a new password for your user. Enter it twice, and don't forget it. ;-)

Type: 

reboot

And you should be good to go.

---

### Post by Kersus on 2006-03-18
Thank you for the instructions.  Issue resolved with entering Ubuntu OS.

---

