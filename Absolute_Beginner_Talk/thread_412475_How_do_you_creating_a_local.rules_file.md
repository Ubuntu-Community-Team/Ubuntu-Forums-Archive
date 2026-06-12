---
title: "How do you creating a local.rules file??"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Dotbond on 2007-04-18
Hi. Very new to Linux. 
I have just installed 6.10 and have a dial-up modem which i found out was a Intel536EP type.
I downloaded the driver for it and have it just about installed according to the HowTo page. 
The last part of the install relates to creating a file  /etc/udev/rules.d/10-local.rules
How do you do that?
I have opened up the text editor and typed in the lines required and when i go to Save As it says i don't have permission.

---

### Post by PurplePenguin on 2007-04-18
You need to open up the text editor with sudo (that is "sudo nano nameofdocument" or "gksudo gedit nameofdocument").  You don't have write permission to the /etc directory, but sudo (the command that gives you superuser/root power) does.

EDIT: [Here's a bit of a permissions primer for you]("http://www.psychocats.net/ubuntu/permissions") and a bit of an explanation of [Ubuntu's use of sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Dotbond on 2007-04-18
Thanks.
I almost got it right but i Saved it from the dropdown menu at the top. I didn't know what the /\ ment. Do know tho, Control key.
I now have a 10-local.rules.save file with a red box and a white x inside it at the top right hand corner.
I tried making another file but i just made a file called 10-local.rules.save.1 with a red box.
How do i delete these files? :confused:

[IMG]http://i156.photobucket.com/albums/t38/Dotbond/Screenshot.png[/IMG]

---

