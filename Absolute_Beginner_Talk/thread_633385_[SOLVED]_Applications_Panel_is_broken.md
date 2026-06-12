---
title: "[SOLVED] Applications Panel is broken"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2007-12-06
I'm running Ubuntu 7.10, new to Linux in general. I managed to break the Application Panel and I'm not sure how to fix it. Here's what happened:

Hard drive ran out of space on "/"
Turns out this was because it's a 30GIG partition and I had configured "simple backup" to save backups to /var/backups and that directory was at 30GIG.

I manged to figure out how to use "rm" to delete everything in that directory using the command "rm -v /var/backup/*" and that worked great

But while the machine was in this Out of hard drive space condition, I right-clicked on the word "Applications" in the Panel, and choose the option "Edit Menus" and nothing happened. So as soon as the 30GIG of data had been deleted, I rebooted the machine. 

Now when I click on the "Applications" menu, the menu highlights orange, and then nothing happens. The "Places" and "System" menu work normally - it's just the application menu that is broken.

And when I right-click on the "Applications" and choose "Edit Menus' I see briefly a box at the bottom reading "Starting Main Menu", it lasts for about 10 seconds, and then disappears.

I'm really lost without my Applications menu - how do I repair this?

---

### Post by betes on 2007-12-06
Not sure about a solution, but have you tried removing the Applications menu from the panel and then adding it back.  That has worked to reset the settings on some panel items I've messed up before.  Just 1) right click on the Applications and select remove from panel. Then 2) Right click on blank space on the panel and select add to panel. 3) Find the Menu Bar to add the menu back.  It might not fix your problem, but won't hurt to try.

---

### Post by Nano Geek on 2007-12-06
Run this and see if it helps. It will move you current GNOME configuration to a different folder and give you the default one in its place. ```
mv ~/.gnome2 ~/.gnome2-backup
``` Then restart and see what happens.

EDIT: Try the guy before me's idea first.

---

### Post by daimaru on 2007-12-06
to start main menu edit from terminal use 
```
sudo alacarte
```
maybe this will output some error message if it failes to start. then you could post that here.

you could also try just rebuilding your application menu just right click it on panel choose "remove from panel" once its gone reinsert it by right clicking pannel, choose "add to panel" and then under section "Utilities" right at the bottom choose "Menu Bar" that gets you back your menu. may then it will work: ??

---

### Post by vortex0007 on 2007-12-06
Well I appear to have made it worse.

I misread BETES reply and instead of clicking on the Application menu, I clicked on a blank part of the panel, and chose "delete this panel" - now I have no panels at all.

So I ran "mv ~/.gnome2~/.gnome2-backup" and rebooted
still no panels

so I tried running "sudo alacarte" and I get the following error:

/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
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

### Post by vortex0007 on 2007-12-06
Sorry one more update:

I was able to get the "Main Menu" to launch from terminal using "alacarte" after I switched to root. But I don't show a way to add a blank panel to get all the things listed back. I clicked on the "revert" button but I think all that did was reset the options shown in the menu - it certainly did not add a panel back.

---

### Post by Nano Geek on 2007-12-06
To get you old panel back, just right-click on your current one and click **New Panel**. Also run ```
sudo apt-get install ubuntu-desktop
``` it could be that something important got deleted accidentally.

---

### Post by vortex0007 on 2007-12-06
Running "sudo apt-get install ubuntu-desktop" and rebooting has not solved the problem.

Running "sudo apt-get autoremove ubuntu-desktop" was successful, then re-running 
"sudo apt-get install ununtu-desktop" and receiving "install successful" followed by a reboot has not solved the problem.

At this point there are no Panels on the desktop at all and if I hadn't accidently put a launcher to the terminal on the desktop prior to screwing the panel up, I wouldn't even be able to launch the terminal (for lack of knowlege - not because something is necessaryly broken).

---

### Post by betes on 2007-12-07
What about trying this:

sudo apt-get --reinstall install gnome-panel gnome-panel-data

And just fyi- if you need to get to a terminal and you don't have the panels or the desktop launcher you can always press ctrl+alt+F1 !!!!BUT BEFORE YOUR DO THAT!!!! make sure to know that to return to your normal graphical interface you need to press ctrl+alt+F7.  The first time I read a howto about switching to another session using ctrl+alt+F1 I did it before I read how to switch back, and since I didn't know any commands, I was stuck!

---

### Post by vortex0007 on 2007-12-07
THanks. I ran your command and before I reboot I thought I'd post the output here, in case it helps troubleshooting....

Here's the output: off the reboot

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/1095kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 113340 files and directories currently installed.)
Preparing to replace gnome-panel 1:2.20.1-0ubuntu1 (using .../gnome-panel_1%3a2.20.1-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-panel ...
Preparing to replace gnome-panel-data 1:2.20.1-0ubuntu1 (using .../gnome-panel-data_1%3a2.20.1-0ubuntu1_all.deb) ...
Unpacking replacement gnome-panel-data ...
Setting up gnome-panel-data (1:2.20.1-0ubuntu1) ...

Setting up gnome-panel (1:2.20.1-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by Krydahl on 2007-12-07
Have you tried typing "gnome-panel" into a terminal?

---

### Post by vortex0007 on 2007-12-07
I really appreciate the help.

Okay, making progress, still not fixed.

After the reboot I still do not have a panel at the top of the desktop screen.  I didn't realize I could right-click on the panel at the bottom of the screen, and choose "New Panel,", so I went ahead and did that, and then dragged the panel to the top of the screen.

So I had a bottom panel where everything is normal and a top panel that is blank.
I right-clicked, chose "Add To Panel" and this launched the menu to select what you want on the panel.

After a few minutes playing around with different options, I've isolated the problem as follows:

What I want to get back on my panel is the option named "Menu Bar" - when I click on this option, from the "Add to Panel" menu, the "Menu Bar" is added to the blank panel at the top of the screen, but when I click on the word "Applications", instead of dropping down the menu bar with a list of items all I get is what looks like a single pixel drawn just below the Ubuntu logo. I'll attempt to post a screen shot. What's interesting, is that the rest of the "Menu Bar" works correctly.

I've tried removing "Menu Bar" from the panel, and adding it back, and that makes no difference. 

How can I get just the "Menu Bar" option to reset back to normal - or even better, what can I do to diagnose why this isn't working anymore?

---

### Post by vortex0007 on 2007-12-07
Okay forget it - I'm screenshot challenged in Linux. :-(

---

### Post by betes on 2007-12-07
I might be at the end of my limited knowledge. But I'll keep responding to bump your thread up and hopefully someone who knows more will help. 

Here's one more thing to try:

1) Right click the "Menu Bar" on your top panel and uncheck "Lock To Panel".
2) Right click the "Menu Bar again and select "move".
3) Move the "Menu Bar" to your bottom panel (by moving your mouse down there and right clicking)

That probably won't fix it, but it will rule out that your top panel is somehow the problem.

Another diagnostic (not a fix) is to

1) Create a new user by going to System>Administration>Users and Groups.
2) Log in as the new user and see if the new user also has the same problem.

---

### Post by vortex0007 on 2007-12-07
Thanks - I tried moving it (neat trick) to the bottom panel - I was able to move it below, but it doesn't change the behavior. Still broken. :-(

---

### Post by betes on 2007-12-07
Another try! (I keep getting new ideas.)

1) Right click the "Menu Bar"
2) Select "Edit menus"
3) A new window will open with 2 panes.
4) In the left pane choose "Applications"
5) If nothing is checked in the right pane then thats your problem!
6) If Nothing is checked just check what you want to appear there "Accessories, Games, Internet, Graphics, Office, Sound and Video, and Other" are standard.
7) If everything is checked and its still broken...I'll try to think of another idea.

---

### Post by Niniel on 2007-12-07
I'm surprised nobody's suggest the obvious yet - reinstall the whole system. :lolflag:

But seriously - Vortex, have you tried Bete's idea of creating a new user yet?

---

### Post by vortex0007 on 2007-12-07
So I'm trying betes latest idea: 

1) Right click the "Menu Bar"
2) Select "Edit menus"
3) A new window will open with 2 panes.

I'm stuck at 3) - a new window never opens with the 2 panes. 

I'm also attempting Niniel's idea and creating a new user.

Will post back when this finishes.

---

### Post by betes on 2007-12-07
> **vortex0007 said:**
> So I'm trying betes latest idea: 

1) Right click the "Menu Bar"
2) Select "Edit menus"
3) A new window will open with 2 panes.

I'm stuck at 3) - a new window never opens with the 2 panes. 


hmm... I thought that was going to work, because when I unchecked all of my menus in the "edit menu " tool I got the exact same outcome as you do, just a single pixel appeared below the Ubuntu logo. (It looked exactly like your screenshots.)  

So when you right click and select "edit menus" what happens?  Nothing? Just to be sure (I know this sounds condescending) are you *clicking* on "edit menus"?  I just want to make sure you didn't expect a drop down box to appear.

---

### Post by vortex0007 on 2007-12-07
The problem is solved!

Creating a new user fixed the problem. 

Thank you everyone for your suggestions.

---

### Post by Niniel on 2007-12-07
> **vortex0007 said:**
> 
I'm also attempting Niniel's idea and creating a new user.


That was *Bete's* idea, not mine. :)

Glad that's working for you now. Don't screw up again! :)

---

### Post by betes on 2007-12-07
> **vortex0007 said:**
> The problem is solved!

Creating a new user fixed the problem. 

Thank you everyone for your suggestions.

Excellent!

Just to make sure you are aware, you have to give the new user admin privileges if you plan on running as the new user permanently.  This has to be done from the old users account (by going to the same place you went to set up the new user.)  Also, if you have things on your home folder you'll need to share them with the new user so you can copy them over.  Plus whatever settings you've made as the original user will be lost (though programs installed will still be the same).

All of that is a pain, which is why I said that the new user was more of a diagnostic than a solution.  That is to say, it proves that your user settings are somehow the problem.   Anyway, none of the above matters to you then you can run as the new user permanently and it shouldn't be a problem.

---

### Post by vortex0007 on 2007-12-08
Thanks for the additional details Betes. That was another lesson I learned the hard way when I deleted the old user account and then logged back in under the new user and met permission hell. Through some freak accident  I got the terminal to load and was able to restart so I could log back in under root, then I restored the permissions to the new user account and now things are working wonderfully.

---

### Post by jollo on 2007-12-13
I have exactly the same problem with 7.04 (feisty): while temporarily out of disk space, right clicked on Applications menu, clicked on Edit Menus, got a "Starting Main Menu" tab in the panel (bottom) for a few seconds but the Menu Layout window did *not* open and the Applications menu is *broken* since (that is, looks "empty" - nothing drops down), even with Alt-F1. :(

Places and System menus look fine. On reboot the desktop wallpaper disappeared (got reset to "no wallpaper"). The Run Application window (Alt-F2) shows an *empty* list of known applications :( :(

I would have liked to check with Add/Remove if the information on the installed applications is ok, but I don't know how to invoke it form a command shell. Synaptic reports all packages are ok, though.

Adding a Main Menu to the top panel creates a duplicate Applications menu with exactly the same problem:  it looks "empty" - nothing drops down.

Trying sudo alacarte from a terminal gives the same error reported by Vortex:

[I]Traceback (most recent call last):
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
xml.parsers.expat.ExpatError: no element found: line 1, column 0[/I]

seems to suggest that it failed to load some menu configuration file, but then trying to run it as root givers:

[I] /var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py:50: GtkWarning: cannot open display:  
  self.gnome_program = gnome.init('alacarte', version)[/I]

??? :(

My - uninformed - hypothesis is that the Menu Layout editor (alacarte) corrupted the menu configuration while out of disk space. Since the system looks otherwise sound, I would like to try and restore just that: can anyone advise what files are we talking about, where are they located and how to - if possible - rebuild  or get back to a "default" Applications menu?

Thanks in advance!

---

### Post by jollo on 2007-12-13
Just an update: reinstalling gnome-panel (*sudo apt-get --reinstall install gnome-panel gnome-panel-data*) didn't reset the Applications menu (still "empty"). Moving it aroount doen't matter. 

A new user, on the other hand, gets a fully functional Applications menu. 

Of course, I could switch permanently to the new user, but I would really like to fix the broken one... perhaps by copying the applications menu configuration freshly created for the brand new user? I just need to know where to start looking...

Thank again in advance for any tip...

---

### Post by jollo on 2007-12-14
Found the corrupted file: ```
/home/affecteduser/.config/menus/applications.menu
```

It was overwritten to empty by alacarte while out of disk space. Just copied the same file from an unaffected user's home (If you don't have another unaffected user, just create one), edited the home paths appearing in the file to show the correct (affected) user name and saved. The menu is back to normal without rebooting :cool:

Hope this helps! 

Take care

---

### Post by mikebeecham on 2007-12-17
Can I just say that I have been working on this for about 5 hours solid.

Jollo...yer a star.  Actually, I navigated to the same folder.  I have an applications.menu.back file.  I copied the contents from there, and pasted into my blank applications.menu file and saved....

...everything is back fine now!

---

### Post by jollo on 2007-12-19
Way to go! Your solution is even better...

I didn't have an applications.menu.backup, perhaps because I had never actually edited the menu layout before, so I had to go and find it in another user's home.

Actually, a friend suggested an even simpler solution: just rename (or delete) the whole .config directory in the affected user's home and it gets rebuit to default. I didn't want to loose Wine menu settings, so I wouldn't have gone this way...

Take care!

---

### Post by ben2talk on 2007-12-30
Hi everyone, I followed this user's problems. The problem doesn't exist with another user account - but in the ORIGINAL account with the problem. Is the problem to be left unfixed? It seems a rather weak solution to have to delete my account and start over . . .

My problem is identical. Wouldn't it be a good idea to duplicate the MENU settings from another account?

---

### Post by ben2talk on 2007-12-30
Hi everyone, I followed this user's problems. The problem doesn't exist with another user account - but in the ORIGINAL account with the problem. Is the problem to be left unfixed? It seems a rather weak solution to have to delete my account and start over . . .

My problem is identical. Wouldn't it be a good idea to duplicate the MENU settings from another account?

---

### Post by ben2talk on 2007-12-30
Okay. Thanks for your attention. I think that your solution works, however I don't want to start a new account. There are many settings, and many hours of work here... so I tried something else first.

I started up my Thunar file manager, and found my way to [I]ben/.config/menus[I] which showed me many backup files, which I assume were written whenever I moved and adjusted my menu contents.

I simply deleted all of these files, except for the 'applications-merged' folder. My applications menu (which was still running) now opens with all of my programs (including recently installed software) listed there.

I have a question about menu's. Something I discovered I could do with XP was to 'browse' the menu with explorer, and simply drag and drop the shortcuts into folders of my choosing. This is very simple to do, and allowed me to make up my own trees. Would this be difficult to achieve in Ubuntu?

The second thing I do really miss with Vista is that just one key press is all you need to launch everything - press the windows button and start to type....

Maybe something for another thread. Thanks a lot for the practice, and for the pointer to /home/affecteduser/.config/menus/ - this ultimately was all that I required.

---

### Post by jollo on 2007-12-30
> **ben2talk said:**
> Hi everyone, I followed this user's problems. The problem doesn't exist with another user account - but in the ORIGINAL account with the problem. Is the problem to be left unfixed? It seems a rather weak solution to have to delete my account and start over . . .

My problem is identical. Wouldn't it be a good idea to duplicate the MENU settings from another account?

Yes, exactly! That's what I meant... perhaps not too clearly! :) The idea is to replace the corrupted file (which, for the sake of clarity, in my case was ```
/home/affecteduser/.config/menus/applications.menu
``` ) with one from an unaffected user's home. If you don't have an unaffected user on your system, you can create it on the fly and then, once you have fixed the problem with your "original" account, get rid of it. 

> ... found my way to [i]ben/.config/menus[i] which showed me many backup files, which I assume were written whenever I moved and adjusted my menu contents.

You're right, the backups are an even better solution *if* you've got them. Problem is, you get backups only when you edit menus, and I hadn't... 

> Something I discovered I could do with XP was to 'browse' the menu with explorer, and simply drag and drop the shortcuts into folders of my choosing. This is very simple to do, and allowed me to make up my own trees. Would this be difficult to achieve in Ubuntu?

I agree, Gnome's xml-style proprietary menu definition files seem an over-complicated answer to a very simple problem... for once Win-doze got it right and don't see why Gnome's guys can't copy the approach.. no shame in learning from competitors! But you're right, this is stuff for another thread...

Take care!

---

### Post by [h2o] on 2008-01-06
Just removing ~/.config/menus/application.menu got me my menu back.
Thanks for the suggestions in this thread that made me find it out :)

---

### Post by jollo on 2008-01-08
You're right, h2o: the applications menu works fine without an applications.menu file; the file gets regenerated to default the first time that you invoke the menu editor. 

So, summarizing for anyone experiencing this problem: the cause is the ~/.config/menus/application.menu that gets corrupted (empty file). You can either:
a) replace it by renaming a backup file *if you have it* (that gets you back to your next-to-latest personalized configuration) or, 
b) if you don't have a backup, you can simply remove the corrupted file and get back to the default applications menu.

Forget about creating (or, worse, moving to) new accounts...

Take care!

---

