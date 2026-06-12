---
title: "Stupid Me Kills Dapper Desktop - Pse Help me restore it"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Busta999 on 2007-02-02
OK - I confess I did a REALLY (R) REALLY dumb thing..........

While trying to hunt down the process that was eating my CPU I saw that a process called XORG was grabbing 30-40%

OK - Now know that was dumb but...

I killed XORG...

OK so my VNC session died.....

I went to the machine and the screen was frozen so I ended up by having to kill the power to get it to reboot. I made sure nothing externally was writing to the machine.

I kinda hoped it would just reboot but.....

Now it boots I get a responsive mouse pointer and the Ubuntu background but that is all - nothing else.

It does not respond to keyboard or mouse.

Can't telnet into it either.

Is it a re-install to fix or is there some way to get it going again?

Thanks

---

### Post by Patrick-Ruff on 2007-02-02
I'm not sure how you messed it up so bad, but don't do it again, this isn't windows.

anyways, you'll have to reinstall most likely, *snip*

---

### Post by shareMenaPeace on 2007-02-02
Not sure if there is no way to do this easy but at last you can backup all your personal files with the live cd and mounting the old device containg eg your home dir.

---

### Post by jd65pl on 2007-02-02
Boot using standard mode, then when you get to the login screen change the session to failsafe gnome this should give you some kind of error message on which to base the next step in fixing your problem.

---

### Post by Busta999 on 2007-02-02
Thanks guys

I am going to boot the command line and try an apt-get and re-install the X Window System and see if that gets me anywhere.

As I said I kill the XORG process from System Monitor 

Will let you know how it goes

Mike

---

### Post by Busta999 on 2007-02-02
that didn't work too well - apt-get remove x11-common had lot's of errors and adding it died - so backing up and will do a rebuild - I know alot more about it this time.... So should be quicker.

All good experience...

---

### Post by shareMenaPeace on 2007-02-02
TO backup old data you need to check your partition

and than mount the partition which includes the files to backup(burn).

example
```
sudo mount /dev/hdb1 /media/music
```

---

### Post by Busta999 on 2007-02-02
Thanks - I mounted my old boot drive, chown ubuntu * -R so I could copy it easily to a new mounted USB 400GB drive now just kicked it all off.

It will take a couple of hours but I will have the entire boot and all my personal stuff off there and on the USB 400GB.

Then, when I re-install back onto boot I can find my old config files and anything else I spent hours trying to to get to work.

Hey maybe now is the time to put Kubuntu on it?

Thanks for all your help with this.

Hopefully I can get this all back up and runningin 24hrs, this machine is the media server to two Liteon NetPlayers and several PCs and a MAC. I had 3 TB of video and 300GB of music hanging off it, moved all my CDs and DVDs onto it. Also it is the print server.

---

### Post by Busta999 on 2007-02-18
Ha

It idid it again this time following a normal reboot to test something was loading properly.

This time I was able to get a command line and install the KDE desktop, then completely uninstall gnome and re-installed it again. Go it all back OK.

Definitely flakey though.

Things keep uninstalling themselves..

---

