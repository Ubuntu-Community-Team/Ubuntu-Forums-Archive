---
title: "Installing/booting Ubuntu 7.10"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Seltox on 2008-01-12
Hey all,  I am pretty much a newbie to anything Linux - I just wanted a change from Windows.

Anyway, I also have have no idea how to partition things for Linux.  So I just wanna check if this is vaguely what I should have done.  I made a partition for Linux, then a 4gb partition for swapping or something?  I will still be running Windows primarily, so my other partitions are divided into storage for that.


Anyways.  I am having trouble installing Ubuntu 7.10.  I put the cd in and booted from it.  It all worked fine the first time.  I got to the Ubuntu desktop and everything.  Went to install it, and got to the step where it asked me to choose the partition and such.  It didn't display any partitions, so I got confused.  When I checked, my HDD didn't have the power plugged in :P  Not sure how that happened.

Anyway, I turned my computer off, plugged in the power, and started up again.  I got to the menu where it asks me what I want to do ( Start or install Ubuntu, Start Ubuntu in safe graphics mode, install with driver update CD, etc).  But when I select to Start or Install Ubuntu, it just goes to a screen with a flashing underscore in the top left corner.  I left it here for a long time too, still nothing.

Any help?  I was very very excited about getting Ubuntu running.

---

### Post by ubutufan on 2008-01-12
Hi there and welcome to ubuntu.

Your current situation is most likely a hardware issue. I would suggest/recommend that you shut down the machine and replug all cables to make sure that disks/etc are working properly.
Let us know of the outcome and we can take it from there

---

### Post by Seltox on 2008-01-12
I unplugged my HDD and dvd/cd burner and it's doing the same thing.

I noticed that the dvd's "busy" light isn't on, which it was doing before :/

---

### Post by ubutufan on 2008-01-12
Hardware. Try unplugging ALL cables, PCI's, DIMMs everything.
Reassemble and let us know
It is hardware at least the way you describe it

---

### Post by Seltox on 2008-01-12
Okay, well I done that.  I took out everything (apart from my Processor.  I have way too much trouble getting that thing in and out :P.)  I Connected it all up again and started it up.  Done the same thing though.

Seems the dvd drive works really hard at first and then just...stops...

---

### Post by ubutufan on 2008-01-12
If you have another dvd you may want to try that. If not then either the dvd malfunctions or the ubuntu livecd is damaged

---

### Post by Seltox on 2008-01-12
I can't imagine how the dvd would have been damage when I plugged power into my HDD...  Would it be possible i'm not getting enough power or something?

Only a 400w PSU, Antec Nine Hundred Advanced Gaming Case (3x 120mm fan, 1x 200mm fan), 200GB Samsung HDD, Pentium D 3.4GHz processor, 1gb DDR RAM, Asus dvd-rw, nVidia GeForce FX 5200 128-bit 256mb Video card, Modem-ey thingo, USB/FireWire PCI card and a Really bad Gigabyte Motherboard...

Oh, and I burnt two copies of the ISO.  One for a friend.  I've tried both copies and both do the same thing.

---

### Post by ubutufan on 2008-01-12
> **Seltox said:**
> I can't imagine how the dvd would have been damage when I plugged power into my HDD...  Would it be possible i'm not getting enough power or something?

Only a 400w PSU, Antec Nine Hundred Advanced Gaming Case (3x 120mm fan, 1x 200mm fan), 200GB Samsung HDD, Pentium D 3.4GHz processor, 1gb DDR RAM, Asus dvd-rw, nVidia GeForce FX 5200 128-bit 256mb Video card, Modem-ey thingo, USB/FireWire PCI card and a Really bad Gigabyte Motherboard...

Oh, and I burnt two copies of the ISO.  One for a friend.  I've tried both copies and both do the same thing.

I can't really see something wrong in the configuration. Ok yes the PSU is small but that is not the problem. I would try removing one after the other (trial and error) the modem and then the firewire

Just to make sure before you start this procedure. Did you unplug-plug the nVidia? do it to be on the safe side

---

### Post by Seltox on 2008-01-12
Yeah, I took out everything :P  Except for the PSU and the power switch/reset switch things.

I dunno what the modem is even doing in there.  It's just always been in my computer :P  I'll go try the trial and error thing.  It's 3am and i'm at a friends house... this is sucky :P

---

### Post by Seltox on 2008-01-12
Well, I took out the modem,  nothing.  USB/FireWIre, nothing.  HDD, nothing.  Took out the video card and used my motherboard onboard video and tried.  Got a slightly different reaction here.  Instead of the flashing underscore, it looks like it's gonna do something, then the monitor gives that half light-ish thing it gives rather than black when it's gonna display something.  But it just sits there.  With nothing.

---

### Post by ubutufan on 2008-01-12
Sorry mate, just a friendly advice.
3 am in the morning you said. Go to bed.
Where I come from the expression is "we laugh in the morning looking at what we did at night"
In the morning you can start again. If I am not around other people will.
Everybody here is willing to help.

---

### Post by dstew on 2008-01-12
It seems that the LiveCD is having trouble running your display. This is a common problem, and it doesn't necessarily mean there is anything wrong with your hardware.

You get the initial menu, correct? Then, when you choose "Start or Install Ubuntu" you get a blank screen, or screen garbage, right? This is because the LiveCD at this point starts using different software to work your display. Why it worked when your HDD was unplugged is hard to say.

You have two options at this point. One, you can try to modify the kernel boot parameters, by pressing F6 at the initial screen, and adding them to the kernel line before starting the LiveCD linux system. The other, and maybe better option, is to install Ubuntu using the Alternate Install CD. It installs the same Ubuntu system using a text-based installer that is easier on your system. You get it on the same Ubuntu Download page, just check the box below the Start Download button. Once Ubuntu is installed, you can deal with any graphics issues then.

---

### Post by Seltox on 2008-01-12
Oh, if it matters... I think I hit f6 accidentally at one point and might have changed something.  Oh I dunno.

What is it _meant_ to say there?

---

### Post by dstew on 2008-01-12
The changes you make with F6 are not permanent. They are only effective for one boot. Changing boot parameters is mostly guessing. If you want to try boot parameters, remove the word **quiet** from the kernel line, and change **splash** to **nosplash**. At least you should be able to see the kernel messages as the LiveCD tries to boot, and maybe you can figure out where it is having problems.

My recommendation is to try the Alternate Install CD.

---

### Post by Seltox on 2008-01-12
Okay, this is strange.   I went to bed, and when I got up, i changed that 'f6' stuff.  I thought I found the problem when in the startup it gave an error, something about I/O.  But as I was starting up this computer to post about it, Ubuntu actually started up.  Took less thatn a few minutes, when I had left it for about an hour at one point last night.

---

### Post by Seltox on 2008-01-12
Okay, I have a further problem.  I successfully installed Ubuntu (at least it seems I did?) and when it was finished told me I had to restart and such.

But now when it goes to boot up, I get to a screen where it says "Starting up ..." and then has a flashing underscore under it.  :(

---

### Post by dstew on 2008-01-13
Did you see the grub menu and pick a particular item to start? Did the menu appear at all?

---

