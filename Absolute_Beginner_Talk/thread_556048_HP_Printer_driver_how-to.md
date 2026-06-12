---
title: "HP Printer driver how-to"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-09-20
For all of you with Hp printers and can't seem to find a drier for it...I have just the fix! I have an hp deskjet 932C and I couldn't find a driver. Well HPLIP (hp linux imaging an printing system) is just the anwer!

sudo apt-get hplip

after it's done installing:

sh hplip-2.7.7.run

That should configure everything then print a test page!

(make sure you're a root user):guitar:

---

### Post by wjp.reg on 2007-09-21
> **nikoPSK said:**
> For all of you with Hp printers and can't seem to find a drier for it...I have just the fix! I have an hp deskjet 932C and I couldn't find a driver. Well HPLIP (hp linux imaging an printing system) is just the anwer!

sudo apt-get hplip

after it's done installing:

sh hplip-2.7.7.run

That should configure everything then print a test page!

(make sure you're a root user):guitar:

That's funny, because during my install ubuntu already had the 932c driver in it's database.  Are you using some other distro or older 'buntu version?

---

### Post by darren1270 on 2007-09-21
Same here mine was there just had to add printer and it detected it and was printing in under a minute!

Darren

---

### Post by nikoPSK on 2007-09-21
Nope mine wouldn't work. Had to get the driver. Same with my Sound Blaster Audigy can't find a driver. I'm using feisty...:confused:

---

### Post by LowSky on 2007-09-21
mine works just fine in gutsy tribe 5, I guess the new verison is better!

---

### Post by nikoPSK on 2007-09-21
I'll just wait for the next version of linux... (ubuntu):popcorn::KS

---

### Post by Maestro23 on 2007-09-21
> **wjp.reg said:**
> That's funny, because during my install ubuntu already had the 932c driver in it's database.  Are you using some other distro or older 'buntu version?

Same here in Feisty.  No problems.

---

### Post by nikoPSK on 2007-09-21
iunno what's up. Synaptic blahblahblah isn't working anymore!!! AAAAAAAAAAAAAAAAA:mad:

---

### Post by nikoPSK on 2007-09-28
nvm. fixed but still no sb audigy drivers.... no sound coming from the card...

---

### Post by Lady Owl on 2007-10-15
The system detected my deskjet correctly - but the test page still comes out wrong... :mad:

---

### Post by nikoPSK on 2007-10-15
I'm in gutsy now and it works fine.:) I guess this was more for people who's printer wasn't detected.:p

---

