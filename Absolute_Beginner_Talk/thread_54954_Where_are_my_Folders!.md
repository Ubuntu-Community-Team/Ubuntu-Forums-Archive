---
title: "Where are my Folders!?"
date: 2005-08-06
forum: Absolute Beginner Talk
---

### Post by Epyon on 2005-08-06
alright this is really becoming annoying.

like when i am in /home/edgar i see my desktop and folders.

now Azureus and other programs that i have installed so far are supposldy in /home/edgar but they are not

to access them i have to do /home/edgar/.Azureus this is kinda annoying.

like why dont i see a folder for Azureus in /edgar? why isnt it visable?

---

### Post by aysiu on 2005-08-06
Because it's hidden. Go to View > Show Hidden Files.
Can't you change the default save directory for Azureus?

---

### Post by bored2k on 2005-08-06
[QUOTE=aysiu]Because it's hidden. Go to View > Show Hidden Files.
Can't you change the default save directory for Azureus?[/QUOTE]
 Yes you can, just like you would on any other Operating System.

---

### Post by Epyon on 2005-08-06
is there a way so that no folders are ever hidden from me?

---

### Post by aysiu on 2005-08-06
[The Azureus User Guide](http://azureus.sourceforge.net/doc/Azureus%20User%20Guide.htm) says:

Either you want to save the file in a default directory (that you can specify in Configuration > File (see 3. a.)) or you may want to save it elsewhere.

---

### Post by bored2k on 2005-08-06
[QUOTE=Epyon]is there a way so that no folders are ever hidden from me?[/QUOTE]
 [QUOTE=aysiu]Because it's hidden. Go to View > Show Hidden Files.[/QUOTE]
Just leave that option on. You would eventually (actually, really quickly) get annoyed by seeing dozens of folders you don't need to see on your $HOME, cluttering it up and making you use the scrollbar to access your now "hidden" folders, but if that's what you want, rock _on. Just keep in mind that deleting one of those folders will delete config files and possibly temp files from what you just erased.

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=Epyon]is there a way so that no folders are ever hidden from me?[/QUOTE]

Well.....once you tell it to show hidden folders, I think it does for good.

---

### Post by aysiu on 2005-08-06
[QUOTE=Epyon]is there a way so that no folders are ever hidden from me?[/QUOTE] In Nautilus (the file manager), go to Edit > Preferences and select Show Hidden and Backup Files. As stated before, though, you can get annoyed pretty quickly with all the many folders you see. I'd just change the default save folder in Azureus.

---

### Post by Epyon on 2005-08-06
nah, i kinda dont want my OS hiding files from me lol

---

### Post by TravisNewman on 2005-08-06
It's not that it's secret or anything, its just settings that you'll rarely need. If you do need one, make a symlink to it so you can see it. For example, I have a symlink in my home dir called "azureus-downloads" that links to .azureus/downloads so that I don't have to see the settings until I want them.

---

