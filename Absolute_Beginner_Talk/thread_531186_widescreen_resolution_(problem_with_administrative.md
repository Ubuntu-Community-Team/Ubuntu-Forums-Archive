---
title: "widescreen resolution (problem with administrative right when editing files)"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by noobie_uds on 2007-08-21
Hello, i'm new here.

I'm using a 1440x900 monitor and a Nvidia 7300GT card. But i cannot change the resolution. I follow this tut [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto). Then, i reallize that i'm having another problem. I can edit the file xorg.conf but cannot save, it said i dont have the right, this file doesnt belong to me....  I dont know how to login as Root.

Could somebody please show me how to deal with this problem.

---

### Post by ddrichardson on 2007-08-21
yes ```
gksudo gedit /etc/X11/xorg.conf
```

Backup first

---

### Post by noobie_uds on 2007-08-21
after messing around, finally i can get into Root 
```
http://ubuntuforums.org/showthread.php?t=31053
```
and then into something like Display Properties in Windows
> If all else fails, try running the following command:

sudo nvidia-settings

Under Video Configuration set your resolution and refresh rate, click apply, then save X Config.

:lolflag:

---

### Post by rolf-c on 2007-08-21
...what dd said, and I'll add that the password being asked for by gksudo is yours.  This will allow you to edit the file and save changes.

---

### Post by mikeyphi on 2007-08-21
> **noobie_uds said:**
> Hello, i'm new here.
  I dont know how to login as Root.


There's a good guide here:
[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29)

basically you type sudo  before a command
and enter your password when prompted

---

### Post by southernman on 2007-08-21
The root account is disabled by default. Using it can only lead to serious trouble... In other words, only use sudo (gksudo for launching gui applications like gedit or nautilus but any other gui as well), on a very limited as needed basis.

You've been warned!

---

