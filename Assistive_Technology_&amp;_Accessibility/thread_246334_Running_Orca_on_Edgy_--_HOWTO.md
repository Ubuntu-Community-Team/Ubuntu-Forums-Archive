---
title: "Running Orca on Edgy -- HOWTO"
date: 2006-08-29
forum: Assistive Technology &amp; Accessibility
---

### Post by Henrik on 2006-08-29
**Update:** Orca on the live CD has now been fixes to Just Work, so this thread is obsolete. I'll post new, simpler instructions in a new thread. Leaving this one for historical value ...

------------

This thread contains basic instructions in getting Orca running on the Edgy live CD, installing the system and finally setting up Orca on the installed system. These instructions are temporary while we work out a more elegant way of enabling speech. The aim to to help get people up and running so they can help with testing. This section focuses on setting up the speech synthesis function; magnification should be described separately.


**Step 1: boot the live CD.**

(this assumes that you have downloaded and burned a recent Edgy Live CD from [here]("http://cdimage.ubuntu.com/daily-live/current/"). For best results use the i386 version).

Just boot as normal. If you simply wait 3-4 minutes the whole process should be automatic, booting you into the standard desktop. You should hear a jingly sound at the end (the special boot categories are not enabled on Edgy yet so don't worry about those).

**Step 2: Running Orca for the first time.**

The first time Orca runs it must be run from a terminal because it runs through an initial setup procedure.

a) Press Ctrl-Alt-F1 to switch to a virtual terminal

b) type 'orca' and press Enter. You will now be greeted by the message 'Welcome to Orca' and a few questions that you can answer with y or n +Enter.

c) Press Ctrl+Alt+F7 to return to the normal desktop

When the initial setup is complete the following things have happened:

 * Orca has created a user profile for you so that it does not have to ask these questions again next time it starts
 * The Gnome Accessibility support system has been activated so that other applications can supply Orca with text information. Important note: This will not be activated until you log out and back in (see next step).
 * Also note: While the Gnome Accessibility support has now been configured to start next time you log in, Orca itself has not been configured to do that so it must be started again later.

**Step 3: Logging out **

When the initial setup is complete you need to log out to allow the access framework to be started. The simplest way of doing that is by pressing Ctrl+Alt+Backspace to kill the X-session (don't do this normally if you have unsaved work). 

This will take you to the normal login prompt, which in turn is configured to log you back in automatically. If you just wait 30-40 seconds you should be returned to the default desktop.

**Step 4: Starting Orca a second time**

Repeat steps 2 a-c. This time Orca should start speaking without asking you questions. The access infrastructure should now also be active so other applications should work as well. Take some time to explore the Ubuntu menus and applications. Alt-F1 opens the gnome menu.

**Step 5: Installing Ubuntu (Optional!)**

(You may well prefer to simply play with the live CD for a while.)

On the desktop there is a link called 'Install' which starts a guided install program. It can also be located by going to the Places menu, Home Folder, Desktop folder. This is a guided install that will ask you some questions (but needs more usability testing with Orca). The disk partitioning is the most critical and difficult step. If you have questions about this, I suggest you ask in the beginners forum section.

At the end of the install process you will be asked to reboot.

**Step 6: Rebooting the installed Ubuntu**

Remove the CD as it is Ejected and wait for the system to reboot. You will be prompted by a login screen where you must enter your user name and password.

This will start the default desktop, which again has the accessibility tools installed, but not activated. Repeat step 2, 3 and 4 to activate the access tools and Orca again. Note that this time you will not be logged in automatically, but have to enter you user name and password again.

**Step 7: Making Orca start up by default**

Finally you might want to configure Orca to start automatically each time you log in. Do this by selecting 'Assistive Technology Preferences' from the System -> Preferences menu. The tick the 'Screenreader' box and press Esc.


**Notes:** These steps work for me but may not work equally well for others. The steps will also change (be reduced in number!) as we improve the process. I will update this post as we go along to reflect that. Hopefully we will end up with a much shorter guide that we can post on the website. For more information on accessing the desktop, including keyboard shortcuts, see the [GNOME Desktop Accessibility Guide]("http://www.gnome.org/learn/access-guide/latest/").

Please post you comments, corrections and experiences in the thread below.

---

### Post by jasongrieves on 2006-09-01
Hi,

orca -s runs the graphical setup which is so far the only way I can find to configure the magnifier

When you chose the Orca from the menu all I get is orca begining to talk.  Shouldn't the menu item provide a link to the GUI, what most people would expect?  

Orca GUI should have an apply, so that we can "test" our settings without closing the GUI.  This is vital for the Magnifier.  Shouldn't be to hard to implement.  If no objections I will request this via orca bug request

---

### Post by Henrik on 2006-09-03
I agree that the way Orca starts from the menu should be more clear. I've posted on the orca devel list about it.

---

### Post by jasongrieves on 2006-09-03
Hi,

great i see the bugs on bugzilla.  I added my own today about magnifier...

Are we sure we want to leave Gnopernicus off the default install of edgy now?  I haven't done enough testing of Orca + Magnifier but am a little worried about our new users coming into the scene.

---

### Post by Henrik on 2006-10-03
We have limited space so we have to make a choice of Orca or Gnopernicus.

btw, a temporary way of getting the install to work:

run orca from the terminal as root, then run 'ubiquity' as root as well. Works for me.

---

