---
title: "My Terminal and/or Konsole don't start"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by plugitin on 2006-11-26
Neither the Konsole or terminal will start up for me.

If I press the terminal icon, then it says 'starting terminal' in the taskbar, but nothing happens and then it doesn't say it anymore. For Konsole, nothing happens.

So now I have no terminal program....anybody know how to fix this?

---

### Post by LLRNR on 2006-11-26
Wow, that looks *really* strange... It worked before, right? 

If you hit Alt+F2 (the "Run" command) and type in "konsole" (or "terminal") what happens? If the konsole/terminal shows up, it's most likely that's a shortcut mis-behavior that you're facing with. 

Well if that DOESN'T work...

Anyway there is a way to input commands, of course: you'd have to switch to a tty: tty1 is Ctrl+Alt+F1, ... , tty6 is Ctrl+Alt+F6; tty7 is Ctrl+Alt+F7 and that's your GUI.

So from where you're now you can press Ctrl+Alt+F1, you'll see a black screen with a login prompt, you have to login, type in your password (it won't echo on the screen though, but you're actually typing it) and then try
```
sudo aptitude install konsole
```...Assuming you somehow managed to uninstall it by "accident". The konsole is the one used in KDE, I don't know the name for the "Terminal" in Gnome (well yeah it _could_ just be "terminal" I don't really know but the idea is to have at least one of them...)

When you're done, press Ctrl+Alt+F7 and you're back in the GUI. Check out if you can launch it from the menu.

---

### Post by ewl1217 on 2006-11-26
If that doesn't work, you could try starting Konsole from xterm. Press Alt+F2 and run xterm. Then, in xterm, run konsole and watch for any error messages. Of course, this is assuming that xterm will work...

---

### Post by plugitin on 2006-11-26
> **ewl1217 said:**
> If that doesn't work, you could try starting Konsole from xterm. Press Alt+F2 and run xterm. Then, in xterm, run konsole and watch for any error messages. Of course, this is assuming that xterm will work...

Didn't start with Alt-F2, so I just rebooted and it worked fine. That was really weird.

Thanks anyways!

---

### Post by kevinf311 on 2006-12-15
I have a similar problem. I thought that I had gotten rid of it, but it is back. After updating the kernel, my programs and folders stop opening. It takes a few hours of X running, but I get the same symptoms of the OP. The bottom bar will read "Starting 'whatever'" and then disappear. I had this problem a few weeks ago after I ran the Envy script tseliot wrote. I blamed it on his script and re installed, but it apparently runs deeper than video drivers. 

If I restart X the problem goes away for a little bit, but comes back after a few hours. I'd prefer not to have to restart my X session every few hours as I like to keep my standard programs open and logged in/running. 

I literally *just* got rid of this problem a week ago and now it's back ](*,) 

Any help/insight would be very appreciated. Thanks

-Kevin

[edit] When I switched over to tty 1 and then back to tty 7 everything was working again. I was also able to keep my session (programs were still running). I am ok with this as a permanent fix. However, if someone knows what causes programs from launching, any information on it would still be welcomed.

---

### Post by thePuck on 2006-12-16
Is this in KDE or gnome?

---

### Post by kevinf311 on 2006-12-22
> **thePuck said:**
> Is this in KDE or gnome?
I'm using gnome. Not sure about the OP.

---

### Post by mephistofun on 2007-01-18
I am also having this problem.  I am running ubuntu edgy server 6.10 and I have installed ubuntu-desktop.  I mostly use this computer as a server (webserver, download torrents, samba, ssh, etc.) but I have the GUI installed because occasionally I will get on it to view webpages and look at email (the thing is sitting the corner of my dining room after all).  System resources never seem to be a problem as nothing ever seems to run "slow" like it would on Windows.

The server apps and Azureus all work very well but after continued use with firefox and GAIM I can no longer load any new apps.  Gnome-terminal shows "Starting Terminal" in the taskbar and then just disappears.  I think Firefox would do the same thing if I closed it and tried to reopen it.  If I reboot the problem goes away.

I tried reinstalling gnome-terminal and gnome-terminal-data and I tried running xterm which would not load either.  The only thing I have not done yet is reboot, which I don't like to do.

Any ideas as to what is going wrong?

---

### Post by mesach on 2007-03-15
I'm having a same/similar issue, My terminal does the same thing, but konsole will work(when i have kubuntu installed too, i dont right now since i just reinstalled) HOWEVER, for me a reboot will not solve the issue.

Also around the same time i notice this starting, I get certain webpages acting funny, like the DNS entry is messed up on them, I'll pull up google.com, and it will take me to OSnews, or BBCUK or some other site, and it SWITCHES, one minute it will be one page, the other a different page, then a few minutes later everything will be fine!

Does that sound like something someone has dealt with in the past, maybe they are related since they are happening to me at around the same time.

---

### Post by puterboy on 2007-11-28
I know this in an old topic, but I'm having the same problem. Anyone find a solution? xterm works, but at the same time, my system slowed right down, and terminal stopped working. no idea what's happening.

---

