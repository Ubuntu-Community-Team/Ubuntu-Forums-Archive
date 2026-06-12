---
title: "Open a Folder as Root"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by brownjl on 2006-07-19
Hello,

I am a fairly new user of linux, been playing with truecrypt an app I used on windows, I have got it so I can mnt a truecrypt volumne to /mnt/vault but I can not change the permisions of the folder or files within its probabbly because its a truecrypt volume.

Anyway I have created a link to it on my desktop "ln -sf /mnt/vault /home/brownjl/Desktop/vault" 

Is there a way I can then open the folder as su in the gui? and then say edit the spreadsheets files within or drag and drop files etc? 

Cheers for any help,

James

---

### Post by OrganicPanda on 2006-07-19
well you could just run the window manager as root so for gnome that would be: "sudo nautilus" but theres an excellent script around these forums for right clicking and opening a directory in root mode, i'll try and find it, its very useful.

---

### Post by scxtt on 2006-07-19
try **gksudo nautilus** if you're using gnome or **kdesu konqueror** if you're using KDE - and enter your user password ...

---

### Post by Malac on 2006-07-19
Right click on Desktop and choose create launcher
Enter in command. 
 "gksu nautilus [SIZE=2]*/path/to/folder*[/SIZE]"
or
 "gksudo nautilus [SIZE=2]*/path/to/folder*[/SIZE]"

Without the quotes and replacing [I][SIZE=2]/path/to/folder
[/SIZE][/I]Nautilus can be replaced by konqueror or whichever file manager you are using
If you are using kubuntu then replace gksu with kdesu.
and gksudo with kdesudo.

It may be worth looking into the differences between "su" and "sudo" as they do different things.
Hope this helps.

---

### Post by OrganicPanda on 2006-07-19
ok i found the script i was wafting on about, it can be found [Here ]("http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here") to install first get a terminal going then create a new document with gedit in your nautilus-scripts directory (gnome this is) like so:

```

sudo gedit ~/.gnome2/nautilus-scripts/root-nautilus-here

```

then paste the affore mentioned script into that file so it looks like:

```

#!/bin/sh
# root-nautilus-here
# opens a root-enabled instance of a nautilus window in selected location
# requires sudo priviledges and gksudo, which may involve security risks.
#Install in your ~/Nautilus/scripts directory.
#
# Placed in the public domain by Shane T. Mueller 2001
# Fixes provided by Doug Nordwall
#
# 2004.04.18 -- keith@penguingurus.com - Added gksudo usage to provide popup
#               password window if sudo has expired.  Line only echos got
#               root to std output.  But gksudo updates your sudo access
#               privs, so running nautilus with sudo will succeed
#               without asking for a password.


foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI

```

save that file and exit gedit, go back to the terminal and make that file exacutable with:

```

sudo chmod 777 ~/.gnome2/nautilus-scripts/root-nautilus-here

```

(note i dont know the correct chmod value for this but 777 works)

and then you can navigate to any directory in nautilus, right click, goto scripts then 'root-nautilus-here' which will prompt you for a password if you havent put one in recently and then open a root nautilus in that location, even works on special folders like the desktop.

enjoi

---

### Post by Crosbie on 2006-07-19
I think Automatix includes an option for installing this right-click script too.

---

### Post by brownjl on 2006-07-19
Thank you for all your help that worked a treat, I ended up creating a launcher on the Desktop for that folder, and also created that nautilus script incase I need it in the future!

Cheers again,

James

---

### Post by Malac on 2006-07-19
Your Welcome :D

---

