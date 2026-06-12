---
title: "Wine Question..."
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by tomwell on 2005-11-24
Hi,

Ok i have installed wine now, using apt-get... Do i just go into my windows partition and run .exe files by double clicking?? is there a GUI for wine??

Peace

Tom

---

### Post by aysiu on 2005-11-24
[QUOTE=tomwell]
Ok i have installed wine now, using apt-get... Do i just go into my windows partition and run .exe files by double clicking??[/QUOTE] Yes. You can also set up a command for the .exe. It's preferable to install Wine-run applications into /home/tomwell/.wine/drive_c/Program Files/name_of_application/name_of_application.exe. Then, you can create a launcher with the command ```
wine "z:\home\tomwell\.wine\drive_c\Program Files\name_of_application\name_of_application.exe"
```

---

### Post by tomwell on 2005-11-24
Aysiu,

Thank you for that, would it be possible that you repeat that with the knowledge that i am a total noob... LMAO 

1st what is wine run??
Do i just create folders like you have written ie hom/tomwell/.wine/drive_c...etc etc?? 

Sorry for my ignorance...!!

Peace 

Tom

---

### Post by aysiu on 2005-11-24
[QUOTE=tomwell]
1st what is wine run??[/quote] *Wine-run* simply means *run by Wine*. It's sort of like saying *homemade*--i.e., *made at home*.

> 
Do i just create folders like you have written ie hom/tomwell/.wine/drive_c...etc etc?? Thanks for clarifying what you do and don't understand. I'm going to move you to Absolute Beginners--that's where I assume people know pretty much nothing. It's hard for people to target helpful responses otherwise.

/home/tomwell is your directory where you have settings and files. Your settings are stored in a bunch of hidden folders that start with **.** For example, the hidden folder settings for Firefox would be stored in /home/tomwell/.mozilla. So, the settings for Wine are stored in /home/tomwell/.wine.

To see hidden files, press Control-H.

Within the /home/tomwell/.wine folder, you'll see something that looks like a mini-replica of a Windows environment. So, if you install any programs (by double-clicking the setup.exe and choosing to run it with Wine) and they ask you where you want to install the program, the default will probably be C:\Program Files\name_of_program. You should change that to be z:\home\tomwell\.wine\drive_c\Program Files\name_of_program.

I'm assuming your Ubuntu username is tomwell. It may be harryberry or theman or something. Substitute your real username for what I'm calling tomwell.

---

### Post by peanut butter on 2005-11-24
after you install wine you should go to terminal and type ```
winecfg
``` there you can tell it what version of windows to act like.:)

---

### Post by tomwell on 2005-11-24
All Understood Aysu...

Is Z:/ the name of the drive i use for my machine?? why is it Z:/

Thank you for all the help!

Peanut Butter, I have run winecfg and set it up to run like XP thanks for that!!!

Peace

Tom

---

### Post by aysiu on 2005-11-24
Wine kind of makes your Ubuntu computer temporarily speak Windows-ese.
So instead of drives being /dev/something-or-other, they're C:\ (Windows) and Z:\ (Ubuntu). Or, at least on my machine, it's Z:\

---

### Post by tomwell on 2005-11-24
Thats what i was wondering...its z on my machine so i guess its to do with being ubuntu... dont know if that makes any sense... lol (i am in the ab beginner forum now so i guess its ok...)

it's working fine now so all is well...

Peace

Tom

---

### Post by tomwell on 2005-11-24
OMG i have to post again am on post 66 and am kinda supersticious.... dont wanna be a nuissance but sorry...

Peace 

Tom

---

