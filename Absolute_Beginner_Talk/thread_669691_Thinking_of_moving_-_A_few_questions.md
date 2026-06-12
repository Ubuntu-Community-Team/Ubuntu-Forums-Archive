---
title: "Thinking of moving - A few questions"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by DuckFury on 2008-01-16
So I've been thinking about it for a while, and I got the change to try it on the Live CD and my friend's laptop. It looked good but I still have a few questions about Ubuntu. I'll probably install it if I still love it after I get those answers, but it's going to wait untill I get my own computer...


  1-Is it easy to share a network with a Windows user?

  2-Is there an equivalent to Windows' Batch Files for the Terminal? And can you assign Keyboard shortcuts to those files?

  3-How do you create shortcuts for a program and place in , for exemple, on the desktop?

  3-Tar.gz : What are these files?

  4-Are there different terminal commands for different Linux distro? (In case Ubuntu does not fill my need and I need to switch to another distro)

  5-I'm using very often the Command Prompt and Batch files of Windows, so I'm planning to learn using the Terminal. Is there some Terminal Commands Database or a Terminal Tutorial (for basic commands) somewhere?


Thank you in advance for reading and answering these questions

PS: Sorry if I made mistakes while writing, english isn't my mother-language

---

### Post by lgambett on 2008-01-16
*1-Is it easy to share a network with a Windows user?*

In general terms, yes. You can browse directories on the Windows PCs, share folders, use shared printers, share printers, etc....

[I]2-Is there an equivalent to Windows' Batch Files for the Terminal? And can you assign Keyboard shortcuts to those files?
[/I]Yes, Linux batch files are way more powerful than Windows ones. But... I do not know how to assign keyboard shortcuts to these files.

*3-How do you create shortcuts for a program and place in , for exemple, on the desktop?*
Right click over the desktop, then create shortcut.

*3-Tar.gz : What are these files?*
Compressed files more or less like zip files in Windows

*4-Are there different terminal commands for different Linux distro? (In case Ubuntu does not fill my need and I need to switch to another distro)*
No, commands are the same for every distro (and more or less the same for Unix, Mac OS X, AIX, HP UX, Solaris...)
[I]
5-I'm using very often the Command Prompt and Batch files of Windows, so I'm planning to learn using the Terminal. Is there some Terminal Commands Database or a Terminal Tutorial (for basic commands) somewhere?
[/I]
Try to Google bash commands, you will find a lot of links.

---

### Post by kellemes on 2008-01-16
For GNU/Linux "batchfiles"
[http://bashscripts.org/](http://bashscripts.org/)

---

### Post by kebes on 2008-01-16
1. It's possible to network with Windows computers, yes. ("Easy" is a subjective term!) You can share a folder from Linux (using a program called SAMBA) and Windows computers will see a normal network drive.

2. Yes, in Linux they are called "shell scripts" (or bash files). The capabilities of the Linux commandline are quite sophisticated, so there is practically no limit to what you can do in a script. And yes you can assign Keyboard shortcuts (I usually add the script as a menu item and then bind a keyboard shortcut to that).

3. "tar.gz" is a compressed file format, just like a "ZIP" file in Windows. In Linux you can right-click on them to uncompress them.

4. 99% of the commands are the same for every distro (and actually most of the commands will work on BSD, Mac OS X, and UNIX...). Each distro will have a few commands that are different, but it usually doesn't take very long to learn the differences.

5. There are tons of online tutorials. The commandline is often called "the terminal" or "the console" or "virtual terminal" and so on. The Linux scripting environment is usually "bash" and the scripts you make are "shell scripts".

If you search for those terms (like "bash tutorial" or "linux shell script tutorial"), you'll come up with lots of tutorials. These ones look pretty good:
[http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)
[http://www.usd.edu/~sweidner/lsst/](http://www.usd.edu/~sweidner/lsst/)
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)


Hope that helps! Good luck and have fun!

---

### Post by wolfen69 on 2008-01-16
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by DuckFury on 2008-01-16
Wow, that was a quick answer!
Thanks for the help :)

---

### Post by stchman on 2008-01-16
> **lgambett said:**
> *1-Is it easy to share a network with a Windows user?*

In general terms, yes. You can browse directories on the Windows PCs, share folders, use shared printers, share printers, etc....

[I]2-Is there an equivalent to Windows' Batch Files for the Terminal? And can you assign Keyboard shortcuts to those files?
[/I]Yes, Linux batch files are way more powerful than Windows ones. But... I do not know how to assign keyboard shortcuts to these files.

*3-How do you create shortcuts for a program and place in , for exemple, on the desktop?*
Right click over the desktop, then create shortcut.

*3-Tar.gz : What are these files?*
Compressed files more or less like zip files in Windows

*4-Are there different terminal commands for different Linux distro? (In case Ubuntu does not fill my need and I need to switch to another distro)*
No, commands are the same for every distro (and more or less the same for Unix, Mac OS X, AIX, HP UX, Solaris...)
[I]
5-I'm using very often the Command Prompt and Batch files of Windows, so I'm planning to learn using the Terminal. Is there some Terminal Commands Database or a Terminal Tutorial (for basic commands) somewhere?
[/I]
Try to Google bash commands, you will find a lot of links.

Linux calls shortcuts "symbolic links".  To create a symbolic link you can do this via one of two ways.

1.  Use the command ln -s
2.  Middle mouse click and drag the icon to where you need a shortcut placed.

---

### Post by thelatinist on 2008-01-16
Tar.gz files are, as others have said, compressed archives.  It is important to know, however, that if a Linux program is distributed in a tar.gz that tar.gz probably contains source files (the uncompiled code for the program) which you will have to compile before installing.

And, while the comparison of tar.gz is broadly correct, there are some important differences.  Tar archives preserve many attributes of files such as user access permissions which can be very important in *nix OSes and which zip archives do not preserve.  The trade-off is speed: zip files compress each individual file and save them in an archive; tar.gz files are first archived and then zipped, resulting in somewhat better compression but much slower extraction of individual files.

---

