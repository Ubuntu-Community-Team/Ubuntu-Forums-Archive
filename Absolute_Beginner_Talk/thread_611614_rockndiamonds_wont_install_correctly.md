---
title: "rockndiamonds wont install correctly"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-11-13
i started up synaptic package manager and did a search on games to see what was there.

i found "rocksndiamonds" and i thought i would give it a go.
i started up terminal and typed in

sudo apt-get install rocksndiamonds

and it said it d/l and installed some data

next i type in to terminal

rocksndiamonds

and i get this error

-e Game data not installed!

-e usage: 

-e # dpkg-reconfigure rocksndiamonds

for install/update game levels
exit: 19: Illegal number: -1


so i copy and paste 

sudo dpkg-reconfigure rocksndiamonds

in to terminal and i see a bluescreen come up that lets me pick what games to download data from.
no matter what game i select and press ok on, i get returned to the terminal screen and it says

Update menu


thats it!!!
im just going round in circles. can anyone help at all??
Thanks

---

### Post by justleen on 2007-11-13
possibly it needs more files then just the file you downloaded and installed.. 

Try installing it through the package manager?

or do a apt-cache search rocks |grep diamonds, to see what other files there are

---

### Post by el10t on 2007-11-13
Yep - same problem here.  It must be to do with the availability (lack of?) of the game data files.  It says they are non-free.

---

### Post by Paul820 on 2007-11-13
If you do it through synaptic package manager it will do it all properly for you. There will be no menu entry for it so you will have to make one.

---

### Post by stinger30au on 2007-11-13
ok, now i feel dumb.

i went in to synaptic and i have uninstalled rocksndiamonds. and i have then selected it and re installed it and it gives me the same error.

---

### Post by Paul820 on 2007-11-13
It worked fine for me, it installed the main program, then a blue box came up with others other things to download, i clicked a couple that looked ok and it downloaded them for me. I went to the menu under games and couldn't find it. So i went to the terminal and typed
> whereis rocksndiamonds
It came back with this
> rocksndiamonds: /usr/games/rocksndiamonds /usr/share/man/man6/rocksndiamonds.6.gz
I then went to System->Preferences->Main Menu, clicked on games in the left box, on the right i clicked on **new item**, called it Rocks and Diamonds, browsed to the file where the command whereis told me it was and clicked the file, pressed ok and started the game from the menu.

---

### Post by el10t on 2007-11-14
> **stinger30au said:**
> ok, now i feel dumb.

i went in to synaptic and i have uninstalled rocksndiamonds. and i have then selected it and re installed it and it gives me the same error.
Hehe me too - I also tried again using Synaptic and got exactly the same problem.  I think the game data download is failing because it drops out really quickly back to the terminal window after the blue selection screen - there is no hint of it downloading any data.

---

### Post by forestpixie on 2007-11-14
I just did it through synaptic - it appears to download game data when synaptic is configuring rocksndiamonds

---

### Post by stinger30au on 2007-11-14
ok, feeling dumb again.

i have ininstalled it from cli as well as synaptic and reinstalled from cli and synaptic and i still get the same error

i did a "whereis" and found it. added it to games menu and it still says

-e Game data not installed!

-e usage:

-e # dpkg-reconfigure rocksndiamonds

for install/update game levels
exit: 19: Illegal number: -1



*sigh*


i will stick to playing burgertime, at least it works

---

