---
title: "Shamefull noob looking for advice."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by phlegms on 2008-03-31
Just installed ubuntu on my vista laptop fairly flawlessly( I hope), however, since installation i cannot seem to be able to log in. Unless there is another reason for this i have most likely forgotten my user name and password. What are my options for getting around this?
Can i simply create another account and use that, or can i reset both my user name and password?
Or will i have to delete ubuntu and re-install?
Thanks in advance,
phlegms.

---

### Post by scragar on 2008-03-31
[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

you'll need to know your username though.

---

### Post by NR1224 on 2008-03-31
assuming this is a fresh install, just reinstall, there may be a way around it, but I dont think that there is. Hopefully you dont have any data that needs backed up

---

### Post by phlegms on 2008-03-31
Thanks for the advice and quick response time.
Im fairly sure i know what my username is, silly me kinda rushed the installation.
Was looking at the link you posted and had one question about it, whats the grub prompt?

---

### Post by Joe325 on 2008-03-31
Heres a little something

[http://www.ubuntuforums.org/showthre...howto+password](http://www.ubuntuforums.org/showthre...howto+password)

Enjoy...

---

### Post by NR1224 on 2008-03-31
the grub prompt is the cmd line that u use when configuring te boot loader, grub

---

### Post by forrestcupp on 2008-03-31
Here's how you do it.  Boot to your recovery mode command line.  When you start your computer you will see your GRUB boot menu, and the 2nd choice in the menu should say the name of your kernel with (recovery mode) after that.  Choose that and you will end up at the command line.  If you're using Hardy, when you boot to recovery mode, choose to drop to root for the command line.  Then type
```
cd /home
ls -a
```
That should list all of the user names that you have set up.  Now you know your user name, so type:
```
passwd ***username***
```
substituting your user name there.  It will prompt you to enter your new password twice.  You may not be able to see any output for the letters you type for the password, I don't know.

Then type
```
exit
```
And it will reboot to your login and you can use your user name and new password that you are not going to forget from now on.

---

### Post by phlegms on 2008-03-31
> **forrestcupp said:**
> Here's how you do it.  Boot to your recovery mode command line.  When you start your computer you will see your GRUB boot menu, and the 2nd choice in the menu should say the name of your kernel with (recovery mode) after that.  Choose that and you will end up at the command line.  Then type
```
cd /home
ls -a
```
That should list all of the user names that you have set up.  Now you know your user name, so type:
```
passwd ***username***
```
substituting your user name there.  It will prompt you to enter your new password twice.  You may not be able to see any output for the letters you type for the password, I don't know.

Then type
```
exit
```
And it will reboot to your login and you can use your user name and new password that you are not going to forget from now on.

Cant thank you enough, after a few attempts it worked!
I cant wait to start using ubuntu now, thanks again,
phlegms.

---

