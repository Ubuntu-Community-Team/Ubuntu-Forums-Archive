---
title: "unable to read screens that are WAY TOO big"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Hope on 2007-04-14
Hi everyone, I've just installed Xubuntu on a Benq. It works ok but the screens are TOO big and I can't read or access all the stuff. For instance - trying to set up the printer I'm unable to set it correctly as the bottom part of the page is off my screen and I can't even shrink it and move it up, if you get my drift.
How the heck do I reset this???:confused: 
I'm totally new at this and my 'friend' who convinced me to use ubuntu is also in the dark.
Help!
Hopeful

---

### Post by BoneKracker on 2007-04-14
Did you try changing the resolution?

---

### Post by Hope on 2007-04-14
If you mean in 'display preferences' there aren't any real options other than default and '320 x 240 @60' and when I even click here it magnifies the screen almost off the scale!
Other than that I don't know how to change the resolution
Thanks
Hoping.

---

### Post by BoneKracker on 2007-04-14
I don't know what a Benq is.  I'm going to assume it is capable of better resolution than that.  The installer usually automatically sets up a pretty decent configuration, but it may be unfamiliar with your hardware.

What you probably need to do is correct the configuration of the monitor that is being used by X windows.  That configuration is kept in a file called /etc/X11/xorg.conf.

First, you need to find out what the specifications of your display or monitor are.  Specifically, you need to know what it can handle in terms of Horizontal Sync and Vertical Refresh frequencies.  This information should be available in the manual that came with it, or on the manufacturer's web site.

Although it is tedious reading for someone who is not familiar with Linux and X Windows (which is commonly referred to as simply "X" or "Xorg" these days), I recommend that you try to read through the manual that describes this configuration file.  You can do this by issuing the following command in the terminal:```

man xorg.conf
```
You will need to edit the configuration file:
```
sudo nano /etc/X11/xorg.conf
```If you are unable to do so , you may need to get out of X and do it at the virtual terminal (vt).  You may be able to switch to a virtual terminal (vt) by holding down ctr+alt+F1.  If not, you should be able to exit from X by holding down ctrl+alt+backspace and then immediately logging in to the vt that comes up before X restarts.

Here is an example of the section that I think you may need to fix (it starts with Section "Monitor".)  Note that it includes the lines HorizSync and VertRefresh.  You should not guess, and _you should not simply copy what somebody else uses, unless they have the same display as you _(you can actually damage your display).
```

Section "Monitor"
        Identifier      "Monitor0"
        VendorName      "MAG Innovision"
        ModelName       "720V2"
        HorizSync       30-70
        VertRefresh     50-120
        Option          "DPMS"
EndSection
```You should also probably use your favorite web search engine to look for tips from other users of the same machine.  Search for "benq xorg.conf".  Search for "<insert your display nomenclature> xorg.conf".

There are some autoconfiguration utilities that set up the xorg.conf file for you.  The installer uses one of these and it apparently didn't work right, so that's why I'm suggesting the manual route.  But you should be aware that they exist.  One of these is mentioned at the top of the xorg.conf file.

---

