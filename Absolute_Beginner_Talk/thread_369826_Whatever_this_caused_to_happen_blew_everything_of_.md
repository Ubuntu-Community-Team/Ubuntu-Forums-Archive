---
title: "Whatever this caused to happen blew everything of the left end of the top panel"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by housekid on 2007-02-25
I was in the process of changing the  permission on the media/cdrecorder to:
	$ sudo chmod 777 /media/cdrecorder

Instead I used "gksu" and I got this error:

	jar@jar-desktop:~$ gksu chmod 777 /media/cdrecorder
	jar is not in the sudoers file.  This incident will be reported.
	
	Failed to run chmod '777' '/media/cdrecorder'
	The underlying authorization mechanism (sudo) does not allow you
	to run this program. Contact the system administrator.

Whatever this caused to happen blew everything of the left end of the top panel.



I have added the Menu Bar back to the panel but now the Administration menu on the System menu
is all but wiped out. The Admin. menu only has these items:
	Device Manager
	Network tools
	Printing
	System log
	System Monitor

I think I just found out that I can not mix these two commands "sudo and gksu"!
But, I haven't been able to get my Administration Menu completely back. HELP!!

---

### Post by zvacet on 2007-02-25
You create common user(or whatever the right name is),and you don´t have administrator privileges anymore.It is good thing to do for security reasons,and I advice you to run your Ubuntu in that mode as far as is posible.To do what are you trying to do change user(red button on the top right)and you will be root(administrator).After finishing your work back to common user for security reason.I hope this is halpfull.

---

### Post by alienexplorers on 2007-02-25
You might have to run gksudo instead of gksu.

---

### Post by housekid on 2007-02-25
The red button on the top right was blew away also. 
I understand the need for the security, I just don't think I was applying it correctly.
So, how will that get back all the missing panel/menu items?

---

### Post by housekid on 2007-02-25
By running gksudo will it re-install the missing panel/menu items?

---

### Post by moshuptrail on 2007-02-25
I think you have logged in as root and you have root's default panel.
I suggest logging out, and back in with your normal user ID.

Perhaps the two commands you are mixing should be sudo, and gksudo?
sudo to execute the following command in text mode as root
gksudo to execute the following command in graphics mode as root

gksu - don't use it.  period.  It will only get you in trouble.

---

### Post by housekid on 2007-02-25
I logged out and back in as user. That is how I was logged in when all the items were blew
from the top panel. I have tried to log in as root in the past but Ubuntu will only let me log in
as a user form one of the two user accounts I setup in the beginning.
Now what? 
Soooooooooo, I must have to do a re-install to get everything back on the panels as they were!!!!

---

### Post by moshuptrail on 2007-02-25
Well, you can right-click on the panel, select "add to panel" and start re-building all the stuff.
It will take about half an hour.

Or, complete re-install. (45 mins?)

Or, try to figure out what went wrong:  If we knew where Panel saves it's configuration we might figure out if the previous file is gone, or what.  I'm not sure, myself.  

'lil help?  Where does Panel save it's config?  Anyone?

---

### Post by aidanr on 2007-02-25
i think in ~/.config/menus and i also see lots of undo files there so maybe rename the last undo file?

ps. i'm not sure if thats for xfce or gnome, i have both installed

---

### Post by picpak on 2007-02-25
Try running

```
cp .gnome2 .gnome2.bak
rm -r .gnome2/
```,

that should reset your configuration. After that, log out and in.

---

### Post by aidanr on 2007-02-25
eh, might want to back that up before removing it :-s

---

### Post by picpak on 2007-02-25
Good idea. I've done it so many times that I've stopped caring whether I lose anything or not.

---

