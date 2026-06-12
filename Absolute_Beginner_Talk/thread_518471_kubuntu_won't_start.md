---
title: "kubuntu won't start"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by cplspafford on 2007-08-05
I have kubuntu installed and everything has been working fine.  Recently though when I try to log onto kubuntu it gives me the log in screen, and then when I type my name and password all it does is go to a black screen for a second then right back to the log in screen.  It is not an incorrect password because when I type in a wrong one it gives me a wrong password error.  Any ideas what it could be??  I did not make any big changes recently. Thank you all in advance.  People here have been a huge help before.

---

### Post by overdrank on 2007-08-05
> **cplspafford said:**
> I have kubuntu installed and everything has been working fine.  Recently though when I try to log onto kubuntu it gives me the log in screen, and then when I type my name and password all it does is go to a black screen for a second then right back to the log in screen.  It is not an incorrect password because when I type in a wrong one it gives me a wrong password error.  Any ideas what it could be??  I did not make any big changes recently. Thank you all in advance.  People here have been a huge help before.

HI and could you give us some info on what type of graphics card you are using and if you did some updates recently?

---

### Post by cplspafford on 2007-08-05
I have an ATI Radeon Xpress 200.  Everything has been working fine for the last couple of months.  I have not made **_any_** changes except for the updates it tells me to.

---

### Post by overdrank on 2007-08-05
> **cplspafford said:**
> I have an ATI Radeon Xpress 200.  Everything has been working fine for the last couple of months.  I have not made **_any_** changes except for the updates it tells me to.

Ok have you tried to configure you xorg to see if that will help. You do this by using the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
in the terminal and hopefully this will get you back to the desktop. You can access the terminal but using the ctrl,alt,F1 keys at the same time.

---

### Post by cplspafford on 2007-08-05
I think my problems started with a setting.  I can get on another user profile but not the main one I had.  I THINK I may have messed up the refresh rate?? would that mess up the settings so bad that I cannot log into the user account.  The profile I am using now does not have any rights!!  The last post did not help.  It enabled me to change some settings but I still cannot log on.

---

