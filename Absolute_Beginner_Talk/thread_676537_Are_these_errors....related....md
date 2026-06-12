---
title: "Are these errors....related..."
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Lisa Y on 2008-01-23
hello...i was HOPING someone here would be able to help me here....

i installed 2 programs..hoping that it would help me get my intergreated wireless to work...but i seem to have ran into those two errors...does anyone know..where i went wrong...

All i know at this point...with the headache that ive gotten...trying to figure this out is that after i installed the Wireless Assistant...when i went to my Apps>Wireless...and opened it..i already received the error...As for the Drivers...im lost...

PLEASEEEEEEE HELP!!!

I provided a picture here...

[IMG]http://i22.photobucket.com/albums/b303/xtwoface/IMG_7065.jpg[/IMG]

---

### Post by PeterJS on 2008-01-23
On the drivers front, looks like you've got an Atheros card with the correct driver, showing up as the ath0 interface.

In line with the question presented by the program what happens if you run the wireless assistant with elevated privilages using sudo?

---

### Post by Lisa Y on 2008-01-23
i tired runnin it with sudo as well...no luck the screen pops up with the same error?? could i be missing a dependency somewhere...or a file...


and as for the ath0 interface....im totally lost...have no idea what im doing wrong... 

::sigh::

---

### Post by PeterJS on 2008-01-23
> **Lisa Y said:**
> i tired runnin it with sudo as well...no luck the screen pops up with the same error?? could i be missing a dependency somewhere...or a file...

That's weird there are very few things root shouldn't be able to do.


> 
and as for the ath0 interface....im totally lost...have no idea what im doing wrong... 

::sigh::

I don't think there's anything to be done, it looks like works. The interface shows up, it associates with an essid, does it just not get an address?

What version of ubuntu are you running?

---

### Post by Lisa Y on 2008-01-24
well i get an MAC address......and im running 7.10 (32 bit) good ole gusty

---

### Post by PeterJS on 2008-01-24
> **Lisa Y said:**
> well i get an MAC address......and im running 7.10 (32 bit) good ole gusty

Mac addresses are burned in to the card at the factory, they're kinda hard to lose. Are you getting an IP address? (try ifconfig ath0). Does the standard network manager applet not work with your card?

---

### Post by Lisa Y on 2008-01-24
This is what i get from ifconfig ath0 

[IMG]http://i22.photobucket.com/albums/b303/xtwoface/IMG_7065-1.jpg[/IMG]

Do you think i might have the incorrect drivers installed or maybe installed incorrectly??....I did download the drivers for my w-fi which are the Atheros AR5006EG 802.11

from this site...[http://www.atheros.cz/](http://www.atheros.cz/)

---

### Post by PeterJS on 2008-01-24
> **Lisa Y said:**
> This is what i get from ifconfig ath0 

[IMG]http://i22.photobucket.com/albums/b303/xtwoface/IMG_7065-1.jpg[/IMG]

Do you think i might have the incorrect drivers installed or maybe installed incorrectly??....I did download the drivers for my w-fi which are the Atheros AR5006EG 802.11

from this site...[http://www.atheros.cz/](http://www.atheros.cz/)

If you had the incorrect drivers the interface wouldn't even show up at all. what happens if you run:```

sudo ifup ath0

```
I'm assuming it's not going to work but the question is what reason does it give for failure.

---

### Post by cubeist on 2008-01-24
Also, Lisa, just a helpful fyi, you can take a screenshot from within the computer by going to the Accessories/Take Screenshot app

In regards to your Atheros card, I found this link in my bookmarks which may help... It details the process of getting your wifi working via NDISWrapper.

Update... [http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

---

### Post by Lisa Y on 2008-01-24
That command gave me...

ifup: interface ath0 already configured :confused:



and ill take a look into that link as well...

---

