---
title: "help please help with password and driver issues"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by rab4567 on 2007-03-12
I did something really stupid I change my password and it won't let me log in, fiddle sticks!
Also is there some easy way of installing drivers for nvidia geforce 6150 for a AMD4200 64 x2 dual with 2.0 of ram. I'm running everything in 32 bit mode maybe thats the problem I get a delay waving effect when I scroll up or down.


[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by Najand on 2007-03-12
Use recovery mode and change your passwd using "passwd <Username>" command. (Change <Username> with your username ofcourse.)

---

### Post by rab4567 on 2007-03-12
Ok i tried it and it didn't work perhaps maybe you can tell me how to do this line by line I really don't know what I'm doing. It look****s like basic to me and that was 100 years ago!

---

### Post by Najand on 2007-03-12
You mean you could not enter the recovery mode or you could not change the password or changing the password was not effective when you came back to normal mode?

---

### Post by rab4567 on 2007-03-12
oh yes when I typed in the command line  i got bash: syntax error near unexpected token ' newline. Again I need a step by step approach, I'm real green.

---

### Post by Najand on 2007-03-12
Ok, let us see how can we figure it out?
First, let us do it again;
1. Reboot  your computer;
2. Boot up using recovery mode
3. When it loaded, then use
```

passwd ***najand*** 

```
where ***najand*** is your user ID.
If it  fails with a syntax error message, then try to add another user, using:
```

adduser ***najand2***

```
where ***najand2*** is your new user ID.
then restart your computer and try to login your computer again.

---

### Post by rab4567 on 2007-03-16
Sorry I been away for a couple of days. Ok back to the problem I tried the option typed in passwd(my password),it then asked me retype my unix password which I did and rebooted. I stil was not able log in, then tried option #2 which open a whole bunch of questions name house# work# and so on I got scared and rebooted, is there some way to look at the current user name and password.

---

