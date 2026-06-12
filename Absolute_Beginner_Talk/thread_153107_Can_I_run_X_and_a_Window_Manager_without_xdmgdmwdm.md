---
title: "Can I run X and a Window Manager without xdm/gdm/wdm ?"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by technasma on 2006-03-31
Hello there fellow Ubuntu users! I'm a 3 hour newbie!!

I am on my 3rd installation... I have an old laptop (Thinkpad X20) and I am trying to achieve a super-streamlined system. I've been reading about this for the last hour or so but am yet to fully grasp what xdm/gdm/wdm etc does for the system... are they "session managers"? Are they required or will they be required later on?

I hope to install fluxbox, synaptic, dillo, abiword, maybe firefox etc

I kind of get that xdm/gdm is meant to manage users on the system who want to log into an X session and let them choose their window manager... but if there's only going to be one window manager so why do I need a session manager? Is anything else dependent on a session manager?

Apart from the cloud of confusion in my head I love Ubuntu... using the shell makes me feel like I'm an astronaut!!

---

### Post by rmjokers on 2006-03-31
You dont need a session manager at all.  In the good old days, you logged in at the command line and typed "startx" to start an X session.  The window manager listed in the file ~/.xinitrc determined what was used.  I presume that this could still be done today with a window manager like fluxbox.  You can also disable use of the login manager by removing the startup script from the directory for the current runlevel.  The default runlevel in Ubuntu is 2 and the scripts for it are in /etc/rc2.d.  The relavent one for you is probably name something like S13gdm (just remove the softlink).

---

### Post by trent dillman on 2006-03-31
Well, you could not use [gkwx]dm....

....just set Gnome or whatever to start in your .xinitrc.

You would have a text-mode login prompt though.

---

### Post by technasma on 2006-03-31
Excellent, excellent... I'm starting to learn about run levels now!!

Thanks for the info guys... I much prefer my machine starting up to the command prompt... I don't plan on rebooting... this is linux after all ;)

---

### Post by technasma on 2006-03-31
Ok, everything installed ok... I found the latest .deb for fluxbox and used dpkg -i which gave me dependency issues... sudo dpkg -f install fixed that (gotta love forums)... 

But now when I start X, fluxbox works great (menus etc) but I can't seem to open any applications... e.g. when I open the menu and click on synaptic nothing happens... nothing happens for any app!

Maybe I need xdm after all?

---

### Post by rmjokers on 2006-03-31
XDM should have nothing to do with that.  What happens if you start the apps from the terminal?  Do you get any errors or do they just not work?  It is also possible that the dependency issues you mentioned have something to do with it.  Do you remember which packages it said were missing?

---

### Post by technasma on 2006-03-31
"What happens if you start the apps from the terminal?"

I can't open terminal in X at the moment... when I try to start synaptic from the command line shell I get "(synaptic:6948): Gtk-WARNING **: cannot open display:"

The packages that were missing from fluxbox were libimlib2 and related ones.. but they all installed after I did "sudo apt-get -f install" (I mistakenly called that dpkg -f install in my post)

The menu for fluxbox works fine... and I can even configure the menu bar... but clicking on apps just has no response.

---

### Post by rmjokers on 2006-03-31
I have to admit this is quite a strange problem.  Have you tried any non-gnome related X applications like "xterm"?  It might be possible that there are still some gnome applications running that are interfering with your new X session if you havent rebooted the system.  You might also try looking at the currently executing process list "ps aux" and killing any gnome apps.  The only other thing I can think of is removing any gnome-related configuration files (things like .gnome and .gconf in your home directory).  Good luck...

---

### Post by technasma on 2006-03-31
Thanks for the help rmjokers... just installed dillo and it works!!

Will try xterm now and see if I can sort out this gnome business! There shouldn't be too much gnome going on... haven't installed any of it.

---

### Post by antiemptyv on 2006-04-05
i am having the same problem, and i have no idea why yet.

just some background--
I have been experimenting around with various window managers, and have decided that i prefer fluxbox to others, so on my laptop, i did a server reinstal, and apt-got fluxbox, added "exec startfluxbox" to my .xinitrc file, and fluxbox starts up fine with the "startx" command.

the problem--
just like *technasma*, no applications are running from the menu, thought the menu, slit, and iconbar are all fully configurable.  apps that can run in a terminal run before starting up X, such as Nano.

the question--
have you figured this out, *technasma*, or does anyone else know what's going on?

thanks.

---

### Post by rmjokers on 2006-04-05
Have you actually verified that any of the apps listed in the menu are actually installed?  If you just did a server installation with fluxbox, there may be no other X applications on the system even though they are listed in the menu.  I dont have  a setup like yours, so I have no way of testing.

---

### Post by antiemptyv on 2006-04-05
well nano works from the command line before i run startx, but it does nothing in fluxbox

---

### Post by rmjokers on 2006-04-05
I believe applications like nano require some sort of terminal to be open in order to run.  From the command line, it uses your current terminal.  In an X session, it uses the pseudo terminal of a comman line window like xterm, rxvt, Eterm or something along those lines.  If you dont have any of those applications installed, nano wont work in X.  I believe the command in the fluxbox menu to start nano actually opens an xterm window and runs nano inside of it.  That brings us back to the original question, is xterm or whatever fluxbox expects to use installed on your system?

---

