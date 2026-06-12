---
title: "New issue - slow program executions"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by DonDodge on 2007-12-21
This install has been one thing after another but I've muddled through most of it. Some of the early problems are resolved but those were piddling. Now they just keep getting bigger and better.

I lost my xserver due to changing to an inappropriate graphics card driver in attempt to resolve one problem. I fixed that with:

dpkg-reconfigure -phigh-xorg

This gave me back the display and coincidentally resolved the original display problem but everything became painfully slow with a three minute boot and my panels goofing up. I got: The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitch Applet". I was asked to delete it which I declined and promptly lost all my panels and all functionality requiring a hard reset. Nothing worked again until I ran the xserver reconfig from recovery console. This didn't help with the panel problem but once again offered the opportunity to delete the errant applet mentioned above. The only thing deleting the applet accomplished was losing everything but desktop icons and and mouse functionality. After this, the panels kept freezing, disappearing or simply not loading. 

Since then I've repaired the panels by making a terminal launcher and running:

sudo debconf gnome-panel

Now everything works but system executions are still taking forever. It's taking 42 seconds to start anything like gedit, terminal, system log or control center. I get the spinning disc icon  and a panel button that says "Starting (whatever-program)" for 15 seconds, then the disc icon changes to an arrow and the button goes away until the 42 second point when the panel button reappears and the app starts.

I suppose there's some sort of an error or timeout that's worked it's way into the system. Does anyone know a command that will repair this latest problem?

---

### Post by Cypher on 2007-12-21
Open up the terminal..Application->Accessories->Terminal and type "top". This should show you the current system usage, idle time and other information. It will also constantly update to show the processes that are hogging any CPU power..

If nothing jumps out at you, you might want to take a screenshot and post it here..

---

### Post by DonDodge on 2007-12-21
I've discovered the problem. I created it by trying to solve another problem in the midst of this PITA install. That problem is the computer connecting to the dialup internet during the boot and being connected before I even get logged on to ubuntu.

If I disallow that bootup connection by shutting it off in System/Network/Modem Connection or Properties, it takes over four minutes for ubuntu to complete the boot sequence with the loading and activation of my panels. This is also what's making these applications load so painfully slow.

As soon as I manually make an internet connection/disconnection, the problem is over. A terminal, text editor, file browswer, etc. loads in about a second instead of 42 seconds.

If I allow the autodialed internet connection to be made during the boot, all the panels are loaded and the computer is ready to work in under 75 seconds and application excution is as it's supposed to be.

The only way I can kill this autodialed internet connection is with a sudo poff command in a terminal.

Is there any way to deal with this? I really don't want my gizmo to autodial the internet every time I boot into ubuntu and it just don't seem right for a computer to be totally crippled until it gets it's little dose of internet. 

The system won't allow me to solve the problem by taking away the modem, phone number or anything else in Network Settings. The computer is simply useless until it's allowed to connect to the 'net. How dumb is that?

---

