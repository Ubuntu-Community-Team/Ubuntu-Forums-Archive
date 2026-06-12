---
title: "sreen resolution and kvm"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by gatoruss on 2007-03-04
I have Ubuntu running on it own machine.  It shares a monitor/mouse/ketboard with an XP machine thru a kvm switch.

When I boot Ubuntu, the resolutiuon is low (800 x 600, 60 hz).  When I try to change, there are no options for a higher resolution.  If I reboot Ubuntu, it reboots at a higher resolution (like 1024x768, 75 hz).  Problem seems to occur when Ubuntu boots while the kvm switch is reading the xp machine?

Any solution other than not to boot Ubuntu while switch is reading the XP machine?

---

### Post by whein on 2007-04-13
I'm having the exact same problem.  Anybody got a solution?
-Will

---

### Post by twogunmickey on 2007-04-23
I to have the same problem.  It first appeared with 6.06 but went away with 6.10.  I thought I was rid of the problem for good but it seems to have returned after moving up to 7.04 (clean install).

---

### Post by TURNER on 2007-04-23
Hi all, 

In order to add additional resolutions you will need to amend your xorg.conf file

first make a backup of the original "working"file as follows:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then edit the xorg.conf file

```
sudo gedit /etc/X11/xorg.conf
```

scroll to the bottom of the file, where you should see your default screen resolutions, under the depth (default depth is usually 24 I think!)

remember to look up your manufacturers settings before you amend the xorg!

if this doesn't work, back up your xorg, open a terminal and enter:

```
sudo dpkg-reconfigure xserver-xorg
```

using this method you are required to go through the entire xorg.conf however it is effective in many cases, mine included!

hope this helps!

---

### Post by Terl on 2007-04-23
I am assuming you all have your xorg.conf set up correctly as I write this.  Are each of you letting the Ubuntu system boot through while the kvm is set to the other pc?  

I ask because I have a kvm (Belkin flip) but I am not having any problems.  I do watch my pc boot through though and do not switch off of it until I see it has booted succesfully.  Silly, maybe, but I watch each of them boot--just in case.

---

### Post by whein on 2007-04-23
Terl:
I've looked around a bit more and found many others with the same problem.  The common thread seems to be that the KVM is looking at another computer when the X server starts, leading to the low resolution.  An explanation I came across which seems likely is that the X server tries to query the monitor for its configuration, but the KVM blocks this conversation.  X thinks that the monitor must be old/cheap if it won't respond to the query, so it defaults to the crappy resolution to err on the side of caution.  I do know that if you restart the x server (Ctrl-Alt-Backspace) while the KVM is looking at the computer, the resolution will go back to normal.

Now, I think it would be great if there was a way other than restarting the X server that one could use to change the available resolutions.  I understand the decision to set the display to the low resolution at first, but not clear why it keeps you from changing it manually (say after you log in maybe) later.  Maybe this was just overlooked or maybe there is a technical reason or maybe something else entirely.  Like I said, sure would be nice... but since I can't devote my time to it at the moment I can't complain too loudly.  :)  The work that _has_ been done by all the programmers on Linux and everything related to it is fantastic, and the fact that it is distributed free of cost is unbelievable.  I can live with the minor annoyance of restarting the X server when I forget to switch the KVM over in time.

That said, I like to do other things while my machines (re)boot, so I'll play on one until the other is ready for me to log in.  Since they share a mouse/monitor/keyboard that means the KVM is not looking at the right computer.  It's also a problem if I boot both machines at the same time.  ;)
-Will

---

### Post by twogunmickey on 2007-04-23
I can't speek for the others but I'm getting the impression from what I've read that their complaint is the same as mine.  I do not think the problem is setting up screen resolutions under depth in the xorg config.  It is a deeper problem.  And as far as the suggestion of having the KVM switched to the machine while booting is not the right answer.  Yes this will allow it to boot up properly with the all the proper resolutions and that is the way I have to boot the machine now. The problem is that I should not have to wait and watch a machine boot when I have a switch that lets me use the other machine.  It should boot while I am being productive with the other machine.  Then when boot is finished I can switch to a fully working Ubuntu.  It worked under 6.10 for me.

---

