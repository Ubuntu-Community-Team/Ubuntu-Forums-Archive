---
title: "Switching"
date: 2005-05-08
forum: Apple PPC Users
---

### Post by LittleFae on 2005-05-08
Okay, I have my Ubuntu disks (Kudos to Ubuntu devs for Free CDs - will make a donation as a token of thanks next pay-day), and am about ready to leave the world of the Macintosh, and enter the world of Linux-PowerPC.

I tried out the Live CD, worked fine, perfectly fine, even tuxracer ran (Again with no sound though. :( )  But before I make the final push to Linux, there's a few things I'd like to be warned/informed about.  I'll do this by describing my needs, and, if Ubuntu doesn't support it out of the  box, I'll accept workarounds (that work), and begin working on the switch.

Needs:
I have a vast library of AAC audio files that I've backed up (.m4a), that I want to play
I live to watch DVD's, DivX video, WMV and MP4.
I like the Linux games: Armagetron and Tuxracer - Would like sound
I do a lot of scanning using a Lexmark X1180 printer/scanner
I like my keyboard just as it is, the Live CD didn't seem to have a suitable keyboard layout for a snow iBook G3, is there one?
Developer tools, for doing on-the-fly compiles for stuff that Ubuntu doesn't have, even in Universe, like tinyfugue, TinyMUX/MUSH/Penn etc.
I like to Skype
Easy web-serving, Mac is great for that, just click and go, and it runs.
Support for the built-in 'Close laptop and sleep' mode.
A keyboard way to eject the CD tray, as F12 is hooked by the mouse emulator
A right-click like OSX, using CTRL instead of F12, therby freeing up F12

---

### Post by Rxke on 2005-05-08
I like skype, too.
Worse: i depend on it to connect to some people.

...But no Skype for ppc Linux. Yet.

---

### Post by slux on 2005-05-09
[QUOTE=LittleFae]
I have a vast library of AAC audio files that I've backed up (.m4a), that I want to play
[/QUOTE]

Should work as long as they're not DRMed... Even that can be fixed, I think.

> 
I live to watch DVD's, DivX video, WMV and MP4.


Everything else should work but you won't be able to play WMVs.

> 
I like the Linux games: Armagetron and Tuxracer - Would like sound


Sound is working on pretty much each and every new world Mac as far as I know so I suspect it was mainly an issue with the LiveCD.

> I do a lot of scanning using a Lexmark X1180 printer/scanner

A quick Googling revealed [http://www.sane-project.org/unsupported/lexmark-x1150.html](http://www.sane-project.org/unsupported/lexmark-x1150.html). 
It might of course be outdated but doesn't look good for that one...

> I like my keyboard just as it is, the Live CD didn't seem to have a suitable keyboard layout for a snow iBook G3, is there one?

What was wrong with the LiveCD's layout? There are some differences in the way the chooser keys work but I suppose it's possible to change that if you really want to...

> 
Developer tools, for doing on-the-fly compiles for stuff that Ubuntu doesn't have, even in Universe, like tinyfugue, TinyMUX/MUSH/Penn etc.


This one's easy, every GNU/Linux distribution worth it's salt provides a very comprehensive set of developer tools. You might try getting what's missing from Debian repos, though.

> 
Easy web-serving, Mac is great for that, just click and go, and it runs.

Well, it's the same web server Apple uses, Apache. Not so easy to configure if you want something specific but just installing it will enable you to drop files in /var/www and serve them. 

> 
Support for the built-in 'Close laptop and sleep' mode.


Not absolutely sure but I know it's working on some iBook G3s so might very well be on yours too...

> 
A keyboard way to eject the CD tray, as F12 is hooked by the mouse emulator
A right-click like OSX, using CTRL instead of F12, therby freeing up F12


You can configure this from the GNOME settings. You can also change the place of the mouse buttons on the keyboard if you wish to do so but I think there isn't a ready solution for making it ctrl-click. I think it would be nice too although it's mostly a matter of what you're used to.

---

### Post by Marcus Sipor Isalicus on 2005-05-09
I am also working to switching; I am now on Mac Mini, which I received only days ago. As I want to try out Ubuntu, I thought of partitioning my Hard disk and set OS X Tiger on one and Ubuntu Hoary on the other (got a CD from a friend). However, I am not too deep into computers (I love the Open Source ideology and all that, but I am not too technical), so now I have some questions:

How hard is this operation (partitioning the Hard disk and installing another Operating System)? 
What are the risks involved? (I'll probably lose all my data on the Hard disk, which is no problem, there are only one or two files I need to save as the Mini is brand new)
Should I get my friend over for this? (he's faraway at my parents's village)

---

### Post by Rxke on 2005-05-09
Getting a bit offtopic, but..
I guess the dual-boot approach is the best one, you can always choose which computersystem you use at startup. As a beginner that's great, sometimes one just doesn't feel like learningnew stuff, so back to old trusty OSX, heehee.

Installing dual boot is fairly easy if you partition your disk in 2 (or more) partitions using OSX's diskutilities. (both hfs+ journalled is ok, ubuntu change it, so no worries)  (to make it super easy later on, partition yr disk in non-identical sizes, say 20 and 30GB or something like that, and write down on which one you put your OSX os, so later when the Linux-gobbledygook  ;) starts, you can recognize the partition by its size, not by the weird descriptions (assuming total linuxnewbieness here...) and know you should keep your sticky hands off it, heehee... 
 In order to do that you'll have to startup from your systemdisk, (press c during startup) and select the diskutils in the menu, instead of installing X.

Yuo do indeed lose all your stuff, but as you say you're on a fresh machine that's no biggie.
Then install OSX on one of the partitions
Next insert your ubuntudisk keep c pressed at (re-)startup and follow the instructions.
When in doubt, just quit, go back to OSX, and post a question here.

Good luck!

(diskutils in Nederlands: schijfhulpprogramma...)

---

