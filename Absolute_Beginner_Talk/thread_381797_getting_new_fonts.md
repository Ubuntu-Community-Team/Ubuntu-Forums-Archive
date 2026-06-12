---
title: "getting new fonts"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by 006rocks on 2007-03-11
Can someone explain how to install new fonts? What should the format be? i found a couple cool fonts off of defont.com but im not shure if they are the right format.

---

### Post by Linux Lover on 2007-03-11
if you want to install true type fonts (.ttf) then you may just copy those fonts to the /usr/share/fonts/truetype/

or you may make a directory under truetype dir and copy fonts there. Do not forget to refresh the font cache or restart the machine after copying the fonts.

---

### Post by 006rocks on 2007-03-11
it wont let me. it says i cant because its restricted or something...how do i change the settings so i can add stuff to it?

---

### Post by qamelian on 2007-03-11
Open Nautilus and make sure the location bar is displayed. In the location bar, 
type ```
fonts://
``` and press the enter key. This will take you to the fonts folder for your user. Copy the fonts you want to use into this location. 

To make fonts available to all users, use the sudo command in front of your copy command to copy files to the location mentioned in previous posts. Enter your password when it is requested.

---

### Post by 006rocks on 2007-03-11
i know where to put them but it wont let me. its restricted. how do i unrestrict it?

---

### Post by diatribe on 2007-03-11
All you have to do is copy the .ttf files to /home/your_login/.fonts or you can type:

 cp font_name.ttf ~/.fonts

hope this helps

Edit:  if you want to enable the globally you will have to use the sudo command before attempting to copy them to usr/share/fonts/truetype, it would look like

sudo cp font_name.ttf /usr/share/fonts/truetype

then type your password when it prompts for the password

2nd edit:  this is all done from console in case you didn't realise

---

### Post by 006rocks on 2007-03-11
i know where the folder is. when i try to copy the font into it, it tells me failed because permision is denied or somthing like that. what do i do to make it let me put the fonts into the fonts folder?

---

### Post by diatribe on 2007-03-11
use the commands I gave you.  You have to use sudo because regular users cant write to /usr/share.  you must use sudo or login as root to write to this directory.  I will walk you through it now though.  I will assume a login name (what you type to get into ubuntu) is ubuntu.  assuming your font that you want to use is on your desktop, you would type from the console:

cd /home/ubuntu/Desktop
sudo cp font_name_here.ttf /usr/share/fonts/truetype
now it will ask for your password, type in your password

then it will copy them for you

if you have more problems email me your yahoo or aim id at [email]51kfysbnxmw8j7v@golfilla.info[/email] and I will walk you through it

---

### Post by 006rocks on 2007-03-11
its saying command not found or somthing...i just sent an email to u that has my aim id...so yea...

---

### Post by vinchi007 on 2007-03-11
> **006rocks said:**
> it wont let me. it says i cant because its restricted or something...how do i change the settings so i can add stuff to it?

most likely try your command with "sudo" in front of it. 
Example: 
$sudo cp /media/sda1/WINDOWS/Fonts/*.ttf /usr/share/fonts/truetype/

Where /media/sda1 -> is the drive where your windows is mounted

---

### Post by 006rocks on 2007-03-11
figured it out ^^

---

