---
title: "Remove Launchable Link"
date: 2013-02-01
forum: Any Other OS
---

### Post by clearasmud on 2013-02-01
I have been using _Linux for Non Geeks_, by Rickford Grant to install and learn about Linux.
I created a launchable link for a game called pyWings as instructed in the book.
The instructions are as follows:
 
1. In the terminal, type [FONT=Courier New]**[FONT=Palatino Linotype]cd /usr/local/bin[/FONT]** [/FONT][FONT=Tahoma]and press [FONT=Times New Roman]ENTER[/FONT]. [/FONT]
[FONT=Tahoma]This puts you in [/FONT][FONT=Tahoma]one of the searchable bin folders.[/FONT]
2. Type [FONT=Courier New]**[FONT=Palatino Linotype]su[/FONT]** [/FONT][FONT=Tahoma]and press [FONT=Times New Roman]ENTER[/FONT]. [/FONT]
[FONT=Tahoma]Type root password and press [/FONT][FONT=Times New Roman]ENTER.[/FONT]
3. Type 
**[FONT=Palatino Linotype]ln -s /home/username/LocalApps/pyWings/pywings.py pywings[/FONT]**
[FONT=Tahoma]and press [/FONT][FONT=Times New Roman]ENTER.[/FONT]

 
The problem I'm having is that in step three, I should have substituted my own username where it says [FONT=Palatino Linotype]**username**[/FONT] in the command, but since I didn't, it doesn't work and won't let me just put in the correct command because a link already exists. 
**[FONT=Palatino Linotype]ln: 'pywings' File exists[/FONT]**
**[FONT=Palatino Linotype][root@ubuntu bin][/FONT]**
 
What are the correct commands to remove the incorrect link so that I can start over?
 
The book came with installation cd's which installed: [FONT=Palatino Linotype]**Fedora Core release 1 (Yarrow)**[/FONT]
[FONT=Palatino Linotype]**Linux 2.4.22-1.2115.nptl**[/FONT]

---

### Post by xenopeek on 2013-02-03
Change the -s to -sf, where the f options means the command should remove existing destination files.
```
[FONT=Palatino Linotype]ln -sf /home/username/LocalApps/pyWings/pywings.py pywings[/FONT]
```Or you could first remove the destination file yourself. You do that with the rm command.
```
rm [FONT=Courier New][FONT=Palatino Linotype]/usr/local/bin/pywings[/FONT][/FONT]
```The Introduction to the Command Line ([link]("http://en.flossmanuals.net/command-line/")) may be a good reference to get somewhat more comfortable on the command line.

---

