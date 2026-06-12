---
title: "how to use WINE"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Arc Owner on 2006-04-04
I want to use WINE to play some old Win98 war games. I've installed WINE, but I don't get exactly how I'm supposed to use it. Can someone help me? 


Thanks,
Arc Owner

---

### Post by hollywoodb on 2006-04-04
first run 'wine'
this will create wine's default files & folders in your home directory

second run 'winecfg'
make sure things look good, if you're not sure then leave the settings alone

third, cd to the directory that contains setup.exe or whatever it is to install your program, and run 'wine setup.exe' (obviously replace setup.exe with what you want to run)

fourth, assuming the game installed correctly, it will have installed in ~/.wine/drive_c/  ... from there it looks like a default C:

fifth, keeping this in mind, run 'wine <path to game>.exe'
"wine ~/.wine/drive_c/Program\ Files/Starcraft/Starcraft.exe" for example.
you can create menu launchers like that as well.

there's lots of great info @ [winehq]("http://www.winehq.com") and [frankscorner]("http://www.frankscorner.org")

---

### Post by Arc Owner on 2006-04-04
Thanks, most of it worked great, but when I launched the setup.exe file from the cd I received this error-

C:\windows\temp\GLC174d.tmp File Not Found


What does this error mean?

---

### Post by Arc Owner on 2006-04-04
Never mind, I made a stupid mistake. I forgot to login as root 'sudo -s'.](*,)

---

### Post by Scooby_Doo_102 on 2007-10-30
Hi, I have set my pc up for dual boot, and I want to use wine to use programs from xp on ubuntu 7.4. I have the latest version of wine but I can't find the file in the program files list. Can you please help me. Thanks.

---

