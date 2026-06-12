---
title: "[SOLVED] Ubuntu Install Freezes at 15%"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Futures Trader on 2008-01-15
Hi. I'm completely new to Linux and Ubuntu. Thought I'd give it a try since I had an older computer just sitting around not being used.

I have a Pentium III 100MHZ with 256meg memory.

Using the LiveCD installation, most recent desktop version 7 Ubuntu.

CD was verified good.

I'm able to boot up with the CD and I get the desktop just fine. Really nice look.

So I run the INSTALL icon and answer some questions. It then goes to the Partitioner and I select that it do a full Guided installation. I have two hard drives, one is 110gig and the other 160gig. They are both blank and available for use.

From this point, you see it working and the percentage gets to 15%. This is where it says...

"Installing System"

"Detecting File Systems..."

After two hours of sitting at 15% and the wording not changing, I realized it was not working. I know the machine is slow, but something is not right.

I even tried to partition the drives PRIOR to using the INSTALL icon. That didn't make a difference.

Sure could use some help.

Thank you!

---

### Post by JoshuaRL on 2008-01-15
Are you sure that the processor is a PIII 100mhz?  Maybe a 1.0ghz?  But if not, you'll have to use a smaller desktop manager.  You see, Ubuntu uses a GUI called Gnome.  You should probably use the one called Xubuntu which uses XFCE and is easier to run on older computers.  It's still the same base OS, but with a different GUI on top.  And I would suggest using the Alternate CD since that needs less system resources to install.  The regular CD needs to boot into the Live CD to install, and the Alternate CD runs off of a text-based installer that is just as easy.  That should solve your problem.  It may take a while still, but it should work.

---

### Post by Futures Trader on 2008-01-15
Thank you JoshuaRL.

I was just coming back to post an AMAZING thing.

You see, I started this installation just before 8:30pm my time. When 10:30pm came around and the screen was still showing the SAME progress bar at 15%, no change in the wording, and the mouse was still frozen in place, that is when I realized a problem and posted my original message.

No sooner than 5 minutes after posting it, my slow machine started making activity noises (the CD and hard drive), and things started to get lively. Minutes later, the desktop disappeared, came back, and the mouse is no longer frozen. In fact, a window is now showing on the desktop with folders in it!  IT'S ALIVE!

Maybe this will be helpful to other newbies to let the machine just sit there a few hours. I didn't do anything to bring it back to life. It just happened.

Wonder why the progress bar was sitting stuck at 15% and the mouse would not move. That is what made the whole thing appear dead.

Thanks again JoshuaRL.

:)

---

### Post by Sef on 2008-01-15
> Are you sure that the processor is a PIII 100mhz? Maybe a 1.0ghz?

The PIIIs started at 450 mhz and 500 mgz, so most likely 1.0 GHz. (Not a PII, which started at 233 and 266 mhz.)   With 256 mb ram, the alternate install will work better.  Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").  To get the alternate download, just click the box at the bottom of the [download site at Ubuntu]("http://www.ubuntu.com/getubuntu/download").

---

### Post by Futures Trader on 2008-01-15
Thank you Sef.

I'll check the POST again when I'm able to reboot to note the MHZ information. I was pretty sure it said 100MHZ, but then I could be hallucinating. :b  I'll edit this message once I get a chance to find out what it is.

Meanwhile, the progress bar is now showing 27% "Copying Files...". So it's doing something now. Was very strange just sitting there at 15% for over two hours, and now it just comes alive all by itself and is making a rukus installing.

The response on this forum is fantastic. I think I'm going to enjoy working with this OS. Just purchased 3 books 10 minutes ago so I can get up to speed quickly. Living in the Windows world for two decades, this Linux thing is a whole new world for me.

Again, thanks much!  :)

---

### Post by Futures Trader on 2008-01-16
My mistake. It's a Pentium III at 600MHZ, not 100MHZ. (ahhh. better.)

The installation completed! It's now downloading updates. Super cool!

Anyway, total time to install on this machine is 3.5 hours. 2 hours sitting at 15%.

All is well now.

:)

---

### Post by Sef on 2008-01-16
> My mistake. It's a Pentium III at 600MHZ, not 100MHZ. (ahhh. better.)

The installation completed! It's now downloading updates. Super cool!

Anyway, total time to install on this machine is 3.5 hours. 2 hours sitting at 15%.

All is well now.

1) 600MHz: That makes more sense.  

2) Had a hiccup for some reason.   Just glad it worked itself out.

---

### Post by Toribor on 2008-01-23
I have a Dell XPS M1210 and I am trying to install Ubuntu on an external hard drive. The install stops at 15%, it doesn't freeze, it just stops. I have plenty of space for everything, and can't seem to figure out what is going on...

---

### Post by philinux on 2008-01-23
It could be the nvidia graphics card. 

I'd get the Alternate Desktop Cd. It's not live and is a text based installer.

On the ubuntu download page below "Start Download" is the checkbox for it.

After the install you can use ENVY to set up your gfx card or the restricted drivers.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

