---
title: "Continue remote X application after disconnect?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by ResumeMan on 2007-11-24
I'm in the process of setting up an Ubuntu-based home file server. I've got it set up and can access the box remotely via SSH. I also have Webmin installed and am starting to learn my way around that.

I have also figured out how to run applications on the server with a display on my laptop (SSH -X <server IP>). This pops up the application on my laptop, while actually using the server to run the program. My hope in this is to be able to, say, start a bittorrent on the server from my laptop.

Unfortunately, of course, when I close that window on the laptop (to turn of the laptop for instance), the program on the server terminates.

Is there any way to run a remote application using the display on the remote computer that keeps the session alive after I close the window?

I'm vaguely familiar with the 'screen' program, but it seems that although it will let me disconnect the shell session it still kills the program when I close the application window.

I suppose I could use VNC, but that's a little more clunky and I'd like to do it using SSH.

Is there any way to do this?

---

### Post by p_quarles on 2007-11-24
The best way to make a remote command persistent is to prepend it with the "nohup" command. That's short for "no hangup." 

In other words, if I wanted my server to download a large file overnight, I would run:
```
nohup wget http://path.to.site.com/filename.ext
```
Then I can close the terminal window, and the download will continue. 

That said, I don't use any X11-forwarding, and have never tried this with a graphical app, so I don't know if it will work as smoothly. If not, there is a semi-graphical torrent app called rtorrent. That one will certainly work for your purposes, but might add a little to the learning curve.

---

### Post by CatKiller on 2007-11-24
There are command-line BitTorrent programs you know :)

Personally, I use btdownloadcurses with screen. Then you can detach from the screen, log off, turn off the laptop. Connect from another computer somewhere else to check on it... Whatever you want, really.

---

### Post by Capricori on 2007-11-26
Is there a way of doing this with graphical apps.
For example, is there a way to ssh into my server from a laptop, start Amarok, tell it to play a playlist, then shutdown the laptop, and leave the music still playing?
It would be a bonus if I could then restart the laptop, ssh back into the server, and pull the Amarok display back onto the laptop. 
Any ideas?

p.s. Sorry to hijack your thread ResumeMan, but I think my question is along the lines of what you want anyway? :)

---

### Post by ResumeMan on 2007-11-26
> **Capricori said:**
> 
p.s. Sorry to hijack your thread ResumeMan, but I think my question is along the lines of what you want anyway? :)

Not a hijack at all, it's the exact same question :)

Anyone who knows anything more about this, I'd appreciate it!!:confused:

---

### Post by p_quarles on 2007-11-26
Did you at least give the "nohup" command a try? It might work with graphical apps, I just don't know. Aside from using a VNC, that's the only possibility I'm aware of.

---

### Post by ResumeMan on 2007-11-26
I did; it didn't work (when I closed the window the application stopped on the server side). That said I only tried it once and didn't play around with it any more than that. Maybe I'll try again.

---

### Post by p_quarles on 2007-11-26
Try closing the terminal from which you started the application instead.

---

### Post by Capricori on 2007-11-26
I messed with 'nohup' for a while and couldn't get the remote app to continue. I think there may be a way to do this with [Gnu Screen]("http://www.gnu.org/software/screen/"), but I had no luck with that either, although it sounds like the right tool. Does anyone else have more experience with this?
Regards.

---

### Post by ResumeMan on 2007-11-29
Well I've tried nohup a couple times. Also tried to work screen in there too (ran screen, then ran nohup <application> then did ctr+ad, then closed terminal. That worked and the application continued, but when I closed the app window, the process terminated).

Any ideas?

---

### Post by KnuX on 2008-02-19
up ? ;)

---

### Post by punzada on 2008-03-09
I'd just like to bump this thread, I feel like it would be fantastic functionality that I've been scouring the net for (being able to visually pause remote x sessions and reconnect to them) and have been unable to solve, thanks for anyone with any heads up :P

---

