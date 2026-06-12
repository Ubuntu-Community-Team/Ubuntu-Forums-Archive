---
title: "Your advice please!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-04-21
Related Launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+bug/104521](https://bugs.launchpad.net/ubuntu/+bug/104521)

Okay, originally I'd intended to backup my Ubuntu partition with Partimage. Now, xserver crashed about 30 mins to 45 mins ago(got a Bonobono+ nautilus crash error) and since then, my Applications menu is inaccessible and same for Main menu" from "System===> Preferences".  A short while later, I found out that Firefox crashed and lost all its' history. 

Launching programs within Terminal give me various errors and warnings(perhaps because I'm not launching them the right way, that is, through the GUI). 

Is this a sign of some corruption(that is, a sign of greater problems) within Ubuntu or should I just fix this error and just go on with my life(that is, clone the partition using Partimage)? If this is a critical issue, I'd rather just download Feisty final and patch from there. 

Sorry if I'm being paranoid but after trudging through 2 corrupted installs of Dapper and other issues, I just want to try and play it safe this time round. Normally, if this was WindowsXP, I'd just do a fresh reinstall. 


So, your advice, please! :)

---

### Post by Pobega on 2007-04-21
Did the crash have anything to do with PartImage?

And what are the errors?

---

### Post by Lucifiel on 2007-04-21
No, the crash has nothing to do with Partimage.

This was the error:
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory.Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

Then, I restarted the pc and I can't access the "Applcations menu" anymore. Also, "Main menu" from "System===> Preferences" is not accessible either.

Does this mean I should go ahead and kill bonobo-activation-server  ? I'm not too familiar with the finer points of Ubuntu. :p

---

### Post by Pobega on 2007-04-21
Hm. What do you mean that you can't access it? Is it a permissions error, or is it just not opening (i.e. Empty)

---

### Post by Lucifiel on 2007-04-21
Oh when I try to click on "Applications" from the top taskbar, it doesn't appear.

And when I click on "Main menu", it will say "Starting Main menu" but then the service doesn't start. Hmmm...

---

### Post by Pobega on 2007-04-21
Maybe try reinstalling gnome or gnome-panel to see if that works? I'm not sure where GNOME keeps it's menu data (I'm not using GNOME but I'd guess ~/.gnome or ~/.gnome-panel), but if you don't want to mess with removing/installing packages you can try clearing files that look like menu files.

Or maybe it's a simple fix, just try turning everything back on in alacarte (The GNOME menu editor) by running alacarte from the run dialog (Alt+F2).

---

### Post by Lucifiel on 2007-04-21
> **Pobega said:**
> Maybe try reinstalling gnome or gnome-panel to see if that works? I'm not sure where GNOME keeps it's menu data (I'm not using GNOME but I'd guess ~/.gnome or ~/.gnome-panel), but if you don't want to mess with removing/installing packages you can try clearing files that look like menu files.

Or maybe it's a simple fix, just try turning everything back on in alacarte (The GNOME menu editor) by running alacarte from the run dialog (Alt+F2).

Hmmm... I tried to launch alacarte from alt + f2. Hmmm... it didn't start. 

From reading the site below, it seems that Bonobo controls all the Gnome components? Okay, *takes a deep breath* I'll try to kill it. Hopefully, that won't kill Ubuntu. Then, if that don't work, I'll try reinstalling gnome-panel. 

[http://www.die.net/doc/linux/man/man1/bonobo-activation-server.1.html](http://www.die.net/doc/linux/man/man1/bonobo-activation-server.1.html)


Thank you for your help! :D

---

### Post by Pobega on 2007-04-21
If it's not starting from Alt+F2 try starting it from a terminal, usually the terminal outputs good error messages (Something I can work off of to help identify your problem).

If the problem is bonobo then it sounds like you'll need a reinstallation of GNOME; I'd purge and then reinstall, just to get rid of everything. But that **will** clear out a lot of your settings.

---

### Post by Lucifiel on 2007-04-21
Oh dear, killing bonobo + restarting the pc didn't work. I wonder if installing Gimp killed my applications. Yikes... reinstalling Gnome, huh? 

lucifiel@lucifiel:~$ alacarte

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

---

### Post by Pobega on 2007-04-21
It looks to me like Python/XML may be the problem. First off, try installing:

sudo aptitude install python-xml python-lxml

If that doesn't work I'm out of ideas, maybe someone more knowledgable will be able to come along and help you out.

---

### Post by Lucifiel on 2007-04-21
Huh, so I ran :
sudo aptitude install python-xml python-lxml

It installed but nothing happened yet, I'll try restarting X and if not, I'll restart the pc. Be back soon.

It was really nice of you to help. :)

Edit: Okay restarting X didn't work, neither did restarting the pc. Geez, why do computers break so much sometimes? :P

---

### Post by Pobega on 2007-04-21
Yeah, it sounds like either python or GNOME need a reinstall.

sudo aptitude reinstall python2.5

**Edit:** It's nice to be thanked, and no problem :)

Even though I come from the Debian community I see Ubuntu users as my fellow brothers and sisters, so I try to help you guys out as much as I can; Who knows, maybe one day someone from here will be the next Debian Project Leader?

---

### Post by Lucifiel on 2007-04-21
All right, I reinstalled python 2.5 . I'll restart the pc now.

Edit: Hmmm... nope, restarted the pc and still Applications menu is gone. How about I try uninstalling Gimp and see if that does anything?

---

### Post by Pobega on 2007-04-21
That might do something. I'm not an expert at this (Again, I don't use GNOME) but I doubt the GIMP would have done much. But it's definitely worth a shot.

---

### Post by Lucifiel on 2007-04-21
Uh oh, it seems that I installed Gimp 2.2.14 over Gimp 2.2.13 and now I can't find a way to remove it. =/

Yikes... next time, crashes or not, I'll wait for someone to compile the .deb file instead of trying to install the application myself.

---

### Post by Pobega on 2007-04-21
You can still remove it; Go into the source directory (if you installed it from source) and run:

make uninstall

Should work.

If you **did** install it from a .deb, you can always use apt/dpkg to remove it. dpkg -r gimp, or something similar, should work.

---

### Post by Lucifiel on 2007-04-21
Woot, thanks!!!

That worked, man. :) Now that it's uninstalled, perhaps I'll try reinstalling python, etc. again. This is because Gimp uses Python dependencies and it might have broken some of them. :p

---

### Post by Pobega on 2007-04-21
Yeah, just do a quick

sudo aptitude reinstall python2.5 gimp

And see if everything works. Installing from source on a Debian-based system generally doesn't work unless you know how to mess around with the source code to get everything playing nicely together.

---

### Post by Lucifiel on 2007-04-21
Okay now that I ran "sudo aptitude reinstall python2.5 gimp"
I'll try restarting the pc again.

Edit: Well, I didn't really know I could get so many problems by installing from source. ^^;;

---

### Post by Lucifiel on 2007-04-21
Darn... that didn't quite work. 

And reinstalling Gnome isn't the best idea, is it?

---

### Post by Pobega on 2007-04-21
It sounds to me like it's the only option left for you, unless someone comes along with an amazing solution.

I'm not sure what the problem could be related to, maybe try reinstalling Alacarte first and see if it happens again, I don't know.

This is a pretty weird problem, and I'm surprised I'm the only person helping you.

---

### Post by Lucifiel on 2007-04-21
> **Pobega said:**
> It sounds to me like it's the only option left for you, unless someone comes along with an amazing solution.

I'm not sure what the problem could be related to, maybe try reinstalling Alacarte first and see if it happens again, I don't know.

This is a pretty weird problem, and I'm surprised I'm the only person helping you.

Yeah well, you might be right.

I'm not sure if reinstalling Alacarte will work but I'll give it a shot.

Well, for me, most of my Ubuntu problems have been pretty weird or strange. =/ They're likely to make you wish you could hold a conversation with your computer.

Btw, should I try reinstalling everything related to python?

---

### Post by Pobega on 2007-04-21
I really doubt it's a problem with Python, I was just taking a quick guess.

A reinstall of GNOME and if possible Ubuntu would be the best solution in my opinion.

Maybe try Googling around to see if others have experienced this problem too.

Your best bet is to google your error message with quotation marks around it (The last line with the bit about xml).

---

### Post by Lucifiel on 2007-04-21
> **Pobega said:**
> I really doubt it's a problem with Python, I was just taking a quick guess.

A reinstall of GNOME and if possible Ubuntu would be the best solution in my opinion.

Maybe try Googling around to see if others have experienced this problem too.

Your best bet is to google your error message with quotation marks around it (The last line with the bit about xml).

Okay thank you. :) 

Hmm... there are others who've the same problem like me too but one link is in French, lol, and the other topic: no one replied to it.

[http://72.14.253.104/search?q=cache:QUmnnFe2UDEJ:forum.ubuntu-fr.org/viewtopic.php%3Fpid%3D862536+xml.parsers.expat.ExpatError:+no+element+found:+line+1,+column+0&hl=en&ct=clnk&cd=23&gl=sg&client=firefox-a](http://72.14.253.104/search?q=cache:QUmnnFe2UDEJ:forum.ubuntu-fr.org/viewtopic.php%3Fpid%3D862536+xml.parsers.expat.ExpatError:+no+element+found:+line+1,+column+0&hl=en&ct=clnk&cd=23&gl=sg&client=firefox-a)

[http://gnomesupport.org/forums/viewtopic.php?t=12445](http://gnomesupport.org/forums/viewtopic.php?t=12445)

---

### Post by Pobega on 2007-04-21
Looks like neither has answers; A clean GNOME or install may be the best option here.

---

### Post by Lucifiel on 2007-04-21
Yeah you might be right. :D 

I'll try googling around some more and asking in Gnome forums too or LinuxQuestions. :p

---

### Post by Lucifiel on 2007-04-21
Ooh, I was chatting in #ubuntuforums-beginners and they got me to create a new user profile. Wow.. that totally worked, man! No more problems!!! :)

---

### Post by Danger2Society on 2007-05-17
Well basically your problem was that the .menu files in your ~/.config/menus folder were corrupt.
So the most basic way to is to create a new user account then open up a shell and then copy your newly created menu files and replace the old ones in your old user account.

---

