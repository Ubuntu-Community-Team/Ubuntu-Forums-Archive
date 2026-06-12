---
title: "no password clue"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by GolfGeek on 2006-03-12
HI
I know this is really dumb but I installed Ubantu on two systems. Started playing and using it on the second and went back to the first (my laptop which had once again crashed XP). I have absolutely no idea of what I entered as a password (hell, I'm not even sure of what my user name is). The operative question is : Is there any way to uncover this or is it easier to just reinstall. I have nothing on the laptop (after the windows crash, I reformatted the drive). Is there anything special about reinstalling with the existing system in place?

---

### Post by Zelut on 2006-03-12
If you dont have anything to lose on there you could just re-install it.  You dont need to change anything during the installer in order to re-install over top of it.

There are also some tips about [regaining access]("http://ubuntuguide.org/#rescuemode") after you've lost track of your password.

---

### Post by GolfGeek on 2006-03-12
Thanks for the quick reply. I suspected it was far easier to reinstall so I'll go that root. These forums are really excellent and I appreciate the quickness.

---

### Post by mcduck on 2006-03-13
[QUOTE=GolfGeek]Thanks for the quick reply. I suspected it was far easier to reinstall so I'll go that root. These forums are really excellent and I appreciate the quickness.[/QUOTE]
When you boot Ubuntu, there's an option for 'recovery mode' in grub menu. Choose that, and you'll en in command line as root. Now you can do 'ls /home' to find out names of all users on that machine, and 'passwd <username>' to change user's password. (replace <username> with the users name). Way easier than doing a full reinstall..

---

### Post by Madpilot on 2006-03-13
Avoid ubuntuguide.org, it is getting more and more out of date...

Try [https://wiki.ubuntu.com/LostPassword](https://wiki.ubuntu.com/LostPassword) - and after you've recovered, [https://wiki.ubuntu.com/StrongPasswords](https://wiki.ubuntu.com/StrongPasswords) is recommended reading.

---

