---
title: "[SOLVED] System freezing when connecting to wireless network"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by SegaFan on 2007-12-15
**Edit: This is now solved. To help people in future, here is what I did:**
The problem was with the default driver for the network card (an RTL8185) that I was using. The driver that was causing the problem was rtl8180. Once I realised this I installed a new driver with help from the Wireless and Networking forum and it now works fine. The topic (with full instructions) is here:
[http://ubuntuforums.org/showthread.php?t=642996](http://ubuntuforums.org/showthread.php?t=642996)
I hope this is helpful to other people with this network card. Thanks.

Original post:

When I select my network and enter the WEP key, then click Login to Network, it appears to begin to connect but freezes after a couple of seconds, all I can do is reset, I've tried it about 3 times. Any ideas of what the problem is?

Also a general question, since I'm a completely new to Ubuntu and Linux, is there an equivelent of Windows 'ctrl+alt+del' that I could try when things like this happen?

---

### Post by SegaFan on 2007-12-15
Still haven't got any further with this. Ubuntu itself is great so far, I really like it, but I can't do anything without the internet. Please, any suggestions, even if its not a total fix, would be appreciated.

---

### Post by daimaru on 2007-12-15
can't help you with your first question, but as to the ctrl+alt+del equivalent:
to restart xserver (you land at login screen again)
hit ctrl+alt+backspace
if your computer is totally frozen and that does not work you can try this:
 [SIZE=3]_Alt+PrintScreen_+R+S+E+I+U+B

more info in this [thread]("http://ubuntuforums.org/showthread.php?t=617349&highlight=raising+skinny+elephants")
[/SIZE]

---

### Post by SegaFan on 2007-12-16
I'll give some more details to see if that helps. Please give me any information that *might* be useful, even if you can't fix the problem the more things I can try the closer I can come to diagnosing the problem.

I should probably point out that this is a brand new machine that I built myself, I only had it up and running since yesterday and it's never had anything other than Ubuntu on it so I still don't know whether it's a hardware or software problem.

It can see my network fine, the problem appears to be when it first tries to connect. It doesn't get anywhere near as far as checking my WEP key, I don't think it establishes any kind of connection before it freezes, just attempting it makes it freeze (though it does seem to recognise that my network requires a WEP key before I attempt to connect). Sometimes it freezes in a second, sometimes it takes several seconds and then freezes.

I'm finding this incredably difficult to troubleshoot. I tried using Fedora's live CD to see if it's just an Ubuntu problem, but I can't figure out how to set up wireless networking *at all* in Fedora, I don't know if you can help me there.

Then I tried using the same Ubuntu disc in a laptop of mine that I know works on the wireless network in Windows. Just running it off the CD, not a full install. But I get a *different* problem, as far as I can tell it doesn't recognise my wireless network card. Usually a light flashes on my laptop when the wireless function is switched on, but in Ubuntu it doesn't. But nevertheless, when I try to connect anyway it doesn't freeze, eventually it just times out, which is unlike on my new PC when it freezes before anything happens (regardless of whether it's in range of a network or not).

I don't know if this'll help. There are two LEDs on the back of my wireless network card, one that says ACT and one that says LINK. The one that says ACT flashes continuously, the one that says LINK is off all the time, and turns on when I attempt to connect and is on when it is frozen.

Thanks to daimaru for your help, it's given me something else to try; When it is frozen, ctrl+alt+backspace and Alt+PrintScreen+R+S+E+I+U+B both don't work (and I'm pretty sure I'm entering both of them correctly because I just tried them out beforehand). It's completely frozen, nothing moves except for the still image of the desktop, the on-screen clock doesn't move forward, nothing happens. I see in that thread daimaru linked to it says:
> NOTE:- This keystroke does not work in the event of a kernel freeze as the keystroke sequence depends on the kernel in order to unmount and make the required steps before the restart.
So does this mean that the kernel has frozen?

---

### Post by SegaFan on 2007-12-16
I hope no-one minds if I bump this.

---

### Post by Bigbird999 on 2007-12-16
Noob here!  I maybe way off base, so act accordingly  on my advice.  It sounds like a wrong driver issue, so you need to try using ndiswrapper.  Not all wireless cards are supported by Ubuntu.  Search through the wireless and networking forum and you should find a bunch of "how to" links and maybe somebody has your exact laptop and can get you going.  

BB

---

### Post by SegaFan on 2007-12-17
OK, it's a desktop PC, not a laptop, one I built myself so no-one will have the exact one. I did check the driver and it does appear to be properly installed. I will look at the wireless and networking forum if I don't get any success from here, but since I'm a n00b I want to try here first.

Thanks.

---

