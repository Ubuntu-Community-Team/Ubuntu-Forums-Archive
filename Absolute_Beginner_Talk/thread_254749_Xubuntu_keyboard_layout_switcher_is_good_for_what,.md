---
title: "Xubuntu keyboard layout switcher is good for what, again?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-09-10
Fair warning: I'm a little frustrated, to put it mildly. Any and all sarcasm and/or resentment in this post should not be taken personally 

I switched to the Xubuntu desktop environment yesterday,and spent hours playing around with it. I like it. It's sleek and pretty, and the laptop runs faster now than it did on the Gnome desktop. However, there is one problem. I need to have the ability to switch between keybord layouts, US-SWE to be specific.

I found the layout switcher and locked it to the panel to be able to switch between the two languages, and looked for a keyboard shortcut for it. I can't find one, but I couldn't in the Gnome environment either. What frustrates me a lot more is that *there is no way of adding the second layout!* I have looked in Keyboard settings, User Interface settings, Language Support, but found no way to tell the system that when I press that layout switcher, I want the keyboard layout to change to that of a Swedish laptop keyboard. I would like to believe that there is a way, since the promise of a function that turns out to be broken,or not even there, is one of the things I despise most about Windows, and I have enjoyed not having to deal with it in Ubuntu. Until now.

Help me, please. What is the obvious solution that I am missing? 

/Mimsy

---

### Post by whizbaby on 2006-09-10
Hello!
Go to a terminal (e.g. ctrl-alt-F1, not on desktop) and edit your /etc/X11/xorg.conf
 
**sudo nano /etc/X11/xorg.conf**

find the keyboard section, and in it a line similar to this:

Option          "XkbLayout"     "us"

then add your layout

Option          "XkbLayout"     "us, swe"

save the file and quit the editor. Then restart the X-server:

**sudo /etc/init.d/gdm restart **

If it doesn't launch you back to the graphical login automatically switch manually with (ctrl-alt-F7)
(If it doesn't restart (then *swe* is not a layout description, but I think it's right) then you can still browse the internet with e.g.:
**w3m [http://ubuntuforums.org/](http://ubuntuforums.org/)** or of course undo manually the change you applied and restart the X-server.
This console-internet-thing is only good to know.

---

### Post by Mimsy on 2006-09-10
Thanks for the quick reply!

I actually went back to the Gnome desktop, since the option was still there to log in to that environment, and since I am still a bit too wary of editing too much in my Ubuntu installation. If anything breaks I have no idea how to fix it, and no way of going to these forums to ask for help for at least a couple of days.

But thank you again, I appreciate the help nand the quick reply one the less. I'll file it away and try it in a few months or so, when I'm more familiar with how Ubuntu and Linux work.

/Mimsy

---

### Post by whizbaby on 2006-09-10
Actually this would be a good place to start digging a bit because you can't *break* anything doing this, the changes are easily revertible (besides xorg.conf is an important system file (for gnome too), so it's never too early to learn anything about it). If feeling unsafe you could even backup the file (**sudo cp /etc/xorg.conf /etc/xorg.conf.safe**) and recover it if anything goes wrong (**sudo cp /etc/xorg.conf.safe /etc/xorg.conf**). I don't want to force you into anything, I only want to mention that it's perhaps easier than you think (and you get familiar with the system, too). So if you would like more detailed information about any step just say it.

---

### Post by Mimsy on 2006-09-10
When I got the option of borrowing a computer and connection, so I could browse the forums anyway if something went wrong, I decided to give it a shot.

I'm not sure what happened, but the keyboard layout switcher symbol in the top panel is now set to UNKNOWN where it used to be US. I can't change it to anything else either, though I tried, so I hit ctrl-alt-F1 to try to remove the editde changes, but that command stopped working. I'm confused. How do I get back to that screen so I can take the change away?

Thanks,
Mimsy

---

### Post by Mimsy on 2006-09-10
I tried booting into Gnome to get to the terminal that way, but it wouldn't work. So I removed the Xubuntu Desktop and then booted into Gnome again, and now ctrl-alt-F1 worked, so I could open the file and remove my changes.

I felt very smart. :) 

Now I wonder though... After I logged back into the GUI, I got a popup saying that the X keyboard layout settings are different from the Gnome one, and then it asked me which ones I wanted to use. If I removed the Xubuntu dekstop stuff, shouldn't the keyboard layout settings also be gone? If not, how do I remove all of it, so it won't be there clogging things up when I try to start over again?

Also, I noticed that CPU load on average was higher in Xubuntu desktop environment than it is in Gnome. Is that a fluke, or something I should have expected?

Thanks,
Mimsy

---

### Post by whizbaby on 2006-09-11
> **Mimsy said:**
> I felt very smart. :) This usually changes from time to time: smart-dumb-smart-dumb-smart...
> 
 If I removed the Xubuntu dekstop stuff, shouldn't the keyboard layout settings also be gone? If not, how do I remove all of it, so it won't be there clogging things up when I try to start over again?

Open synaptic and look at the text of the *xubuntu-desktop* entry and you'll see: removing it doesn't really do anything. Install *ubuntu-desktop* to get more out of your gnome environment, and this should uninstall xubuntu-specific stuff, too. (the ***-desktop packages only enhance one special window manger each)
> 
Also, I noticed that CPU load on average was higher in Xubuntu desktop environment than it is in Gnome. Is that a fluke, or something I should have expected?

Sounds new to me.(on my comp it's the other way 'round)

---

### Post by Mimsy on 2006-09-11
> **whizbaby said:**
> This usually changes from time to time: smart-dumb-smart-dumb-smart...

Well, yes. Five minutes later I was sitting there like an idiot, stumped by the panel preferences. I'll spare you the details. :rolleyes: 

> **whizbaby said:**
> Open synaptic and look at the text of the *xubuntu-desktop* entry and you'll see: removing it doesn't really do anything. Install *ubuntu-desktop* to get more out of your gnome environment, and this should uninstall xubuntu-specific stuff, too. (the ***-desktop packages only enhance one special window manger each)

Aaahhh... I'll try that and see what happens. Thanks!

> **whizbaby said:**
> Sounds new to me.(on my comp it's the other way 'round)

I expected it to be theother way around; that's why I installed Xubuntu in the first place. I'm going to keep experimenting and compare, and go with whichever one taxes the CPU more. It's a seven year old 1.2 GHz Pentium 3, so I'm trying to to go easy on it...

Thanks for all the answers. The more I ask, the more I learn. :) 

/Mimsy

---

