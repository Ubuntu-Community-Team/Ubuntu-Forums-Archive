---
title: "Launchers in XFCE:  Desktop vs. Panel"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by The Realms of Gold on 2008-01-23
Here's a fun newbie problem for you all that probably gives away my total lack of understanding of the underpinnings of Linux, but also might demonstrate why so many people find it impossible to learn, despite its user-friendlieness.

Today I installed OpenOffice.  Writer made itself a launcher on the desktop.  The fields for that launcher look like this:

Name:  OpenOffice.org Word Processor
Comment:  Create and edit text and graphics in letters, reports, documents and Web pages.
Command:  ooffice -writer %U
Icon:  [big square button with a round, white, OO writer icon].

Just as you'd expect.  And to change the icon, you just click the big square button, and get a window full of icons to choose from, with a drop-down box at the top to specify group of icon, or a browse window to locate your own.

I wanted to create an identical launcher on the panel, so I right-clicked the panel and added a launcher.  To my dismay, I found a counterintuitively different set of properties, in a different dialogue box.  The notable difference is in the icon choosing.

For panels, it seems you can create a menu of launchers, the first one of which determines the icon.  Fine, I thought, I'll just make one launcher, for oowriter, and choose the same icon.  No dice.  Clicking that gear-icon chooser button (which seems to replace the big square button from the Desktop's Edit Launcher dialog), you don't get a set of icons to choose from -- you just get a browse dialog, and heaven help you if you don't know where the icons you want are.

And I don't.  /usr/share/icons is full of seemingly identical copies of the same icons, dozens of times in different sizes, but the round, white, OO Writer icon from the default desktop launcher is nowhere to be seen.

Where is it?  Help!

(I should add that I'm aware the desktop launcher is a "desktop configuration file," and the panel one is not.  But that doesn't help me.)

Thanks in advance, everybody!

---

### Post by gn2 on 2008-01-23
As an example, right-click on one of your existing Panel launchers, say Firefox, and look at properties.

This shows the location of the icons you need which is /usr/share/pixmaps/firefox

The Command is firefox, this links to the location of the executable, which is  /usr/bin/firefox

A useful launcher to create is for Synaptic Package Manager, 
icon = "synaptic" (without the quotes) 
command = "gksudo synaptic" (without the quotes)

If you create a desktop launcher, as you type the name of the launcher, suggestions will drop down which you can select.
When you have created the desktop launcher, right-click on it and open it with Mousepad.
This will give you the name of the icon and the command to enter when creating a Panel launcher.

Open Office Writer is:
Command: ooffice -writer %U
Icon: ooo-writer

---

