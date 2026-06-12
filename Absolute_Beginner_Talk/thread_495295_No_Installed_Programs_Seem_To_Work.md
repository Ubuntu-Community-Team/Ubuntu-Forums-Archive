---
title: "No Installed Programs Seem To Work"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by the.eagle on 2007-07-07
Today I installed FM Radio TUNER;), but a window came up saying 'Could not open device "/dev/radio0" !'Check your Settings and make sure that no other
program is using /dev/radio0.
Make also sure that you have read-access to it.' This always happens when I go to install a new program. Two days ago I tried ADEPT and a similar thing happened. It said I had to use SUDO or something else. Why don't they just work if they are able to be installed?  Mystifying  ....    Ian

---

### Post by Vajra Vrtti on 2007-07-07
How did you install those programs?

---

### Post by the.eagle on 2007-07-07
I went into 'synaptic package manager' and let it do  the installing.

---

### Post by Vajra Vrtti on 2007-07-07
[LIST]
[*]What packages did you try to install?
[*]Does the installation always fail?
[*]What exactly is the error message?
[*]Is the error message the same to all packages?
[/LIST]

---

### Post by PilotJLR on 2007-07-07
You have a radio tuner installed in the machine, right? What type of tuner card is it??

---

### Post by the.eagle on 2007-07-10
The  error message I got was pasted above. I have always had trouble with ADEPT, so I don't even know if it is of any benefit to have as I have never been able to use it. I am running a dual boot hybrid and have a 'COMPRO X200 pci tv and fm card' installed. When I installed ubuntu fm tuner it would not let me make or alter any settings, just the error message (above). I thought ubuntu would recognize the installed hardware and utilise it.  Any clues?       Ian

---

### Post by PilotJLR on 2007-07-10
I'm not familiar with this card... so I'm not sure if linux drivers exist or not.

Could you post the output from this command:
```

lspci -v

```

That will show the chipset(s) used by the card... based on that, we could at least try to find the right driver.

---

### Post by the.eagle on 2007-07-11
It's no good, I can't work this command line at all. I tried 'sudo -i  lspci -v' and it said '/usr/bin/lspci: /usr/bin/lspci: cannot execute binary file. I don't seem to be able to find any text to learn how to use command line. It's all too advanced.

---

### Post by Vajra Vrtti on 2007-07-11
Try just this: > **lspci -v**

---

### Post by Vajra Vrtti on 2007-07-11
> I don't seem to be able to find any text to learn how to use command line. It's all too advanced.Try this: [Learn UNIX in 10 minutes]("http://freeengineer.org/learnUNIXin10minutes.html").

---

### Post by the.eagle on 2007-07-11
The only console I can find has 'ian@ian-desktop:~$' on it and when I put that command in it goes back to that thing. There must be another console somewhere.

---

### Post by Vajra Vrtti on 2007-07-11
> The only console I can find has 'ian@ian-desktop:~$' on it
That's it!
> and when I put that command in it goes back to that thing.
Copy and paste it here so we can see what is happening.

---

### Post by PilotJLR on 2007-07-11
Copy and paste in the terminal works just like a word processor...

BUT - you may find this to be easier. Type this (or paste this) into the terminal just like below, then press enter:
```

lspci -v > ~/Desktop/lspci.txt

```

The squiggley character next to the greater-than sign is the tilde, which is left of the 1 key on US and most English keyboards.

This command will create a plain old text file called "lspci.txt" on your Desktop! Just attach that file to a post here.

If this sounds more complicated, then ignore it and just do the copy paste we mentioned earlier. I just think this file attachment may be simpler for you.

---

### Post by the.eagle on 2007-07-13
It would seem that I can't get Linux drivers for this TV card, so I will abandon the idea. Thank you anyway for trying to help.   Cheers    Ian:)

---

