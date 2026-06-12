---
title: "is via the problem?? if not i dont know ! SOMEONE PLEASE HELP ME"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Attila2452 on 2007-11-04
ok i have Ubuntu on my PC and when i start my computer up, i have the 2 options (windows XP or Ubuntu) i go to Ubuntu and my computer goes through the start up process and  then it takes me to the login screen. i have already made my account and my password i even wrote it down but when i go to log on, it says "the user name or password is in correct." i have tried uninstalling it and re-installing it OVER AND OVER AGAIN but nothing seems to work.

i have also looked through what i can on that screen and i found out that there is nothing for "Remote Via"  and i don't know what it do (it is blank) i don't know what it is and I'm thinking that might be my problem... i have been looking at a lot of forums today and nothing has worked... i really need someones help. FAST

 - Attila Hajzer -

---

### Post by Bachstelze on 2007-11-04
Moved to ABT.

---

### Post by kejava on 2007-11-04
Hi Attila,

What you are seeing is fairly unusual.  Sounds like your user account is not being created during installation.  If you went through a reinstall, it's possible that you didn't choose to reformat the drive.  If that's the case, any existing username and password could still be there.  Sorry, I'm doing a lot of guessing here.

**Method 1:** The fastest solution to try out is to force a password change.  At power up then the grub boot prompt, you should have another OS option to boot called "recovery".  Select that on your next reboot.  It will put you into a single (root) user mode and will only bring you a black screen with a command prompt.  From here you can change your password for the username in question.  Just type the command:```
passwd <enter your username here>
```It will then prompt you for a new password ... assuming that user really exists.  If it works without error, reboot (ctrl+DEL) and boot using the normal boot method.  You should be able to log in normally.

**Method 2:** Now, it sounds like you're a newbie so if that username doesn't exist or you're just uncomfortable with the command line, here's another alternative.  While you're still at the command line after booting into "recovery" mode.  Type the following command at the prompt:```
startx
```This will bring you to a graphical interface just like on a regular bootup.  The only difference is that you're the root user so be careful what you do.  In the top left desktop menu go to System --> Administration --> Users and Groups.  From that interface you can change your password or even add yourself as a user if you find you don't exist.

-kevin

---

