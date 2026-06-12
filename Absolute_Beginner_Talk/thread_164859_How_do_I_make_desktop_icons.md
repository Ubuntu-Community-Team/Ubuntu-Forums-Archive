---
title: "How do I make desktop icons?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by babel on 2006-04-23
I am very new to Ubuntu :)  

Generally, I would like to know if one can make desktop icons for various programs.

Specifically, the first one I want to make is an icon that would show me a window containing all drives (harddrive, CD drives, etc).  I guess I'm looking for something similar to Windows' "My Computer".  Is there a way I could go about this?

babel.

---

### Post by ncappel1 on 2006-04-23
One oway of doing this is to pull down the "system" menu and simply dragging the filesystem icon onto the desktop. 

Also, you can go into applications-->system tools-->configuration-->then once in there navigate to apps-->nautilus-->desktop and activate the buttons you want. 

sorry, if this is unclear it's because 'm not at my ubuntu box, I will check it and edit it when I get home.

---

### Post by steve.horsley on 2006-04-23
right-click the desktop and add a custom launcher. The command is **nautilus**.

---

### Post by babel on 2006-04-23
Thanks!

It appears that ncappel1's method will put system icons (computer, trash) and steve.horsley's method will put on icons for individual programs.

I've tried the first to put computer & trash icons on the desktop.

I'll play around with the second, though it appears that I'll have to first find where a particular program is located (might be difficult?) and then find within the folder the particular icon that launches the program (even more difficult?).

---

### Post by babel on 2006-04-27
Let's suppose that in addition to the Firefox "globe" icon in the upper left corner of my screen, that I wish to make a desktop icon for it as well.

I right-click the desktop and create a launcher.

Now all I have to do is browse to Firefox.

But where is Firefox ?

I looked, but couldn't find it.

---

### Post by ComplexNumber on 2006-04-27
>  I looked, but couldn't find it. go to the command line and type in 'which firefox'. that should give you the location. it should be in /usr/bin or /usr/local/bin. note that its sometimes called mozilla-firefox.

---

### Post by babel on 2006-04-28
This may sound silly, but where do I find the "command line"?

I went to Places > Search for files and searched in "file system" for "which firefox".  It came up with nothing.  I had it search for "firefox" and it came up with several dozen entries.  I certainly don't know which one to link to.

Is this the "command line" I should be using, or is there something else?  If it is the command line I should be using, is there a particular name within the list of dozens of Firefox entries that I should be linking to?

---

### Post by babel on 2006-04-28
OK, I found it !

I went to /usr/bin and found a Firefox icon with an arrow, which looks like the "shortcut" icon from Windows.  I opened a desktop launcher and browsed to this icon and was able to create a functioning desktop icon for Firefox. 

Questions**:** 
(1) am I correct that this is simply a shortcut to Firefox?  
(2) I am still interested in knowing where I can find the command line.

Thanks,

babel .

---

### Post by ncappel1 on 2006-04-28
you can access the command line by going into applications-->accessories-->terminal

inaddition: when you create a launcher, it is not necessary to browse to the comman in /usr/bin. if you know the command you can just type that in. the commands are usually part of the titles.
for example: firefox command=firefox
gedit=gedit
vim=vim
gaim instant messanger=gaim
gimp photo and image editing=gimp

get it?

---

### Post by babel on 2006-04-29
[QUOTE=ncappel1]you can access the command line by going into applications-->accessories-->terminal

inaddition: when you create a launcher, it is not necessary to browse to the comman in /usr/bin. if you know the command you can just type that in. the commands are usually part of the titles.
for example: firefox command=firefox
gedit=gedit
vim=vim
gaim instant messanger=gaim
gimp photo and image editing=gimp

get it?[/QUOTE]

Yes, sort of :-| , although, it seems like I must know which folder in File System my target is in before I can type in a program to search for.  For instance, I opened a Create Launcher on the desktop & browsed to file system > /usr/bin.  I right-clicked for options then left clicked on "open location" & typed in "firefox".  It came up with nothing.  I typed in mozilla-firefox and it also came up with nothing.  I also did the same in /bin and found nothing.

Any suggestions to steer me in the right direction?

---

### Post by Joey French on 2006-04-29
Maybe this will simplify things for you. It is not necessary to have a target file/folder to get firefox running. You simply need to give the command "firefox" in a shell (terminal), make a shortcut for it on the desktop (using the command "firefox") or whatever app you know the name of. If you are just needing to make an icon on your desktop to launch firefox, right click on the desktop, create new link to application, then simply type "firefox" into the command dialog. You shouldn't need to do any searching, except in the case that you just want to know where everything is. In that case, you should do some reading [here]("http://www.pathname.com/fhs/pub/fhs-2.3.html"), which will help you understand the filesystem (if it's the first time you are seeing it). 

Good luck!

---

### Post by babel on 2006-04-29
It worked !

I was able to, for example, open Evolution Mail by applications > accessories > terminal and typing "evolution" into the terminal.

I was then able to create a desktop shortcut to Evolution by right-click on desktop > create launcher, then typing evolution in the Command area.

Thank you also for the link to the Filesystem Hierarchy Standard webpage.

Thanks ! :)

---

### Post by Joey French on 2006-04-29
No problem at all. Good luck!

---

### Post by jms830 on 2006-05-09
for the most part, anything in /usr/bin you can just launch by typing the name of the file anywhere in terminal (or as a command for a custom launcher). For instance "/usr/bin/firefox" could be launched by simply typing the command

```
firefox
```

so in your custom launcher, type "firefox"  (no quotes) for where it says Command.

If you want to add a desktop icon, a quick way to get the information about what to put for the custom application info is to go to Applications then right click and click "add this launcher to panel" for any program, then right click on the icon that got added to your panel and click "properties".

---

### Post by Clay85 on 2006-05-09
[QUOTE=babel]I am very new to Ubuntu :)  
 I guess I'm looking for something similar to Windows' "My Computer".  Is there a way I could go about this?
[/QUOTE]

If you go to Places/Computer I think that's what you're looking for.

---

### Post by salambander on 2007-08-24
A very, very quick and easy way to make all the desktop icons that would normally appear on windows appear on an ubuntu desktop (such as My Computer, My Documents, Trash etc) is the following:

1. Firstly, you must NOT be root for this, or it won't work.
2. In the terminal/command line, type **gconf-editor**
3. <enter> (a window will pop up)
4. In the panel on the left, click **apps** (applications on some machines) -> **nautilus** -> **desktop**
5. On the right, you will see a panel saying "computer_icon_name" blah... Tick the boxes for the icons you want to show up and they'll appear immediately on your desktop. That's it!

If you want to rename your icons, for instance, to "sally" then double-click the name in the Values column. Set the type as "string" for text names. 

Hope this helps anyone who has been having trouble with this!

---

