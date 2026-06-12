---
title: "nautilus search function"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by tc101 on 2007-01-17
Using Nautilus 2.16.1 with Ubuntu 6.10, when I do a search on the whole file system it doesn't ever find anything.  If I want to search the whole file system I have to select the individual directories under the main file system icon.  Also, when I try to search the sys directory it hangs up and never returns any results.

Is this some problem with the way I am doing things, or just the nature of nautilus?  Is there a better search tool available?

---

### Post by Rhubarb on 2007-01-17
I've recently discovered Beagle.
A slightly old version of it is in the Add/Remove software in your Applications Menu.
It's called "Search" there.
It can search your thunderbird email, GAIM logs, music and video (and their tags), documents, and general files.
The newer version that you'll have to compile yourself can search through evolution mail aswell.

[http://beagle-project.org/](http://beagle-project.org/)

---

### Post by ComplexNumber on 2007-01-17
i just use gnome-search-tool. for some reason, its not in the main menu (thats why i added it). i rarely use the search thats on the toolbar in nautilus. there should be an option under 'File' in the menu next to where it says 'Open in Terminal'. however, there is no nautilus-search package in the repositories.

---

### Post by Rhubarb on 2007-01-17
I forgot to mention the newest version of Beagle supports searching from within Nautilus (using scripts / plugins?) too.  ;)

---

### Post by tc101 on 2007-01-25
Beagle search seems very limited.  What if I want to search for files of a particular date or size, or within a particular directory.

---

### Post by Twiggy794 on 2007-01-26
> Beagle search seems very limited. What if I want to search for files of a particular date or size, or within a particular directory.
I'm not sure Beagle is what you want...when you're searching your whole filesystem are you looking for system files?  Beagle will only index the directories you tell it to, and indexing your entire / would be murder on your performance.  As well, it's not designed to be so specific of a search tool.  It's meant to be simple for the layman.  Try using find if you need to do advanced searches.

---

### Post by 23meg on 2007-01-26
Try *locate* / *slocate*.

---

### Post by tc101 on 2007-01-26
Wow !   locate and slocate are just what I was looking for.

Where are some good instructions on these commands?  It would be nice to find some instructions with examples

 This is what I am using but I think there must be better instructions somewhere:
[http://www.onlamp.com/linux/cmd/cmd.csp?path=l/locate](http://www.onlamp.com/linux/cmd/cmd.csp?path=l/locate)
[http://www.onlamp.com/linux/cmd/cmd.csp?path=s/slocate](http://www.onlamp.com/linux/cmd/cmd.csp?path=s/slocate)

---

### Post by tc101 on 2007-01-26
I just learned that everything I was looking for is already there in the "Search for Files" applet.  In case someone reading this doesn't know about it, here are instructions:

Right click on the bar (panel) across the top of your screen and click
Add to panel. You should see a whole bunch of widgets of varying
utility, of which one is the Search application.

---

### Post by Buck2348 on 2007-01-26
I use the gnome-search-tool, which is the same as "Search for Files" applet that you found.  I have noticed that this also doesn't always find everything it's supposed to be looking for.  The only solution I've found is to run it as root, since I don't have permissions to search all directories.  In a terminal type "gksudo gnome-search-tool".  If you want to make a launcher for that in the panel right-click in the panel, select Add to Panel and choose Custom Application Launcher, and give it the same command.

Buck

---

### Post by Drakkor on 2007-01-26
Yep,dito, I used to have the applet, but now I just go to Places>Search for Files, then,select under "Look In", select filesystem, you should find the files you're looking for.

---

### Post by tc101 on 2007-01-26
I either have two different search apps or I don't know how to use them.  

The one I get clicking Places>Search says "Desktop Search" at the top

The one I added to my panel says "Search for Files" at the top and has more features.

---

### Post by mover47 on 2007-01-28
I had the exact same problem with Nautilus's quick find <Ctrl+F>, and Beagle's a pain. I would search for things like 'bin', 'fstab', and parts of file names. The search would consistently return '0 items', which I though was strange. 

Here's how I 'solved' the problem. I accidentally deleted my top panel, then restored it and added the menu bar. On a whim, I tried the Nautilus search again (from any window "Search" button or <Ctrl+F> and viola!--it worked. 

Now, when I search for 'etc', I get 283 items, including the folders I was actually looking for. 

So, there's a weird solution. Anyone want to try and explain it?

---

