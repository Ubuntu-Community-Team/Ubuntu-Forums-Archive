---
title: "Xubuntu Live CD Fades to White on startup"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by kinson on 2006-11-19
Hi guys, not sure if this should be in the installation/setup forum, if its not hope the mod will move this for me(thanks).

I have an old twinhead laptop with specs:

pentium III (can't remember speed, probably 1ghz or something)
256ram

I download Xubuntu(Dapper, 6.06) cause its supposed to be less demanding of its hardware. The boot options("boot live cd" "boot in safe" etc) loaded properly, but when I selected to start the live cd, after the "un/decompressing Linux" graphical(colour bar) finished loading, and I think it stated "decompressing linux - OK" or something like that, the screen slowly faded to white and just stuck there. (Sorry if I didn't mention the options very well, I'm at work, and this happened last night)

I know there are some problems with the laptop(battery, screen going off(black) etc etc). But currently I can boot into Windows XP, so I suppose thats proof that it can run.

Very much a newbie to Linux, just got Ubuntu (Dapper) installed on my AMD64 pc, so trying to get it on the laptop too :p Hope you guys have some idea whats happening, cause I'm lost :|

Much thanks in advance :D

Kinson

---

### Post by Sef on 2006-12-01
Have you tried the Live CD in another computer to make sure the Live CD is not bad?

---

### Post by Falcorian on 2006-12-01
Does it kind of look like the screen "burns" to white as it were? I'd be interested to hear if anyone has a solution, as that sometimes happens to me when using a live CD on my laptop (even on CDs that are fine and that will work most of the time).


EDIT: This might be a good time to mention two things:
1) I've only had this happen on Ubuntu/Kubuntu, both Dapper and Edgy CDs, I've never tried Xubuntu.
2) I've only had it happened when I didn't manually set a screen resolution before trying to run the OS. Maybe try setting a resolution you know it supports for boot up?

---

### Post by kinson on 2006-12-08
Strange, I honestly thought I replied to this thread a while ago, just random checked it, and was curious how come my reply is missing :|

Anyways, I managed to get it working(yay!). I took Falcorian's advice and tried reducing the screen resolution before starting up the OS(the boot up part). Once it boots into the desktop, 1024x768 is fine :) I managed to configure GRUB to keep the 800x600 boot up res, and my desktop is fine now with 1024x768.

Cheers, and thanks :) (sorry for late response :p )

Kinson

(Btw Sef, I tried the Live CD on another pc already, it and worked, but thanks for the suggestion :) appreciate it :))

---

