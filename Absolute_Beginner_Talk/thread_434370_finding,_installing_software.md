---
title: "finding, installing software"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by rufi_dukes on 2007-05-05
my question relates to the main sources of software for my new OS and how to get and then install them;
i have used synaptic to get a few programs, have tried searching for a few others which i was unable to find, and dloaded some which i then cant find on my machine (is this a question of not having installed it correctly...ie pathway or related issue?)

thx,
rufus

---

### Post by taurus on 2007-05-05
Do you remember the names of the programs that you installed with synaptic?  You can try and run them from a terminal like

Applications -> Accessories -> Terminal
```
program_name
```

And for the programs that you downloaded by hand, chances are they are in your ~/Desktop.

```
cd ~/Desktop
ls -la
```

---

### Post by rufi_dukes on 2007-05-05
thx,
i checked out one of the progs using yr advice only to discover that it is written for KDE...
it is called kig: an interactive geometry program, and, while i got it launch, none of its associated files (dependancies?) seem to have been installed and its use, at present, is of limited value...
sigh.... everything seems soooooo hard

ps i would have expected that since i executed the search with synaptic (a packager associated with gnome? exclusively?) that it would only have returned gnome compatible software....
cd u disabuse me of my ignorance on this (and any other that u see) point?
thx again,
rufus

---

### Post by LaurelLynn on 2007-05-05
KDE programs can be installed under Gnome, but there may be some features lost (example, I use Quanta Plus for HTML editting).

If you really need a particular KDE app that will only run under KDE, there is no reason you can install both Desktops, and switch when you need to.

First I would start by looking at this website:

[http://linuxappfinder.com/](http://linuxappfinder.com/)

There are usually multiple programs available to fill the same nitch.

---

### Post by rufi_dukes on 2007-05-06
thx for replies;
how do i get kde interface?
is it like having two desktop environments to choose from?
how does the idea of "desktop" interact with (or not) the idea of OS?
thx again,
rufus

---

### Post by taurus on 2007-05-06
If you want to try out KDE, open a terminal and do

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```
Then, you can choose window manager to run from the Options (bottom left corner) from the GUI login screen.

---

### Post by Marsolin on 2007-05-06
If I understand your problem correctly, it doesn't have anything to do with [Kig]("http://linuxappfinder.com/package/kig") being a KDE program.  I'm guessing that you want the recommended and suggested packages that are associated with it.  Try installing the kdeedu-data and kdeedu-doc-html packages and see if it solves your problem.

---

### Post by rufi_dukes on 2007-05-07
i followed yr advice and installed the 2 packages
but still got error messages when trying to run kig,
which would run, but since it hasn't loaded cleanly, i'm not sure that i have full functionality

thx anyway,
it's all new experience, and each time i have sthg concrete to try, i feel i'm making tiny steps forward...
regs,
rufus

---

### Post by rufi_dukes on 2007-05-07
thx marsolin,
i'll give it a go,
rufus

---

### Post by Nythain on 2007-05-07
more good advice as far as being new to installing new software is making sure you have all the repos available... im not sure if you have done it already but i would gksudo gedit /etc/apt/sources.list and make sure all the addresses are uncommented.

Synaptic, while being a gtk/gnome program, is a front end for aptitude wich will search the repos for any and ALL software available, not just gnome specific. The description of the software usually mentions if its gtk or qt, gnome or kde specific.

Gnome apps will run under kde usually, and kde apps will run under gnome usually, but it requires installing and running all the base libraries for each engine also, so sometimes they run a bit sluggish and usually look out of place in the other environments.

you can, as mentioned, have both gnome and kde installed on your computer, and just switch back and forth if you NEED to, but thats usually just really annoying

---

### Post by rufi_dukes on 2007-05-07
Nythain,
it would tickle me half pink to death to "make sure that  all the addresses are uncommented" if only i knew what that means....
i ran that code and it launched sthg that looked like a text editor,
with the phrase "such and such is commented" peppered throughout,
and i realized that this is beyond my current abilities to tackle,
without point by point instructions ....

i'm all ears....
rufus

---

### Post by Marsolin on 2007-05-07
Can you post the specific error message that you are seeing?  Maybe I missed it, but I didn't see the details in the thread.

---

### Post by rufi_dukes on 2007-05-07
sure,
thx for taking the time to help;
my eyes are bleeding with tiredness..
must sleep..
but if u wd be kind enough to have a look at this and suggest sthg i wd be grateful
when i wake tomorrow and climb back in the torture/pleasure rack...:0 ))
rufus

Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Launched ok, pid = 19040
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2e00a0c

---

### Post by LaurelLynn on 2007-05-07
First when Marsolin suggested uncomenting entries in /etc/apt/sources.list he meant for all the entries that start out:

#  deb ....

Remove the '#' :

deb .....

I suggested installing KDE originally, as the easiest way to install all the dependancies. It's overkill, but saves going through package by package trying to figure out if you need it or not.

Though it says "BadDevice", I would be very surprised if you had actual hardware problems.  Most likely the problem is a low level KDE call to communicate something to the graphics controller/mouse/keyboard. If it relies on communicating with KDE at too low of a level, it may only be runable in KDE. In which case I would follow tauruses advice, and switch back and forth when needed.

---

### Post by Marsolin on 2007-05-07
That error is because you are running it from a terminal.  Mine does the same thing. Try pressing Alt+F2 and then typing kig.

---

### Post by rufi_dukes on 2007-05-10
that did the trick, thx marsolin

---

