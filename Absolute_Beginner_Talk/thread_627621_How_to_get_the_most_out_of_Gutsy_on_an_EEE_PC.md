---
title: "How to get the most out of Gutsy on an EEE PC"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by CodeSamurai on 2007-11-30
Hey everyone! This is my quick little how-to on getting Gutsy to work really well and efficiently on an EEE PC.  First off, follow these steps to get Gutsy installed.  This tutorial worked great for me:
[http://ubuntuforums.org/showthread.php?t=611422]("http://ubuntuforums.org/showthread.php?t=611422")

Once you have this done, you have many options before you that can make your Gutsy + EEE PC experience awesome.  

**_Optimizing Screen Space_**

My first and favorite program is the AWN (Avant Window Navigator) which can be installed by doing the following:

Add the repos: you can paste both of these at once
> echo 'deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator' | sudo tee -a /etc/apt/sources.list

Add reacocard's apt-key:
> wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc

Then install AWN:
> sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

Awesome! After using the AWN manager, I got mine to look something like this:
[IMG]http://i30.photobucket.com/albums/c326/CodeSamurai/Screenshot.png[/IMG]

As you can see, I also removed the bottom toolbar.  I made it so that AWN would also hide when not in use, this gives you another 1/4" of screen space overall.  

More info about AWN is available here:
[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")

For this size of screen, it is best to use the multiple desktop option.  Personally I prefer the wall (although the cube does work flawlessly on the eee pc) so under System>Preferences>Keyboard Shortcuts I set to move 1 space to the right as "Shift+Right Arrow" and "Shift+Left Arrow" to move left.  This gives you a ton more room to work.  Give and take workspaces as you please.  

As for the terminal, I used this great tutorial:
[http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop]("http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop")
One thing I had to change however was when in the profile editor for the terminal, go to the Title and Command tab, set "Dynamically Set Title" to "isn't displayed".  This will get the border to go away.  In the end, I got this:

[IMG]http://i30.photobucket.com/albums/c326/CodeSamurai/Screenshot-1.png[/IMG]

This is an excellent Space Saver.  I set "F10" to open the terminal.  Also, I did not make it so the terminal started on login.  That just got be annoying.  
[B][U]
Tweaks:[/U][/B]

Screenlets and Widget Layer;

Another great tutorial: 
[http://ubuntuforums.org/showthread.php?t=589403]("http://ubuntuforums.org/showthread.php?t=589403")
This will allow you to have a widget layer for your screenlets.  The default accelerator is F9, so you might want to change it to something like F12 under the widget layer preferences.  You can then download screenlets and install them (extract the file to your ~/.screenlets folder).  If this folder doesn't exist, just create one.  The screenlet manager doesn't like to install screenlets yet, so this is the best option.  Mark your screenlets to startup automatically, and you've got yourself a dashboard! 

[IMG]http://i30.photobucket.com/albums/c326/CodeSamurai/Screenshot-1-1.png[/IMG]


For a mail application, I used Thunderbird.  This played more nicely with the screensize than evolution did.  

Other Programs that work nicely:
Sunbird (calendar)
Pidgin (IM)
Tomboy Notes (Notes)
OpenOffice.org 
Firefox
Gimp (Photo editor)

If you guys have any questions or want more screenshots, let me know.  I'll get them answered as quick as I can.  This is my first how-to, so it's a little messy, but I'll work on it.  Thanks!

Trent Out

---

