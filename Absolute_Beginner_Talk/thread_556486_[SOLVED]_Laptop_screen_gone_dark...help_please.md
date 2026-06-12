---
title: "[SOLVED] Laptop screen gone dark...help please"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by laidback on 2007-09-21
I've just had a panic phone call from my daughter whose laptop screen has suddenly gone very dark. She can just read the screen. It's dark all the time, from bootup onwards.
I've looked through the forum and see mention of "failed backlights", what's that?
Also, mention of right click on the battery icon (top right system tray) then preferences where she should find a brightness setting, apparently there isn't one available on her machine.

I installed 7.04 on her laptop which is a Packard Bell Easynote M5255.

For the last month or so, whilst she was at home, it's been absolutely fine. Now that she's miles away at University it's packed up. Don't you just love it.

I doubt that this is anything to do with Ubuntu, appears like a hardware failure to me. Does anyone have any ideas?

Is there a way of adjusting the brightness in Ubuntu, I can't find one.

Many thanks

Kindest regards

---

### Post by ijason on 2007-09-21
hey there.

for my laptop (a dell 6000) i'm able to use the default screen-brightness buttons. for my machine the [function] key and the up and down arrows respectively. one way to tell if the LCD backlight has failed will be for her to get into the CMOS or "setup" screen. usually this is accessable right at the boot-up's beginning by hitting f2 or [del] or whichever key is specified by the splash screen.

and i mean RIGHT when you turn on the computer. this will bring up the base-level menu interface for adjusting boot sequence etc. and it should be at the brightest setting for the screen, because nothing else has been loaded yet which might be telling the screen to be darker. you understand?

LCD's are actually a translucent display, behind them is a sheet of reflective foil and a light source either on all four sides of the display or on one side. if this light fails then you get the symptoms you're describing... a really faded display. if this light HAS gone out it is absolutely a hardware problem, and unless your daughter is proficient at computer hardware she should shop around local shops to find a good price to have it professionally replaced.

good luck!

---

### Post by ijason on 2007-09-21
me again. the good news is that replacement backlights are fairly cheap. and there's usually a bunch listed on ebay ([http://computers.search.ebay.com/lcd-back-light_Desktop-Laptop-Components_W0QQ_trksidZm37QQcatrefZC12QQfromZR40QQsacatZ3667QQsatitleZlcdQ20backQ2dlight](http://computers.search.ebay.com/lcd-back-light_Desktop-Laptop-Components_W0QQ_trksidZm37QQcatrefZC12QQfromZR40QQsacatZ3667QQsatitleZlcdQ20backQ2dlight)). if you can find someone selling a compatible screen to your daughter's notebook you can get that and mail it to her. 

then she'll just need to find someone to do the swap from the cracked display - with working light - to her laptop that needs the light. someone in the computer science dept would probably know someone with enough technical savvy to be able to do the swap. or at least she'll have the parts when she takes it to a shop.

---

### Post by laidback on 2007-09-21
Thanks for quick reply. Will phone her again and try out your suggestions. Understand about CMOS/BIOS etc.
She has a button on the keyboard for brightness but says it doesn't do anything. I'll ask her to press the up/down keys as well as per your laptop.

---

### Post by Rui Pais on 2007-09-21
> **laidback said:**
> I've just had a panic phone call from my daughter whose laptop screen has suddenly gone very dark. She can just read the screen. It's dark all the time, from bootup onwards.
I've looked through the forum and see mention of "failed backlights", what's that?
Also, mention of right click on the battery icon (top right system tray) then preferences where she should find a brightness setting, apparently there isn't one available on her machine.

I installed 7.04 on her laptop which is a Packard Bell Easynote M5255.

For the last month or so, whilst she was at home, it's been absolutely fine. Now that she's miles away at University it's packed up. Don't you just love it.

I doubt that this is anything to do with Ubuntu, appears like a hardware failure to me. Does anyone have any ideas?

Is there a way of adjusting the brightness in Ubuntu, I can't find one.

Many thanks

Kindest regards

Hi,
i have a Packard Bell MX67 that have an issue similar to the one you describe. 

In my version the keys to control brightness are [Fn]+[F6] to dim and [Fn]+[F7] to bright (not sure if they are the same with your sister model). The problem is that with Linux the combination of [Fn]+[F7] don't work. 
So if one dims the screen with the other working combination key he/she can't go back to normal state under Linux.

Your sister must reboot and do the combination of her laptop to brighting from grub menu, and only when brightness it's at full (or close) she should start Ubuntu.

Don't know if thats the same problem, but deserves a try.

Good luck.

---

### Post by laidback on 2007-09-21
No difference once in CMOS. So it looks like the screen has gone.
She's trying to find a friend who has a screen now (most seem to have laptops).
Thanks for that....think I have a problem.

Will view ebay ref too.

Hot news: It works with another screen. So at least I can get her back to working if I simply buy another screen.

Kindest Regards

---

### Post by laidback on 2007-09-21
Rui Pas,

Thanks for that. Once she's back working we'll give your info a try.

Kindest regards

Laidback

---

