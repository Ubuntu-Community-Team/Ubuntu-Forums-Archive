---
title: "Migrating System to New HD"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-07-09
I'm wanting to put a better and larger HD in this Ubuntu box, but was wondering if there is a way to painlessly migrate my current system to the new drive.

Or...would it be better to just start completely over from scratch on the new drive?

As always, thanks for any help.

---

### Post by aysiu on 2005-07-09
[QUOTE=polo_step]I'm wanting to put a better and larger HD in this Ubuntu box, but was wondering if there is a way to painlessly migrate my current system to the new drive.

Or...would it be better to just start completely over from scratch on the new drive?

As always, thanks for any help.[/QUOTE] Hm. The most painless way I can think of doing this is making a copy of your /home directory and pasting it into the new installation on the larger hard drive. Even that can be a little buggy.

This is just me, but when I do new installations, I usually back up just my .thunderbird and .mozilla folders in my home folder. Other settings I reconfigure manually so that I have as clean an install as possible.

---

### Post by polo_step on 2005-07-09
[QUOTE=aysiu]
This is just me, but when I do new installations, I usually back up just my .thunderbird and .mozilla folders in my home folder. Other settings I reconfigure manually so that I have as clean an install as possible.[/QUOTE]
Yeah, I see the point.  

Maybe I can just save the .conf files to diskette.  I can't remember all the stuff I had to tweak just to get it running even as well as it does.

I'm losing Thunderbird as soon as I can find something that works better.  It's too buggy (I found a very funny new one tonight), the obnoxious and unmanageable HTML-style quote bars are not easily done away with and I generally hate it. Evolution Mail does doomsday crashes with the PGP plugin...so I'm trying to find a more stable mail client that services multiple accounts without all these hassles.  I don't need all the feature bloat.

I'm getting kind of discouraged at the instability, bugginess and low functionality of nearly everything I'm trying to use, but that's a different thread. :neutral:

---

### Post by aysiu on 2005-07-09
What are these html-style quote bars you're talking about? Have you tried going to View > Message Body As > Plain Text? I never view messages in HTML. Maybe it's because I first started using email on Pine. Maybe it's because it's easier to see through spam...

---

### Post by polo_step on 2005-07-09
[QUOTE=aysiu]What are these html-style quote bars you're talking about? Have you tried going to View > Message Body As > Plain Text? I never view messages in HTML. [/QUOTE]
Yep.  HTML is disabled in every way it possibly can be and everything is plain text only.

Still, the bars are there in the reply frame and the Mozilla Thunderbird support forum says thay always will be until some obscure file is recoded, and I can't find it in the Linux version.  When the message goes out, they're converted to >s, but there's no way see it that way at my end -- again according to Mozilla support.

In short, they say it's a "feature" that can't normally be turned off, no matter in what mode you are working.  It's not just a matter of annoying appearance, it makes editing and formatting quoted passages virtually impossible.

---

### Post by Kvark on 2005-07-09
I'd make a complete backup of the old drive (not just your files, the whole drive) and then restore the backup to the new one. Not sure which of all the countless backup tools are good for that though.

---

