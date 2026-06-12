---
title: "The 2 USB ports on front of my computer are not working"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-06-26
Greetings, Ubuntu community,

I have a computer with a freshly installed (not an upgrade) Ubuntu 7.04. I've tried using the 2 USB ports that are in the front of my computer but they don't work. What is wrong?
Is there a way to tell if they are really not working, or just not working with Ubuntu?

It would be great if I could get the USB system all working correctly. Thank you very much for helping a newcomer.

---

### Post by matthewboh on 2007-06-26
It should just work - what happens if you type ```
lsusb
```in a terminal window?  Can you post the results?

---

### Post by rajeev1204 on 2007-06-26
That is because the usb ports on the cabinet are connected to headers on the motherboard and not manufactured directly by the motherboard maker .

The four / or more usb ports on the back of the cabinet are directly conected to the mainboard and so they always work fine .

My usb ports on the front too dont work . The cabinet is a cheap model .

But taking out the ports and cleaning the contacts could get them to work . 



regards

rajeev

---

### Post by matthewboh on 2007-06-26
It should just work - what happens if you type ```
lsusb
```in a terminal window?  Can you post the results?

---

### Post by Cypher on 2007-06-26
Dumb question, but you have plugged the wires from the front USB ports to the Motherboard? If not, that's your problem..

---

### Post by Bartender on 2007-06-26
> **hanzj said:**
> Is there a way to tell if they are really not working, or just not working with Ubuntu?

What do you mean by this?  I'm guessing that you got the PC with no OS at all so you've never seen the front USB ports function?  Is this a hand-me-down or salvaged PC?  As was already mentioned, these should "just work" AFAIK.  

If it were me and I'd never seen the ports work with another OS I'd take the side off and do a visual inspection.  The wires going back from the front USB ports may be damaged or knocked loose from the tiny pinset on the motherboard.  

If you've never messed with this stuff inside the case, the first time can be intimidating.  But it's really very simple.  The front USB plugs are just a little assembly incorporating the 2 ports and the wires that lead back to the pinset on your motherboard.  This is are a mass-produced item that's fairly common from PC to PC. Take a look at the wires leading back from the USB plug assembly.  Those wires will terminate in a little black terminal that fits onto the pinset on the motherboard.  Inspect all of it for any signs of damage.  Also pop the pinset off the motherboard and look closely at it.  You'll see one pin connection is blanked off so that you can tell which way to plug it in.  Take a close look at the pinset on the motherboard.  Do the pins look straight?

One word of warning - if you have a Firewire pinset on your motherboard it'll look just like the USB pinset.  Don't get them mixed up.  You can damage the motherboard if you plug USB into Firewire by mistake.

If you end up suspecting the hardware is damaged, you could take the front bezel off your PC and talk a friend into letting you plug just your USB wires into the pinset on their PC motherboard.  Open up their PC, remove nothing but their USB terminal from the motherboard pinset, (if they have a front Firewire connection be sure you have the right pinset!) then plug your USB terminal in.  See if their PC can run your USB plug.  Then you'll know for sure whether your USB front port hardware is good or bad.

---

### Post by wink on 2007-06-26
As a newbie I was not aware of the **lsusb** command so - naturally - I had to give it a try. Imagine my surprise when it came up listing only 3 ports even though I know (and have since verified again) that I have 4 working USB ports on my Ubuntu-only (no dual-boot) desktop. 

Can anyone explain this discrepancy?

wink

---

### Post by hanzj on 2007-06-27
> **matthewboh said:**
> It should just work - what happens if you type ```
lsusb
```in a terminal window?  Can you post the results?

Matthew,
```
~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by hanzj on 2007-06-27
> **Cypher said:**
> Dumb question, but you have plugged the wires from the front USB ports to the Motherboard? If not, that's your problem..

Well, that's a great question. I guess I could check. I got this computer like this. So I haven't tinkered inside, with the "innards" of the system.

---

