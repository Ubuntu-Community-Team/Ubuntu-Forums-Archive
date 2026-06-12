---
title: "Trouble putting computer to sleep"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Movie_Maniac on 2006-11-26
I'm fairly new to Linux and have just got to the point where I'm comfortable enough to use Ubuntu more than Windows.  My one major problem now is that I can't get my computer to go to "sleep".  I don't have any problems doing that with Windows, so I know it must be a setting I'm overlooking in Ubunutu.  

If I choose to "hibernate", my monitors briefly shutoff but then powerup again and there is no change in the power of the computer.

If I go into the power management menu and enable "suspend", choosing suspend shuts off the monitors but the computer remains running (and I can't wake it up at all).

Any help would be greatly appeciated. I'm searched-out. . .everywhere I look for solutions to this problem have yielded results for laptop owners.

---

### Post by 56phil on 2006-11-26
This may sound crazy ... is swap working correctly? Do a ```
free -m
``` and if the last line looks like this:```
swap 0 0 0
``` I might be able to help. Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=307009](http://www.ubuntuforums.org/showthread.php?t=307009)

---

### Post by vtel57 on 2006-11-26
I've found true Sleep/Suspend to be a contentious issue in Linux. About the only type of power-saving mode you'll get using a desktop computer is monitor off mode. Linux usually uses a "journaling" file system. Access to the drive to write to the journal requires that the drives never spin down. You can manually set your drives to spin down, as I understand it, but it's stated that this is a dangerous thing to attempt. Maybe someone with a bit more knowledge will come along here and give you their opinions. In my own experience, though, you'll not be getting the same type of Sleep/Suspend modes that you were used to in Windows.

---

### Post by Movie_Maniac on 2006-11-26
swap is fine: 3192 0 3192

---

