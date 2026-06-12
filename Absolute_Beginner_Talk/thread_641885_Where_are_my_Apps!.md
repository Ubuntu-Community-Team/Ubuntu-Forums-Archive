---
title: "Where are my Apps!?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by barbedsaber on 2007-12-15
I downloaded heaps and heaps of apps using synaptic, and some of them went into that menu thingy at the top of the screen, but some of them didn't. I assume they are in a folder (possibly with a . at the begingin) but I want to know where, so I can delete the bad ones and get new ones.

I would really appreciate your input on this, thanks.

---

### Post by thelatinist on 2007-12-16
What packages specifically did you add that aren't showing up in the applications menu?  Not every package or application has a GUI; command-line utilities, drivers, and libraries won't have an associated launcher...

---

### Post by erfahren on 2007-12-16
sometimes you need to refresh the menu - in terminal do: killall gnome-panel  -that will cause the panel to restart, refreshing the menu

sometimes you jsut ned to create launchers, see: [http://ubuntuforums.org/showthread.php?t=533265](http://ubuntuforums.org/showthread.php?t=533265)

---

### Post by tweaked on 2007-12-16
> **erfahren said:**
> sometimes you need to refresh the menu - in terminal do: killall gnome-panel -that will cause the panel to restart, refreshing the menu

sometimes you jsut ned to create launchers, see: [http://ubuntuforums.org/showthread.php?t=533265](http://ubuntuforums.org/showthread.php?t=533265)

That tutorial is fine, IF YOU CAN FIND THE PROGRAM! I downloaded gui Bittorrent and have no idea where it is. None. Along with several other things. Additionally, where is the tutorial with commands to run the non guis?  ](*,)](*,)

This is incredible. How hyped this OS is.The Help file is garbage and if it hadn't killed my XP bootup when installing I'd be long gone because this ain't in any way ready for prime time. And some kid in Africa is supposed to be able to use this with his $100 laptop, what a joke.

---

### Post by thelatinist on 2007-12-16
> **tweaked said:**
> That tutorial is fine, IF YOU CAN FIND THE PROGRAM! I downloaded gui Bittorrent and have no idea where it is. None. Along with several other things. Additionally, where is the tutorial with commands to run the non guis?  ](*,)](*,)

This is incredible. How hyped this OS is.The Help file is garbage and if it hadn't killed my XP bootup when installing I'd be long gone because this ain't in any way ready for prime time. And some kid in Africa is supposed to be able to use this with his $100 laptop, what a joke.

If you want to open Bittorrent, just click on the torrent file you want to download.  That's simple enough.  I would highly recommend using the much more user-friendly and flexible Deluge client, though.  It's easy to get from Applications > Add/Remove...  That's one application: you said there were "heaps and heaps"?  What are the others?

I know you're frustrated, but you needn't take that attitude.  Ubuntu is an incredibly flexible, secure, and easy-to-use operating system once you've unlearned the things you learned in Windows.  Give it time.  And we are here to help.  Who needs help files when there is a vast community of friendly users ready to answer your questions?

---

### Post by erfahren on 2007-12-16
> **tweaked said:**
> That tutorial is fine, IF YOU CAN FIND THE PROGRAM! I downloaded gui Bittorrent and have no idea where it is. None. Along with several other things. Additionally, where is the tutorial with commands to run the non guis?  ](*,)](*,)

This is incredible. How hyped this OS is.The Help file is garbage and if it hadn't killed my XP bootup when installing I'd be long gone because this ain't in any way ready for prime time. And some kid in Africa is supposed to be able to use this with his $100 laptop, what a joke.
that has happened to me before, where I installed a program through Synaptic then had no idea what command to use to launch it.

here's what I did:

many of the programs listed in Synaptic give a website address in the description (not quite *all* of them still good - lol !), anyway, I go to it and look at their documentation - often just the basic install instructions will give you the command.

Or - I Google the program (sometimes with the word "linux" to narrow the results)

but the documentation for the program is installed along with it. Many put it in /usr/share/doc
or you can search for all the directories the program has with like:
```

sudo find / -name *name-of-program*

```
see the documentation for the find command (man -find) or: [http://www.linuxcommand.org/superman_pages.php](http://www.linuxcommand.org/superman_pages.php)

in a worst case scenerio you can look for the package at the Ubuntu packages site, which lists all the packages available in the repos: Google search like:
*name of package* site:[http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

if you go to the bottom of [this page](http://packages.ubuntu.com/gutsy/net/bittorrent-gui) for example you'll see "list of files" - it will list the files and *exactly* where they were installed.
(btw: I first found that site myself by a regular Google search for a package I wanted to know more about).

--- So with Linux, unlike Windows, there's usually a number of different ways to go about something, and with complete transparency at that. It's just a matter of looking for the information, that's where Google comes in handy. 

BTW: the fact that a program installed didn't create a menu entry isn't Ubuntu's fault, and really not even the fault of the developer(s) of the program. These programs are distributed as mere source code for the explicit purpose of being portable and able to be compiled to run on different architectures. Because of this there are *thousands* of programs available for linux for free. 

So Ubuntu *Linux* isn't only ready for prime-time, it *is* prime-time. It's the rest of the industry that needs to keep up.

---

### Post by tweaked on 2007-12-16
Thank you for the advice regarding Deluge, it is working and showed up promplty in the menus. 
I followed advice on another page and attempted to install menu-xdg, a menu app that supposedly willshow  installed apps better. problem is, it didn't show up either. No sign anywhere except in a terminal search. I followed the thorough advice above and attempted to open the documet file for menu-xdg with the text editor and no-go. I search google to find the linux command to open the doc file so I can maybe learn how to launch this program and after 15 miinutes, I don't find that simple command and I don't really know if thats what I want anyway. I'm sorry, the average person will have no patience for this when there is an easier chioce. Imagine the new computer user who wouldn't even know what a command line is....
You know, with all due respect, if this were a windows app, it takes all of maybe 3 mouse clicks to download, install, and launch(unlees it needs reboot). No arcane language necessary, no google search for instructions on how to launch it, and few worries about compaptibility. 
I can understand how linux has power, although the fact that it is source code and flexible means absolutely nothing to the layman who doesn't even know what source code is, nor to the person who hasn't spent considerable time learning its eccentricities. They really don't need nor understand that power, they just need it to work in a simple manner. Like a car, they want it to start, go and stop. Very few want to know about tweaking the injectors, grinding the valves, tuning the suspension or any of the other stuff. They just want to turn the key and go. The same goes for the operating system. I spent 4 days just getting Ubuntu installed! I will continue to play around (my second go-round with linux)and maybe will get the hang of things but looking at it from the outside, it still is nowhere near ready for prime time.

---

### Post by TeaSwigger on 2007-12-16
> **tweaked said:**
> 
You know, with all due respect, if this were a windows app, it takes all of maybe 3 mouse clicks to download, install, and launch(unlees it needs reboot). No arcane language necessary, no google search for instructions on how to launch it, and few worries about compaptibility. 
I can understand how linux has power, although the fact that it is source code and flexible means absolutely nothing to the layman who doesn't even know what source code is, nor to the person who hasn't spent considerable time learning its eccentricities. They really don't need nor understand that power, they just need it to work in a simple manner. Like a car, they want it to start, go and stop. Very few want to know about tweaking the injectors, grinding the valves, tuning the suspension or any of the other stuff. They just want to turn the key and go. The same goes for the operating system. I spent 4 days just getting Ubuntu installed! I will continue to play around (my second go-round with linux)and maybe will get the hang of things but looking at it from the outside, it still is nowhere near ready for prime time.

Windows offered a free repository for one click installations of just about every utility you wanted? News to me! These things kind of "come out in the wash." Tradeoffs. Like a lot of things in life. My gosh you'll have to give yourself time. Windows took plenty of your time to learn once, but we tend to forget that. I suggest it's worth it in the larger picture.

Seriously, it's just like anything else in the world. Like a car. The fact that most people want to just turn a key and go is a recipe for being taken. By dealers, by manufacterers, by parts suppliers, by materials suppiers, by mechanics (er, they're factory certified technicians now that the shops cost twice as much to fix that "turn key and go product" these days, I forgot), by glass shops, by Kragens, by paint shops, by body shops, and it goes on and on. We pay a lot more than usually appreciated for the "turn key and go, then get a new one every few years" approach to cars. Then there's the aspect of humanity; if we just want function, the items, whatever they be, will become utilitarian (read: ugly, cold) or subject only to commercially motivated image trends (read: artless and heartless). Kinda like... most cars.

Now imagine there are only two car makers in the world besides obscure do it yourself kits. In the computer realm, it's awful close to that now. Microsoft became one of the top wealthiest global megacorporations in the history of the world by packaging & marketing what you could get elsewhere for less or even for free. Heck they've lifted plenty of their product features from others (without acknowledgement or renumeration need one say). They've made the deals so almost all the equipment you can buy either comes with their product ready-to-use (er well you do have to buy more software from one of their partners or some other commercial entity that designs largely or exclusively for use with their products to actually do much specific, but back to the point) or was "designed for" it, often without concern for your ability to use anything else. 

Price for alternatives? You will almost certainly have to be involved somehow. Pay the corporations anything they want or "do it yourself"... while there's still a choice. That choice is here largely thanks to folks like those behind the open source software scene. Without the  leveraged... well. The existence of alternatives can and does mean plenty to the "average person" whether they know it or not.

The good news? Knowledge is power. The more knowledge you gain, the more and more you can do with less and less reliance on your pocketbook opening for corporate providers, and the more you can do things as you personally choose.

---

### Post by erfahren on 2007-12-16
@tweaked - I looked into that "menu-xdg" (even installed it) and I don't think it does what you think it does. I'm not exactly sure what it's for to be honest!

Anyway, I did forget one tip (probably the easiest) to find installed programs and the command they use (oops!)

In Synaptic Package Manager go to Settings > Preferences from the menubar. Check the box that says "Show package properties in the main menu"

then when you install a program you can click on the "Installed Files" tab. You can look for where the program's bin (executable) was installed - usually to /usr/bin or possibly /usr/games if it's a game.

About the documentation... sometimes the documentation is in a archive, you can just do "sudo nautilus" in the terminal to open the file browser with root permissions - browse to the directory and copy the archive into your home folder and open it there.


-- I don't know. I went and figured out much of this stuff for myself. Maybe because I was used to using FOSS and freeware on Windows I expected to do some research. Or maybe I installed Linux just because it was *Linux* and not to just play with desktop effects and the like (in fact, I didn't even know about that then!).

---

### Post by macogw on 2007-12-16
Mostly, if you want to launch a program, you can just type its name in all lowercase either into a terminal or into a launch box.  To get a launch box, hit alt+f2 (you can put it in the panel too, right click > add to panel) and just type in the name of whatever you want to run

---

### Post by thelatinist on 2007-12-16
> **tweaked said:**
> You know, with all due respect, if this were a windows app, it takes all of maybe 3 mouse clicks to download, install, and launch(unlees it needs reboot). No arcane language necessary, no google search for instructions on how to launch it, and few worries about compaptibility.

You still haven't told us what the 'heaps and heaps' of applications you're trying to run are.  If you would take a little time to do that rather than venting, perhaps you would get the help you need.  Frankly, I'm getting tired of your posting threads demanding help, refusing to answer simple questions, then posting diatribes when you can't figure out something as simple as creating a launcher (which is quite as easy as creating a shortcut in Windows).

---

### Post by bazanime on 2007-12-16
I need assistance please.

My Applications menu doesn't have any apps in it.  When i click on it to give me the usual list of categories that contain the apps, all i get is a tiny one pixel size box at the left corner. They were all there two weeks ago and now their gone.  Strange thing is that the associated files open fine, so the apps are still there in the system.  I cant even reach the Add Remove app.

I hope i have explained right?  Can anyone help out in a clear concise manner?

---

### Post by thelatinist on 2007-12-16
This is really a different issue and should have its own thread.  Have you tried editing the menu by right-clicking on Applications and choosing "Edit Menus"?

---

### Post by bazanime on 2007-12-16
Yes i have but that doesnt even show up. The taskbar says "Starting Main Menu" for a few seconds, then disappears.

Sorry, its just that my past experience in forums has taught me not to create new threads if there is already a related thread.  i figured this would be appropriate enough place to post my issue.

---

### Post by erfahren on 2007-12-16
@bazanime try going into Synaptic package Manager and search for the package "gnome-menus" and reinstall it. (the menu editor itself is called "alacarte".)

do you think you might have installed a package you found somewhere that may have effected it?

---

