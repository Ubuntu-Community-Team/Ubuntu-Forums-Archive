---
title: "How did I transfer a virus??"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2006-10-16
I transferred some .doc format files to a friend's computer. He informed me that my files were infected and created a problem on his windows XP. 

how can i transfer viruses to XP since I don't seem to be affected (ubuntu loveya for it) . And how can I stop transferring viruses to windows run PCs(or stop catching them for that matter)

---

### Post by weird_c00kie on 2006-10-16
with word documents it's easy to carry viruses in the form of macros. maybe you're infected tooa nd you just haven't realised :p

have you considered investing in a virus scanner for your XP? heheh

---

### Post by maneesh77 on 2006-10-16
well i don't think windows viruses can do any damage to me here in my fortress of Linux  but is there anyway to [COLOR="DarkOrange"]detect/stop[/COLOR] them from going to windows PC's ( i don't know why my friend doesn't have a antivirus)

---

### Post by JonahRowley on 2006-10-16
There are also virus scanners for Linux.  Albeit one that looks for Windows viruses, but it should be what you want here.  I've tried it, have no idea if it's suitable for desktop use (I think it's primary use is mail servers), etc, but its name is ClamAV.

Of course, you could always copy and paste the content of the document into a newly created document as well.  Or, if the document is only intended to be read, export to PDF.  I export to PDF whenever possible, not everyone has office and I don't want to bother them installing the word reader, but virtually everyone has Acrobat Reader (or another PDF program).

---

### Post by Perfect Storm on 2006-10-16
Other:
F-prot - [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)
AVG - [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

AVG free edition for linux can only detect viruses though. I recommend F-prot.

---

### Post by CaveRat on 2006-10-16
> **Artificial Intelligence said:**
> Other:
F-prot - [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)
AVG - [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

AVG free edition for linux can only detect viruses though. I recommend F-prot.

Yes and Avast also has a command line Linux scanner. Also free.

---

### Post by ScrewItFix on 2006-10-16
Hi maneesh77,
you wrote :
"I transferred some .doc format files to a friend's computer. "

 1. Q - was the .doc created by you ? 
 2. Q - did you use Linux / Open Office to create it ?
 3. Q - is it possible that you used (may be by mistake) a       Macro-Code for Open-Office ?

If so - it is possible that Windows-AntiVirus dedect a MacroVirus in the Document even if there is no , dune to an OpenOffice-Macro. 

If you get the .doc from someone , it is most likly that there is a WindowsMacroVirus in sight. So you better give the alert to the one who give you the file.

brgts Screw It Fix

---

### Post by 3rdalbum on 2006-10-16
Don't forget that some people don't know what a virus is, and they assume that any error message they get is caused by a virus.

If you created them in OOo but forgot to save them specifically as .doc (i.e. you put the .doc extension on the end, but saved them as OpenDocument), then Word will give an error message when you try to open them.

---

### Post by jd65pl on 2006-10-16
> with word documents it's easy to carry viruses in the form of macros. maybe you're infected tooa nd you just haven't realised :razz:

have you considered investing in a virus scanner for your XP? heheh
 		 	 		 		 		 		 		 	 		 			 			 			 			 				[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=1622702")

I don't think open office is capable of executing VBA macros as default, I'm sure one would at least need a plugin and to enable it for the code to be executed.

---

### Post by PriceChild on 2006-10-16
Personally i use clamav.

I use clamtk as a graphical frontend, availiable via the repos:
```
sudo apt-get install clamtk
```

---

