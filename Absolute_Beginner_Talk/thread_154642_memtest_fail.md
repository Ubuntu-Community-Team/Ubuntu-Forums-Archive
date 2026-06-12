---
title: "memtest fail"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by mrose2n on 2006-04-03
Hello all.  I recently installed Breezy and my system has been freezing up regularly.  I just ran a memtest and it seems to have failed.  Here's what it tells me as of right now (it's still making passes):

Tst: 3 Pass: 0 Failing Address: 00000100020 - 1.0MB Good: 80808080 Bad: 80808000 Err-Bits: 00000080 Count: 88 Chan:

So, I don't have a real strong grasp on what this means.  I assume it means I have a bad DDR chip.  How accurate is this test?  Should I just go out and get a new chip?

Thanks

Matt

---

### Post by az on 2006-04-03
[QUOTE=mrose2n]Hello all.  I recently installed Breezy and my system has been freezing up regularly.  I just ran a memtest and it seems to have failed.  Here's what it tells me as of right now (it's still making passes):

Tst: 3 Pass: 0 Failing Address: 00000100020 - 1.0MB Good: 80808080 Bad: 80808000 Err-Bits: 00000080 Count: 88 Chan:

So, I don't have a real strong grasp on what this means.  I assume it means I have a bad DDR chip.  How accurate is this test?  Should I just go out and get a new chip?

Thanks

Matt[/QUOTE]

You can use the badram kernel patch to avoid using the bad spots in memory, if you like.  You would have to use a kernel with the bad ram patch
[http://ubuntuforums.org/showthread.php?t=102254](http://ubuntuforums.org/showthread.php?t=102254)

---

### Post by dvarsam on 2006-04-03
Sorry to ask, but here seems the right place to ask:

How can I perform a Test on my PC's memory?

...to see it is ok or has any problems (I do not know of)?

How did you do it?

Thanks.

P.S.> You seem to know how to do it & that is why I am asking here...

---

### Post by Panhead Bill on 2006-04-03
[QUOTE=dvarsam]How can I perform a Test on my PC's memory?[/QUOTE]

dvarsam:  Start your PC with the CD.  Instead of hitting enter, (to start the install), type:  memtest  (then hit enter).  The test will start, and run several minutes per pass with 128 K installed, longer with additional memory.  It is best if you let it run overnight so you get severl passes, and the PC and memory are fully warmed up.

[QUOTE=mrose2n]I just ran a memtest and it seems to have failed.
Matt[/QUOTE]

That does look like a failed module to me.  if you have more than one stick installed, test them individually to find the bad one.

How much memory do you have left?  Others here can tell you if you need more memory to run Ubuntu, I'm still learning basics myself - but my pc is running so far with 320Meg of ram.

---

### Post by mrose2n on 2006-04-03
Thanks for getting back to me.  I ended up taking the "easy way out" and bringing my computer, still under warranty, in for service, expecting just to get a RAM stick replaced.  We tried several sticks and all failed.  So it must have been a problem with the mainboard.  Anyway, new computer, all is well.  :)

---

### Post by mrose2n on 2006-04-03
Whoa... all is not well...  I just ran memtest again on my new machine and it's giving me the same error.  The same address and everything.  Keep in mind this is a totally new tower.  The only hardware in the tower that is the same is the wireless network card.  Outside the tower, the monitor, keyboard and mouse are the same, but that shouldn't matter.  This is very strange.  Any ideas?

I'm assuming that perhaps the architecture of this particular setup causes errors in the memtest, which I wouldn't be too concerned about, but my Ubuntu partition keeps freezing up.  Might this be a model that doesn't support Xorg?  Any ideas what I should check?

[QUOTE=mrose2n]Thanks for getting back to me.  I ended up taking the "easy way out" and bringing my computer, still under warranty, in for service, expecting just to get a RAM stick replaced.  We tried several sticks and all failed.  So it must have been a problem with the mainboard.  Anyway, new computer, all is well.  :)[/QUOTE]

---

### Post by jason.b.c on 2006-04-03
[QUOTE=mrose2n]Whoa... all is not well...  I just ran memtest again on my new machine and it's giving me the same error.  The same address and everything.  Keep in mind this is a totally new tower.  The only hardware in the tower that is the same is the wireless network card.  Outside the tower, the monitor, keyboard and mouse are the same, but that shouldn't matter.  This is very strange.  Any ideas?[/QUOTE]


Then there has to be something on the motherboard not set right, like ( dip switches, Jumpers, etc ):)    Or in your **B.I.O.S.** ;) !

---

### Post by mrose2n on 2006-04-03
So that would mean it's set incorrectly for every tower of this model they ship?  Any idea how to go about figuring out what is wrong?  I know that's kind of a vague question, I'm new to this.  Any logs/diagnostics I could check?

[QUOTE=jason.b.c]Then there has to be something on the motherboard not set right, like ( dip switches, Jumpers, etc ):)    Or in your **B.I.O.S.** ;) ![/QUOTE]

---

### Post by jason.b.c on 2006-04-03
[QUOTE=mrose2n]So that would mean it's set incorrectly for every tower of this model they ship?  Any idea how to go about figuring out what is wrong?  I know that's kind of a vague question, I'm new to this.  Any logs/diagnostics I could check?[/QUOTE]

> So that would mean it's set incorrectly for every tower of this model they ship?

uumm, ok is this like the second or third tower that you've tried or something??:confused: 

If not,like i said it might be something just set wrong, because computers today are so mass produced it would be easy to get one that isn't set up right..!
Remember just because **you ** bought it brand new in a store dosen't mean it's of good quality, like most new cars today.!!!:( 

> Any idea how to go about figuring out what is wrong? 

And you've taken it back to where you bought it?, What do they tell you??:confused:

---

### Post by mrose2n on 2006-04-04
[QUOTE=jason.b.c]uumm, ok is this like the second or third tower that you've tried or something??:confused: 

If not,like i said it might be something just set wrong, because computers today are so mass produced it would be easy to get one that isn't set up right..!
Remember just because **you ** bought it brand new in a store dosen't mean it's of good quality, like most new cars today.!!!:( 



And you've taken it back to where you bought it?, What do they tell you??:confused:[/QUOTE]

Yeah, it's the second one.  Both had the same issue.  If I use the 386 kernel, things seem to go smoothly.  If I try to take advantage of the dual core, using the 686, it freezes up.  memtest alwasy returns errors.  I took the first one back to where I bought it.  They said it must be an issue with the motherboard and replaced it.  The replacement has exactly the same issues.

---

### Post by jason.b.c on 2006-04-04
[QUOTE=mrose2n]Yeah, it's the second one.  Both had the same issue.  If I use the 386 kernel, things seem to go smoothly.  If I try to take advantage of the dual core, using the 686, it freezes up.  memtest alwasy returns errors.  I took the first one back to where I bought it.  They said it must be an issue with the motherboard and replaced it.  The replacement has exactly the same issues.[/QUOTE]


What brand name is it???:confused:      How much did it cost??:confused:

---

### Post by mrose2n on 2006-04-04
[QUOTE=jason.b.c]What brand name is it???:confused:      How much did it cost??:confused:[/QUOTE]

Haha. It's a Gateway and I thought it was a good deal, but apparently not.

---

### Post by Bartender on 2006-04-04
mrose -
There was just a post this morning where one of the replies mentioned that memtest isn't perfect - with some hardware it'll show errors when the RAM may not be at fault.
This may be a stupid idea, because memtest runs before the OS loads so it shouldn't make any dif how you run it, but I wonder what would happen if you downloaded memtest from a Windows machine, made the bootable floppy, and ran memtest from the floppy?  
One way to pin this down would be to get your hands on another PC with the same type of memory slots and test each RAM stick individually from the bootable memtest floppy.  It doesn't sound to me like you've got bad RAM.  I mean, how could both Gateways come up with the exact same memory error?

---

### Post by mrose2n on 2006-04-04
[QUOTE=Bartender]mrose -
There was just a post this morning where one of the replies mentioned that memtest isn't perfect - with some hardware it'll show errors when the RAM may not be at fault.
This may be a stupid idea, because memtest runs before the OS loads so it shouldn't make any dif how you run it, but I wonder what would happen if you downloaded memtest from a Windows machine, made the bootable floppy, and ran memtest from the floppy?  
One way to pin this down would be to get your hands on another PC with the same type of memory slots and test each RAM stick individually from the bootable memtest floppy.  It doesn't sound to me like you've got bad RAM.  I mean, how could both Gateways come up with the exact same memory error?[/QUOTE]

Thanks for the input.  I'm starting to think that maybe memtest isn't compatible with this system's hardware architecture.  The 386 kernel runs flawlessly (at least for the day I've had it), even if the 686 kernel freezes.  Makes me think it's an issue with the drivers rather than the hardware.  I'll try to check this RAM in another machine and other RAM in this machine when I get the chance.

---

### Post by trent dillman on 2006-04-04
Also, take it to your distributor and have them check for a faulty PSU?

Just throwing it out there...

---

### Post by jason.b.c on 2006-04-04
[QUOTE=Bartender]mrose -
There was just a post this morning where one of the replies mentioned that memtest isn't perfect - with some hardware it'll show errors when the RAM may not be at fault.
This may be a stupid idea, because memtest runs before the OS loads so it shouldn't make any dif how you run it, but I wonder what would happen if you downloaded memtest from a Windows machine, made the bootable floppy, and ran memtest from the floppy?  
One way to pin this down would be to get your hands on another PC with the same type of memory slots and test each RAM stick individually from the bootable memtest floppy.  It doesn't sound to me like you've got bad RAM.  I mean, how could both Gateways come up with the exact same memory error?[/QUOTE]


>  but I wonder what would happen if you downloaded memtest from a Windows machine, made the bootable floppy, and ran memtest from the floppy?  

You know thats funny that you mention that:o , i did the very same thing last night, i download the windows version of memtest, made my disk and restarted my computer to run it. After screwing it up three times and having to remake the disk:(   I ran memtest and it showed no errors, although it takes freakin' forever to finish once it has started.;)   Running it that way ( from floppy ) might show differant results.

---

### Post by mrose2n on 2006-04-04
[QUOTE=jason.b.c]You know thats funny that you mention that:o , i did the very same thing last night, i download the windows version of memtest, made my disk and restarted my computer to run it. After screwing it up three times and having to remake the disk:(   I ran memtest and it showed no errors, although it takes freakin' forever to finish once it has started.;)   Running it that way ( from floppy ) might show differant results.[/QUOTE]

Ok, I downloaded the memtext x86 ISO from a Windows machine, burned it to disc, and booted from the disc.  It showed the exact same error.  I emailed Gateway's customer support and they recommended a memtest exe file from Softpedia.  I downloaded the file and am running it on the Windows partition of my "broken" machine.  It tests "all unused RAM".  It's running right now on my Windows desktop, has made a couple passes w/o any error.  So this either means it is better or worse suited to diagnose my computer's architecture.  Haha.  Who do I trust?

UPDATE:  Gateway also suggested this option: [http://www.softpedia.com/get/Tweak/Memory-Tweak/Microsoft-Windows-Memory-Diagnostic.shtml](http://www.softpedia.com/get/Tweak/Memory-Tweak/Microsoft-Windows-Memory-Diagnostic.shtml)
It can be burned to a bootable disc and the interface looks surprisingly similar to memtest x86.  It seems to have similar functionality as well.  I have run it for several passes w/o any errors detected, whereas memtest detects the first error in my system almost immediately and the error count goes up by about 100 errors per pass.  It seems unreasonable that these other diagnostic tools would completely miss an error so flagrant, so I think I can assume that memtest is not appropriate for my system.  Any thoughts?

---

### Post by mcduck on 2006-04-04
You should always run memtest for hours, not just once. It might take even long time until first error, but after that you'll get lots more. I usally leave it to run over night.

Also, keep in mind that memory error doesn't always mean that the stick is the fault, it could also be your motherboard, or simply that the motherboard doesn't like that particular memory. For example nForce2-based motherboards are/were very delicate about what memories they work with.

And how reliable it is? Enough that I have taken a mem stick back to shop, only telling that it gave errors in memtest after 8 hours and they replaced the stick with no further questions. (I had other stick of the very same RAM that worked fine, so it was clear that this was not because of my chipset).

---

### Post by dvarsam on 2006-04-04
Is everything else running OK on your PC?

Example:
1. Ubuntu OS,
2. Applications,
3. etc. etc.

How do you know they replaced your Mobo & did not give you the SAME one?

Were you there (to see it with your own eyes)?

Or did they tell you, come tomorrow & we will give you another Mobo?

Do you trust the guys?

Is the Serial# of the new Mobo they gave you different from the one you gave to them (as defective)?

Good Luck!

P.S.1> Some times you never know if the Computer Shop guys are trustworthy or not - it also depends on which country you are having the problem...
If you are in Greece or Argentina,... , you never know...
If you are in the U.S. or Germany, things are more serious there... & I would trust the guys more...

P.S.2> If I were you & my Motherboard was brand new, why would I risk it?
I would replace with a different brand Mobo...
Let's say the chance is 1/1.000.000 that your Mobo is defective...
There will always be a "maybe" in your mind, although you would NOT be able to prove it...
And whenever you are having trouble, crashes, or anything you would think:

1. A virus?
2. That faulty Mobo I bought?
3. The Memory?
4. etc. etc...

And you won't sleep well at night, will you?

---

### Post by mrose2n on 2006-04-04
I was there when they replaced my tower.  Basically, they just gave me a whole new tower and my old tower was sitting right in front of me, so I'm not concerned about having been given the same board.  And I trust these guys, at least to be honest, not necessarily to know what they're doing :)

Everything runs ok when I'm in the 386 kernel.  If I try to use the 686-smp kernel, everything else being equal, it freezes with the first few hours.  That is, the keyboard locks, the mouse still moves, but I can't click on anything.  If I have the system monitor open at the time, CPU1 is at 0% CPU2 goes back and forth from 100% to 0%.  No processes show up as taking up any memory except the system monitor, which takes about 1%.  When I hard-reboot, I have to reconfigure Xorg, it loses settings and won't let me increase my resolution past 640x480.  But the 386 kernel runs fine, or at least has for the past couple days I've had it.  So I'm kind of at a loss.  Hope it's not the board.

[QUOTE=dvarsam]Is everything else running OK on your PC?

Example:
1. Ubuntu OS,
2. Applications,
3. etc. etc.

How do you know they replaced your Mobo & did not give you the SAME one?

Were you there (to see it with your own eyes)?

Or did they tell you, come tomorrow & we will give you another Mobo?

Do you trust the guys?

Is the Serial# of the new Mobo they gave you different from the one you gave to them (as defective)?

Good Luck!

P.S.1> Some times you never know if the Computer Shop guys are trustworthy or not - it also depends on which country you are having the problem...
If you are in Greece or Argentina,... , you never know...
If you are in the U.S. or Germany, things are more serious there... & I would trust the guys more...

P.S.2> If I were you & my Motherboard was brand new, why would I risk it?
I would replace with a different brand Mobo...
Let's say the chance is 1/1.000.000 that your Mobo is defective...
There will always be a "maybe" in your mind, although you would NOT be able to prove it...
And whenever you are having trouble, crashes, or anything you would think:

1. A virus?
2. That faulty Mobo I bought?
3. The Memory?
4. etc. etc...

And you won't sleep well at night, will you?[/QUOTE]

---

### Post by jason.b.c on 2006-04-04
> Hope it's not the board.

I find that very interesting that you were able to get **Ubuntu** to work on _your_ Gateway computer to begin with:confused: , I tried and tried to get Ubuntu to go on my buddies computer, ( Same brand name ) and it was a no go.!!:( 

I really wanted to show him how cool ubuntu is.!!:D

---

