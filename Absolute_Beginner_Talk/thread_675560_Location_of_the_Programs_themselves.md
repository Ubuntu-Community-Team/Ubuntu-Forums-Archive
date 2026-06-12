---
title: "Location of the Programs themselves"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by OZFive on 2008-01-22
I am a bit new to all this and am configuring my system to my liking and am making program launchers in Xubuntu.  I have been successful with Firefox, Thunderbird, Open Office Writer, and Gimp.  But I am having a devil of a time locating the programs Pigdin and AbiWord to complete my launchers.  I have looked all over!  Can someone help me find these sneaky files?

---

### Post by spiderbatdad on 2008-01-22
those can be added to the panel as launchers by right clicking on the icon applications launchers found in the menus. Also you can search using the search tool...System>>Places>>Search for files...and select file system rather than /home. Generally the command for launchers is the program name, I think, and not necessarily the path/to/program.

---

### Post by LarryJ2 on 2008-01-22
You can try  

sudo find / -name pidgin  

and 

sudo find / -name abiword

---

### Post by smwny on 2008-01-22
One way to find programs is to open a terminal and type "which <Program Name>" (no quotes). which pidgin returns /usr/bin/pidgin.

---

### Post by OZFive on 2008-01-23
> **spiderbatdad said:**
> those can be added to the panel as launchers by right clicking on the icon applications launchers found in the menus. Also you can search using the search tool...System>>Places>>Search for files...and select file system rather than /home. Generally the command for launchers is the program name, I think, and not necessarily the path/to/program.

I have been looking for the search tool for a long time and have not found it yet.  I looked in your instructions to find it and it is not there in the xfce menu I went to the xfce menu>> system>> the options I have in there are.....

Add/Remove
Language Support
Network
Restricted Drives Manager
Services
Shared Folders
Software Sources
Synaptic Package Monitor
System Monitor
Time and Date
Update Manager
Users and Groups


any idea where Places and the search for files tool is at?

---

### Post by mcduck on 2008-01-23
You can find the executable of a program using the 'which' command. For example, running 'which firefox' will return '/usr/bin/firefox'.

Anyway, pretty much always the executable of programs for normal users are located in /usr/bin.

---

### Post by Odd-rationale on 2008-01-23
This thread might interest you...
[http://ubuntuforums.org/showthread.php?t=620215](http://ubuntuforums.org/showthread.php?t=620215)

---

### Post by stalkingwolf on 2008-01-23
try Places > search for files

---

### Post by hyper_ch on 2008-01-23
and mostly you just need to enter the name of the program as the executable will reside in one of the system paths.

so just use

```

pidgin

```

as starter

---

