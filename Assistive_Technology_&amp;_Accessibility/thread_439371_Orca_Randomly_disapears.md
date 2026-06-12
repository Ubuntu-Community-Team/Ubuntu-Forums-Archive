---
title: "Orca Randomly disapears"
date: 2007-05-10
forum: Assistive Technology &amp; Accessibility
---

### Post by Turtlecatpurrz on 2007-05-10
Hello,

I am an absolute Linux Newbie.  I only just  installed Ubuntu today.  I am also a legally blind Linux newbie, and am unsure if I am causing this problem, if it is my hardware, or simple a bug in the program, but there are the details.  

I set up Ubuntu to run Orca automatically when I start the OS.  It seems to work for a little while, but after not very long Orca seems to just drop out.  It makes some sort of an error noise, and will not come back until I re-click on the apply menu in Orca itself.  

I am running a dual boot,Win XP hiome and ubuntu has 10 GB of space.  I have a 1.5 ghz celeron processor with 512 Ram.    It is a laptop also, and I am using an external monitor.  My Graphics card is  Raedon 9000 (ATI) with 32 MB of power.  Sound is intergrated on the mother board.

I do not recieve any error messages from Orca. 

Should I try Gnopernicus instead? or should I try to keep working with Orca?  Also, what is the best way to fix this problem?  I appreciate the help, and the friendliness of everyone on the Ubuntu forums.  

Oh, one other thing,  Where can I get a good comprehensive list of keyboard shortcuts for GNOME?

---

### Post by americux on 2007-05-11
Firstly, don´t leave Orca. It´s been improved and constantly upgraded.
A question: what ubuntu version did you install?
Other questions: have you tried run it from a terminal console?
have you tried with alt+f2 and type orca and do enter?
Good luck.

---

### Post by Turtlecatpurrz on 2007-05-11
Running Fiesty Fawn.  Should I have installed something else?

Alt f2 is an improvement on getting it back up and working.  thanks for that one.  I haven't tried in true terminal yet.. its my very first Linux experience, and I haven't done much with terminal except the ls command.  That was mostly just to see if it worked.  

Also, I am confused by a few things in Orca itself.. what is the default  Orca key for example.  I was looking at the keybindings to see if I could understand what was going on, and the orca key was never specified.

Also, like I said, I am a pretty high partial, visually, and sometimes I like to just sluff the speech program when me and the mouse can do it quicker.  I can't use magnification because it upsets my stomach,, so how would I turn orca on and off at will?

Thanks for all your help.  I hope I answered everything you asged.  If not I will edit the post.

---

### Post by americux on 2007-05-14
The orca key usually is "insert". Look for it. it is different in each laptop. I press Insert+space to bring up the Orca preferences (when orca is running), where you can redefine indivual key bindings (on the "Key Bindings" page) or see what you now have defined and can use.
Try to do this:
Again "Alt + f2" to open a dialog window to run a command. Type: gnome-terminal and enter.
Now we have a window with a virtual console loaded.
To ensure you have all you need to run orca, type inside the terminal window: sudo apt-get build-dep gnome-orca
And do enter. This will ask you for your administrative password, and will install, reconfigure or whatever the system need to run orca.
Now, again inside the terminal: orca -s.
With the last command, you will configure orca. Follow the instructions.

To learn about orca, visit: [http://live.gnome.org/Orca](http://live.gnome.org/Orca)
Look for a link named FAQ (frecuently asked questions).

Good luck, A.

---

