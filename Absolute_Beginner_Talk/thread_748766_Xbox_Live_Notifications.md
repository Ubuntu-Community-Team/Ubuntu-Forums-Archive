---
title: "Xbox Live Notifications"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2008-04-07
How would I make it so when I go to the Applications<Internet then when i see XBL status, I can just click on it and make it open

thanks!

I know you go to Main Menu  then add program but im not sure what the command is

---

### Post by Joeb454 on 2008-04-08
Hi there, and could you please provide a bit more info as to what it is you want?

I don't know if you can display the status of Xbox Live in a menu, though I'd imagine you can write a small application to do that.

---

### Post by Crafty Kisses on 2008-04-08
> **LiNuXxToOthEMaX said:**
> How would I make it so when I go to the Applications<Internet then when i see XBL status, I can just click on it and make it open

thanks!

I know you go to Main Menu  then add program but im not sure what the command is

Do you want it like in your Applications menu?

---

### Post by twisted_steel on 2008-04-08
> **Codename said:**
> Do you want it like in your Applications menu?

Yeah, I believe that's what LiNuXxToOthEMaX is looking for.  I also sent a PM before, but I'll add the info here in case anyone else comes across it.

If anyone else is wondering, [XBL Status]("http://ubuntuforums.org/showthread.php?t=520113&page=7") is the application LiNuXxToOthEMaX is referring to.

I just made a bash script that changes to the correct directory and launches it.

```
#!/bin/bash
cd /home/myuser/code/xblstatus-testing/xblstatus/
./xblstatus.py &
```

You would of course change the path to the location of the program.  Also, make the script executable and use that location for the application launcher.  For example, I put mine here: "/home/myuser/code/xblstatus-launcher.sh" Then I added that to my applications menu.  The 48x48 icon is in the ui folder.  Attached is a screenshot.

---

### Post by Crafty Kisses on 2008-04-08
Thanks!

---

