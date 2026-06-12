---
title: "Stuck in a catch 22, help!"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Mariposaloca on 2007-03-10
Ok, so I got Ubuntu cuz I think a virus fried a few things on xp.  I'm pondering getting a bigger hd and setting up both xp and Ubuntu, but I'm trying it out first.  The trouble is, I can't get online!  For some reason, when I try to install a dialer, it insists that I go online to dl it.  Well how do I get online to dl it without a dialer?!  (Yes, I've only got old school style dialup at home, I'm poor.)  

Ok, so I tried all the helpful looking files under "read this first before posting" and none of that has worked.  I've successfully configured, in fact, I had already figured out how to configure before reading the files, but I still cannot dial.  Pon does nothing, and I have found no other option besides gnome-ppp, which I cannot dl, because I can't get online.  Perhaps I need a driver for my modem?  How would I know and how would I find this and get it on  my machine, and then how do I get pon to work, or otherwise get a dialer installed on the machine when I can't connect to dl it?  I've been going back and forth for a few days, because I have to go to work or a library or something to get online.  I can't be putsing around with help files because when they don't work, I have to wait a day or two to get back online and look for something else to try.  Please help!!

---

### Post by igknighted on 2007-03-10
If you can go on windows or another computer and go to packages.ubuntu.com, search for the dialer program there and download the .deb file.  Then put it on your Ubuntu system via floppy disk or jump drive and install (either right click and install w/ gDebi or run "sudo apt-get install <pakagename>.deb" in the terminal).  You might need to do a few rounds of this to get all dependencies, im not sure.

---

### Post by Mariposaloca on 2007-03-10
Does this mean I only need the dialer and no driver for my modem?  The help files seemed to indicate I would not need a driver, but then I'm not sure why pon does nothing.  (I've got an internal hardware modem.)  Perhaps the problem is I don't know which port it is on and guessed wrong?  But how do I find this out?  I thought device manager might indicate this, but if it's there, I'm not seeing it.  I suppose if nothing else I could try configuring it for each possibility and see if one of them works.  Might be nice to know where to find this out though.

---

