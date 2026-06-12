---
title: "wine - access denied- wtf?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by velozoom on 2007-07-25
On Fiesty fawn (7.04)- trying to install a program using wine off of a windows installer cd.  Navigating to the cdrom and trying to run the .exe returns the error "Access Denied".  I tried this at the command line-

root$wine filename.exe 

and was given this series of messages
```

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

As far as I can tell, my X-server is running fine although I am using a restricted Nvidia driver on my laptop.  I have installed programs with wine before without a problem.  WTF, over?

thanks for any comments

---

### Post by trak87 on 2007-07-25
I don't have an answer, only a question. Why do you run a wine (windows) program as root? Seems like a bad idea.

---

### Post by velozoom on 2007-07-25
trying to install the app, not just run the program.  I've tried Linux-based web development tools but I am addicted to the colour-coding and embedded ftp of Dreamweaver.....want it on my laptop!  ;)

---

### Post by Acglaphotis on 2007-07-25
Try winedoors. It installs this stuff without going thru the hassle. [http://www.getdeb.net/app.php?name=Wine-Doors]("http://www.getdeb.net/app.php?name=Wine-Doors")

---

### Post by velozoom on 2007-07-26
thanks but I'd like to sort out what's wrong with the wine installation/system.......I've removed and re-installed wine with no change in the situation

---

### Post by trak87 on 2007-07-26
Firstly, not all programs will run in wine. Check the wine website app database to see if your particular package (Dreamweaver?) will actually run before attempting to install: [http://appdb.winehq.org/](http://appdb.winehq.org/)

Second, I'm not a wine expert, but everything you install via wine will be located under your home dirctory in the .wine/ directory. I still see no need to become root to install a windows program in wine. It's not as if windows libraries are going to share the same space as Linux libraries.

---

