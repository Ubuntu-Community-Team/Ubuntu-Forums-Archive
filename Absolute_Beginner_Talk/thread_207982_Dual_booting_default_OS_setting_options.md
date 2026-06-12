---
title: "Dual booting default OS setting options?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by dderolph on 2006-07-02
I have not installed Ubuntu yet. I currently have a dual boot configuration for Win 98SE and Win XP Pro.  If I install Ubuntu, and after GRUB does it's work, will I be able to change the default startup OS, as I now can?  When I start my computer and it stops at the OS selection screen, does startup automatically continue after a certain time, or does it wait until I hit Enter?  And, if it automatically proceeds, will I be able to set the length of time that screen is displayed before bootup proceeds?

---

### Post by Jagot on 2006-07-02
Check here for changing the default OS on GRUB:

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

GRUB automatically loads the default OS after 10 seconds, but this time can be altered.

---

### Post by Dr. Nick on 2006-07-02
yes you can change the default os option, you can change the time limit aswell.

All of this is set in the file /boot/grub/menu.lst

here are the excerts from mine
```


## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

``` 
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10
```

---

### Post by dderolph on 2006-07-02
Thanks for the replies.  I forgot to mention another option currently in my startup list, Windows Recovery Console.  Can that also be part of the startup list?

---

### Post by Apple 101 on 2006-07-03
Windows Recovery Console?  You get to that after selecting Windows XP though.  Why would you have that in your OS boot list?

---

