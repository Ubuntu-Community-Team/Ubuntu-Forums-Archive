---
title: "Ubuntu doesn't want to install"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by chatterbabies on 2007-01-06
I have a Dell Latitude LS Series. Pentium III/398 Mhz/256 MB RAM. I am getting this from the identical twin and don't know what some of it is but in the twin on Windows XP Device Manager it says the Computer is a ACPI. Display is NeoMagic MagicGraph256AV. IDE Intel 82371AB/EB.  Network Adapter 3Com 3C920. I don't know how much of that will help but...
I downloaded 6.10 Edgy and burned to CD. I did the number compare file thing to make sure it matched first and burned it at the slowest speed possible 1x. I ran the disc live and loved what I saw so I tried to install it. Bad thing. I had to move the bottom task bar because the install window was hiding under it, but when I set the time and date it freezes every time. I can't click back, I can't tab, I can't cancel, esc . I tried everything. Had to kill it by holding down the power (OUCH). So I had it check the cd the next time and even checked my memory. Tried to run in safe graphics.  I always freeze at the same screen. 
Next I tried doing the same with 6.06.1 can't even get that far. Won't load the desktop. It gets to the loading hardware and freezes. I waited 20 minutes the second time I tried thinking it was my own lack of patience. Please help I really want Ubuntu and to be a part of this awesome community. I can already tell from going through the post you all are great!

---

### Post by rosieg on 2007-01-06
When I tried to install Dapper on my laptop I had a similar problem - I think it was because I only had 256MB RAM (same as you) which wasn't enough despite what they say.

I think I may have used the live CD to create a 500MB SWAP partition which solved the problem.

This may or may not help - but 256ram is a little low.

---

### Post by chatterbabies on 2007-01-06
Now that was fast. Thanks, although I wouldn't have the foggiest what that means. Guess I gotta read some more. :D 
I know it's a tiny computer. Has only 10 gig HD ;) . It is just the only available computer i have to put Ubuntu on that i won't get killed for messing up. The others are my husband's and business computers. 

I'm gonna try one more time just to watch for error messages or anything that might be one and let ya'll know.

---

### Post by jvc26 on 2007-01-06
Use Xubuntu rather than Ubuntu - download Xubuntu 6.10. I say this because you have fairly low specs, and your HDD is very small. You should be able to run Ubuntu with 256MB, but, Xubuntu will run faster as it uses what is called the Xfce desktop environment, which was designed for lower end computers and uses less resources - that may well solve the problem
Il

---

### Post by kebes on 2007-01-06
Your hardware is modest, so I would try to do a more minimal install. Try installing off of the Alternate CD for Ubuntu 6.06 (Edgy), and only install the things you really need.

There is also an Ubuntu variant called Xubuntu that uses the xfce window manager instead of Gnome. Xfce is ver 'lightweight' and specifically optimized for modest hardware. You could try installing that one instead and see if that solves your problems.

If none of that works (still getting random freezes and such), then there's probably some sort of hardware conflict. You seem to be getting freezes during boot... Before actually hitting enter for "install" you can push a button (I think it's F6 or F8 or something) to access "other options" and enter kernel boot flags. You can add things like "noapic" or whatever, which sometimes can be used as work-arounds for hardware.

For instance, this (somewhat old) thread discusses a problem very similar to what you're seeing:
[http://www.mepis.org/node/3770#comment-17524](http://www.mepis.org/node/3770#comment-17524)

The suggestion is to add this kernel boot option:
acpi=off'


Also take a look at this post:
[http://www.linuxextremist.com/?p=33](http://www.linuxextremist.com/?p=33)

Where the guy says installation of Xubuntu was difficult, and even after installing the whole thing was very unstable.


Sorry to say that this particular laptop is not a great candidate for Linux installation...

---

### Post by jvc26 on 2007-01-06
If it was running XP (as the post suggests??) then it should be able to run Xubuntu to be fair. I'd definitely recommend giving it a shot! :)
Il

---

### Post by chatterbabies on 2007-01-06
live desktop loads fine. All messages had OK out by them. I set the city but not the time (since it seemed like it was sticking on that button) and didn't move that bottom task bar even though just a tiny bit of the buttons were showing.  I GOT to the next menu YEAH! It's installing now. That's just weird. Hope it isn't hard to change the time later.

---

### Post by chatterbabies on 2007-01-06
> **kebes said:**
> Your hardware is modest, so I would try to do a more minimal install. Try installing off of the Alternate CD for Ubuntu 6.06 (Edgy), and only install the things you really need.

There is also an Ubuntu variant called Xubuntu that uses the xfce window manager instead of Gnome. Xfce is ver 'lightweight' and specifically optimized for modest hardware. You could try installing that one instead and see if that solves your problems.

If none of that works (still getting random freezes and such), then there's probably some sort of hardware conflict. You seem to be getting freezes during boot... Before actually hitting enter for "install" you can push a button (I think it's F6 or F8 or something) to access "other options" and enter kernel boot flags. You can add things like "noapic" or whatever, which sometimes can be used as work-arounds for hardware.

For instance, this (somewhat old) thread discusses a problem very similar to what you're seeing:
[http://www.mepis.org/node/3770#comment-17524](http://www.mepis.org/node/3770#comment-17524)

The suggestion is to add this kernel boot option:
acpi=off'


Also take a look at this post:
[http://www.linuxextremist.com/?p=33](http://www.linuxextremist.com/?p=33)

Where the guy says installation of Xubuntu was difficult, and even after installing the whole thing was very unstable.


Sorry to say that this particular laptop is not a great candidate for Linux installation...

I got one even smaller I am going to try these ideas on. This is just temporary to get me familiar with linux and ubuntu. When I get brave I am going to put it on my main business computer, but I can't afford downtime while I learn. Maybe i should figure out how to partition my current drive on my business and have a dual boot, but I am afraid I'll goof and wipe out files I need. I know there is back ups, but it's still scary. 
Thanks a bunch

---

### Post by chatterbabies on 2007-01-06
That's what I thought. If it would run XP without a glitch, just a bit slow I should be able to put Ubuntu on it. I may just try the smaller one like you all suggest to be safe, but I know i am going to want Ubuntu on my business computers, that's why I shot for it.
Thanks

---

### Post by kebes on 2007-01-06
> **chatterbabies said:**
> Maybe i should figure out how to partition my current drive on my business and have a dual boot, but I am afraid I'll goof and wipe out files I need. I know there is back ups, but it's still scary. 
Thanks a bunch

When I was just starting with Linux I was also afraid of screwing up any 'important' computer. So I tried LiveCDs (as you've done), then I found a hard drive and swapped it into my main comupter. I installed Linux onto this drive. Every so often I would switch which hard drive was attached and play with Linux for a bit. When I was ready I switched to dual-booting. (And now I only have Ubuntu installed!)

So if you're comfortable with installing new hard drives, you can test a full Ubuntu install on your real machine without fear of screwing up your original install. You can probably find an old hard drive lying around somewhere.

Good luck!

---

### Post by chatterbabies on 2007-01-06
I got one of those! That is an awesome idea! Oh boy I am about to have fun! Thank you so very much!

---

