---
title: "Keyboard not working..."
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by deaddylan123 on 2006-06-07
Whenever i start installing ubuntu by putting the cd in, i get to choose to install with my keyboard, then it brings me to the live version and i can't use my keyboard, so i click install and try to answer the questions and it doesnt work...

Please help!!!!!!!

---

### Post by xyz on 2006-06-07
Hi deaddylan,
I don't understand this: " i get to choose to install with my keyboard, **then it brings me to the live version**".
When I get to keyboard layout, I'm asked abount language and then I can even try and type a bit to see if it's to my convenience. Then I press Enter and go on. Unclear about your question here!!

---

### Post by Ghil on 2006-06-07
It's probably not it but let's try something: is your keyboard USB? if yes, did you activate USB legacy support in the BIOS? if not, look around, that just might be it.

edit: oh and a little more info would be useful: what type of keyboard is it?

---

### Post by deaddylan123 on 2006-06-07
Ok, I mean i choose the first option (navigating with my keyboard), the it goes to the live version. I then  click the install icon, choose my time zone and the time, click next, then go to the keyboard thin and when it sais to type there, i cant type - no text comes up!

---

### Post by Impsy on 2006-06-07
how about we get your mouse working before you install it? what kind of mouse do you have? I had a serial mouse that I had to get working (2 screw things and a middle thing on it).

---

### Post by deaddylan123 on 2006-06-07
The mouse works just fine - It;s a USB  optical mouse.

---

### Post by deaddylan123 on 2006-06-08
Is there anybody?

---

### Post by Fafnir on 2006-06-08
I think we really need to know everything you can tell us about your keyboard, since this seems to be a pretty uncommon problem. Is it PS/2 (round connector) or USB (flat connector)? Have you had any problems with it under windows? Is it a standard UK keyboard layout? If so, did you choose British English in the language options? (I admit I'm clutching at straws there...)

You might also have a corrupt ISO - it could explain things a bit if the keyboard drivers on the disc were damaged. You can find out how to check for that [here]("http://www.psychocats.net/ubuntu/windowstoubuntu.html").

---

### Post by deaddylan123 on 2006-06-08
it's a ps/2 keyboard, a standard 104 key layout.

I'll check to see if it is corrupt. Is there a checksum or anything?

---

### Post by Fafnir on 2006-06-08
Yup - location was given in the link I gave you :-) [Here]("http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/MD5SUMS")'s a direct link for Dapper, and [here]("http://deinix.dei.uc.pt/pub/dists/ubuntu/breezy/MD5SUMS")'s a direct link for Breezy. Use whichever checksum in those files matches the name of your .iso. You might also want to try reburning the iso at a slower speed - errors sometimes creep in that way.

---

### Post by deaddylan123 on 2006-06-08
ok, im gonna go try to reload it. I'll keep you updated ;)

---

### Post by deaddylan123 on 2006-06-08
Nope...it has to be something with ubuntu for this reason - i could navigate to the install ubuntu. Also, the numlock light freezes, and never turns off if i press the button. 

PLEASE HELP!!!

---

### Post by xael on 2006-06-08
deaddylan123,

Have you tried any other keyboard in that computer?. It could be damaged & you never noticed.

---

### Post by Fafnir on 2006-06-08
OK, recap:

- You've tried reburning the ISO on another disc at a lower speed.
- You've checked that the ISO wasn't corrupted during the download with md5sum.
- You're not getting any error messages on install (drivers not loading etc).
- Your keyboard's a standard layout, and you're not trying to do anything unusual with it.
- It really is a case of your keyboard not being recognised at all.
- Your keyboard is working normally in Windows (I would guess, from the fact that you're posting this). If you're posting this on a different computer and you haven't checked if it works in Windows, definitely try switching keyboards and/or make sure the keyboard's hasn't come unplugged.

Very, very strange. The only other thing I can think of that might be the cause is that you've got a keyboard with a normal layout, but lots of non-standard buttons as well (things like "Media" and so on). That might conceivably need proprietary drivers that Ubuntu wouldn't have - but I'm using one of those and it worked fine in the install!

I'm not giving up hope, but I think it might be easiest to salvage another keyboard from another computer (or a friend) for the duration of the install, then fix things from inside Ubuntu where we'll have more information and we have far more tools - as xael says. It would also help pin down whether the problem really *is* with the keyboard - if you try a completely different keyboard, and *that* doesn't work, it indicates the problem's in the iso or elsewhere in your system (somehow).

Sorry about this - it's not really the best introduction to Ubuntu...

---

### Post by deaddylan123 on 2006-06-08
Well I've tryed 3 different keyboards, but all have some to very few extra buttons - mainly volume, mute, etc...I suppose I'll try a usb keyboard. And I will also run the option on the cd that says something like make sure cd is ok. I'll post back in at least 30mins. (and they do work with windows)

---

### Post by Fafnir on 2006-06-08
If you've tried three keyboards, I very much doubt that's the problem - the odds are so low it was only really an option if you'd only tried one keyboard. Go ahead and verify the disc - if that doesn't show anything, then I have two last, wild stabs at the problem.

1. Check the BIOS itself is recognising your keyboard by going into the BIOS setup (you normally have to hit <Del> or <F2> or something on boot).

2. Google up your make of motherboard to see if it has any known incompatibilities with the install.

I'm reaching a bit here, but if the CD's OK (proved by checksum and self-verification), the keyboard's OK (proved by repeated replacement), the install program's OK for at least 99% of keyboards (or this would be a more common problem and we'd be able to find something on it elsewhere), we're running out of points of failure...

---

### Post by deaddylan123 on 2006-06-08
ok, ill look up the motherboard (the computer is an precisin 380 if any one else has ne)

---

### Post by chuckyp on 2006-06-09
I'm also having the same problem.  I tried a server install with no luck.  Num Lock lit solid and won't turn off and kb won't work.  My install of Dapper from testing with an older kernel was working fine.  Looks like a problem with the 23 kernel.  I remember having the same problem during beta of dapper with another kernel.

---

### Post by sherlock-holmes on 2006-06-09
[QUOTE=chuckyp]I'm also having the same problem.  I tried a server install with no luck.  Num Lock lit solid and won't turn off and kb won't work.  My install of Dapper from testing with an older kernel was working fine.  Looks like a problem with the 23 kernel.  I remember having the same problem during beta of dapper with another kernel.[/QUOTE]

sometimes the numlock is a secondary function which has to be activated using shift button..like a laptop... not sure though...just varifying everything..as Fafnir said....:roll:

---

### Post by deaddylan123 on 2006-06-09
hmmm...i guess it is the kernel. This sucks...

---

### Post by chuckyp on 2006-06-09
Well i'm still trying a few things.  But for the sake of documentation I'm running the following system specs.

ECS Mother Board 865PE-A7
Keyboard is a microsoft internet keyboard PS2
Mouse USB MS Optical
P4 3GHZ with HT
1GB Ram
200GB IDE WD HDD
AC97 Sound
Nvidia Geforce 6200

---

### Post by chuckyp on 2006-06-09
Okay I'm posting this from the dapper desktop live cd now.  It appears it may just be a problem with server kernel.  I'm going to do an install from the live cd now and see how it goes.

---

### Post by chuckyp on 2006-06-09
Okay install of Dapper Desktop 6.06 from the live cd works fine.  Thats what i'm posting this message from a fresh install.  I don't know why the server iso did that.  Perhaps when I get more time I will try verifying the cd and possibly burning it slower; however, I'm tending to believe there is a problem witht he server kernel.  I wish I could do base install as I really didn't want gnome.  But I guess I'll have to live with it this way.

---

