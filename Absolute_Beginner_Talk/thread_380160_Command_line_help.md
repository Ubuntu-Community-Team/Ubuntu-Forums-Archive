---
title: "Command line help"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by anthonie on 2007-03-09
This is the place for newbees to ask stupid questions, right?

Let me kick off than...

The situation:

I run a dualboot Ubuntu 6.10 (updated) and WinXP.
As a windows manager I use Enlightenment D17.

Somewhere I read a thread that advised the start of gnome-theme-manager in order to get some more nifty icons on programs like Firefox and Nautilus. Now I know that is not the way it should be done, but it does get rid of an annoyance, the ugly icons...

My question now is, how would I automate that? Atm, whenever I log in to Ubuntu, the first thing I do is start a terminal and start gnome-theme-manager. 
As soon as that program has started my icons are just that bit better to bear. After it has been started (the gnome -theme-manager) I have to stop it by hand by either pressing the close button of the theme-manager, or close it by shutting down the terminal. Either way, it requires me to do two actions by hand, start the theme-manager and after that stopping it again.

I'm quite sure this could be done in a different way, but I don't see how.
If I write a batch script, the terminalprocess will be active for as long as I don't close the theme-manager. 

Any directions for some automation?

kind regards from a very happy Ubuntu user

---

### Post by maxamillion on 2007-03-09
I can't say much for e17, but in other desktop environments (Xfce and Gnome for example) have an "auto started applications" configuration tool and you can just enter that command as something to be auto started. I might recommend looking around e17 documentation or checking an irc server to find such a utility because writing a script and/or editing files to perform this for you would probably be more of a head ache then its worth especially if there is a tool to do it for you.

... just a thought :)

---

### Post by anthonie on 2007-03-09
Well, starting the app is not the problem. The problem is that the terminal that starts the gnome-theme-manager stays active until I press close on the g-t-m or close the Terminal screen. I have tried to include another script from the first one, opening another terminal will a kill command for the g-t-m, but somehow I can get it to work. I need a process ID for that (kill gnome-theme-manager does not do the job) but that ID changes with every boot so automating it does not work.

I have read the complete manual for E17, and couldn't find any mention of scripting in such a way.

Thanx for the reply, though!

---

### Post by Motoxrdude on 2007-03-09
Goto:
System>>Preference>>Sessions>>Startup Tab.
Click new and enter in a name (just any name, it doesn't really matter) and enter in the same command you would use in the terminal to start the theme manager.
Now click OK, and Close. Restart to see if it works.

---

### Post by anthonie on 2007-03-09
> **Motoxrdude said:**
> Goto:
System>>Preference>>Sessions>>Startup Tab.
Click new and enter in a name (just any name, it doesn't really matter) and enter in the same command you would use in the terminal to start the theme manager.
Now click OK, and Close. Restart to see if it works.


But would that also close the gnome-theme-manager after it has started?
I asking because I have some trouble finding the sessions under E17. It seems to be hidden somehow. Is there a terminal equivalent to start the same thing?

---

### Post by tcrroadie on 2007-03-09
^^^anthonie^^^

I believe what you are looking for is how to auto start gnome-settings-daemon when E17 is launched.  

gnome-settings-daemon will apply the GTK and Icon themes you set with gnome-theme-manager to your GTK applications.

Please see the link below on instructions on how to create an application launcher for E17 Startup Applications. 

Simply replace the reference to Esetroot with gnome-settings-daemon

[http://www.ubuntuforums.org/showpost.php?p=2139824&postcount=133](http://www.ubuntuforums.org/showpost.php?p=2139824&postcount=133)

---

### Post by anthonie on 2007-03-10
What I am looking for is not so much a way to start gnome-theme-manager at startup, as that should not be a problem. I want to stop that process automagicaly after it has started, without having to touch it myself, preferably without actually having to see the screen of the theme-manager at all. It is only used for the initiation of the icons that I start the program.  I still don get it, how I should stop that process.

---

### Post by tcrroadie on 2007-03-10
A little clarification.  

Gnome-theme-manager is used to set your gtk widget theme and icon theme for all gtk applications.  Think Firefox, Nautilus, Banshee.

Gnome-settings-daemon is a service that applies the gtk themes you set in gnome-theme-manager to your gtk applications. 

You only need to have gnome-settings-daemon auto started when E17 is launched.  Gnome-settings-daemon is a background service.  You won't even know it is running.  

Please see the link in my previous post for instructions on how to configure E17 to auto start gnome-settings-daemon.

---

