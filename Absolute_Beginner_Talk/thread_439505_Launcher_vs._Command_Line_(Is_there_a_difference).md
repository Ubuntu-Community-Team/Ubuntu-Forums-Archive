---
title: "Launcher vs. Command Line (Is there a difference?)"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Chris S. on 2007-05-10
I just installed Matlab R14 for Linux on Feisty.  The program itself works despite a few OpenGL problems (that's for another thread), so I want to make a launcher on the Main Menu.  I choose to add an item, give it the name "Matlab," and the command "/usr/share/matlab7/bin/matlab".

After clicking on this in the Main Menu, the Matlab logo pops up as usual, but it only sticks around for about a second before disappearing.  Matlab never starts up after that.  I get the same behavior if I create a launcher on the desktop and double-click it.

If I run the same command from the terminal, the logo pops up, stays for around five seconds, then the main Matlab window appears, and all works well.

So my question; what is the difference between a command input via the terminal, and a command run by a launcher?  Is the launcher command treated differently, run with different permissions, or something?  I'd like to not have to run this from the terminal, nor have future problems with other applications/launchers.

---

### Post by Foxmike on 2007-05-10
Not as what I know.  Maybe just entering "matlab" in the launcher may solve the problem?

Regards,

-FM

---

### Post by Chris S. on 2007-05-10
Oh yes, I've tried that as well.  The "matlab" link points to the path I gave above, so it should be the same as using the executable directly, right?

---

### Post by Chris S. on 2007-05-11
Well, the problem is solved:

Matlab is one of those programs that requires a "controlling terminal." (sigh)

So setting "Application in Terminal" opens the controlling terminal and lets Matlab run just fine from a launcher.  Hooray!  For Matlab, you can set the "-desktop" option to avoid terminal dependence, so that solves that problem entirely.

Yeah, to all the Ubuntu noobs like me, there really is no difference between the two, except for the lack of terminal with a launcher.  Duh!

---

