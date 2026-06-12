---
title: "Recovery Best Practices?"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by DA_uf on 2006-05-10
I seem to have a gift for hosing my system.  ](*,)   What are the best practices for recovering so I do not have to reinstall?  :-k   This is as much as I know to help others, and I need the blanks filled in to help myself.  Please advise.

_Your GUI froze:_  Your mouse isn't responding.
Did you try Ctrl+Alt+Backspace to restart the X Window System?
Did you try Ctrl+Alt+F#?  (Any of the F keys F1 through F6; F7 may be your GUI again)

_Your keyboard does not respond:_  Did you try to login from a remote machine to restart the X Window System or to invoke an orderly reboot?  Please advise how.

_Remotely Restart the X Window System:_  Please advise for all *ubuntu distributions.  You may need to install sshd or openssh (server) from Synaptic.  Check out the XLiveCD for remote login and GUI app execution.

_Excecute an orderly reboot:_
From a terminal; perhaps Ctrl+Alt+F1, type **sudo reboot**
Enter your password.

_Learn more about sudo:_  From a Terminal, type **man sudo**

_Learn more about man:_  From a Terminal, type **man man**  Hit the Enter key or Space bar to scroll down or Q key to quit.
Incidentally, you can look up anything, not only commands.  or instance **man xorg.conf** or **man xorg**

_You cannot ping from a remote machine:_  Please advise.

_You pressed your warm-reboot button and you hosed your system:_  Please advise.  My system is now hosed.

_You pressed your cold-reboot button and you hosed your system:_  Please advise.  My system is now hosed.

_You have seen a recovery image from GRUB:_  Please advise.

_You told Synaptic to continue even though it said it could not get all the updates:_  :confused:   Please advise.  My system is now hosed.  Next time I'll try, "Cancel".

The Synaptic hosage was on Dapper Flight 7 (which curiously displays Ubuntu Dapper Beta on the desktop), but I've been hosed this way in Breezy as well.

I installed Dapper Flight 7, then did an update.  It need 152 packages or so.  Synaptic (actually the top right update icon app) said it couldn't get everything, I said Continue, then X froze the mouse.  I did not try the keyboard, only the mouse.  I could not ping the machine remotely.  I then warm-rebooted.  Currently I can login graphically (i.e. enter my username and password), but the desktop is brown and I have the mouse arrow but no click response, but movement responds.  I have terminal access via Ctrl+Alt+F1.  Please advise.  Maybe apt-get uninstall something?  I did see an xserver update.

_You've been running stable and have installed many new items; but now you're hosed:_  Maybe you need to start creating a separate /home partition?  :-|   Please advise.

---

### Post by Omnios on 2006-05-10
Bit off topic but one recovery practice that has helped me a lot is if I get in trouble sit back and think about it before jumping in. I useualy go have a  coffee or a smoke then come back in a few to address it after thinkilng about it.

---

### Post by DA_uf on 2006-05-10
[QUOTE=Omnios]Bit off topic...[/QUOTE]

I forgot to say I could not figure out where to post this.  But this seemed like the best place.  Where would you recommend?

---

### Post by DA_uf on 2006-05-12
> You've been running stable and have installed many new items; but now you're hosed:
I've been investigating partition recovery and it turns out a tool I've been using for partitioning, the already useful System Rescue CD [http://www.sysresccd.org/](http://www.sysresccd.org/), already has a tool Partimage [http://www.partimage.org/](http://www.partimage.org/) on it.  Instead of reinstalling and answering configuration questions for the OS and your installed applications, this looks like a great tool to integrate into your Recover Best Practices toolbox.

The approach I am planning to use is to install "partimage" from Synaptic so that I can create the backup from within a running system.  Then if I need to restore from that backup, use the Partimage tool from the System Rescue CD.  I don't know which repository needed to be added to get "partimage", I just added them all.

---

### Post by Omnios on 2006-05-13
[QUOTE=DA_uf]I forgot to say I could not figure out where to post this.  But this seemed like the best place.  Where would you recommend?[/QUOTE]

 No I was a bit off topic lol. Anyways I think begginer talk deals with anything pertaining to a begginer.

---

### Post by DA_uf on 2006-05-13
Well, taking a break and thinking about it is also a good practice, like you said.

---

