---
title: "eXeSMS install to Ubuntu 12.04"
date: 2012-08-21
forum: Australia Team
---

### Post by pushbike06 on 2012-08-21
I recently installed eXeSMS (other sys) onto a user login of Ubuntu 12.04 Desktop.
The eXeSMS zip file was unpacked in the Downloads folder of the Admin directory (Home/"Admin name").
From the user login I then used Gnome Panel to create a link to the eXeSMS.jar file in the Admin Downloads folder.
This provided a Launch Panel icon that works(one click)and a Desktop icon that works (double click).
Well, except for one little glitch.
First activation of either icon produces an error panel to display with a reference to "unable to access database file".
Subsequent activation eXeSMS works.
[COLOR=#ff8000]Q1: Can anyone explain why this happens and is there a fix?[/COLOR]

Also reading that some time ago a complaint to the ISP (Exetel) was made about double billing occurring for some messages that were not exceeding the 160 char limit.
I think I have experienced this (14c instead of 7c) but I cannot check the length of the sent message.
[COLOR=#ff8000]Q2: Is double charging an outstanding problem?[/COLOR]
[COLOR=#ff8000]Q3: Are sent messages stored somewhere for retrieval?[/COLOR]
[COLOR=#ff8000][COLOR=Black]Thanks[/COLOR]
[/COLOR]

---

### Post by pushbike06 on 2012-08-22
Double billing SOLVED,
Subsequent to my earlier post I found the location of my stored SMS messages and did a char count on the particular message and it exceeded 160 chars.
My apology to Exetel, my ISP, :oops:

---

### Post by pushbike06 on 2012-08-23
Further to my post,
eXeSMS is a free 3rd Party Java application supplied by my ISP.
Where should an application such as this be located.
Could I create a "My Apps"  directory in /usr/bin to locate such apps and scripts.

---

### Post by ikt on 2012-08-25
Very nice, what does exesms do?

---

### Post by pushbike06 on 2012-08-27
The script enables SMS to be sent from a PC. It is provided by EXETEL (ISP) for their clients.
Single or group SMS can be sent from a pop up panel on your Desktop.
It works but I dont think I have installed it properly, I think it should have been installed in usr/local/bin.
I have been unable to drag the app and associated files from its installed location, "Admin"/Downloads.
I intend to download the zip file again but this time I will configure Firefox to target usr/local/bin Dir. then extract it and change the command path in the Users Desktop icon to the usr/local/bin Dir. which is one of the environment paths.

---

