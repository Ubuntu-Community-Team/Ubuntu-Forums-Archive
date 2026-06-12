---
title: "I recently installed Ubuntu... but i can't use it!!"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by blueangel on 2006-04-12
This is my problem. I've recently installed Ubuntu, in the installation i set the user and it's password, but, when ubuntu starts and asks me this data, i put it, but it says to me that "invalid user or password".

What can I do???

I really need help!!!

Thank you very much!

Mati.

---

### Post by davebgimp on 2006-04-12
I'd hazard a guess that when entering either your username or password, you either accidentally spelled something other than what you intended...or perhaps had capslock on or the shifft button depressed for some or all of the keys entered.

You could re-install or if you're up for it, search this forum on how to replace your account password. I believe there is a way to do it if you boot in recovery mode.

---

### Post by pbaehr on 2006-04-12
This will get you up and running enough to fix the problem:

[http://ubuntuguide.org/#rescuemode](http://ubuntuguide.org/#rescuemode)

From there you'll need to change the password for the user you created during setup (provided that user exists)

To change the password type
```
passwd <username>
```
and it will prompt you for the new password. That will work assuming you didn't mistype the user name.

---

### Post by jazzmuzik on 2006-04-12
Linux is case sensitive. Did you mistype?

---

### Post by r4ik on 2006-04-12
Little bit the same but straight to the piont,

[http://www.ubuntuforums.org/showthread.php?t=133102&highlight=howto+password](http://www.ubuntuforums.org/showthread.php?t=133102&highlight=howto+password)

Good luck !

---

### Post by blueangel on 2006-04-12
Thanks, now i'm gonna try it. I have spelt ok the password and the user, that's the problem.

Soon, some news!!

---

### Post by blueangel on 2006-04-12
Doesn't appear the root.

Appears : "Give root password to ....."

What should I do??

I'm sure that i set the password and the user name in the installation, i don't know what happens!!

---

### Post by r4ik on 2006-04-12
Try this plaese,

You can use an Ubuntu Install CD to Reset the ROOT Password.

1. Insert the Install CD & at the CD Boot Prompt, type:

rescue

2. Follow the instructions & when you are in the "Terminal", type:

passwd root

3. Enter the ROOT Password twice in there & Add a NEW User account with:

adduser

4. Enter your NEW User info & when your finished, type:

adduser your_new_user_name admin

Note:
This is performed so that the NEW User can access System Tools as ROOT.

5. Then remove your InstallCD, Reboot your Ubuntu (by typing "reboot" or
"shutdown -r now") & Log in with your NEW User account.

Good luck !

---

