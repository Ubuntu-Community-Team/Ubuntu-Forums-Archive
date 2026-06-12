---
title: "where does wine install stuff?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-11
SOLVED

if i just hit install and it installs to the normal c:\\ area, where do i find that to open the program i just installed?

---

### Post by visik7 on 2007-04-11
~/.wine/drive_c/

---

### Post by useResa on 2007-04-11
From the [Wine User Guide]("http://winehq.org/site/docs/wineusr-guide/index") (paragraph 4.1):
> 
	Some programs install associated control panel applets, examples 	of this would be Internet Explorer and QuickTime. You can access 	the Wine control panel by running in a 	*terminal*:       
	 $ wine control
      	which will open a window with the installed control panel 	applets in it, as in Windows.       
	If the application doesn't install menu or desktop items, you'll 	need to run the app from the command line. Remembering where you 	installed to, something like:       
	 $ wine "c:\program files\appname\appname.exe"
      	will probably do the trick. The path isn't case sensitive, but 	remember to include the double quotes.  Some programs don't 	always use obvious naming for their directories and EXE files, 	so you might have to look inside the program files directory to 	see what was put where.
Hopes this helps you start your program.

---

### Post by locke.dragon on 2007-04-11
thanks for the help guys.  i got it figured out.  sorta.  :P

---

### Post by Patrick K on 2007-04-11
Open the file browser. In Home Folder hit "ctrl+h" this will make hidden files visible. Scroll down and you will find a directory named ".wine" (the dot makes it a hidden dir). This is the wine folder. Click on it. You will see a dir named "drive_c" this is the fake "C" drive wine installed. Open it and you will fine a "Program Files" and "windows" directory. Your installed programs are in the "Program Files" dir.

---

### Post by the8thstar on 2007-04-15
Quick question here:

Is it possible to copy the entire c:\windows directory contents to ~/.wine/drive_c/windows, assuming that my Windows XP partition is mounted and accessible from Ubuntu. If so, how do I do it?

I mean, if that works, all I need to do is transfer the files from c: to ~/.wine/drive_c to have a dormant MS Windows system. Then, Wine comes around and wakes up the components I need, right?

---

### Post by vanadium on 2007-04-15
Probably this would not work. During installation, programs also have settings in the registry. Moreover, some settings/paths/etc. might be different on your Windows system than under Wine. Just re-install programs under Wine.

As a general advise: avoid using Windows programs to the maximum extent. In the majority of cases, there is excellent Free Software available that can fill the gap.

---

### Post by the8thstar on 2007-04-15
Hmm... I might have known it wouldn't be that easy. :(

Wine developers, that one is for you: can Wine load up a virtual registry in the memory?

Another question: is there a way to load Ubuntu AND Windows at the same time and switch between the OS with a command like Alt + Tab?

---

### Post by locke.dragon on 2007-04-17
i don't know about your question, but if you really want it answered, i suggest you make a new post.  more people will answer.  at the moment, your question is only being seen by the select few who run across it in this unrelated thread.  :P  just a suggestion!

---

### Post by the8thstar on 2007-04-21
Done. Thank you **locke.dragon**.

---

