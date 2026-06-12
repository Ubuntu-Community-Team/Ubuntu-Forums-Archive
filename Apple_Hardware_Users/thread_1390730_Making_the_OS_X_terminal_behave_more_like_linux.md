---
title: "Making the OS X terminal behave more like linux"
date: 2010-01-25
forum: Apple Hardware Users
---

### Post by kyle.M on 2010-01-25
Hello All,

I might have thought that it would be a common complaint, but I haven't found anything about it.  After recently buying a macbook I have been continually frustrated by my inability to simply type the name of a program and have it run.  On linux I can type 'firefox' or 'gvim' or whatever and have it run, but the closest corollary in OS X seems to be something like open -a <program name>.  Is there a best-practice solution for this?

Also, is there a way to open a "run command" dialog box?  This is far and away the convenience that I miss the most.  On slack or ubuntu I would type something like "Alt+F2".  If one right-clicks the terminal icon and selects "New Command" then they are able to pull something like this up, but is there a nice keyboard shortcut or other slicker way to do this?

Thanks in advance!

---

### Post by wheredidrealitygo on 2010-01-26
You can either use Spotlight (cmd-space) and start typing the name of the program and hit enter, the same functionality but more eye-candy'ish is available with [Quicksilver]("http://www.blacktree.com/").

Quicksilver can be summoned with ctrl-space.

---

### Post by Seq on 2010-01-26
> **kyle.M said:**
> Hello All,

I might have thought that it would be a common complaint, but I haven't found anything about it.  After recently buying a macbook I have been continually frustrated by my inability to simply type the name of a program and have it run.  On linux I can type 'firefox' or 'gvim' or whatever and have it run, but the closest corollary in OS X seems to be something like open -a <program name>.  Is there a best-practice solution for this?

Also, is there a way to open a "run command" dialog box?  This is far and away the convenience that I miss the most.  On slack or ubuntu I would type something like "Alt+F2".  If one right-clicks the terminal icon and selects "New Command" then they are able to pull something like this up, but is there a nice keyboard shortcut or other slicker way to do this?

What wheredidrealitygo said. Gnome-do on Ubuntu and Spotlight on OS X make switching slightly less painful.

The reason you need to 'open' is that an "application" on OS X is really a just a directory with some meta-info in it (They like the term "application bundle"). As such, there is no one 'bin' folder have all your OS X apps into your $PATH. Bash doesn't know how to run a directory. The bundles typically also contain multiple versions (intel & ppc, 32 & 64 bit) and 'open' parses the meta-data and runs the right one, just like if you clicked on it.

I'm pretty sure 'open' can be used on arbitrary documents as well, and it will open the proper handler for that file type (Or the program that has tagged the file last. Files can be persistently associated with programs that are not the default handler for that type). On the Gnome side, we have 'gnome-open', which does the same thing (though I believe only for documents. Not for executables).

---

### Post by kyle.M on 2010-01-29
Excellent suggestions, and Seq's explanation is quite helpful.  Is there no keyboard shortcut for pulling up the "run command" dialog box?  

Spotlight is an imperfect substitute because it cannot run commands, as opposed to opening programs, and because it takes longer than instantaneous to open.  Because of me linux heritage, I guess, I hate the idea of needing software just to do something so simple.

---

