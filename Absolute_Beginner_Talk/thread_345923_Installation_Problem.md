---
title: "Installation Problem"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2007-01-24
I want to install Ubuntu on my system.Infact I dont want to use any disk partitioner.I want to remove windows completely and install Ubuntu. The problem is whenever I run the partitioner the system hangs. The installation procedure always starts with the partitioner. Plz Help

---

### Post by drascus on 2007-01-24
hmm... This is an interesting problem. What version of ubuntu are you trying to install? and what kind of computer are you running it on? I would suggest making sure that you have a good iso file. If that checks out. I would also make sure that while you are installing that you tell the program to format the hard drive not partition it. As partitioning will create space while formatting will erase your windows program. 
~drascus~

---

### Post by vivin_west on 2007-01-24
I am using a pentium 4 processor,256MB RAM. The CD is from Ubuntu(Shipped). I have installed Unbuntu on 5 systems previously. I dont know why my system is hanging during partition. Can I install through terminal window

---

### Post by vivin_west on 2007-01-24
Version is Dapper Drake

---

### Post by vivin_west on 2007-01-24
How do I tell to format the hard drive and not partition it.

---

### Post by drascus on 2007-01-25
Ok after you click the install icon. you should be asked to select your language.
Next step it will ask you to select your location.
next you will be asked to specify you time zone do this as well
Next you will be asked to specify your keyboard type.
Then it will ask you information to set up your account. 
The you will be brought to the partitioner window. There will be an option should be the second one down that says Erase entire disk:
Select this  by clicking in the circle to the left. 
click forward.
It will the tell you that proceeding will erase all disk information. select install 
that should be it. 
beyond that its a different issue I don't understand. 
~drascus~

---

### Post by vivin_west on 2007-01-25
I really appreciate your help Thanks.But I have a more complex problem. After entering up my account information the gnome partioner program starts running. Here the system hangs.So I dont even get the erase disk option. I want to know how to format the disk or install using terminal window.I dont see any other solution.So Any suggestions?

---

### Post by Patrick-Ruff on 2007-01-25
this is weird.

looks like you're gonna have to touch the TERMINAL!

I forgot the command though, it was rm -f or something like that. 


someone with better memory then I do reply to this please.

---

### Post by Patrick-Ruff on 2007-01-25
another option, I remember there being a nuke disc somewhere around the web 

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

dban boot and nuke. basically, a nuke disc, you boot that baby up and type "autonuke" it'll erase everything and you shall install ubuntu.

good luck to you

---

### Post by drascus on 2007-01-25
here is a link to a free program that will format the hard drive for you. 
[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by Patrick-Ruff on 2007-01-25
did you not notice my solution for him? 

you gave him shareware, I gave him an open source hard drive formatter that uses linux to format, no free/professional crap.  you needn't give people lame solutions just to get a post count.

---

### Post by confused57 on 2007-01-25
> **vivin_west said:**
> I am using a pentium 4 processor,256MB RAM. The CD is from Ubuntu(Shipped). I have installed Unbuntu on 5 systems previously. I dont know why my system is hanging during partition. Can I install through terminal window

You might have better luck with the Alternate install cd...256MB system RAM may not quite be enough to install using the live cd.  
The gparted live cd is a great partitioning tool(small download), but I'm not sure if prepartitioning would help:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I'll look through my plethora of "Bookmarks" & see if I can find anything to help you install with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=218036&highlight=legacy](http://www.ubuntuforums.org/showthread.php?t=218036&highlight=legacy)
[http://www.ubuntuforums.org/showthread.php?t=313406](http://www.ubuntuforums.org/showthread.php?t=313406)

---

