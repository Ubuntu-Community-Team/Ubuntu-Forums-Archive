---
title: "[SOLVED] Linux Terminal"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by linux.convert on 2007-09-07
I recently exchanged Windows Xp for Ubuntu 7.04 on my laptop. My question is about the Terminal. where can I find a list of keywords? what kind of language is it based in? and what all can I use Terminal for?

---

### Post by ThrobbingBrain66 on 2007-09-07
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by mendingo84 on 2007-09-07
you can use terminal for virtually everything ;) . it uses scripting language, which is interpreted by a number of interpreters, but for ubuntu the standard interpreter is bash.

---

### Post by codesplice on 2007-09-07
The terminal really is a great thing.  Coming from the Windows side, you may or may not have used the DOS-based Command Prompt.  For the average user, there's not really any reason to.

On Linux, though, the terminal is extremely versatile.  You can do pretty much everything you could possibly want to do from the terminal, and once you learn the essential commands it will often be far quicker than doing it the graphical way.  

For example, the only time that I use the graphical Aptitude package manager is when I don't know what I'm looking for.  If I at least have an idea of what package I need, it's a lot quicker to just do it via a ```
sudo apt-get install XXXXXXX
```.

Just take some time to get to know the terminal, and make full use of the man command and the --help switch.

```
man nmap
``` for example would give you likely more information about the nmap scanning utility than you would ever care to know, while ```
nmap --help
``` would just print the usage syntax and commonly used flags.

Use these help functions to find out about any command or program you need to use.

---

### Post by Bothered on 2007-09-07
Two commands that really help to get you started are:

apropos [keyword] - gives a list of commands that match the given keyword
man [command] - displays a manual for the given command

Those two commands can be used to learn how to use almost all the others. If you want more details on them, type "man apropos" and "man man" in a terminal.

---

### Post by Terl on 2007-09-07
Here is another nice reference about terminal commands:  [Command Reference]("http://www.oreillynet.com/linux/cmd/")  Just click on a command and it will tell you what it does etc.

---

### Post by ronmarley1 on 2007-09-07
> **ThrobbingBrain66 said:**
> [http://www.linuxcommand.org/](http://www.linuxcommand.org/)
+1

---

### Post by kevinlyfellow on 2007-09-07
Also, you can auto-complete commands by hitting tab once if it's the only option, hit tab twice if you want to see all possible options. (just a helpful hint).  You can get a list of EVERY possible command by hitting tab twice without putting in anything.  That won't really help you much since you will have between 1000-3000 commands.

---

### Post by SpiritIsReality on 2007-09-07
howdy

ya, what they said.
great place.

trails

---

### Post by vanadium on 2007-09-07
I just want to emphasize Bothereds post

> 
apropos [keyword] - gives a list of commands that match the given keyword
man [command] - displays a manual for the given command


The problem usually is that you do not know what command to look up to do something. There, apropos is the life saver. For example, apropos mp3 will tell you all commands that know about mp3 files with a brief explanation. Once you have the name of the command, man <command> gives you detailled info. I advise you: man pages are something you will need to get used to. In the beginning, they are tough reading!

---

### Post by linux.convert on 2007-09-07
awesome

---

### Post by asmoore82 on 2007-09-07
but not even the mighty Linux can help where you really need a manpage ...

```
~$ man women
```

:lolflag:

---

### Post by ThrobbingBrain66 on 2007-09-08
I think you forgot to complete the joke:)
```
~$ man women
No manual entry for women
```
:(

---

### Post by JohnCub on 2007-09-08
alas man man does work.  :(

---

