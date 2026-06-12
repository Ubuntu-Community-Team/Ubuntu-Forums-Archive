---
title: "command lines"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-12
80% of linux command work only in command line
could you give me some links to sites that you could search for "what do u want to do" and it gives you the command ?
I prefer that the site would explain why and what the command do excactly

p.s
were do you know all the command lines from ??? :confused: 

thanx ahead !!!

---

### Post by matrooswolf on 2006-06-12
Try this for starters:
[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)

Big guide here too, not especially about commands, but you can learn a lot:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Good luck!

---

### Post by aysiu on 2006-06-12
There are command sites out there that will list a whole bunch of commands.

[quote=MAXDDARK]were do you know all the command lines from ???[/quote] I would have to say, though, that I learned commands mostly from just hanging out on the forums.

I see people's problems, and I see the proposed solutions.

When someone says > Make a backup copy of your sources.list file ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` I just figure *cp* must be *copy*, which it is.

It never hurts to ask questions either, like "What does *mv* mean?"

---

### Post by elemental666 on 2006-06-12
try this: [http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/index.html](http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/index.html)

---

### Post by MaximB on 2006-06-12
thanx you are quick...
BTW - will there be any GUI for the command lines ? like windows does ?
or is there yet ?

---

### Post by elemental666 on 2006-06-12
[QUOTE=MAXDDARK]BTW - will there be any GUI for the command lines ? like windows does ?
or is there yet ?[/QUOTE]

I'm not sure I understand your question.  In Ubuntu (Gnome) there is a terminal which is like start->run->cmd in windows...   Kubuntu(KDE) has Kterm, etc etc.

Linux also provides several ttys.  X runs in tty7, tty1-tty6 are available to you by default.  to switch hit ctrl-alt-f# where #= the tty you want.

so for example, boot up ubuntu and your in x (on tty7), to get a full screen terminal session hit ctrl-alt-f1, and log in.  To get back to x hit ctrl-alt-f7.

personally I use the terminal app tho.

If this isn't what you were asking then please restate your question.

---

### Post by MaximB on 2006-06-12
elemental666 - thanx but I didn't understand what is tty1-7 ???
and I think you didn't understand my question
what I meant was that most of the commands in linux are done via command line
and I'm asking for GUI (graphic user interface)
cuz there are TONS of commands to learn and it's very complicated

---

### Post by mostwanted on 2006-06-12
Yes, there are GUIs for most things.

---

### Post by MaximB on 2006-06-12
how ? were ?

---

### Post by elemental666 on 2006-06-12
ttys are kinda hard to explain, just hit ctrl-alt-f1, then ctrl-alt-f7.  this will switch you back and forth between the X enviroment and the terminal, or shell interface.  TTYs are what provide this ability.  They are kinda like Workspace 1-4 in yuor x session, but not really.  

So your asking if there is a GUI for the command line commands?  The answer is yes & no.  Some commands have GUIs, some don't.  Some commands are not suited to gui's, like simple commands such as cp, mv, rm, mkdir; however their functionality is built into GUI apps, like nautlis.

The problem is all these commands and GUI apps come from the community.  So person x decides to write application y, that operates from the command line.  Person X doesn't care about the GUI as he never uses it, so he isn't going to waste his time developing it.  In this case, unless Person Z comes along and decides to make a GUI app for application y, it'll never exist.

Its a good idea to learn both the command line functionality and the GUI functionality for this very reason.  Its not so much complicated as it is overwhelming.  So start small and work your way up.

---

### Post by mostwanted on 2006-06-12
[QUOTE=MAXDDARK]how ? were ?[/QUOTE]

Commands are just small programs with one specific function. For example: the cp, mv, rm commands are represented as a file manager (in Gnome it's called Nautilus, you can access it from your bookmarks in Places). It can do the same thing as those commands can do. Same with other commands.

---

### Post by MaximB on 2006-06-12
BTW - is there somthing in linux like ctrl+alt+del in win ?
bcz I played the live dvd 6.06 and searched some screensavers - and then it "stopped" - I couldn't do anything beside restart my pc.

---

### Post by ProjectGod on 2006-06-12
there's a hoard of command line sites... but there are two nifty tools i found very handy.

try this at the command line... tap "tab" key on your keyboard twice in close intervals. you'll get a list of every command / utility there is...

**[tab] [tab]**

another nifty tool... type:

**apropos <string>**

where <string> is anything you would want to find... e.g. apropos browser

this utility searches the MANUAL pages for keywords you defined in the <string>.

---

### Post by matrooswolf on 2006-06-12
[QUOTE=MAXDDARK]BTW - is there somthing in linux like ctrl+alt+del in win ?
bcz I played the live dvd 6.06 and searched some screensavers - and then it "stopped" - I couldn't do anything beside restart my pc.[/QUOTE]
ctrl+alt+backspace will restart X  
This is mostly all you need.

---

### Post by matrooswolf on 2006-06-12
[QUOTE=ProjectGod]there's a hoard of command line sites... but there are two nifty tools i found very handy.

try this at the command line... tap "tab" key on your keyboard twice in close intervals. you'll get a list of every command / utility there is...

**[tab] [tab]**

another nifty tool... type:

**apropos <string>**

where <string> is anything you would want to find... e.g. apropos browser

this utility searches the MANUAL pages for keywords you defined in the <string>.[/QUOTE]

that of course and 
```
fortune
```
;)

---

### Post by mdsmedia on 2006-06-12
[QUOTE=MAXDDARK]BTW - is there somthing in linux like ctrl+alt+del in win ?
bcz I played the live dvd 6.06 and searched some screensavers - and then it "stopped" - I couldn't do anything beside restart my pc.[/QUOTE]Think of the current GUI interface as a lot of the command line (terminal) commands made into GUI. So in answer to your question "is there going to be a GUI for the command line?" there already is for most commands. Unlike Windows, it's easy to do CLI (command line interface) commands in the terminal, and these make it a lot easier, once you get used to it, to get things done. In Windows you ONLY have the GUI to get things done, although some commands are available via a DOS window through START...RUN....CMD or something similar.

The equivalent of ctrl+alt+del in Linux depends what you want to do with it. In Windows, ctrl+alt+del brings up the application manager AND allows you to restart (warm boot) your OS. The application manager in Linux can be brought up by pressing ctrl+alt+F1 to bring up the terminal window. Then log in by inputting login name and password, then type "top". This will bring up a list of processes that are running. Then type "k" (which is kill) and input the number of the PID (see the left most column) you want to kill. Then confirm as requested.

---

