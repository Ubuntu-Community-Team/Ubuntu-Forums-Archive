---
title: "Size descrepancy between .iso and cdrom?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-03-21
When I type "**du -ba**" (options show in bytes, all) in the terminal I get:
4585072497      cdrom0

When I right click on an .iso image I pulled from it, I get this:
4542758912

Obviously I have a 42313585 byte difference, which doesn't seem like a lot until you do some light calculations and realize it's a 40.35mb difference...that's a small-medium size application's worth, what gives?

I know it seems like I'm being nit-picky - and that this is really weird - but for some reason I simply don't trust the ripper (nautilus ripped it, I think more specifically file juicer...whatever it uses when you right click on a CDRom and hit "copy" and "save as .iso").

Any help would be appreciated.

I know the most common response will be "don't worry about it."

---

### Post by TheLions on 2008-03-21
maybe .iso is little compressed...

---

### Post by fela on 2008-03-21
as TheLions said, it could be compressed, but if you're that worried about it you could just run ```
dd if=/dev/cdrom of=filename.iso
``` (assuming you want an iso called 'filename.iso' and your cd drive is at /dev/cdrom)...see if that leaves any suspicious size differences...

---

### Post by LowSky on 2008-03-21
FYI your Hard drive auto compresses... some damn setting to save space

BTE how is RIT, I had a friend who went there... class of 05

---

### Post by Syndacate on 2008-03-22
Aight, I won't worry about it then if it's just some compression bull.  I'll copy it using "if" and see if that  does anything - just for giggles' n such.

RIT is fine...the calc teachers sucks (yet supposedly it has a great math dept.), that's about it.  The male:female ratio blows, it's a sausage fest - the girl in your mechanics class that was looking so-so at the beginning of the year is now looking like a goddess...

Aside from those few shortcomings it's great - though this well rounded education ******** is pissing me off, I just wanna get my degree and get tf out.

---

