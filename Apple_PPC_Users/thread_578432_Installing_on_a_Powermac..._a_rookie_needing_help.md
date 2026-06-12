---
title: "Installing on a Powermac... a rookie needing help"
date: 2007-10-17
forum: Apple PPC Users
---

### Post by tjdixon27 on 2007-10-17
Hey Guys,

I just downloaded a copy of Ubuntu 6.10 Desktop for Powerpc, and am trying to work out how to install.

At this point I have burnt it just booted off the CD. A black screen comes up with no user interface and some text, telling me to press enter to continue (you all probably know what i'm talking about). After this, the screen changes and I get stuck on a white screen.

I have tried "live video=ofonly", "live" and "live-powerpc" but no matter what i can't get past the white screen.

I'm running a G4 Powermac with a 867Mhz PowerPC Proccessor G4, and i Have a gig of RAM in the computer. I'm trying to install on a empty hardrive.

I'm really new to Ubuntu, so directions to a good installation tutorial or any other hints you can give me would be really appreciated.

---

### Post by roazena on 2007-10-17
As often as not PowerMacs need to be installed from the Alternate installer CD rather than the LiveCD. Ubuntu LiveCDs are great, but one of the main reason the Alternates are still maintained is because they are more stable for a wider variety of hardware (esp. older hardware) on both the PPC and Intel platforms.

Download the Alternate CD and try from there.

---

### Post by ticopelp on 2007-10-17
I've had an identical problem trying to install the Gutsy RC on a Powerbook, but the Feisty CD worked just fine. You might consider giving Feisty a try. 

I was going to say, try booting with

```
live-powerpc video=ofonly
```

and see if that works. That's what worked for me on Feisty. It sometimes does take awhile to boot off CD, I've noticed. 

Be advised that if you do boot / install with video=ofonly, you'll later have to remove that option from yaboot.conf, or your laptop won't suspend / sleep properly. An entirely different issue, but I thought I'd let you know, in case you manage to get it running.

Here's the link to the PowerPC ISOs for Feisty:

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

Best of luck.

---

