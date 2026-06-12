---
title: "Very Basic Script needed"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Naegling23 on 2006-08-29
Ok, so I know nothing about how to write a script, so I am hopeing that someone can walk me through this so that I can learn for the future.  (I'm running kubuntu dapper i386)

In order for my mp3 player to work, I need to run the following command in konsole: easyh10 -Un -on /sda1/media

I would like to automate this so that I can run it by clicking a link on my desktop rather than having to type the command everytime I need to sync my mp3 player.  The problem is that I have almost no idea how to go about automating this process.  Can anyone help me out?  Thanks.

---

### Post by Tomosaur on 2006-08-29
Right click on desktop > Create Launcher, paste that command into the 'command' section, then fill out the rest as you desire.

---

### Post by johnnymac on 2006-08-29
Don't need a script.  Just do the following:

1.  Right Click on your desktop (assuming Gnome) and create a launcher (I think that is what it is called.
2.  Add an icon or whatever you want for the icon
3.  For the command put this:

```

xterm -e easyh10 -Un -on /sda1/media

```

or possible just this

```

easyh10 -Un -on /sda1/media

```

Now you have a clickable icon on your desktop to execute it...

---

### Post by Daishiman on 2006-08-29
Well, there's a couple of great little apps for what you're looking for. If you prefer KDE dialogs, try kdialog. If you're into GNOME, try zenity. The help and man pages are more than enough to show you the basic dialog types available, and they allow you to use the output of those dialogs within a script.

Hope this helps.

EDIT: tutorials.
KDialog: [http://developer.kde.org/documentation/tutorials/kdialog/t1.html]("http://developer.kde.org/documentation/tutorials/kdialog/t1.html")

Zenity forum post: [http://ubuntuforums.org/showthread.php?t=148677]("http://ubuntuforums.org/showthread.php?t=148677")

---

### Post by Tomosaur on 2006-08-29
> **Daishiman said:**
> Well, there's a couple of great little apps for what you're looking for. If you prefer KDE dialogs, try kdialog. If you're into GNOME, try zenity. The help and man pages are more than enough to show you the basic dialog types available, and they allow you to use the output of those dialogs within a script.

Hope this helps.

EDIT: tutorials.
KDialog: [http://developer.kde.org/documentation/tutorials/kdialog/t1.html]("http://developer.kde.org/documentation/tutorials/kdialog/t1.html")

Zenity forum post: [http://ubuntuforums.org/showthread.php?t=148677]("http://ubuntuforums.org/showthread.php?t=148677")

Overkill :O

Seriously, just make a launcher :/

---

### Post by Naegling23 on 2006-08-29
wow, I got up to get a cup of coffee and came back with 4 responses.  Great forum, im going to be here more often now, get ready for all of my n00b questions!

Thanks for the help, I'll try it out when I get home from work.

---

### Post by Naegling23 on 2006-08-30
hmmm, so none of this seems to work.  When I right click on the desktop, I dont have an option to create a launcher.  I get create new (text file, etc), run command (cant save it though.  Im running kde, so it might be a little different, any suggestions?

---

### Post by fritz_monroe on 2006-08-30
How about this?  I'm not a scripter, so it may not work.

```
#!/bin/bash

xterm -e easyh10 -Un -on /sda1/media
```

Put that in a text file.  Do a 

```
chmod <filename> +x
```

That look about right to the experts here?

---

### Post by John.Michael.Kane on 2006-08-30
If this is being done under KDE try to right click in the desktop-> select new->file-> link to application, and fill the proper fields.

---

### Post by Naegling23 on 2006-08-30
How about this? I'm not a scripter, so it may not work.

Code:

#!/bin/bash 
xterm -e easyh10 -Un -on /sda1/media



After I posted the most recent reply, I started banging around while waiting for a responce.  Thats what I ended up figuring out, well, except for the xterm -e anyway.  It seems to work without the xterm -e.  I tried it out with another script to launch mythtv, and it worked.  So what is the xterm -e, and is the term necessary (well, I guess its not, is it necessary in some cases would be a better question)?

---

