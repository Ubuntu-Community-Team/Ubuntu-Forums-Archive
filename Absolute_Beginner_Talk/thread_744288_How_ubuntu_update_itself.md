---
title: "How ubuntu update itself ?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by alcedo on 2008-04-03
Hi everyone, i would love to try ubuntu 8.04, hardy heron though i have some concerns.

1. Since hardy heron is still in development stage at this in time, should i wait for the official release, or simply download the development stage one ? 

my main concern is that if i apply updates to the this beta version after the official release, it probably isnt as good as a fresh install of the official release ? 

as in im not sure how linux updating works. Cause for windows updates, it simplys makes windows much laggier =/ 

2. or should i install ubuntu 7.10 and wait for official release of 8.04 than update to 8.04 ?

3. How easy isit to update ubuntu ? by simply clicking yes to the update prompts (at the top right corner of the screen) would always ensure that i would get the latest release?

Thanks in advance, cheers !

-Victor.

Edited: Explanation by fellow forumers, some are summarised by my own understanding->

[LIST=1]
[*]Official release are often the best if you can wait

[*]Security patches are different from software updates. Security patches does minimal changes to your system, just to make it more secure only.

[*]creating a separate folder for /home for easier clean installs later on is important !

[*]If you want the latest and greatest during a support cycle (ie. after a ubuntu version is released) then you will need to enable the backports repository, and/or install any new software you want manually using .deb files, .bin files or if nessesary by compiling the software yourself.

[*]Updates on Ubuntu replace the files that are updated, and do not keep "uninstall" files around. So you end up, after updates, with the same system you would've had you just installed the packages directly in the first place. Fragmentation is also less of an issue on ubuntu so even there you'll not be much worse (if at all) off if you install and update vs. making a clean installation.
[/LIST]

---

### Post by Tatty on 2008-04-03
1. Yes you are right, wait for the official release.

But dont worry about updates, only security patches are released during a support cycle for Ubuntu, so only the minumum is changed to keep your system secure.

2. This is probably your best option.  It is how most people will probably get Hardy.  It is not quite as ideal as doing a clean install of hardy when it comes out, but its rare there are actual problems.  Make sure you backup anything important first though - theres always that possibility of problems.

3.  Those updates only give you security patches, not software updates.  The only exception is when a new version of ubuntu is released, in which case it will notify you that there is a new version and give you an option of updating.

If you want the latest and greatest during a support cycle (ie. after a ubuntu version is released) then you will need to enable the backports repository, and/or install any new software you want manually using .deb files, .bin files or if nessesary by compiling the software yourself.

---

### Post by forestpixie on 2008-04-03
1/2 - if you have beta and apply updates when it is released officially you will have the same system. If you're at all unsure about fixing it if you have problems with updates - don't do it and either install gutsy or wait for the release.

3 - updating should be as simple as clicking a button, but it might be better to do a clean install - you'll get both sides of that argument from different people.

---

### Post by ByteJuggler on 2008-04-03
To add to what forestpixie has said: Updates on Ubuntu replace the files that are updated, and do not keep "uninstall" files around.  So you end up, after updates, with the same system you would've had you just installed the packages directly in the first place.  Fragmentation is also less of an issue on ubuntu so even there you'll not be much worse (if at all) off if you install and update vs. making a clean installation.  Personally, I'd install Hardy, test it, and stick to it if it works well enough and then update it when the final release comes out.  If it doesn't work well enough on test I'd probably wait and install Gutsy instead until then, and then try upgrading.  Most important however would be to ensure my data (/home) is on a seperate partition - this makes reinstallation scenarios *so* much less hassle, should you ever, for whatever reason, feel the urge to do a clean installation.

---

### Post by erginemr on 2008-04-03
+1 to everyone posted before and +1 to creating a separate folder for /home for easier clean installs later on. 

As a suggestion on partition sizes:

Manual install in Ubuntu Live CD (Crucial if you want to dual-boot with Windows)
Root system [ / ]-> 10-12 GB 
Swap [swap] -> 1 GB if you have 1 GB RAM or more, 2 GB if you have less
Home  [/home] -> The rest (some 15-20 GB or more)

---

### Post by alcedo on 2008-04-03
Thanks to everyone for the clear explanation !

I think i would just bite my lips and wait for the official release of 8.04, since i don't really mind the wait(not that long of a wait anyway =X lol)

I have updated / edited my very first post on what ive learnt to make it easier for ppl to learn as well if they stumbled onto this post :D

---

### Post by Tatty on 2008-04-03
> **alcedo said:**
> Thanks to everyone for the clear explanation !

I think i would just bite my lips and wait for the official release of 8.04, since i don't really mind the wait(not that long of a wait anyway =X lol)

I have updated / edited my very first post on what ive learnt to make it easier for ppl to learn as well if they stumbled onto this post :D

Theres nothing wrong with grabbing a 7.10 disc now and giving it a go...  That way you will have some practice getting ubuntu up and running before your 8.04 install.

Remember, you can install/uninstall/break Ubuntu as many times as you like :popcorn:

---

### Post by alcedo on 2008-04-03
> **Tatty said:**
> Theres nothing wrong with grabbing a 7.10 disc now and giving it a go...  That way you will have some practice getting ubuntu up and running before your 8.04 install.

Remember, you can install/uninstall/break Ubuntu as many times as you like :popcorn:


Ar yes, but 7.10 doesn't have wubi :-( 

I am mostly installing and running linux on "virtual box" something like vm-ware.  

With wubi,  i think the performance would be much much greater ! hence the yearn for hardy hero :P

---

