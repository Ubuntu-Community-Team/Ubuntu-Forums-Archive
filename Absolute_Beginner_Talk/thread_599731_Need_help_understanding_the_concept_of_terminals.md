---
title: "Need help understanding the concept of terminals"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by pcjason on 2007-11-01
I'm still really new to linux and I'm trying to wrap my head around the concept of multiple terminals.  My understanding as of now is that there are 8 consoles running at once (tty0 through tty7), which I can switch to using CTRL+ALT+F#.  I was reading online about consoles and it mentioned that some of the consoles are called pts/#.  Am i correct in thinking that if, for example, X-server is running on console tty7 and I open up a console window from within Gnome these become "virtual" consoles with the pts/# ?  Or am I completely off base here?  

My other question involes connecting to running processes.  Lets say, for example, I hit ALT+F2 and run the command "vim ~/Desktop/README" I can now see the process is running if I open a console and type "ps -A", but I have no way to actually see the output from vim.  I was wondering if there was a way to somehow "connect" this running process to a terminal.

Thanks for any and all help!

---

### Post by ddrichardson on 2007-11-01
Pty are pseudo-terminals - where a single process replaces all of the underlying hardware, where as a tty is a full terminal.

---

### Post by CatKiller on 2007-11-01
> **pcjason said:**
> My other question involes connecting to running processes.  Lets say, for example, I hit ALT+F2 and run the command "" I can now see the process is running if I open a console and type "ps -A", but I have no way to actually see the output from vim.  I was wondering if there was a way to somehow "connect" this running process to a terminal.

You can use **screen** for this. If you used ```
screen vim ~/Desktop/README
``` then you could "detach" from this screen without stopping the process, and later re-attach to it. I use this to start torrents over SSH, and then I can check them from a different computer entirely.

Instead of using Alt-F2 to start a terminal program, start a terminal window (Applications -> Accessories -> Terminal) and run your application from there. Alt-F2 is for graphical applications, like GEdit, Synaptic, and the like.

Hope this helps.

---

### Post by pcjason on 2007-11-01
> **CatKiller said:**
> You can use **screen** for this. If you used ```
screen vim ~/Desktop/README
``` then you could "detach" from this screen without stopping the process, and later re-attach to it. I use this to start torrents over SSH, and then I can check them from a different computer entirely.

Instead of using Alt-F2 to start a terminal program, start a terminal window (Applications -> Accessories -> Terminal) and run your application from there. Alt-F2 is for graphical applications, like GEdit, Synaptic, and the like.

Hope this helps.

I appreciate the help, guys!

@CatKiller:  How woudl I go about re-attaching to a process?

---

### Post by CatKiller on 2007-11-02
> **pcjason said:**
> @CatKiller:  How woudl I go about re-attaching to a process?

Well, it's not that you'd re-attach to a process as such. You'd re-attach to your arbitrary screen.

When you turn your computer on, you (more-or-less) already have 7 terminal windows open, with X running in one of them. You can open more terminal windows at any time by selecting Applications -> Accessories -> Terminal. Terminal windows created this way will already have you logged into them. tty1-6 you need to log into to use. Normally if you open a terminal window and start a program in it, and then close the window, it also automatically closes the program that you started.

Screen is a way to keep programs running, even after you've closed the terminal that started them. So you would use ```
screen <command>
``` to create a screen and run <command> in it. Mine is usually **screen btdownloadcurses sometorrent.torrent**, but it could be anything. Then you can detach from the screen with Ctrl-A, d. And log out if you want. Then, later, you can log back in, (possibly remotely) and run ```
screen -R -D
``` to find a running screen and attach to it. It's very flexible, and very cool. But a bit hard to get your head around.

Of course, none of this screen stuff really has anything to do with running programs in a terminal. And as far as I know, you can't put the output from an arbitrary running process into a given terminal window. I could be wrong, though, it's happened before :) But if it's possible, I don't know how to do it. Sorry.

---

