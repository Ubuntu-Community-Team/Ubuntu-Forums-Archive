---
title: "Help! Installing Issues - Missing Programs"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by robin3513 on 2007-03-31
I'm very new to linux and ubuntu, and I'm very confused on how to solve this issue.

I am trying to install Dungeon Siege II, and I looked up some info on the Internet, only to find out that I needed to install Wine.  So, I go to Applications, Add/Remove Programs, then installed Wine.  Or so I thought.  It is no where to be found, searching the hard-drive for it gave 0 results.  I have had this issue before with trying to install Step Mania.  

Updating and restarting the computer was no help. 

Any ideas on how to install Dungeon Siege II would be great.  Thank you.

---

### Post by Maestro23 on 2007-03-31
You need to enable additional repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Also some more links to help with Ubuntu:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Welcome to Ubuntu and Good luck.

---

### Post by robin3513 on 2007-04-01
I have those repositories, and the add/remove programs software and the synaptic package says that wine is installed, yet I can't find it, or how to install Dungeon Siege II.

---

### Post by Maestro23 on 2007-04-01
> **robin3513 said:**
> I have those repositories, and the add/remove programs software and the synaptic package says that wine is installed, yet I can't find it, or how to install Dungeon Siege II.

MIght help: [http://www.ubuntuforums.org/showthread.php?t=397750&highlight=wine+installation](http://www.ubuntuforums.org/showthread.php?t=397750&highlight=wine+installation)

---

### Post by WW on 2007-04-01
In your original post, your referred to Wine with a capital W.  You may already know this, but just in case you didn't, the actual command is wine. (Linux commands and the linux file systems are case sensitive.)

There will not be a menu entry for wine anywhere. wine is a command line program.  If you have a windows program to run, say program.exe, you would run it by starting a terminal, and entering the command
```

$ wine program.exe

```
I don't know anything about Dungeon Siege II.

---

### Post by robin3513 on 2007-04-01
Sweet! I got Wine to work, thank you.

Except for another problem :P  Dungeon Siege II is now asking for the CD key, and then comes up with an error, saying I need to insert the CD in to the drive  (which has been there from the beginning)...  Hunh What??

After all this mess, I about to light the whole thing on fire and have a BBQ.

---

### Post by robin3513 on 2007-04-01
More info:  It says that " Cannot load PidGen.dll "

Also, I believe my computer is possessed.  Even my programmer friends agree with me...  

So this might just be my comp acting out against me... again...  I really ought to burn it.

---

### Post by zvacet on 2007-04-01
Type in terminal
```
winecfg
```
and you will have wine configured.After that type
```
winefile
```
and you will see wine.Good luck.

---

### Post by macogw on 2007-04-01
You probably need a no-cd crack.

---

