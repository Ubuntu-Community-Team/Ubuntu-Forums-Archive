---
title: "How do I log on as root?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-07-07
What I need to do is log on as root so that I can move files around to where I want them.


Currently trying to install phpsysinfo and I can't as I dont have write privilages to /var/www


And no I do not want to start changing privilages as I eventually want to keep the security as it is, AFTER I have set it up!!!


I just don't see the need of spending ages trying to find CLI commands and how they work when I have a nice GUI I could use!


](*,)

---

### Post by araz on 2006-07-07
Why dont you just type "sudo nautilus" and use nautilus as a SuperUser?

---

### Post by richbarna on 2006-07-07
> **Scorpuk said:**
> What I need to do is log on as root so that I can move files around to where I want them.


Currently trying to install phpsysinfo and I can't as I dont have write privilages to /var/www


And no I do not want to start changing privilages as I eventually want to keep the security as it is, AFTER I have set it up!!!


I just don't see the need of spending ages trying to find CLI commands and how they work when I have a nice GUI I could use!


](*,)

You CAN use the GUI.
...after you type this into the console.
> gksudo nautilus

That will open the file browser with root priveledges.

---

### Post by Scorpuk on 2006-07-07
sweet, tnx peeps

CLI to get GUI ;)

---

### Post by richbarna on 2006-07-07
> **araz said:**
> Why dont you just type "sudo nautilus" and use nautilus as a SuperUser?

GKSUDO nautilus in Gnome
KDESU konqueror in KDE

You don't use sudo with graphical programs.

---

### Post by Scorpuk on 2006-07-07
And it works

[http://scorpuk.plus.com/phpsysinfo](http://scorpuk.plus.com/phpsysinfo)


:-D

---

### Post by picallo on 2006-07-07
"sudo passwd root"

---

### Post by 3rdalbum on 2006-07-07
I advise putting that command into a launcher on your top panel or a menu, so then you won't need CLI to get GUI! (it's also more convenient).

---

### Post by slimdog360 on 2006-07-07
this sort of question should really be a sticky. It comes up everywhere, hell even I asked it once.

---

### Post by bluenova on 2006-07-07
> **picallo said:**
> "sudo passwd root"
This is not recommended.

---

### Post by richbarna on 2006-07-07
> **slimdog360 said:**
> this sort of question should really be a sticky. It comes up everywhere, hell even I asked it once.

Or, maybe people can use the forum search ie, "root permission" or "sudo".

I find it quicker than starting a new thread ;)

---

### Post by Scorpuk on 2006-07-07
> **3rdalbum said:**
> I advise putting that command into a launcher on your top panel or a menu, so then you won't need CLI to get GUI! (it's also more convenient).

How would I do this? :)

---

### Post by araz on 2006-07-07
Here's a guide to help you.
[http://ubuntuguide.org/wiki/Dapper#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus]("http://ubuntuguide.org/wiki/Dapper#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus")

---

### Post by Scorpuk on 2006-07-07
nm worked it out :) 


right click desktop and and create launcher, put gksudo nautilus in the command part and hey presto.


tnx every1  :D

---

### Post by T700 on 2006-07-07
> **richbarna said:**
> Or, maybe people can use the forum search ie, "root permission" or "sudo".

Amen.  We really don't need more sticky posts that few read.  I find it annoying enough to have to scroll past 1/2 a page of them already.

Paul

---

