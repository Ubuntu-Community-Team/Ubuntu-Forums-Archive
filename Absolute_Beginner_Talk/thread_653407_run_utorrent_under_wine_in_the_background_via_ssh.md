---
title: "run utorrent under wine in the background via ssh"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by uknowho008 on 2007-12-29
so i just set up a "torrent server" first i installed a command line system using the xubuntu disk, then i installed ssh, xorg, wine and utorrent.

so how can i start utorrent via ssh and have it run without me having the terminal up on my computer? i installed "screen" but when i detatch utorrent is still running on my desktop and if i close the terminal it kills utorrent.

i just want to be able to start it via ssh and have it continue to run when i leave.

im also cerious as to why utorrent seems to look so much better with only xorg installed? it has always looked a little off until i set this up.

and lastly, what would be the easiest way of making a shortcut from my desktop computer. make a shell script or something that ssh's to the server then runs utorrent? where should i start?

thanks in advance.

---

### Post by uknowho008 on 2007-12-30
any ideas?

---

### Post by eternicode on 2007-12-30
For starting Utorrent in the background, just add "&" to the end of the command you use; this will automatically send the process to the background (unless you have to enter a password for sudo, in which case it'll just run then immediately close.)  It should continue to run even after the SSH session is exited.

As for the "shortcut", you would probably want a batch script, but you would have to somehow pipe your ssh password to ssh after it prompts for it; not sure how to do that.

---

### Post by uknowho008 on 2007-12-30
it crashes as soon as i close the terminal

---

### Post by peabody on 2007-12-30
nohup ssh -f -Y username@host wine /path/to/utorrent.exe >/dev/null 2>&1 &

If you sleep or suspend or have network trouble, the program will close.  I would recommend vnc instead.

---

### Post by uknowho008 on 2007-12-30
can i install vnc with only xorg installed?

---

### Post by peabody on 2007-12-31
Not sure if I understand your question?  vncviewer comes default installed with ubuntu I think...if not sudo apt-get install vncviewer should do the trick.  That's the only thing you need to view a vnc desktop and they have viewers for windows and mac os x as well.  VNC is nice because if you lose your connection, the remote desktop keeps on running in the background and all you need to do is reconnect to it.

The server you're running utorrent from, on the other hand, does need to have the vncserver installed.  It's not that hard however.  To install vncserver on the host from which you wish to run utorrent, just do:

sudo apt-get install vncserver

Then run on that machine the following command

vncserver -geometry 1024x768 -depth 24

I'm guessing you can understand what the command line options mean and can adjust them to your tastes?  You'll be prompted for a password the first time you run the program.

If you have any sort of firewall or NAT between you and the server, but you can ssh to the server, you can use ssh tunneling to get to the vncserver

ssh -N -f -L 5901:localhost:5901 user@host

Then just run a vncviewer on the platform you wish to view the running mutorrent from and use localhost:1.0 as the display.

Also, Remote desktop sharing in Ubuntu works from vnc as well, so you can use the same ssh tunneling method using Ubuntu remote desktop tools (using port 5900 instead and localhost:0.0).

---

### Post by uknowho008 on 2007-12-31
thanks for the info. the thing is im trying not to install any desktop if possible as the computer is only p3 300mhz. if do install a desktop i want only the desktop and nothing else and i cant seem to be able to do that. i used sudo apt-get install xfce4 and it wasnt found. but i wasnt connected to the internet at the time. i was trying to get it off the cd. maybe its just not on there? anyways. i also didnt like the fact that vnc is supposed to be so insecure but oh well. i guess i should just try to figure out how to install xfce without anything else and install vnc as well...

---

### Post by peabody on 2008-01-01
As long as you've got a firewall or the machine is behind NAT, ssh tunneling vnc is not that insecure.  Just make sure to pick a secure password.

if you install vncserver it only installs twm I think.  That's painfully minimal, but it does the job.  You might try fluxbox if your looking something truly small yet functional.

---

### Post by hyper_ch on 2008-01-01
why run µTorrent in the background? Why not just switching to rTorrent?

---

