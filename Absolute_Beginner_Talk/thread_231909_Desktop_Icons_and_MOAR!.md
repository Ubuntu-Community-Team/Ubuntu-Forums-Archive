---
title: "Desktop Icons and MOAR!"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Tixer on 2006-08-08
I just installed ubuntu in VMWare (Current box hosts site, Ubuntu'll go on new desktop when it arrives, but for now, I just thought I'd play around since I convinced some friends to switch, and they'll be coming to bug me for tech support, UGH!

Aynways, aside from dragging items to the desktop, how do I get icons for Trash, Compy, etc?

How do I enter a space? I broke my space bar from eating cereal and watching anime, so I've got 48 hours till new one arrives. In Windows, like now, I either use Alt-32, or copy a space, but Alt-32 doesn't work.

Also, where can I get a list of items in Apt-get? I've noticed that  there are specific names, like Mozilla-thunderbird, so is there a list?

Also, I wish to play Starcraft, is there a guide for n00b wine?

Also, is there a list of Keyboard shortcuts available?

BTW, I'm on Kubuntu.

---

### Post by Danblade on 2007-05-31
I hit your post in search of how to get the apt-get list of items that are accessible.  I found the following info on the "debian" site... 
Whether you're online or not--

[SIZE="6"]"[/SIZE]How do you find the package that's got the feature you're looking for? First, do 
#** apt-get update**
		
 
so your package list is up-to-date, and then try something like                                                      
% **apt-cache search** tunnel
% apt-cache search 'php.*sql'
% apt-cache search apache.\*perl
% apt-cache search elvis\|vim
		
 
That is how you tell apt to search the packages you've downloaded, using REGEX (regular expression, a pattern-matching 'language') -- if your pattern uses any keystrokes that mean something to your command shell (e.g. [|?*] ) you'll need to quote them so that apt-cache will be able to see them, instead of having the shell expand the term to a list of file names that mean something else entirely.[SIZE="6"] "[/SIZE]

This of course is the way to run it in a terminal, (I have not yet learned how do do this in the GUI).

---

### Post by Zero Prime on 2007-05-31
To get icons on your desk top (ie..the trash can and more) the easiest way is to right click on your applications menu and click on edit menu.  Go down to System Tools and click it.  Put a check mark in the box beside configuration editor.  Now close the menu.  Go back and left click Applications and go to System tools, open configuration editor.  Expand Apps, then Nautilus, then open Desktop.  In the right pain you will see options that will place certain icons on your desktop.  Check the ones you want then close.  You may have to restart X to get the icons to show.

---

