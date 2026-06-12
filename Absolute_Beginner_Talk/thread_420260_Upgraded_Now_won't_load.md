---
title: "Upgraded: Now won't load"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by carpola on 2007-04-23
So I just updated to 7.04 from 6.10 by means of the Update Manager, but it had a few errors, some I can't remember. Now, when I restarted the computer after the update was finished, the loading bar with the Ubuntu logo comes up, but the bar does not fill and nothing happens. What should I do?

---

### Post by Happy_Man on 2007-04-23
Boot into the 6.10 kernel, and install from a CD. At least, that's what i did when I got your error. I have no idea why it never loads.

---

### Post by carpola on 2007-04-23
I tried booting in 6.10 but the same thing happens. Only the initial blank bar loads and it doesn't complete nor start.

---

### Post by annda on 2007-04-23
when you get to the GRUB options list, choose an option and hit 'e'
find the kernel line, hit 'e' again and remove the quiet and splash options.
hit 'b' to boot. that way you will be able to see at which step it's stalling. make a note of the error and post back.

---

### Post by carpola on 2007-04-23
It stalls on line:

sr1: scsi3 -mmc drive: 40x/48x writer cd/rw xa/form 2 cddm tray

---

### Post by annda on 2007-04-23
is this an internal or external cd drive? if it's external, try booting without it.

if it's internal, try booting into recovery mode and see what happens.

---

### Post by DrinkYourOvaltine on 2007-04-23
--- WARNING! I do not know what I am talking about, BUT...

I had the same problem last night, and after going further and further back in the GRUB recovery mode I made it to a command prompt.

There, after failing with many other methods, I got through it with:

```
sudo dpkg --configure -a
```

This may be overkill as it seemed to check and reinstall everything.
(again, I am an idiot - could have been making toast remotely for some family in London for all I know)

Also, it may just be the wrong advice for you but if your in a "how much worse could it get?" mindset, it might be worth a try.

Best of luck to you.

---

### Post by carpola on 2007-04-23
It's an internal drive and there are no cd's in any of my drives. I have tried booting in recovery mode yet I still get the same result.

Is there a way to just uinstall Fiesty and revert it back to Edgy?

---

### Post by carpola on 2007-04-23
> **DrinkYourOvaltine said:**
> --- WARNING! I do not know what I am talking about, BUT...

I had the same problem last night, and after going further and further back in the GIMP recovery mode I made it to a command prompt.

There, after failing with many other methods, I got through it with:

```
sudo dpkg --configure -a
```

This may be overkill as it seemed to check and reinstall everything.
(again, I am an idiot - could have been making toast remotely for some family in London for all I know)

Also, it may just be the wrong advice for you but if your in a "how much worse could it get?" mindset, it might be worth a try.

Best of luck to you.

Where could I even enter that into the terminal? Off of a Live cd?? it just freezes at the loading screen.

---

### Post by DrinkYourOvaltine on 2007-04-23
It is possible to get to a command prompt before the loading screen - maybe one of the safe mode kernal options in GRUB. Like I said, I kept going further down that list till I could login at a command line.

---

### Post by DrinkYourOvaltine on 2007-04-23
It may be best to wait for the pros to give you some solid advice - I'm  surprised my machine hasn't exploded from the amount of stupid I put it through.

---

### Post by carpola on 2007-04-24
Any pros' advice? Please?

---

### Post by carpola on 2007-04-25
Anyone? I've tried to the earlier setups and nothing is working.

---

### Post by annda on 2007-04-25
you mean you can't get ANY of the earlier kernels to boot into recovery?

if so, i would recommend booting off live cd and backing up/burning all your important data and reinstalling.

it seems that scsi support got borked during update, causing errors with your cd drive.  which is strange, because it is part of the kernel. so the old ones should work ok.

---

