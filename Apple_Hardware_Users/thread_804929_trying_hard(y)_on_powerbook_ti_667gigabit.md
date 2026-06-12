---
title: "trying hard(y) on powerbook ti 667gigabit"
date: 2008-05-23
forum: Apple Hardware Users
---

### Post by hwk on 2008-05-23
hello,

kind of linux noob here.

i try to install 8.04 from the desktop(live)-cd on my pb ti 667gigabit.
when booting i always get stuck after the bootpromt (also tried with live-nosplash) with some spurious error messages:
[136.762971] ramdisk ran out of compressed data
etc.
resulting in a kernel-panic.

whats going on here?
clueless:confused:
hans

---

### Post by stream303 on 2008-05-23
Ah, you mean this PPC model here:
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_667_dvi.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_667_dvi.html)

You may want to try using the "alternate" image instead of the live-cd.

---

### Post by hwk on 2008-05-23
no, i meant this one:
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_667.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_667.html)

i have tried with the alternate already, but no luck either. i even did a complete install on a wiped harddrive. ubuntu didn´t start, i only got a screen with black and white stripes, which gradually faded into a complete white-out.

very strange

h

---

### Post by stream303 on 2008-05-23
Hmmm.. might have to pass some kernel paramaters at boot time..

With the alternate image, when it comes to the second-stage of the yaboot boot: prompt, can you interrupt it by hitting -tab- and then trying one of the kernel parameters such as

```
install-powerpc video=ofonly
or
install-powerpc nosplash
```

I forgot what the exact parameter options are that you might see...

There are some helpful hints in the faqs and wikis, even if they aren't exactly for your model:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by hwk on 2008-05-23
thanks for the tips!
what parameters would i pass, if i wanted to boot into live -cd only?

want to try first...

h

---

### Post by hwk on 2008-05-23
ok, i got to install it from alternate.
now, when booting i end up in "terminal mode".

there is a message saying:
warning failsafe mode was already attempted within 30 sec
warning falling back to gdm to report the issue

the asking me to retry after configuring xorg.conf properly.

so i tried:
sudo cp /etc/X11/xorg.conf / /etc/X11/xorg.conf.original
sudo nano -w /etc/X11/xorg.conf

which brought me into nano, with the conf-file.
then i was lost as to what to put in there and also how to operate nano.
didn´t even manage to exit this nano thing.:(

any tips appreciated.
hans

---

### Post by stream303 on 2008-05-24
> **hwk said:**
> ok, i got to install it from alternate.
now, when booting i end up in "terminal mode".

Great!  What method did you use to get it to boot, or what kernel parameter did you pass at the yaboot boot: prompt?

> which brought me into nano, with the conf-file.
then i was lost as to what to put in there and also how to operate nano.
didn´t even manage to exit this nano thing.:(

Getting comfortable with a text editor like nano seems to be in the cards for you. :)  No problem.  Nano provides some command hints at the bottom of it's screen.  When you see the caret (^) symbol, that means you need to use the CTRL key.

So after editing the file, you want to write out your changes to it with CTRL-O.  To exit nano, use CTRL-X.

At this point, I'd probably try updating your software and trying again.

```
sudo apt-get update
then
sudo apt-get upgrade
```

If there are problems here, we might have to edit the /etc/apt/sources.list file, but let's see how this goes.

Two good command to know right off the bat are how to reboot and shutdown the machine:

To shutdown (halt):
```
sudo shutdown -h now
```

To reboot:
```
sudo shutdown -r now
```

We still might be looking at editing the /etc/X11/xorg.conf file and others, but I'm hoping we can start with the latest software upgrade.

---

### Post by hwk on 2008-05-24
thanks for getting back to me!

> **stream303 said:**
> Great!  What method did you use to get it to boot, or what kernel parameter did you pass at the yaboot boot: prompt?

don´t remember exactly, probably specifying the architecture ppc



> **stream303 said:**
> So after editing the file, you want to write out your changes to it with CTRL-O.  To exit nano, use CTRL-X.
thanks, thats what i needed and didn´t find

> **stream303 said:**
> At this point, I'd probably try updating your software and trying again.

```
sudo apt-get update
then
sudo apt-get upgrade
```

If there are problems here, we might have to edit the /etc/apt/sources.list file, but let's see how this goes.
this went all well

> **stream303 said:**
> We still might be looking at editing the /etc/X11/xorg.conf file and others, but I'm hoping we can start with the latest software upgrade.
yep, i think this is now upon me.

the xorg.conf reads:

section "monitor"
 identifier "configured monitor"

section "screen"
 identifier "default screen"
monitor "configured monitor"
device "configured device"

any idea, what to put there??

thanks
hans

---

### Post by stream303 on 2008-05-24
Looks like we have to force Hardy to recognize the radeon.

But first, you can peruse what it *thinks* it wants by looking at:

```
less /var/log/Xorg.0.log
```
Note the capital X and the zero.  Less is a simple text pager you can just quickly view files without editing.  Use the up down keys to scroll through the file.  When you are done viewing, just hit the **q** key.  There is a lot of stuff, but this can come in handy later to see if anything you add or subtract from the xorg.conf file gets accepted or rejected.

For now we'll have to rely on the faqs and postings from others about their radeons.  The specs for your box shows that the card supports a 4x AGP mode.  The fist thing I'd try is this:

```
Section "Device"
        Identifier      "Configured Video Device"
        [b]Driver          "radeon"
        Option          "AGPMode" "4"
        #Option         "UseFBDev" "false"[/b]
EndSection
```

If that doesn't work, try removing the # comment character from the Option UseFBDev line.  Any line with # in front of it will get ignored.

There are more things we can try, but this is hoping we can at least get a crackle of video out while using the most amount of Hardy defaults to keep things simple.

How does this work?

---

### Post by hwk on 2008-05-24
ok, ran less. but still clue-less:)

among the first thing it says:
using config file: "/etc/X11/xorg.config.failsafe"

does that mean, it doens´t use the regular xorg.config??

then it proceeds thru a lot of stuff, which i don´t understand and ends with:
fatal server error
no screens found

?

---

### Post by stream303 on 2008-05-24
That's the first time I've encountered the failsafe config.  I suppose you could try editing *that* file and see what happens.

The good thing is that you can actually get to a state where you can edit these files, and hopefully you only need just a few more options to be present to stop it from complaining.

I'd search the forums and faqs a bit and see what comes up for radeon, or maybe a ti-book owner can jump in with some suggestions.

Sure wish I had that hardware so I could go further with you on it.  But hang in there, you are very close.

---

### Post by hwk on 2008-05-24
thanks for your assistance so far!

actually i tried and edited the failsafe-file. it had a vesa-driver specified, which i replaced for "r128". but still no luck.
less stil gives me fatal server error: no screen found.

oh man, thats frustrating..

---

### Post by stream303 on 2008-05-24
One thing I'd do is verify your card with

```
lspci
```

and see what turns up.  Instead of r128 which is for ati-rage cards, try *radeon* instead.

There are also boot parameters which might be needed at the second-stage yaboot: prompt for the radeon - such as

```
Linux video=radeonfb
```

or some other relative.  There's a few tips on lines to use for radeons in the threads here, and once you find one that works, we can make it permanent.

---

### Post by hwk on 2008-05-25
thank you, 

i tried lspci and for vga compatible controler i got:
ati technologies inc radeon mobility m6 ly

its shown on 0000:00:10:0

boot-parameter Linux video=radeon didn´t yield anything.

oh well, it was meant to be an easy thing...
the search continues

h

---

### Post by enigmaSIR on 2008-08-23
Bump:

Has anyone found a solution to this? 
I have the ATI M6 card with 16MB on my tibook. 

I still can't X to start. Any suggestions?

---

### Post by encaputxat on 2008-08-24
please, find a solution, I have the same problem..:(

---

