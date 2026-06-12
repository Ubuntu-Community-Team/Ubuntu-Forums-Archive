---
title: "Ummm something's wrong with Terminal"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by tiggertiffin87 on 2005-11-27
Whenever I try to access it, it opens and then immediately closes.  Is there a way to reinstall it?  Without using the command line since I can't get to it.

---

### Post by amohanty on 2005-11-27
The terminal that you use in ubuntu is an app called gnome-terminal
You do have xterm. To use it just goto Places->Computer, then hunt down /usr/bin/xterm and double click it.
At the prompt type gnome-terminal and post the error message provided.

The most common reason is that something has been borked in the .bashrc/.tchsrc/.cshrc file (based on your shell) which is executed on terminal startup.

HTH
AM

PS: If your .bashrc is borked you will not be able to start xterm either. Rename .bashrc to .bashrc.old and try starting the either gnome-terminal or xterm

---

### Post by tiggertiffin87 on 2005-11-27
xterm did the same thing, opened then quickly closed.  So where is .bashrc located?

---

### Post by amohanty on 2005-11-27
Goto Places->Home Folder
Then goto the View menu and check Show Hidden Files

anything with a '.' as the first character in its filename is hidden in normal views.


HTH
AM

---

### Post by tiggertiffin87 on 2005-11-27
That didn't work either.  I did open up the .xsession-errors file and it shows this:

(gnome-terminal:9314): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed


Does that have anything to do with not being able to open terminal?

---

### Post by amohanty on 2005-11-27
Not that I know of. I mean that pops up everytime I launch synaptic from the command line, but synaptic works fine.

I found a bug with a similar err message related to totem:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=14583](https://bugzilla.ubuntu.com/show_bug.cgi?id=14583)

Can you launch it via sudo gnome-terminal?

AM

Edit:
Did you try reinstalling gnome-terminal and gnome-terminal-data?

---

### Post by tiggertiffin87 on 2005-11-27
I uninstalled and reinstalled gnome-terminal and it still won't open.

---

### Post by amohanty on 2005-11-27
Well I am sorry, but I am at a loss to explain this behavior. The only extreme thing I can suggest is to drop to console (I think it is Ctrl+Shift+F1) and then do an 
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

HTH
AM

---

### Post by tiggertiffin87 on 2005-11-27
[QUOTE=amohanty]Well I am sorry, but I am at a loss to explain this behavior. The only extreme thing I can suggest is to drop to console (I think it is Ctrl+Shift+F1) and then do an 
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

HTH
AM[/QUOTE]

So what exactly does that do?

---

### Post by amohanty on 2005-11-27
Quits gdm and reinstalls the ubuntu-desktop package which will reinstall all of GDM, X and associated apps.

AM

---

### Post by tiggertiffin87 on 2005-11-27
Will I loose all my customizations like my themes?

---

### Post by amohanty on 2005-11-27
No your customization e.g. you themes are in /home/tiggertiffin87/.themes
They remain. This just reinstalls the applications.

HTH
AM

---

### Post by tiggertiffin87 on 2005-11-27
[QUOTE=amohanty]Well I am sorry, but I am at a loss to explain this behavior. The only extreme thing I can suggest is to drop to console (I think it is Ctrl+Shift+F1) and then do an 
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

HTH
AM[/QUOTE]

Ctrl+Shift+F1 didn't do anything.

---

### Post by amohanty on 2005-11-27
Sorry that was Ctrl-Alt-F1

drops you to runlevel 1 - singele user mode.

AM

---

### Post by tiggertiffin87 on 2005-11-27
Hmmm when I uninstalled it said it was never installed.  So I installed it, uninstalled it and installed it again.  When I logged back into Gnome Terminal was open then it closed.  So I thought YAY!  I went to Applications and opened Terminal and it did the same thing again.  Open then close.

On my spash screen I have a menu and I can choose to load the Failsafe Terminal.  When I do it gives me this error "Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem."

Also when I dropped down to console I tried sudo gnome-terminal and it said: "(gnome-terminal:10198): Gtk-WARNING **: Cannot open display:"

---

### Post by amohanty on 2005-11-27
When you drop down to the terminal you cannot run any gui based applications, because the X server is not running. gnome-terminal is a gui based app.

Also disregard the error message on logout for now, since it is supposed to serve as a warning about something going wrong based on login and logout patterns.

If the reinstall did not solve the problem, I am not sure what you can do to fix this.
Hopefully a guru can help out.

AM

---

### Post by tiggertiffin87 on 2005-11-27
How do I find a guru or do I hope that they read this message and take pity on me? :)

---

### Post by amohanty on 2005-11-27
repost with the following title:

gnome-terminal and xterm quit with gtk error

put the error that you got:
(gnome-terminal:9314): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

and provide details as to what you have tried (ie the things you did here).
I will see if I can find some details as to this problem. I have never encountered this specific one, so am at a bit of a loss.

HTH
AM

---

### Post by steve.horsley on 2005-11-27
As a desperation move, try creating a new home directory for yourself. This should leave all the old chaff (including whatever is crashing gnome-terminal).

Log out of the GUI first, and Alt-Ctl-F1 to a useable terminal. Get a root prompt with **sudo bash**. Then **cd /home**. I don't know your username, so I will use mine. Rename your home folder with **mv steve steveX**, then make a new home for yourself with **mkdir steve** and correct the ownership with **chown steve:steve steve**.

This leaves all of your data, settings etc int /home/stveeX, so when you return to the GUI with Alt-Ctl-F7 and log in, you get a clean set of default settings for everything. If things now work, you can start dragging your old data back into your new home. If it all stops working again, it's probably because you dragged the offending setting back home.

It's a load of hassle, but it should get you going again. I hope.

---

### Post by steve.horsley on 2005-11-27
I forgot to add - most of your settings are in hidden files in your home directory (names starting with a dot are hidden), and these are what you are trying to lose.

---

### Post by ssam on 2005-11-27
[QUOTE=steve.horsley]As a desperation move, try creating a new home directory for yourself. This should leave all the old chaff (including whatever is crashing gnome-terminal).
[/QUOTE]

i dont think gnome will start with an empty home folder.

can you create a new user using System -> administration -> users and groups. then log in as the new user and see if the problem persists.

---

### Post by amohanty on 2005-11-27
I second ssam. That would be a good move to try out. 

AM

---

### Post by tiggertiffin87 on 2005-11-27
[QUOTE=ssam]i dont think gnome will start with an empty home folder.

can you create a new user using System -> administration -> users and groups. then log in as the new user and see if the problem persists.[/QUOTE]

I tried that and I still can't access terminal.

---

### Post by tiggertiffin87 on 2005-11-27
[QUOTE=steve.horsley]As a desperation move, try creating a new home directory for yourself. This should leave all the old chaff (including whatever is crashing gnome-terminal).

Log out of the GUI first, and Alt-Ctl-F1 to a useable terminal. Get a root prompt with **sudo bash**. Then **cd /home**. I don't know your username, so I will use mine. Rename your home folder with **mv steve steveX**, then make a new home for yourself with **mkdir steve** and correct the ownership with **chown steve:steve steve**.

This leaves all of your data, settings etc int /home/stveeX, so when you return to the GUI with Alt-Ctl-F7 and log in, you get a clean set of default settings for everything. If things now work, you can start dragging your old data back into your new home. If it all stops working again, it's probably because you dragged the offending setting back home.

It's a load of hassle, but it should get you going again. I hope.[/QUOTE]


Tried that too...still no terminal.

---

### Post by amohanty on 2005-11-28
Reinstall the following packages:

libgtk1.2
libgtk1.2-common
libgtk2.0
libgtk2.0-common

Theres a possibility that your gtk libs are screwed up. Unlikely, but given that other possibilities have not panned out, this can be be a possibility.

Tell us how it goes.

AM

---

### Post by ssam on 2005-11-28
if you press ctrl+alt+f1, can you log in there? (on the full screen terminal).

also, have you any idea of anything you may have done to cause this? have you been installing new software or following instructions from somewhere?

---

### Post by ranf on 2005-11-28
[QUOTE=tiggertiffin87]
When I do it gives me this error "Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.[/QUOTE]
So can you confirm that you're NOT running out of diskspace? `df -Th' from a failsafe terminal should tell you.
I had that once and Gnome started acting really weird.

---

### Post by tiggertiffin87 on 2005-11-30
I actually never tried to log in using the Alt-Ctrl-F1 (or whatever it was).  The only thing I've been installing is themes.
And I'm sure I'm not running out of space.  I put Ubuntu on a hard drive by itself and there's 20GB for it to roam.
I actually just decided to reinstall and reformat the drive.  So I'll carefully monitor what I add in case I get that problem again.

---

