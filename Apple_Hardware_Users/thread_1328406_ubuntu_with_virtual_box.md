---
title: "ubuntu with virtual box"
date: 2009-11-16
forum: Apple Hardware Users
---

### Post by xtreampb on 2009-11-16
ubuntu in a virtual machine

Hey everyone.  I am completely new to linux.  I heard it was great for programming so i thought about giving it a try.  I am using virtual box (developed by sun microsystems) because i am doing a lot of cross platform programming in C++.  I would love to use virtual box so that i can easily share code between OSs.  Is it possible to run this in a virtual box.  I have all the system requirments set up like it needs to be.  It boots off the iso no problem, but when i select to install it, or boot without installing, i get this window.  Is there any advice out there for me.

~xtreampb~

---

### Post by doas777 on 2009-11-16
well, go to your virtualbox menu and ask it to "Install Guest Additions"
then use Ctrl + Alt + F1 to bring up a cli shell.  does it come up?
if so, use the 'cd' command to navigate to /media/cdrom
then run ls to show the files in there.
here is mine:
```
karmic:/media/cdrom$ ls
32Bit        VBoxLinuxAdditions-amd64.run    VBoxWindowsAdditions.exe
64Bit        VBoxLinuxAdditions-x86.run      VBoxWindowsAdditions-x86.exe
AUTORUN.INF  VBoxSolarisAdditions.pkg
autorun.sh   VBoxWindowsAdditions-amd64.exe

```

since I have a 32bit guest, I want to run.
 ```
sudo sh ./VBoxLinuxAdditions-x86.run
sudo reboot
```


hopefully that will work out for ya

---

### Post by xtreampb on 2009-11-16
ok i got it all installed and everything
when i got to install virtual box guest additions, it mounts the iso image and i can navigate the cd through the GUI of ubuntu.  When i find the file and begin to install it, i click on run, it begins to install and then after 4 lines of dots '.' then it says that it needs to be ran with admin rights.  What you told me to do is working now, but it just concernes me that i have granted myself all the priveliges but i still need to go to the terminal to install this software.  I don't want to have to do this each time i wan't to install something like this. :/

---

### Post by doas777 on 2009-11-16
well, the easiest way to do it through the gui, is to hit alt + F2, and enter 
```
gksu nautilus
```. this will open a nautilus window, running as admin. be very careful with that window.

or, you can invoke it from the command line like 

sudo sh /media/cdrom/VBoxLinuxAdditions-x86.run

gksu and sudo are commands used to make an action run as an admin. gksu is for the gui, and sudo for the command line.

---

