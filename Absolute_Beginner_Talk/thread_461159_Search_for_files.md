---
title: "Search for files"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by gspaulding on 2007-06-01
In Feisty, I cannot get the ¨search for files¨ tool to look in subfolders.  It seems to only look in the specified starting folder.  For example, I triple boot with XP and Vista and have the utility that allows windows to see ext3 partitions.  If I use windows to search for ´bookmarks.html´ on my Linux partition it finds files in my home folder and in the .mozilla/firefox/... folder below.  When I am in Ubuntu and start in my home folder, it finds the file there, but does not find the file in the subfolder.  I have not found a setting to say ´look in subfolders´ or something to that effect.  Can someone please explain how to make the search tool look at subfolders?  Thanks in advance.

---

### Post by Cypher on 2007-06-01
I know you probably want a GUI response, but I don't have one of those..

From the terminal you could do
```

find . -name "bookmarks.html" -print

```
and that will search every folder starting in the current directory.

Have you tried Beagle, BTW?

---

### Post by gspaulding on 2007-06-01
Thanks for the response.  Yes, I was hoping there was a non-terminal way similar to the search capabilities in win.  I'll look at Beagle as an alternative and report back.

---

### Post by lbriner on 2007-06-01
In Konqueror - the KDE browser/explorer, if you type "locate:bookmarks.html" in the address bar, it searches the whole directory structure from /.

It is not case sensitive and will show one folder result if there are lots of the same named files under a common directory.

Luke

---

### Post by gspaulding on 2007-06-01
OK, I used Synaptic Package Manager and found and selected Beagle.  I was informed I needed 2 libraries also, which I accepted.  I marked for install and applied.  Said it installed.  Where is it?  I can´t find any reference to a Beagle application.

To Luke:  Can I use Konquerer with gnome?

---

### Post by bobplano on 2007-06-01
yes you can install any kde/xfce app on ubuntu. for beagle i don't use it, but try typing "beagle" (without the quotes) into a terminal

---

### Post by krisfrajer on 2007-06-01
You should be able to install konqueror from the repositories. If you are not sure if you  have konqueror in your system, open a terminal window and type "konqueror &".

---

### Post by gspaulding on 2007-06-01
Well, I tried the commands in terminal for both ´beagle´ and ´konquerer &´ but received a response of bash: beagle: command not found.
Do installed programs not go onto a menu?  If I install a program do I have to run it from terminal?  Sorry for my ignorance, but I´m obviously learning linux.

---

### Post by Cypher on 2007-06-01
When I install Beagle, it went into Applications->Accessories if I'm not mistaken. Also, try logging off and logging back in and you might see a Magnifying glass in your top-bar which is another way to load up Beagle..

---

### Post by krisfrajer on 2007-06-01
If you are in your "desktop", right click on it and create a new launcher...

---

### Post by gspaulding on 2007-06-01
All right, thank you.  I logged out and back in and had the magnifying glass.  Clicked it and went to ´Desktop Search´.  I checked the ´Applications´ ´Accessories´ and found ´Search´ which opens the same program.  I was looking for ´Beagle´, but that´s not the name it uses on the menu.  Again, thanks for the help.  Installed programs do go to the menu, but the name may not be what you expect.

---

### Post by Ek0nomik on 2007-06-01
Beagle works beautifully.  :)

Just have it index your files.  You have to choose what directories you want it to make "note" of.

---

