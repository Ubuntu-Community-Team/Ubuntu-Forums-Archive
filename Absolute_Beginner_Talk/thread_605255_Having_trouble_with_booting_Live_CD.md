---
title: "Having trouble with booting Live CD"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by tba2287 on 2007-11-06
After downloading the ISO and burning it to a CD-RW, I've run into trouble booting up. "Start or Install" leads me to a black screen of death while giving me error messages about things not found (drivers?)
I was only able to boot into Safe Graphics Mode, which ran like a dog and distorts the display of the GUI. 
Is there anything wrong with the Live CD, or is it a driver issue? Does it have to do with my graphics card?

---

### Post by Dr Small on 2007-11-06
It could possibly be your graphics card.
What model is it ?

By the way, did you check the md5sums matched of your download, or did you check the cd for errors ?

---

### Post by tba2287 on 2007-11-06
> **Dr Small said:**
> It could possibly be your graphics card.
What model is it ?

By the way, did you check the md5sums matched of your download, or did you check the cd for errors ?

My graphics card is a Nvidia. 
Also, I checked the Live CD for possible errors, and the scan option that it has for that found nothing wrong.

---

### Post by Dr Small on 2007-11-06
Hmm. Mine is nVidia also. Hmm.
I'm trying to think of other possible problems....

You're trying Gutsy, 7.10, right ?
Perhaps you could try Feisty Fawn, 7.04.

I have no issues with 7.04, yet I had to reconfigure xserver-xorg when booting gutsy because of problems.

---

### Post by tba2287 on 2007-11-06
> **Dr Small said:**
> Hmm. Mine is nVidia also. Hmm.
I'm trying to think of other possible problems....

You're trying Gutsy, 7.10, right ?
Perhaps you could try Feisty Fawn, 7.04.

I have no issues with 7.04, yet I had to reconfigure xserver-xorg when booting gutsy because of problems.

What's "xserver-xorg"?
Also, I thought Feisty was no longer being offered for download? Personally, I'd rather have Gusty.

---

### Post by tba2287 on 2007-11-06
Now it won't even work when I go into Safe Graphics Mode. :(

BTW, when I tried and failed to boot from the Live CD, I wrote down a few things that seem wrong.
I got  a series of problems, such as "no buffer space", "Error Microcode" for something with a .fw extension.
In addition, I got a "System-version no such file directory" and a "System-BIOS no such file directory". I also got similar "no such file directory" errors for several over things that I wasn't able to write down.

---

### Post by mivo on 2007-11-06
> **tba2287 said:**
> After downloading the ISO and burning it to a CD-RW, I've run into trouble booting up. "Start or Install" leads me to a black screen of death while giving me error messages about things not found (drivers?)

What exactly do the error messages say?

Try this: In the menu where you select to start/install Ubuntu, press F6. At the bottom, remove *quiet* and *splash*, and add *nosplash*. Try if this helps, and whether you get an error message at the point where the screen previously turned black. You can also add *irqpoll* to this list, just in case.

---

### Post by tba2287 on 2007-11-06
> **mivo said:**
> What exactly do the error messages say?

Try this: In the menu where you select to start/install Ubuntu, press F6. At the bottom, remove *quiet* and *splash*, and add *nosplash*. Try if this helps, and whether you get an error message at the point where the screen previously turned black. You can also add *irqpoll* to this list, just in case.

I tried adding *nosplash* and all it gave me was a bunch of gibberish in addition to information on my cpu. I didn't add *irqpoll* because I wasn't sure where to put it, since there were two dotted lines at the end of the string of commands.

Just wondering...I have an AMD Athlon X2 64. Is that a 64-bit processor? I have (or think I have) a 32-bit version of Vista, and I downloaded the 32-bit version of Gusty to use. Could that be the source of the problem?

---

### Post by tba2287 on 2007-11-08
I'm bumping this thread up because I'm still having trouble with my Live CD.

---

### Post by mivo on 2007-11-08
The gibberish is the information that might tell us what the problem is. :p Do you have a way to take a picture of the screen? The 64-bit version should do, though you can try the 32-bit version, but I don't think it will make a difference.

*irqpoll* goes before or after *nosplash*. Just anywhere before the "--".

---

### Post by tba2287 on 2007-11-08
> **mivo said:**
> The gibberish is the information that might tell us what the problem is. :p Do you have a way to take a picture of the screen? The 64-bit version should do, though you can try the 32-bit version, but I don't think it will make a difference.

*irqpoll* goes before or after *nosplash*. Just anywhere before the "--".

Well, this is what I got, referring to a previous post:

[I]BTW, when I tried and failed to boot from the Live CD, I wrote down a few things that seem wrong.
I got a series of problems, such as "no buffer space", "Error Microcode" for something with a .fw extension.
In addition, I got a "System-version no such file directory" and a "System-BIOS no such file directory". I also got similar "no such file directory" errors for several over things that I wasn't able to write down.[/I]

---

### Post by Kal-El in SLO on 2007-11-08
i too am having difficulty booting from the live CD. i make it past the ubuntu loading screen, then to a beige/peach colored screen....and nothings happens. I can move my mouse pointer around, but that's it. i can hear the CD drive spinning like crazy...but nothings changes on the screen. what is going on?

---

### Post by Kal-El in SLO on 2007-11-08
bump...

The pc i'm using is a dinosaur...it only has 128MB of RAM, but that shouldn't affect it's ability to boot from the live disk...should it? I performed all checks and verified the disk's integrity.

I'm going to go buy more ram tonight.

---

### Post by Xoanan on 2007-11-08
The live disk requires at least 256 MB of RAM Kal-El;  I learned that the hard way.

---

### Post by Afkpuz on 2007-11-08
Ram could be the problem, but I would suggest trying the alternate install disc. Just goto ubuntu.com and download the alternate install disc.  Then, try installing.  It won't try to live-boot ubuntu, but rather, will just take you to a text installer.  I always use the text installer simply because I don't like waiting around for ubuntu to load.  Also, it seems like certain systems have alot of trouble live-booting ubuntu.

---

