---
title: "Dialing Out.  Day 4."
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Lonelynoob on 2007-03-12
Okay, I swear I should be documenting this.  Let's bring everyone up to speed.

I do not have wireless and an incomplete ethernet connection.  So those are out.
I have an on-board modem on my laptop.
I am using 6.10.

I do not have an Internet dialer.  Which means no Internet access on my laptop.  Any files downloaded from this machine I'm typing on (WinXP) need to be moved via floppy or CD as I don't have a USB stick.

Any attempts to load an internet dialer (or any program for that matter) from the CD says: "This program cannot run on your computer (i386) Your system is missing required parts or the vendor decided to not support your system."

I tried downloading gnome ppp and spent 4 hours trying to make sense of various code commands, which half-worked, but would always fail when using the "make" command.  BEAR IN MIND I HAVE NO IDEA WHAT THIS PARAGRAPH MEANS.

The Synpatic Package Manager gave me grief, couldn't find the program and was obviously missing something. As the "simplicity" of everyone else's experience was only met as retarded-ness on mine.

All I want right now:  Is for this laptop to dial the internet.  It worked with Wondows, I know it functions.

I want a dial tone.  Maybe a few tones and some line noise.  That's it.   That's  All.  Today marks Day 4 trying to get this to work.

If you can do it, I'll be shocked and impressed while I piss my pants.

PLEASE for the sake of keeping me from slitting my wrists, please explain steps instead of just typing out a step, as I likely will not be able to follow you.   If you want a skype or iCall number, we can do that.



And:  Go.

---

### Post by eljalill on 2007-03-13
Hello!

I am probably not up to speed, so these are just a couple suggestions:
Are you sure, your modem is actually up and running?
You could type "lspci" in a terminal and see, whether you find your modem in the output ( if you don't know, how it should look like, post the output here). As far as I know, this gives you a list of all "up" devices, and with me the modem is in there.
Since I expect it's there: in network, you should be able to configure your modem. You find it in the system panel on top.

For both this you should not have to install anything additional.

Hope there was some help in this....

Oh and synaptics can't help you much, if you are not connected to the internet. Some programs you can get from the install CD with synaptics. But make sure, that the CD is enabled as a source for synaptic, only then it will look there: when synaptic is open go to Settings> repositories .

If you are sure to miss anything big, and other people have it, you might consider a reinstallation of ubuntu... especially if you don't have anything important on your laptop yet..

---

