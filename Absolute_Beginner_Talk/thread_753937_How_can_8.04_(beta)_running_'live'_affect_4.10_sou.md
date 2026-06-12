---
title: "How can 8.04 (beta) running 'live' affect 4.10 sound?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by staib on 2008-04-13
Hmmm?   Not sure why this happened but would appreciate any pointers.  Have been running 7.10 happily on a laptop (Lenovo 3000 N200) - and had accepted that on this laptop advanced desktop effects will not run, until I read that they **do** run with the new 8.04 (on this laptop).  

So I grabbed me an ISO of the beta this morning, ran it as a live CD, and indeed could see that desktop effects were enabled by default.  I also tried the Hibernate function - that worked too - doubly cool!

Then I exited, removed the CD and booted back into 7.10 and found that I have now lost all sound...
Can that really happen - I always thought the live CD didn't touch the existing OS.  In 8.04 there is now sound by default, but back in 7.10 it has gone!

Once 8.04 goes stable I will re-install, but meanwhile would appreciate any help getting the sound working again.

Nick

---

### Post by staib on 2008-04-13
For what it's worth I have added the line:
[B]
options snd-hda-intel single_cmd=1 model=lenovo[/B]

But still no sound :(

---

### Post by RTrev on 2008-04-13
> **staib said:**
> Hmmm?   Not sure why this happened but would appreciate any pointers.  Have been running 7.10 happily on a laptop (Lenovo 3000 N200) - and had accepted that on this laptop advanced desktop effects will not run, until I read that they **do** run with the new 8.04 (on this laptop).  

So I grabbed me an ISO of the beta this morning, ran it as a live CD, and indeed could see that desktop effects were enabled by default.  I also tried the Hibernate function - that worked too - doubly cool!

Then I exited, removed the CD and booted back into 7.10 and found that I have now lost all sound...
Can that really happen - I always thought the live CD didn't touch the existing OS.  In 8.04 there is now sound by default, but back in 7.10 it has gone!

Once 8.04 goes stable I will re-install, but meanwhile would appreciate any help getting the sound working again.

Nick

I would have said absolutely no way running the live CD would trash anything in an existing install, but I've never tried hibernating.  That has to write something to the disk, no?  So on the next boot, perhaps that "something" gets read in?  Suggest you shutdown and restart again, and if you're comfortable with GRUB try adding "noresume" to the end of the boot line (without the quotes of course.)

HTH,
Bob

---

### Post by wolfen69 on 2008-04-13
a live cd in no way touches the hard drive. it only runs off the cd and into memory.  your problem is unrelated to hardy live cd.

---

### Post by staib on 2008-04-13
Thanks Guys for the comments - that's certainly what I had assumed - but I did **nothing** else to the laptop that could explain losing the sound. 

The last time I tried to enable desktop effects on 7.10 I lost sound.  At that time it was dual-booting with Vista.  Since then I had formatted the H/D and reinstalled 7.10 - and had sound - and no problems for months... 

Now, within 5 minutes after trying desktop effects, with a live CD of 8.04, I discover that sound has again been lost.  Coincidence? Maybe... but you will understand my 'suspicions'...

Any suggestions?!

Sorry - can someone remind me how to edit Grub?!

---

### Post by RTrev on 2008-04-13
> **staib said:**
> Thanks Guys for the comments - that's certainly what I had assumed - but I did **nothing** else to the laptop that could explain losing the sound. 

The last time I tried to enable desktop effects on 7.10 I lost sound.  At that time it was dual-booting with Vista.  Since then I had formatted the H/D and reinstalled 7.10 - and had sound - and no problems for months... 

Now, within 5 minutes after trying desktop effects, with a live CD of 8.04, I discover that sound has again been lost.  Coincidence? Maybe... but you will understand my 'suspicions'...

Any suggestions?!

Sorry - can someone remind me how to edit Grub?!

When you see the message to hit Escape, do so.  Edit a line by positioning on it and hitting the E key.  When done, hit Enter.  Then you can immediately boot by simply hitting the B key.  (Aside, it's a good idea to do this at least once after install, and after major system changes, and add the word profile to the end of the line.  This will speed up subsequent boots for most people.)

As to your sound, I'm baffled.  You mentioned that you hibernated.  Doesn't hibernation *have* to write the information somewhere so that it survives a boot?  Or am I thinking of suspend?  Anyway, let's generate some hypotheses.. and hopefully others will join in.

If you hibernated, where did the data get written?  

If you used capabilities of the hardware that you normally don't use, could something have over-heated as a result?  Why changing video would have any affect on sound I can imagine, unless perhaps they're both on-board and sharing chips.

Is it possible that you mounted the real hard drive from the CD?  If that were the case, then you would be able to write to it.  I can think of how you could have done this without knowing it, though.

Sorry, I'm out of ideas.. but hopefully someone will jump in.

Bob

---

### Post by staib on 2008-04-13
> **RTrev said:**
> 
If you hibernated, where did the data get written?  

If you used capabilities of the hardware that you normally don't use, could something have over-heated as a result?  Why changing video would have any affect on sound I can imagine, unless perhaps they're both on-board and sharing chips.

Is it possible that you mounted the real hard drive from the CD?  If that were the case, then you would be able to write to it.  I can think of how you could have done this without knowing it, though.

Thanks Bob - I appreciate your interest - and your hypotheses :-)

I just tried the Grub start thing, but no change there.

I can quickly confirm that nothing over-heated - I  just ran the live CD for a few minutes to check what I had read elsewhere that the on-board Intel graphics chip was no longer 'black-listed' on this laptop and that desktop effects would run - which they did...  I tested a couple of the 'Example' media files and all was good soundwise.

I tried one Hibernate - all switched off - then a space bar prod brought the desktop back to life.  Then I exited, removed the live CD as prompted, and re-booted into a strangely silent 7.10 ...

Anyone?!

---

### Post by RTrev on 2008-04-13
Browsing around, I see at least one other person saying that suddenly their audio simply ceased to work.  I wonder.. could you have been bitten by the same bug and it was just coincidence that it bit right after you tried the live CD?  Perhaps that was the first time you'd rebooted after the last batch of updates or some such thing?  

Anyway, I'm now suspecting that your live CD experiments might have nothing at all to do with the loss of sound.

Bob

---

### Post by staib on 2008-04-13
In a way I am pleased!    Otherwise the whole 'live CD' thing would be a little suspect!

I have just decided to go ahead and install 8.04 - albeit still the beta version - so that we can all have the sound working again...

Luckily my 'back-up' Asus Eee comes to the rescue at times like these :)

Cheers.

---

