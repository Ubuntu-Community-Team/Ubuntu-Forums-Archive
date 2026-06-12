---
title: "Good High Level Overview?"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by catnippants on 2007-10-16
Folks,
   What's the best source to get a high level overview of the directory/configuration structure of Ubuntu Linux?   

I'm a fairly experienced PC 'user' (about 27 years now) of everything from old DEC PDP systems Unix, AIX,  DOS, all Windows versions since v1.0, etc.   I recently decided to start playing with Linux and installed UbuntuStudio - fairly successfully.    One thing I've learned already is that Linux is still not ready for prime time.   It's not an operating system for the novice.   Far too many things can go wrong with the installation, it has stability issues, GUIs are incomplete, driver issues, etc.   During my installation, I was able to solve many of my issues through web searches - many of which were pretty obscure.  In many ways, setting up hardware in Linux reminds me of the old DOS days.   Being a person who doesn't mind editing configuration files manually and who actually likes to do things via terminal command line, I'd love to get a feel for what files control what.   In other words:

1. At a very high level, what purpose/function does each of the file system directories serve?   What info is stored where?
2. What are the key hardware and software configuration files?   In dos we has the autoexec.bat, config.sys, etc.    Windows had ini files then the registry.    What .* files do what in Linux?
3. What are the key system editors to do manual configuration? Is this what the gconf-editor is for?

As an example, I'm having a problem with mp3 playback speed at the moment, and I suspect it has to do with default sampling rates somewhere.   Where would I start to look for config files that control this?   As another example, yesterday I had a boot up problem where I'd end up with a blank screen after login, and I had NO clue how to start to diagnose it.   After a lot of reading and troubleshooting, I was able to figure out that my soundcard was set to look for an external clock (ie: SPDIF in), and the os couldn't initialize it during boot (at least that's what I think happened).

Essentially, I'm trying to learn how to figure out where to start when debugging issues.   With DOS I could always delete a few lines from a config file, boot clean and start to troubleshoot.  Linux is MUCH more complex, and I just don't know where to start.   I need a good high level overview.

So, any book or website recommendations?  Keep in mind, I'm not looking for a book on how to use the GUI or how to use Linux through the GUI.   I'm looking for something as a starting point to understanding how Linux works...

Any thoughts would be appreciated...
Thanks,
Mike

---

### Post by Kilz on 2007-10-16
Ok, I think you will love linux. There are tons of good sites. One odf the strengths of linux is the sheer volume of info avilable on the internet. Google is our friend. 
For the most part config files are in /etc

[Here is a good site for the file system overview]("http://tldp.org/LDP/intro-linux/html/sect_03_01.html").
[You might also find this site invaluable for commands.]("http://www.ss64.com/bash/")
[The wiki is always a good place to start for troubleshooting.]("https://help.ubuntu.com/community/")

---

### Post by catnippants on 2007-10-16
Cool - thanks!   I will take a look!

Mike

---

