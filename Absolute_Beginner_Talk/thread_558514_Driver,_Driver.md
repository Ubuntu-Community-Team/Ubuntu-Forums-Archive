---
title: "Driver, Driver"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by group256 on 2007-09-24
Hi everyone
Im absolutely new to ubuntu. Yesterday I was just trying to install my graphic card driver on my system, So I just found a help over the net that was explaining how to install Nvidia or Ati. Im using Ati so I went through the steps, Entered some commands in terminal and then I edited one file(dont remember what the file name was) Then I was told to restart the machine. After restarting, after the bar is filled(when ubuntu is booting) then a message shows up and tells me that "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly . Would you like to view the x server output to diagnose the problem?" So can someone please help me to solve my problem. And afterwards what should I do to install my ati driver???

Thank you

---

### Post by alienexplorers on 2007-09-24
Log in at the terminal prompt.  Run:
> sudo dpkg-reconfigure xserver-xorg
when done restart and reboot

---

