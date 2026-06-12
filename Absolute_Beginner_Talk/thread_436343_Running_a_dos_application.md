---
title: "Running a dos application"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by dbvanhorn on 2007-05-07
I'm looking for something that will let me run a dos app (640x480 graphics) on 7.04
I have 64 bit machines, and apparently wine isn't available to me.

I ripped Vista off my M$ Slutbox, and the laptop is dual boot for this one program only.
I'd really like to get rid of my M$ habit.  

Any hints?
The program in question is the last version of Dos ORCAD for schematic and PCB layout.
There may be other packages out there, but I'm not looking to go exploring at this point.

The final straw (haybale actually) for me was when it took SEVEN HOURS to move 11G between two fast hard drives under vista, on a dual-core athlon with 2G ram.   I knew the first time I saw it happen, that if it needed to calculate the time it would take to delete a few files, it was VERY bad news.

---

### Post by jonom on 2007-05-07
Dosbox?

[http://dosbox.sourceforge.net](http://dosbox.sourceforge.net)

---

### Post by Meneldir on 2007-07-07
Hello.. I'm a noob here. I also have a 64bits machine. An AMD X2 64bits 3800+. I've installed DOSEmu to run some games, but I can't slow them down. They go really fast.. any help?
Thanks.. me love oo-boon-too! :P

---

### Post by Bungo Pony on 2007-07-07
I've been very successful with using Dosbox, however I'm not running in 64 bit. Give it a try and see if it works for you.

---

### Post by p_quarles on 2007-07-07
Like jonom said, Dosbox. Much better than Dosemu. 
```
sudo apt-get install dosbox
```You need the universe repo for this to work. Then install whatever DOS games you want, and remember the directory you installed them to.

Open a terminal ```
dosbox
mount c /home/[I]username/directory-you-installed-your-dos-games-to
[/I]c:
```Then, you can just CD into the appropriate subdirectory and launch the executable.

---

### Post by Doctoxic on 2007-07-15
hi
sorry to hijack the thread but i have a similar problem:


i am having trouble trying to install a game from a floppy

this is what happens:

* start dosbox

* mount c with : mount c  /home/name/dosbox/stalingrad (dir already created)
and it confirms its mounted

* mount the floppy: mount a /media/floppy0
and it confirms its mounted

*  change to a: and run install.exe
install program starts from the floppy

NOW THE PROBLEMS START

* i then get a box asking me to "choose an installation directory" and it defaults to:
C:\STALIN

what should i type in here as i have tried various combos and always get the same error
e.g. if i use "C:\" which is where the file dir was mounted earlier i get this:
"We have encountered an error as follows:On script line 37 we had a problem:creating a binary file"

i suppose it could be an error on the floppy, but it seems more likely that its me doing something wrong

any help much appreciated

thanks

doc


PS in dosbox what the command to unmount a drive?

---

### Post by Meneldir on 2007-08-20
Sorry for telling my experience so late. But i didn't receive a mail from the forum, and I've forgotten. I've erased DOSEmu and tryed DOSBox, setting everything to automatic, and it works perfectly! :D
Thought, it was for just one game, that i've won several time since my last post :P
Thanks.

---

### Post by jimbean on 2007-09-30
this is for Doctoxic
have you tried to just copy the floppy to your harddrive
and run the program from there 
not the setup
but the game

---

### Post by Doctoxic on 2007-09-30
thanks jimbeam

i'll try it

cheers


doc

---

### Post by mivo on 2007-09-30
A bit off-topic, but do I understand this correctly that Wine does not work on a 64 bit machine or 64 bit Linux version?

---

### Post by mivo on 2007-09-30
Okay, I think I can relax. :p Just read here: [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)  and it also says that "64 bit Ubuntu users can also just install the distro packages, which included the instructions below." I worried for a moment because I'm building a 64 bit machine right now and need to be able to run my employer's window application in Wine.  (I don't dual-boot.)

---

### Post by Perfect Storm on 2007-09-30
> **Doctoxic said:**
> hi
sorry to hijack the thread but i have a similar problem:


i am having trouble trying to install a game from a floppy

this is what happens:

* start dosbox

* mount c with : mount c  /home/name/dosbox/stalingrad (dir already created)
and it confirms its mounted

* mount the floppy: mount a /media/floppy0
and it confirms its mounted

*  change to a: and run install.exe
install program starts from the floppy

NOW THE PROBLEMS START

* i then get a box asking me to "choose an installation directory" and it defaults to:
C:\STALIN

what should i type in here as i have tried various combos and always get the same error
e.g. if i use "C:\" which is where the file dir was mounted earlier i get this:
"We have encountered an error as follows:On script line 37 we had a problem:creating a binary file"

i suppose it could be an error on the floppy, but it seems more likely that its me doing something wrong

any help much appreciated

thanks

doc


PS in dosbox what the command to unmount a drive?


Why copy the files to your harddisc.
Then run command;
dosbox <path>/<file>

Also check the gaming frontend for dosbox; [http://gaming.gwos.org/doku.php/guides:dosbox](http://gaming.gwos.org/doku.php/guides:dosbox)

---

