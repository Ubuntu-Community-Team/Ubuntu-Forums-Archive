---
title: "terminal, console, shell, command line ... all the same?"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by robanicek on 2005-12-05
I'm quite new to linux, using Kubuntu. In the past I just did some simple file editing on a UNIX server, but I'm a bit confused about these terms:
 
terminal
console
shell
command line
screen session

Is it all the same? Can I use all of them for example do some sudo dpckg commands? Can I screw up something using the wrong one?

Is there somewhere a comprehensive beginners guide onthis topic?

THNX!

 Nabor

---

### Post by frodon on 2005-12-05
Yes they are all the same exept for screen session, here is a nice guide about the terminal commands, you should read it : [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by atoponce on 2005-12-05
[quote=robanicek]I'm quite new to linux, using Kubuntu. In the past I just did some simple file editing on a UNIX server, but I'm a bit confused about these terms:
 
terminal
console
shell
command line
screen session

Is it all the same? Can I use all of them for example do some sudo dpckg commands? Can I screw up something using the wrong one?

Is there somewhere a comprehensive beginners guide onthis topic?

THNX!

 Nabor[/quote]

Almost.  When talking to fellow *NIX Nerds, when mentioning one of the above, they will know what you are talking about.  Specifically, however, here are the definitions of each:

_Terminal_- technically, this is a station where a user can interact with on operating system.  Think of terminals as being physical boxes that you would sit at.  These terminals could be dummy terminals, relying on a netwok connection to receive data, or smart terminals holding their own OS.  Gnome refers to using the command line as the Terminal, being the name of the software.  KDE calls the exact same thing Konsole.  You can refer to typing commands "in the terminal", however, and everyone will know what you are talking about.

_Console_- This is the specific command-line interface that the user uses to interact with the system.  It should be mentioned that in the older days, we commonly referred to boxes as consoles.  But as far as I am aware, "console" means primarily the text-based command line.  This term is identical to "command prompt" or "command line" as well.

_Shell_- Shells are different, and probably the most confusing for the Linux newbie.  Although pulling up a text-based console can be referred to as the shell, this specifically isn't the case.  The shell is how the user interacts with the command line, not the command line itself.  There are various shells for the command line interface in the UNIX and Linux world.  The C-Shell (csh) developed after the C programming language, the Bourne Shell (sh), the Bourne Again Shell (bash) definitely the most popular, the Korn Shell (ksh) not  named after the metal band, and many others.  Each shell has its strengths and weaknesses.  I prefer using the bash shell when I pull up a command line.  Csh would be my second preference.

_Command line_- See the definition for "Console" above.

_Screen session_- The screen session refers to a user logging in and how long they have been using the system.  For example, if you were to use PuTTY on a Windows box to SSH into a remote Linux server, from the time you login to the time you log out would be referred to as you screen session.  Launching a screen session can happen locally on your box or remotely to a server.

Although these are the specific definintions, you will in no doubt notice that these terms are used interchangably on these forums and throughout the web.  Generally, they can all mean pulling up a command line to execute a command.

---

