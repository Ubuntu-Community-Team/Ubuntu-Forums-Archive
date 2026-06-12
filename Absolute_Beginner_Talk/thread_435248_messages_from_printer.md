---
title: "messages from printer"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Gorsat on 2007-05-06
Printing works fine from my 7.04 desktop to my HP LaserJet and to my Cannon i950 and i9900 (using TurboPrint drivers for the Canons). However, when the printers run out of paper (or ink), ubuntu doesn't give me any notification.  Is this by design or is there a way to get these messages to show up?

---

### Post by cypherzero on 2007-05-06
The notification will probably be sent by the drivers you have installed, not Ubuntu itself.
If your using propriety drivers its likeley they rely on Windows counterpart programs to display such messages. Check to see if your driver has any settings.

---

### Post by Gorsat on 2007-05-06
That's what I assumed about the more complicated case (printing from a Windows box).  But in this case I'm just printing from the ubuntu desktop and, with the LaserJet, I'm just using standard CUPS drivers.  When printing from gedit or firefox in the ubuntu 7.04 desktop, if the printer runs out of paper, shouldn't I get some sort of notification?  This is just standard stuff in Windows, so I'm assuming (read: hoping) that it's also standard in ubuntu.

---

### Post by Gorsat on 2007-05-08
Wow.  This is really frustrating.  I've asked about this many times in these forums.  I've asked about it in other forums.  I've asked about it on IRC in #ubuntu, #cups, #samba and #linux.  I can't get a straight answer.  This seems like a pretty simple question.  Don't some of you ubuntu champions want to help convert me?

When you print from ubuntu and your printer runs out of paper or ink of a certain color then do you get a notification (e.g. a dialog box) or not?  If so then can anyone point me at some documentation on how to configure this?

If these notifications aren't supported then is anyone working to implement it?  Is it something that needs to be done in ubuntu in particular or is it something that needs to be done in CUPS or in the kernel or what?

Assuming that a solution exists or is in the works then what about the network printing case (e.g. printing from Windows via SAMBA to CUPS on ubuntu)?  What has to be done in order to make notifications flow back down this path?

If this isn't the right forum for these questions then can someone point me to a more appropriate place?

---

### Post by Gorsat on 2007-05-17
](*,) 

Seriously...  

No one can answer this?

---

### Post by Sef on 2007-05-17
> When you print from ubuntu and your printer runs out of paper or ink of a certain color then do you get a notification (e.g. a dialog box) or not? If so then can anyone point me at some documentation on how to configure this?

The problem is that Canon does not really provide support for your printer.    For your HP, there is HPLIP Toolbox, which gives the ink levels.   Go to Applications > Add/Remove > Search > type in HP > apply > apply > Finish.   It works with most Laser jets.  

As for you Canon,  I doubt it unless Canon starts open sourcing their drivers.

---

