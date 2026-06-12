---
title: "Ubuntu and a KVM Switch Problem..."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by The Bane on 2007-11-29
Total NOOB here. I just installed Ubuntu 7.10 on an old PC that I had lying around. I like the system, but still have tons of old applications/documents/etc. that I am not ready to give up yet, so...

I bought a Trendnet 2-port PS/2 KVM Switch Kit to start both of the Desktops off of using a single mouse, keyboard, and monitor. Oh, the second machine is Windows XP. Well, Windows XP works fine as PC1 but when I switch to the Ubuntu Machine (PC2) it boots but no mouse or keyboard (Monitor is fine). I tried reboots, changed PCs to Ubuntu PC1 and Windows XP PC2 and it still no worky. Can someone please help. Changing out plugs all the time is not an option.

Thanks in advance!

Best,
The Bane

PS - did a search and nothing there really helped.

---

### Post by The Bane on 2007-11-29
Since I saw it in another thread...

Yes, I have keyboard and mouse 'lights' and the number lock key does lock and unlock, according to the light, but still no mouse or keyboard.

:(

The Bane

---

### Post by The Bane on 2007-11-30
OMG, found my post on PAGE 11 after **only** 13hrs on the forum. If there is this much activity trying to get help, I am wondering if Ubuntu is the direction I want to go. :(

Best,
The Bane

---

### Post by louieb on 2007-11-30
Does the mouse and keyboard work without using the KVM?

When you boot is the KVM set to the Ubuntu PC?

I sometimes have trouble with my KVM when I shutdown a machine and let the switch automatically go to the next machine. But other that that it just works.

---

### Post by The Bane on 2007-11-30
> **louieb said:**
> Does the mouse and keyboard work without using the KVM?

When you boot is the KVM set to the Ubuntu PC?

I sometimes have trouble with my KVM when I shutdown a machine and let the switch automatically go to the next machine. But other that that it just works.

Thanks for replying!!!

Yes the mouse and keyboard work when plugged directly into the Ubuntu system, but do not through the KVM switch. 

I have had the KVM switch set for both the Ubuntu, and my WIndows, systems as the primary (PC1). On both occasions, only the Windows box worked with the mouse and keyboard. I have booted several ways; set the switch manually to PC1, boot it fully, then manually go to PC2 and boot it. Nothing. I have switched the order, as mentioned above, and made the Ubuntu PC PC1, but to no avail. I even tried both ways with a simultanious boot, and no go.

Could it be a driver issue? I would think not since they both work plugged directly into the PC with Ubuntu on it. This is eating me alive. Please help.

Thanks again,

Best,
The Bane

---

### Post by louieb on 2007-11-30
I'm at a loss as to why the keyboard and mouse  doesn't work with the one PC. Not when you can plug the other PC in either side and they work.  

No help here but at least I'll give it a bump.

---

### Post by The Bane on 2007-11-30
New information that I will hope will help someone, anyone, to figure this out...

For shoots and grins, I downloaded a live CD of another release of Linux and fired the second non responsive PC up. Well, the keyboard and mouse worked through the CD load until it got to ask me what type of mouse I was using and it became unresponsive somewhere along the kernel load. 

Thoughts?

The Bane

---

### Post by hummingbird on 2007-12-03
> **The Bane said:**
> New information that I will hope will help someone, anyone, to figure this out...

For shoots and grins, I downloaded a live CD of another release of Linux and fired the second non responsive PC up. Well, the keyboard and mouse worked through the CD load until it got to ask me what type of mouse I was using and it became unresponsive somewhere along the kernel load. 

Thoughts?

The Bane

Hiddy...

I don't have a lot of linux experience but I can tell you about a similar KVM problem with XP on a Dell machine.  The problem was that I couldn't get the keyboard or mouse to work which I think is your problem.  I spent about a year using the monitor shared via the KVM and a separate Mouse and Keyboard on the desk, plugged directly into the Dell machine.  I got quite adept at balancing two mice and keyboards.  You said you have gotten them to work when directly plugged in.  Well, my solution was to go into windows and tell it that the mouse and keyboard were not the special Dell ones but PS2  generic ones and then the KVM switch could find them.  I set my Ubuntu up on the same machine but didn't have any problem with that, but if you installed linux on your machine while the mouse and Keyboard were plugged directly into the PC instead of via the KVM, the install program may have detected special mouse/keyboard types that don't work with the KVM.  How do you fix that?  I dunno, you might try Administration/keyboards there is a choose button that you might find helpful.  I don't have any idea about how to change the mouse since the mouse selection under Administration doesn't seem to let one change the mouse type...perhaps a Linux wizard will read this and tell you the solution.

Hope this helps
Hummingbird

---

