---
title: "Fiesty Fawn Failure"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2007-04-23
I cannot install Fiesty Fawn as I cannot see the entire install window.

My computer specs include, Nvidia 6600GT, 19" CRT monitor.

I start the CD and get the live version running.

Ubuntu locks the screen resolution at 800 x 600 or 640 x 480 with either 60Hz or 56 Hz. 

The install window is too large. It disappears under the task bar at the bottom. The install window cannot be resized. The "ok" or "next" button is hidden.

Pressing the "enter" button only works to the "Migrate settings from XP" and then loops. Obviously some important setting is hidden.

I really have to wonder how Fiesty Fawn managed to pass testing. It is time that Ubuntu increased the minimum default resolution to at least 1024x768 and 75Hz.

Fiesty Fawn Failure - 800 x 600 and 60Hz max, and an install window that is designed for higher resolutions and cannot be resized from the 800 x 600 is a joke.

So how to resolve this Fiesty Fawn Failure?

I tried throwning the CD on the carpet in disgust but that didn't help ! :lolflag: Ok it helped a little.

---

### Post by spin2cool on 2007-04-23
The default resolution should be higher - my default is 1024x768.  It's a problem with your video setting being detected properly.  You might try the alternate CD.

See this thread:
[http://ubuntuforums.org/showthread.php?t=419902&highlight=livecd+resolution](http://ubuntuforums.org/showthread.php?t=419902&highlight=livecd+resolution)

---

### Post by igknighted on 2007-04-23
I've got the same video card and it runs 1280x1024 on the livecd.  I can't use DVI though without tweaking.  Ubuntu has a hard time querying the monitor through DVI.  To fix the issue edit the proper resolutions into xorg.conf and then restart X.  Also "sudo dpkg-reconfigure xserver-xorg" will do the trick as well

---

### Post by LaurelLynn on 2007-04-23
Dear u.b.u.n.t.u,

There are two workarounds I have used for dealing with this type of problem.

1. You have probably tried the first one, which is the VGA function key when the Live CD boots, I think it is F4. Or you can enter the the mode you want at the boot prompt:

boot:  vga=791   (1024x768 16bits)

This link:   [http://gentoo-wiki.com/HOWTO_Framebuffer_Support](http://gentoo-wiki.com/HOWTO_Framebuffer_Support)

Has a table on it of the number to use for each resolution. The numbers are in hexidecimal though and have to be converted to decimal before using. 786 is  1024x768 and _24 bits_.  Even the VESA drivers should support that  for anything but the most ancient of graphics cards.

2. When that has not worked I was forced to use Alt+F7 during the installation.  This allows you to move the current window with the mouse to a new location.  Thus allowing you to drag what is off screen to where it is visible.  I use it just long enough to do the install, then change xorg.config to something with a little more space.

IIt is tedious, but you can install even at 640x480 by filling out the parts you can see, then moving the window to reach what is off screen.

Hope that helps.

---

### Post by robtg on 2007-04-23
I had the same problem on my Compaq laptop; Feisty defaulted to 800x600 unlike its predecessors.  I got around the problem by dragging the upper and lower panels to the left and right-hand sides of the screen.  This let me raise the installation dialog high enough to access the Next button.  Dorky but it worked. 

-Rob

---

### Post by igknighted on 2007-04-23
> **robtg said:**
> I had the same problem on my Compaq laptop; Feisty defaulted to 800x600 unlike its predecessors.  I got around the problem by dragging the upper and lower panels to the left and right-hand sides of the screen.  This let me raise the installation dialog high enough to access the Next button.  Dorky but it worked. 

-Rob

If you hold alt and click you can drag the window around the screen without seeing the titlebar as well.

---

### Post by robtg on 2007-04-23
> **igknighted said:**
> If you hold alt and click you can drag the window around the screen without seeing the titlebar as well.

Aha!  That would have worked too.  I've learned something new; thanks for the tip.

-Rob

---

### Post by u.b.u.n.t.u on 2007-04-23
Thanks LaurelLynn and everyone that replied.

The F4 at boot didn't work. The screen resoliution defaulted back to 800x600.

The "Alt F7" is neat, but I refuse to install Ubuntu 7.04 like that. I have deleted the ISO and binned the CD I burned.

If Ubuntu can stuff up something so simple as screen resolutions (yet again), I am seriously not going to waste my time further on "making things work". I tried to edit the Xorg and the changes should have worked but didn't.

For whatever reason, Fiesty Fawn does not work on my computer and it isn't worth the trouble spending hours to get it to work.

I will lodge a bug report and wait for Gutsy Gibbon in October and see if Ubuntu is working at that time or not.

It simply isn't good enough to have this problem.

I was going to introduce a friend to Ubuntu but that will have to wait now too.

I have used Ubuntu in the past but it simply isn't ready yet as a XP replacement. Just too many "work arounds" needed. Then there is the entire issue of "forget games all ye who enter Linux" - but I am happy to dual boot, if only Ubuntu was up to the task of replacing XP at everything else, but it isn't. It can't even get something so basic as screen resolutions correct (this is an ongoing problem).

Having to Alt F7 and edit the Xorg just isn't acceptable (an Xorg edit was just ignored).

I want Ubuntu to work but it doesn't. Fiesty Fawn can join Vista - both failures.

So much for all the reviews of Fiesty Fawn - it hardly matters when one cannot even install it without working around install breaking problems such as the install window being too large and cannot be resized.

This isn't a dig at Ubuntu so much - they really ought to have such an issue fixed by now!

I wish Ubuntu well, but Feisty Fawn is a Failure. It failed for me and that is enough as I am concerned.

I look forward to Gutsy Gibbon in October.

Cheers.

---

### Post by drsaamah on 2007-04-27
If you took the time to think rationally you would realize that XP is in no more efficient than Ubuntu, Fiesty, Edgy, or otherwise.
The reason you don't have to deal with so may "work arounds" with windows is because when you buy your computer, it comes WITH windows.  The right software, the right drivers, everything is already there.
If Dell and other computer companys cared enough about their customers freedom of choice, they would give us the option of getting Ubuntu distributed with our computers with all the right drivers so that we don't have to deal with these "work arounds."

Regardless, your issue isn't a fiesty problem.  I had the same exact problem when I first switched to Ubuntu 2 or 3 months ago (Edgy).  I can't remember exactly how to fix it but the problem is essentially you have the computer recognizing your monitor as a monitor that isn't.  Search around these forums and you should be able to find a solution.  Thats how I fixed mine.

---

### Post by mosesau on 2007-05-01
Well put drsaamah!
The first thing you have to do with a windows install is to collect all your drivers, then install motherboard drivers. Hmmmm ....
I agree with u.b.u.n.t.u though, to some extent, as I think this bug should have been found before the release and corrected.

---

### Post by ShadowVlican on 2007-05-02
> **LaurelLynn said:**
> 2. When that has not worked I was forced **to use Alt+F7 during the installation.  This allows you to move the current window with the mouse to a new location.**  Thus allowing you to drag what is off screen to where it is visible.  I use it just long enough to do the install, then change xorg.config to something with a little more space.

IIt is tedious, but you can install even at 640x480 by filling out the parts you can see, then moving the window to reach what is off screen.

Hope that helps.
excellent tip! i had absolutely no idea i could do that! i've been having the same problems as the OP and with this trick i can finally install ubuntu 7.04

> **u.b.u.n.t.u said:**
> Thanks LaurelLynn and everyone that replied.

The F4 at boot didn't work. The screen resoliution defaulted back to 800x600.

The "Alt F7" is neat, but I refuse to install Ubuntu 7.04 like that. I have deleted the ISO and binned the CD I burned.

If Ubuntu can stuff up something so simple as screen resolutions (yet again), I am seriously not going to waste my time further on "making things work". I tried to edit the Xorg and the changes should have worked but didn't.
i agree with your feelings

this is an age old problem too... do the developers **not **check out the forums for some criticism?

---

### Post by kakw on 2007-06-08
I'm new to linux as well and was very excited to try ubuntu fiesty fawn, but unfortunately i'm stuck with the 800x600 resolution issue and the laptop freeze issue.   I'm gonna give another shot to go past the 800x600 resolution issue, but dunno what to do about the laptop freeze issue.
fyi, my laptop is an old (few yrs) hp/compaq laptop which has a ATI radeon card and pentium chip.

---

