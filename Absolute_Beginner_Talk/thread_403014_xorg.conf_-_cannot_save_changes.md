---
title: "xorg.conf - cannot save changes"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by christinanilsen on 2007-04-06
freshly installed, ubuntu wouldn't boot up completely - i had the same graphical interface failure that others have observed here (cursor appears in an otherwise blank screen).  

trying the 'fix' noted in these logs, but i know very little and have a slight problem ...

i opened the terminal and added the following to the Device section:

Option "BusType" "PCI"
Option "DmaMode" "None"

Now I want to save my changes to xorg.con but am getting an error message: permission denied.

any idea how i can save these changes, or if there is a better way to solve my root problem?

i'm working on an IBM T20 Thinkpad

thx

---

### Post by Razorback on 2007-04-06
Are you using sudo or gksudo before launching your editor?  You need to do that to have permission to make the change.

i.e.; sudo gedit /etc/X11/xorg.conf

---

### Post by tiendn on 2007-04-06
U try :
"sudo gedit /etc/X11/xorg.conf"

---

### Post by Maestro23 on 2007-04-06
Are you using gedit?

> gksudo gedit /etc/X11/xorg.conf

or sudo gedit

File/Directory is owned by root.  Need sudo in front of your command.

RootSudo: RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by christinanilsen on 2007-04-06
thanks  :) 

the 'fix' worked using:

"sudo gedit /etc/X11/xorg.conf"

---

