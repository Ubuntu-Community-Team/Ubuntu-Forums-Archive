---
title: "Vidoe playback perplexing."
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-09-28
My 'main' computer's feeble vital statistics are 1.8 Celeron, Shuttle all-in board, and 1.5g Ram. It has an onboard video card. The basic machine is about 4 years old. 

I recently purchased a 22 inch w/s lcd monitor.

As soon as I started using the new monitor, video playback was weird. Even with VLC, the sound would start, the screen would black out for a second or so, then the video would appear. (This didn't happen with the 17 inch CRT monitor)

Fair enough I suppose. I need a better video card ...

Just before, I connected a spare box to the same monitor. It's an old Pentium II with about 500 meg RAM and some funny old video card 3D-AGPhantom which doesn't even have a heat-sink. (I just checked)

The movies played back perfectly.....

That card must be much older than what's on the Shuttle board.

Or not. 

Any ideas?

Cheers.

Mike.

PS. OK so I popped the (what turns out to be a reasonably decent)
 old 3D card into a slot where it fitted and fired up the 'main' box. 

After some waiting -at least SOMETHING appeared on my monitor- I wound up with that problem with x-org config screen which I've seen before and don't know what it means.

Presumably I need some drivers for the card. 

Or, ought I get into BIOS and somehow or other disable the onboard card?

Sorry about my lack of correct jargon.

Thanks in advance.

Mike.

---

### Post by overdrank on 2007-09-28
Hi and did you reconfigure your xorg when you attached the new monitor? Also what is the model of the old card you installed?

---

### Post by MichaelSM on 2007-09-28
Thanks for your reply.

No. I didn't configure anything x-org.This is relating to my original hook-up of the monitor with the Celeron/Shuttle scenario.

I simply plugged in the new widescreen monitor and let it go. In other words I connected the vga plug to the motherboard's receptacle.

I didn't know I had to to anything else..

The video card from the old box is a 3D unit, apparently a MicroStar 4420, if that helps.It seems to have other names.

To get my 'screen' back,(using my 'main' box) I had to remove the video card and re-start, with the monitor connected to the onboard vga plug, which is my usual set-up. Which I'm using now.

With the video card in place,  I couldn't get a screen up. I'd hang on fsck and 'it' would recycle.

So, going back to my spare box, the slower unit I mentioned, which handled the video card without me even thinking about it: 

I bought it at a garage sale, so I have no idea who put what into whatever re. BIOS.

So, to put it simply:

Do I need drivers for the new/old video card? It's obviously a far better unit than the onboard one. Since it doesn't have the hang-ups I mentioned previously, and works with a poor old PII and a fair bit of RAM, what do I have to do to utilise it in  my main box?

Is it a BIOS scenario? 

Thank you.

Mike.

---

### Post by overdrank on 2007-09-28
Hi ok I am getting confused with these systems. Lets try and stick with one ( sorry its early in the morning) Ok the card you mention MicroStar 4420, when you put it in the system 1.8 Celeron, Shuttle all-in board, and 1.5g Ram System #1 it does not boot and hangs on fsck. What is the graphics on thats system (intergrated) ? You can check the bios and make sure it is set to the acp (pci ) card. 
Also since you have the card working on system 2 then you can get the specifics on that card with the command lspci in the terminal. That will help to know.

---

### Post by MichaelSM on 2007-09-28
Thank you overdrank and there is no hurry. It's early in the morning for you and just into the  morning for me.I'm pretty stuffed...

Re. lspci. Ok I'll do that on the 'old' box, but I think the card isn't pci; it's in a weirdo slot.

Get some sleep.

It's amazing how a new day brings forth better things.

Thank you. No doubt I'll be back!

Mike.

---

### Post by overdrank on 2007-09-28
> **MichaelSM said:**
> Thank you overdrank and there is no hurry. It's early in the morning for you and just into the  morning for me.I'm pretty stuffed...

Re. lspci. Ok I'll do that on the 'old' box, but I think the card isn't pci; it's in a weirdo slot.

Get some sleep.

It's amazing how a new day brings forth better things.

Thank you. No doubt I'll be back!

Mike.

No problem Mike I just had to get my coffee down. :) The lspci command will list the components of your system no matter if the card is pci, pci x, or agp. also list your nic card and other great information. :guitar:

---

### Post by MichaelSM on 2007-09-28
Thank you again, overdrank. I guess I'll run that through the 'old' PC box and see what's happening. How I translate that knowledge to my 'main' box will be interesting.

I didn't know that lspci interrogated all ports if that's what you mean. Are they 'ports'?

Either way, with the 3D card in my 'main 'box, I must have to get into the BIOS, otherwise it's all a waste of time. if I can't get a screen up, then I can't do anything in terminal or anywhere , lspci included. So long as the card is in its slot I can't boot.

Is it a driver issue? I'd like to think that it isn't. That old video card was around a long time ago, and Ubuntu (in this particular case, Edgy) must have the requisite updates for it but I can't find them in synaptic. Maybe I haven't looked hard enough ...as per usual.

Cheers and have a good day.

Mike.

---

### Post by MichaelSM on 2007-10-05
Hello again Overdrank.

To finish of this thread ..

All fixed. I learnt a lot about xorg in the process, plus that it backs up previous settings automatically.

It's amazing to a relative newbie the effects various combos of cards on different boards with different RAM have on performance. Or even access to gdm. 

All is good until I play with it again. Then at least I know how to fix stuff.

Thank you for your patient advice.

Mike.

---

