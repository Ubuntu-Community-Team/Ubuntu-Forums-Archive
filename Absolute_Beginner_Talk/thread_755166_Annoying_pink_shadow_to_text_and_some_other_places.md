---
title: "Annoying pink shadow to text and some other places"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by SlappyPappy on 2008-04-14
I switched to an ATI video card and now I've got this horribly annoying pink shadow to some text or rather it's the left hand portion of the page. It occurs with text and the left hand edge of windows. I did a search for a fix but didn't find anything.

I'd be willing to kill the shadow if it banishes the pinkness.

Thanks for the help.

---

### Post by tcpip4lyfe on 2008-04-14
What driver are you using?

---

### Post by SlappyPappy on 2008-04-14
Apparently it's the open source ati driver. I installed the card this morning and the problem I'm having is this weird pink cast that shows up in Firefox on the left and now that I'm looking at it it's on the right as well.

---

### Post by tcpip4lyfe on 2008-04-14
Take a screen shot and post it. What kind of video card do you have?  What video card did you come from?

---

### Post by SlappyPappy on 2008-04-14
Had an old TNT2 nVidia card and put in an ATI Radeon 7000.

You can see it in the pic the letter M in message has a pink or purple look to it.

And the box has a left edge that is purple or pink. This is even more pronounced on my monitor. 

BTW thanks for taking the time to look at this for me.

---

### Post by tcpip4lyfe on 2008-04-14
I don't see anything.  Are you sure it isn't your monitor?  You can re-configure the xserver.


Backup your xorg.conf first then:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Then:
sudo dpkg-reconfigure xserver-xorg

Use the vesa drivers and start with a basic 800x600 resolution first.  Compiz won't work but you'll be able to tell if it was the drivers or a hardware problem.

If it's the drivers re-ocnfigure the xserver again with the same command and choose fglrx and the max supported resolution with your monitor.  See if that works. 

If that doesn't work try the ati drivers when you reconfigure.  

Remember to backup your xorg.conf.  If things get sketchy and you break xwindows, all you have to do is:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf 
sudo /etc/init.d/gdm restart

Good luck.

---

### Post by SlappyPappy on 2008-04-14
You might be right, it could be the monitor going wonky it's just that I didn't see it when the nVidia card was installed.

I'll work through this and then see if I can find a 2nd monitor to try out.

Thanks for all the help man. Good to know that process that you wrote down.

---

### Post by SlappyPappy on 2008-04-14
I should add that on the desktop you never see the pinkness at all it's just when you open up Firefox or a directory. 

Damn shame as the screen looks amazing and much better than the previous nVidia card I was using.

---

### Post by SlappyPappy on 2008-04-14
Hey brah, I ran the reconfigure and everything looks great now. No pinkiness at all.

Looks much better than my previous nVidia card. Very happy!

Thanks for all your great help.

---

