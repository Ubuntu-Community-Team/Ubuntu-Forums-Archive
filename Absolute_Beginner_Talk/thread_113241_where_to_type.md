---
title: "where to type???"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by rysher on 2006-01-06
o.k., i have been reading a lot, i have installed my ubuntu softwre for a day now. i have read alot of stuff like typing /usr/, /sudo/ etc.... may i please know where to type it? i am a complete newb here, in a completely diffrent world and my first step into this unknown is really more of groping in the dark. i have been using MS for more than 15 years, And i want to shift to linux, i haven't started anything and i already questioned my decision on OS shift. i was told by friends that linux/ubuntu is EZ well i find it very hard, i guess u cna't teach an old dog some new tricks.

---

### Post by 23meg on 2006-01-06
You need to type them at the terminal, which you can reach via Applications / Accessories / Terminal.

---

### Post by Chipmunk on 2006-01-06
Sure you can teach an old dog new tricks, however it takes a while (people on this forum know I have been screwing up even as recently as last night).

Where you'd use those commands is in a terminal, (equivalent to a dos prompt in windows, but far far more powerful) accessible from the desktop by clicking applications/accesories/terminal.  sudo is a command to execute things as 'root' (the equivalent of administrator on microsoft operating systems but far more powerful again - there's a pattern emerging :D ). The usage is something like rmdir foo  to remove the directory foo, or sudo rmdir foo to remove the directory foo if it won't let you in normal user mode. (Tip, unless you know for sure it's safe to do so, don't, it may be needed, there's usually a reason files and directories are tamperproofed from you).

Some basic commands you can try at a terminal are:
ls  (lists files, like dir)
cd (works the same as dos, only you need a space if you use cd .. or cd / for the root of the filesystem).
mkdir (makes a directory)
rmdir  (removes it again, use with caution, but won't delete a directory with files in it)
rm (deletes files, use with caution)
man [command] will give you all options for that command, most commands also respond to the command switch --help

such that ```
ls --help
``` will give basic options for listing files, whereas ```
man ls
``` will give you enormously complex (and at first confusing) information, but very useful later on when you gain confidence.

With man [some command] when you're done, type Q to quit the manual.

Ctrl+C will stop most executing commands (say you type a command that starts to scroll output and you want to stop it before it lists the entire contents of the computer)

As with dos, exit will exit the terminal window.

A couple of fun commands (also useful) are ```
uptime
``` to tell you your system's uptime, and load averages (I believe the 3 figures are 1 minute, 5 minute and 15 minute load averages), and ```
ps -A
``` which shows all running processes on the system. (ps without the -A will show you only those you're running under your username I believe).

Once again though, be very careful if you use any command with sudo in front, it lets you become root (the superuser) and root can do a LOT of damage, there's not much that he/she can't do.

---

### Post by Omnios on 2006-01-06
YOu might find this usefull its a bunch of links to terminal how to's and reference sites. 

 [http://ubuntuforums.org/showthread.php?t=45651]("http://ubuntuforums.org/showthread.php?t=45651")

---

### Post by arpanaut on 2006-01-06
Here's a couple of links with loads of info:

[http://makuchaku.info/amnesty/#](http://makuchaku.info/amnesty/#)

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

and here's one I found very interesting, a little orientation as it were,

[http://techrepublic.com.com/5100-10877_11-5960961.html#](http://techrepublic.com.com/5100-10877_11-5960961.html#)

It's a tough go at first but if ya keep digging and pay attention around the forum you can get there... If you wnat a quick and easy set up for a lot of "essential" things find the Automatix script and to get things set up real quick.

I've been running Ubuntu for about four months now and am starting to get the hang of it now (first linux after 20 years of windows only hehe).  I hardly boot to windows on this box anymore, It gets addicting, and my ultimate goal is to not to have to shell out any more $$$ to Uncle Bill.

Good Luck!  Have Fun!

---

### Post by 23meg on 2006-01-06
Another great CLI resource for newcomers:

[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by rysher on 2006-01-06
[QUOTE=arpanaut]
my ultimate goal is to not to have to shell out any more $$$ to Uncle Bill.

Good Luck!  Have Fun![/QUOTE]

thanks a lot.

but i have never paid for a software i own, they are all cracked and hacked. so $$$ is not a question. from windows xp to vista- norton to almost anything and everything.

---

### Post by estel on 2006-01-06
^.^

Please, you shouldn't really discuss that here.

Besides, it's the philosophy... the freedom of the software in all respects.

---

### Post by rysher on 2006-01-06
sorry.
btw have mounted my mp3 nad u2 is currently playing. though there's not much option on visual effects on the player and what kind of player is this?

---

### Post by Lord Illidan on 2006-01-06
If you are looking for a good mp3 player, use Amarok.
In sort, use kde..

sudo apt-get install kubuntu-desktop

I take it you enabled the repos? Look at the starter guide :
[Ubuntu Wiki (community-edited website)]("http://www.ubuntulinux.org/wiki/FrontPage")

---

### Post by hobbit1983 on 2006-01-06
My favourite terminal commands are: (I think these are very usefull)

man *command*
tells you all the options for a particular application
apropos *word*
gives you a list of commands that are relevant to the word you entered.  Useful for finding if there is a command to do a certain task

---

### Post by meborc on 2006-01-06
[QUOTE=Lord Illidan]If you are looking for a good mp3 player, use Amarok.
In sort, use kde..

sudo apt-get install kubuntu-desktop

I take it you enabled the repos? Look at the starter guide :
[Ubuntu Wiki (community-edited website)]("http://www.ubuntulinux.org/wiki/FrontPage")[/QUOTE]
hey, you shouldn't do that to a new linux user... he thinks that he gets a cool mp3 player, but he gets A LOT of packages... and a new desktop... so... please... don't urge new users type in just any code you scribe... they may get in trouble that way :D ... and btw - gnome rocks !

offtopic - use bmp (beep media player) for mp3's

---

