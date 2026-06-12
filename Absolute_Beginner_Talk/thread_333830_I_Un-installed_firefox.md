---
title: "I Un-installed firefox"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Oldbones on 2007-01-08
:???: 

It sounds dumb -* it is dumb* - but I did it.

I was grabbing some of my favorite extensions from Firefox, including some new ones.  When I reloaded, the browser just hung and then faided to black (which may be from [Beryl]("http://wiki.beryl-project.org/wiki/Main_Page")).   Whatever caused it to fade to black, it wouldn't let me run the program at all.

Using my Microsoft trained mind, I thought that un-installing the program and reinstalling would be the best option.   There was a warning saying,  "some programs require Firefox, do you wish to continue?"  I hit continue.#-o 

As a result, I lost the remove/install software button from the "Applications" drop-down-menu.  :frown: 

Reinstalling Firefox did nothing.   It didn't even remove the extensions that crashed the program.  

With my meager Linux skilz, I decided to try
 ```
man firefox
``` 
[SIZE="2"]When in doubt, read the manual!!!!![/SIZE]

That's when I learned about running the program from the terminal in "Safe-mode"
```
firefox -safe-mode
```
Firefox game me the option of running the program without the add-ons so that I could delete them.  Fantastic.

[SIZE="2"]**My question is, what programs did I lose by un-installing Firefox?  Aren't they easy to get back?**[/SIZE]


Thanks,

BTW,
Ubuntu rocks!

---

### Post by aysiu on 2007-01-08
Just do this, and you'll get those programs back: ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```

---

### Post by 3rdalbum on 2007-01-08
In future, here's a tip, from the history of the Mac OS. Before you try uninstalling and reinstalling a program (which should be the last resort on a Linux system), instead get rid of the program's user preferences.

In your home directory, you will find lots of hidden directories, whose names start with a dot ("."). These contain your user preferences for that program. So, if Firefox started playing up on my computer, I'd simply remove the .firefox directory from my home directory.

That's usually why Windows programs work alright after a complete reinstall - because during the uninstall process, the user's preferences get deleted.

---

### Post by aysiu on 2007-01-08
Isn't it the .mozilla directory, not the .firefox directory?

And, I would generally advise renaming as opposed to deleting: ```
mv ~/.mozilla ~/.mozilla.old
``` This tutorial also helps you keep your bookmarks:
[HowTo Get Rid of a Corrupt Firefox Profile (and keep the bookmarks)](http://ubuntuforums.org/showthread.php?t=103930&highlight=firefox+corrupt+profile)

---

