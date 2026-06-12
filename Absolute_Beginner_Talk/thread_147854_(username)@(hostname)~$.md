---
title: "(username)@(hostname):~$"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Panhead Bill on 2006-03-21
I had repeated failures trying to install Ubuntu at the "Downloading extra packages" step.

I tried Expert install to bypass extra packages, then after reboot to HD, inserted the CD.  This seemed to work as the packages then downloaded.  After setting screen resolution, I ended up with a screen of text, ending with:
Ubuntu comes with NO WARRANTY, to the extent applicable by law.

followed by (my username)@(myhostmane):~$

I believe this is the BASH shell, and some of the commands I tried seemed to work.

What do I do to get to the Gnome desktop?

Is the fact that I end up in the bash shell telling me that I have some problems? (most likely in the "Additional packaged downloaded if I had to guess)

TIA

---

### Post by verbalshadow on 2006-03-21
from an expert install this command should install all the packages for a normal ubuntu desktop packages

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Panhead Bill on 2006-03-21
So at the Bash shell I type the sudo (etc) after the ~$ and it will retrieve the missing desktop files from the CD. 

How do I determine what else is missing from the standard install?

---

### Post by mcduck on 2006-03-21
If normal ubuntu desktop is what you want, I'd recommend installing again, this time with normal install instead of expert. When you do expert install, you create root user and password, and that seems to cause a lot of problems, like admin tools not working in Gnome etc.. Anyway, Ubuntu is not such a bloat distro that there would be much need to select any packages yourself during install. It's easier to remove extra stuff (if any) after normal install :)

anyway, installing ubuntu-desktop should bring you pretty much everything normal ubuntu install has.

---

### Post by Panhead Bill on 2006-03-21
The problem with that approach is that during normal install my PC errors at downloading extra packages, then it hangs at 0% immeadiately after restart.  This is with 3 different disks, one high speed burn, one low speed burn, and one disk that came with the book.  

The only way I can get through the install is as expert, and then by bypassing the extra packages at that time, waiting until after restart to add them.  (it added them automatically)


I just tried: sudo apt-get install ubuntu-desktop

Result:  next line asked for my password, i inputted the password.
Result: no action other than standard BASH line: (my username)@(myhostmane):~$  

???

---

### Post by Iowan on 2006-03-21
Did you actually enter the password and hit [ENTER], or did you notice no echo on the screen and stop?  No echo is a security feature.

---

### Post by Panhead Bill on 2006-03-21
I did hit enter, and it came back with the bash line.  (otherwise it would still be on the password line.)

---

