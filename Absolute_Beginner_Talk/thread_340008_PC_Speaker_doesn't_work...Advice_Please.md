---
title: "PC Speaker doesn't work...Advice Please"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by noo2bunto on 2007-01-16
I recently installed Ubuntu as an OS on...

Dell Precision Workstation 400,
Pentium II @ 300 mhz,
Matrox Millenium MGA Series w/ Graphics Accelerator,

The problem is that the only sounds I get from this machine are occasional system beeps.  Otherwise, it's as quiet as a mouse.  I don't believe a high end sound card installed; i.e., all sound was from a basic pc speaker.  When I check the Device Manager, and check under pc speaker, I read...

Vendor: Unknown
Device: Unknown
Status: Status
Bus Type: Legacy Device
Device Input: Input
Capabilities: Input

What is the pathway to troubleshoot / correct this?  Do I need a new driver to run this?  Sounds worked fine under Windows 98 & Windows Me...now uninstalled.  Thanks.

---

### Post by carlosfocker on 2007-01-16
First step is what sound card are you using? If its in the mother board what motherboard are you using?

---

### Post by noo2bunto on 2007-01-16
Thanks for the response.  I'm going to have to check this out tomorrow as I'm now away from the machine in question.   Take care.

---

### Post by noo2bunto on 2007-01-17
The online documentation identifies the built in Audio controller as: Crystal CS4236B.  Here's an outtake...

The system board has a built-in 16-bit Crystal CS4236B audio controller chip
and connectors on the back panel for connecting the computer to external audio
devices (such as speakers/headphones and microphone). The controller supports
all the sound functions found on the Sound Blaster expansion card from
Creative Laboratories, Inc.

---

### Post by Arturius on 2007-01-17
That makes it an onboard sound chip I think, what motherboard is it you are using?

---

### Post by irish_flu on 2007-01-17
The Dell Precision workstation uses a proprietary Dell-branded motherboard, IIRC.

That is a full-featured Sound card, as the description says.  Do you have some speakers you can plug into it?

The occasional beeps you're hearing come from the internal "pc speaker".  I *think* that your system might not even have a "real" pc speaker, rather a very tiny one mounted right on the motherboard, designed only to emit the beeps you mention.  It's designed for other sounds to happen via the sound card and attached speakers.

---

### Post by noo2bunto on 2007-01-17
Thanks.  I just finished a chat session with the folks at Dell.  You're right.  According to the representative, the system board is made to Dell Specifications, and "the chipset is: Intel 82440FX PCIset." 

Yes, I have a set of speakers attached.  However, aside from the system beeps I don't hear a thing from them.  The machine seems unusually quiet.  So, I tested it with the Device Manager, and at the point where it asks if I heard anything from the speakers...I don't hear anything.

---

### Post by noo2bunto on 2007-01-17
So, I'm starting to get the feeling that getting this to work isn't necessarily as easy as finding a driver and installing it?

---

### Post by irish_flu on 2007-01-17
Don't take my lack of a response as an indication that your problem is difficult.  I know my hardware, but troubleshooting sound cards in Linux is something I know almost nothing about.  :)

On that note, one of your posts earlier mentioned that the card is very similar to a soundblaster.  Maybe you could use that driver, but I don't even know how to tell you where to start....

---

### Post by cotcot on 2007-01-17
Have you checked alsamixer ?
```
alsamixer
```
This will give you a window with alsamixer settings. There you might need to unmute sound. Use "m" to change from mute to unmute and arrow up to increase the volume.

---

### Post by noo2bunto on 2007-02-09
It Alive!

Many thanks for the help.  As it turns out, it seems I was rushing to reach some conclusions and didn't know to follow [these instructions]("http://www.phptr.com/articles/article.asp?p=667418&seqNum=5&rl=1").  The driver was snd-cs4236, which I also added to the modules file.

There is a helpful sound troubleshooting guide [here]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide").

Thanks again.

---

