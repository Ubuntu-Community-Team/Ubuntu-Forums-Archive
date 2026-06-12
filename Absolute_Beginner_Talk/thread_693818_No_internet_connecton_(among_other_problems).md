---
title: "No internet connecton (among other problems)"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by benlaird on 2008-02-11
Hello:
I have just made the plunge to a complete Ubuntu install from a 6.06 disc after viewing a "live demo" off the disc on my laptop.

I now have a couple of major problems!  #1: I cannot make a connection to the internet from my desktop computer that I installed Ubuntu on (I'm using a WLAN 11g USB adapter to send a signal to the router and cable modem).  Everything was running fine (internet-wise) with Windows but a multitude of other problems caused me to wipe that OS completely.

The other problem I have is this: after viewing the "live demo" off the Ubuntu disc, I closed out the demo, removed the disc as requested, closed the door and hit the "enter" key as instructed.  Since that time, my laptop has been completely frozen!  I cannot even power it down and there is no cursor showing anywhere.  I'm now waiting for the battery to die so at least it will shut down.  I had to go next door and borrow my neighbour's laptop to send this info in to at least attempt to get something running here.

I was under the impression from perusing the internet that this operation would be relatively painless but now I have two computers that are not as they should be.

I can navigate around the Ubuntu program on my desktop but without an internet connection, I can't attempt to download possible fixes or seek info on what to try to get things running. (I can't keep this laptop forever and hopefully, Windows will once again reboot on my own after the battery is re-charged.)

For info purposes, this is what I read when I open a TERMINAL re: the wireless connection:

eth1  802.11g   zd1211  ESSID:off/any
mode:managed  Frequency:2.412GHz  Access point: Invalid  Bit Rate:1mb/s
Link Quality:64/100  Signal level=93/100
Rx invalid  nwid:0  Rx invalid  crypt:0  Rx invalid  freq:0
Tx excessive retries:0  invalid misc:0  missed beacon:0

I am certainly no computer "brain" and I may as well attempt to read the Rosetta Stone as to attempt to understand what all the above means.  Is there anything in there I should attempt to correct to see if a connection to the internet can be made.

Thank you for any assistance you can provide.

---

### Post by dca on 2008-02-11
Press and hold power button on laptop until it shuts down...  Apparently wireless is working (or proper drivers installed).  What kind of security do you have on wireless router you're trying to connect to?  If you click on the network manager applet next to the speaker and time window on the top panel it should give you a list of wireless networks to connect to....

---

### Post by benlaird on 2008-02-11
Hello dca:

Thank you for your reply.

Unfortunately I do not have a "Network" applet at the top right of my screen -- only a speaker icon, the time and the shutdown button.

ben

---

### Post by caricc on 2008-02-11
Try this link for your network problems:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by benlaird on 2008-02-11
Hello Carric:

Thank you for the link... I have spent the past hour reading through this and it is obvious to me that Linux is quite beyond my limited computer capabilities.

As much as I hate to do it, it's back to an old version of you-know-what to maintain contact with the big wide world.

ben

---

### Post by ugm6hr on 2008-02-11
> **benlaird said:**
> Unfortunately I do not have a "Network" applet at the top right of my screen -- only a speaker icon, the time and the shutdown button.

This is because you are using Ubuntu 6.06.

It may be easier with Ubuntu 7.10 (but possibly not!)

Unfortunately, USB wifi device support is not great with Ubuntu...

These commands (in 6.06) may give an indication of how hard it will be
```
lshw -C network
lsusb -v
```

---

