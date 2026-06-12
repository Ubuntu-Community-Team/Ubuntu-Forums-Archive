---
title: "Install Program"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by axxel on 2007-01-23
Hi, i just installed ubuntu 6.10, downloaded the updates, Is there an install program i need when i try to install this game i get this error

                    Error: No Suitable Application
Cannot open /Home/kc/Desktop/wolfet.exe:No
Application suitable for Automatic Installation is 
Available for handling this kind of file.


Any suggestions? Thanks

---

### Post by taurus on 2007-01-23
Looks like you try to install Windows game!  You need to install wine first before you can run or install any Windows program/game in Linux.

---

### Post by geokok1981 on 2007-01-23
Linux does not use .exe files. Exe's are for windows only. Try to find a linux version 
of your application. If it does not exist you could try to run your exe with wine but from what you say I assume you are a new user so I don't know if you could work with wine.

I have one advice for you. To make the most of linux forget anything you know about windows.

---

### Post by shane634 on 2007-01-23
Looks like that file was wolfet. The good news is that there is a linux version of enemy territory and it works fine. Search these forums for enemy territory lots of how to's.

---

### Post by axxel on 2007-01-23
Thanks, i tryed the linux version, now im getting this error

Could not open the file /home/kc/Desktop/et-linux-2.55.x86.run.
gedit has not been able to detect the character coding. Please check that
you are not trying to open a binary file.
Select a character coding from the menu and try again.

Suggestions?
I tryed to run it from command and it say permission denied, and yes im completely new to linux obiously, this is my first day and im lost. Thanks

---

### Post by teitunge on 2007-01-23
when you try to run it from terminal, use the command sudo in front of it. you will be asked for a password, and just type your root-password. you will not be able to see the characters, but that is not your keyboard not working, just the fact that its a password..

hope that helps :)

---

### Post by rocknrolf77 on 2007-01-23
Type ```
sudo sh
``` and drag the file into the terminal.

---

### Post by axxel on 2007-01-23
Alright i tryed that, and it still goes to gedit and gives the message


Could not open the file /home/kc/Desktop/et-linux-2.55.x86.run.
gedit has not been able to detect the character coding. Please check that
you are not trying to open a binary file.
Select a character coding from the menu and try again.

Is there a program that i could download maybe, or should i try to re-download the file?
I really appreciate the help, thanks

---

### Post by taurus on 2007-01-23
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 et-linux-2.55.x86.run
sudo ./et-linux-2.55.x86.run
```

---

### Post by axxel on 2007-01-23
Alright i tryed that code and it was working but i get this error now

Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/kc/.setup5654: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1



Thanks

---

