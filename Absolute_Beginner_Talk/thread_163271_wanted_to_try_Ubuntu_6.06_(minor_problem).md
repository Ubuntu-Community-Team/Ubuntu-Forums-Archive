---
title: "wanted to try Ubuntu 6.06 (minor problem)"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by tLove on 2006-04-20
Total noob here. I just installed to my HD the latest build of Ubuntu 6.06, the beta that was released today (I think it was today).

So it ejects the disk and says reboot. I do, it come up, shows me the usual Ubuntu loading screen (where it says ubuntu and commands are scrolling and its loading it up). And then everything goes blank and suddenly I'm back to logging in where its just a command prompt, not GUI. Gnome isn't loading...  last Ubuntu I installed, the GUI loaded up right away...  so what do I do?

I can log in and run commands, hell I've been doing reboot for a bit trying to get things to work. So, where do I go from here?

If its easier to tell me on AIM hit me on there: tlove2487

Any help appreciated, thanks!:grin:

---

### Post by aysiu on 2006-04-20
After you log in, type ```
startx
sudo apt-get update && sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
sudo dpkg-reconfigure xserver-xorg
``` One of those should work.

---

### Post by tLove on 2006-04-20
[QUOTE=aysiu]After you log in, type ```
startx
sudo apt-get update && sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
sudo dpkg-reconfigure xserver-xorg
``` One of those should work.[/QUOTE]


Ok, I tried 'startx'.  It gives me the message: "Xsession: unable to start X session --- no "/root/.xsession" file, no "/root/Xsession" file, no session managers, and no terminal emulators found; aborting. (OKAY).

So I ran the next command (the sudo apt-get update && sudo apt-get install ubuntu-desktop) and it did a bunch of stuff. I then tried sudo /etc/init.d/gdm restart and it said the file wasn't found. Lastly I tried reconfiguring and went through those steps doing mostly the defaults. No luck, still nothing.

---

### Post by tLove on 2006-04-20
Ok, so I reran the "sudo apt-get update && sudo apt-get install ubuntu-desktop" code and it took about twice as long. Right after I ran startx and everything seems to be working now. THANKS!

---

