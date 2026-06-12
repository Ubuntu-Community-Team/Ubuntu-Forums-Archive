---
title: "No graphics card, only SIS chip!"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by sebz2005 on 2006-10-08
Hi.
With the motherboard that I have, it won't acept the graphics card in the AGP slot, so I'm stuck with a crappy SIS chip on the motherboard.
Using the hard drive from my other PC with ubuntu on it, it won't configure for the new change to the SIS chip!
How would I overcome this?

---

### Post by po0f on 2006-10-08
sebz2005,

There may be an option in your BIOS to disable the onboard video.  This is probably your culprit.  And does the video card work if you still have the onboard hooked up to the monitor, ie video card is in AGP slot, but monitor connected to motherboard?

---

### Post by sebz2005 on 2006-10-08
The SIS chip is 'Inteligent'.
It knows when there's a new card in place, is it is close imposible to disable it. (Next option is to put some C4 next to it!)
The ext. graphics card will not start up, though it is getting power.
The only thing that will work is the on-board chip.

Though as AOpen's support tech says:
[I]"The on-board chip shall disable itself and alow the AGP card to function.
There is no option in the BIOS to disable it. This is how AOpen have designed it.
With the card in, you will get no signal though the motherboard's VGA output, but through the card's VGA output.
Depending on the cards schematics, the AGP slot is made for AGP 2x and 4x."
[/I]The card is 2x (?) and works on an older motherboard!

I should get a new motherboard! The one that I have, the sound chip is shot! :x

---

### Post by fragos on 2006-10-08
Just as a matter of note there is a Gpl sis video driver.  Edit /etc/X11/xorg.conf and change Driver "vesa" to "sis".  On an Acer laptop I set up it had an sis video chip set but even the xserver configuration would'nt automatically set the driver.

---

### Post by sebz2005 on 2006-10-08
How do I do the xserver configurtion thing and restart gdm?

---

