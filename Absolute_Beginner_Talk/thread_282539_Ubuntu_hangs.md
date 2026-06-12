---
title: "Ubuntu hangs"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by kratos1963 on 2006-10-22
When I boot from the cd I get the splash screen.  After the count down it shows that is is loading all sorts of things.  When it finishes My computers internal spkeaker beeps four times and then a text screen appears with a minus sign in the top left corner.  the light on the front shows hardrive activity for about 10 seconds and then stops.  I have even waited up to 30 minutes with out anything else happening.

I read a post that said to disable plug and play os in bios.  I'm going to give that a try. I wanted to post my problem here first incase there is something else I am doing wrong.

Maybe I'm just to dumb for linux.

thanks for any and all help

kev

---

### Post by doobit on 2006-10-22
> **kratos1963 said:**
> When I boot from the cd I get the splash screen.  After the count down it shows that is is loading all sorts of things.  When it finishes My computers internal spkeaker beeps four times and then a text screen appears with a minus sign in the top left corner.  the light on the front shows hardrive activity for about 10 seconds and then stops.  I have even waited up to 30 minutes with out anything else happening.

I read a post that said to disable plug and play os in bios.  I'm going to give that a try. I wanted to post my problem here first incase there is something else I am doing wrong.

Maybe I'm just to dumb for linux.

thanks for any and all help

kev

If you get beeps that normally signifies a hardware error. It could be the video card, or a hard drive, or cdrom drive, etc. Tell us what hardware you are working with and what steps you are taking to install, and what Ubuntu CD you are using. My first guess is the video card drivers.

---

### Post by ReaderRat on 2006-10-22
> Maybe I'm just to dumb for linux.
No, you did the smart thing and asked questions on the forum.

---

### Post by Mimsy on 2006-10-22
> **kratos1963 said:**
> Maybe I'm just to dumb for linux.

There is no such thing. If you're literate and capable of following instructions, you're good. You're obviously smart enough to ask for help in these forums, so you should be fine... if there is a solution, someone will tell you about it when they see your thread. Be patient, and good luck with your problem.

/Mimsy

---

### Post by kratos1963 on 2006-10-22
Still haveing no luck.

First of all I have a voodoo AGP graphics card  16megs i think.

I went into bios and enabled plug and play os.  This had no effect.  I unplugged my USB DVD  still no effect.  Then I pushed F6 at the splash screen and at the end of the command line I added noapic and nolapic. UBUNTU loads some things and they all say "OK" except for PCMCIA.  Later it says no PCMCIA present.  I also noticed something along the lines of  "start raid device"  it didn't show an "OK" next to it. later it started checking files.  when it came to squashfs it said "mismatch".  It continued as if it was going to load but again a got a black screen and everythihng stopped.

---

### Post by kratos1963 on 2006-10-22
oh I forgot to say what Ubuntu I downloaded.  It was the regular Ubuntu 6.06.1 that said for most intel/amd computers.

---

### Post by insub2 on 2006-10-23
how much ram you got?  i had a similar experience when i was installing onto an old comp with not much ram.  if you have less than 192 MB, you need to use the alternative install cd.  (i used a breezy cd i already had lying around.  breezy only requires 128 MB for full desktop install but takes about an hour)

that is my best guess based on what i know now.

you should give us more specs on your machine if the alternative cd doesn't work.

---

