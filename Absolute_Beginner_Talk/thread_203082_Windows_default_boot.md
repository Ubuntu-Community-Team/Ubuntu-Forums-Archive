---
title: "Windows default boot?"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by mbstrlbstr on 2006-06-24
Is there a way to have windows be the default boot in the boot screen. I installed dapper, but my family uses xp. since I also have a lappy, I don't usually use the Desktop, but I want it on there. Please help!

---

### Post by aysiu on 2006-06-24
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by mbstrlbstr on 2006-06-24
thanks man. That was really quick

---

### Post by anaconda on 2006-06-24
It is a good idea to put your windows the first boot option on the file..
So that you dont have to change the 
default 0
-line even if you install updates (eg. new kernel) which changes the numbering of your windows entry, if it isn't the first...

And remember that you dont want to put the windows boot option between these lines:
### BEGIN AUTOMAGIC KERNELS LIST
---
### END DEBIAN AUTOMAGIC KERNELS LIST

Because ubuntu updates CAN (and do) screw the entries between those 2 lines... It is a good idea to put your favorite ubuntu boot entry also outside of those 2 lines, if you dont want updates to cahnge them... 

Just my 2 cents..

---

### Post by dam1an on 2006-06-24
damn, I saw the title and was so eager to help... as I had made XP my default boot option after a bit of googleing a few mintues ago... ahh well, maybe next time
the tip about making XP the first in the list is a great tip, something I overlooked (to be honest, I just didn't think about it, as I didn't want to make any major changes lol, other then changing a digit here and there)

---

