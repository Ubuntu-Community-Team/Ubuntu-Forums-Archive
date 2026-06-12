---
title: "Mac Mini Restart Crash / Hang"
date: 2007-04-25
forum: Apple Intel Users
---

### Post by bazzer on 2007-04-25
Hi All
Well after following a guide on getting Feisty to dual boot with OSX (using rEFIt) on the Mini, I've got it going and it looks great so far with just one large exception... When I select 'Restart' problems occur. I get past the rEFIt screen where you can choose which OS to boot and it briefly shows me a Tux, but then the screen switches off . It doesn't get as far as the 'Grub loading stage2' bit.

Cold boot works fine though, so maybe it's the equivalent of ACPI or something?! I'm outta my depth here though.

I've edited the refit conf to make the default option Ubuntu, as I want to use the box in a kinda 'kiosk' situation and I find Ubuntu allows much more config options than the toy OS they give you with these boxes!!:lolflag: 

I really need to be able to restart the box without manually power cycling... Help!!

---

### Post by bazzer on 2007-04-26
Update - I've kinda got round it by using rEFIt in text mode and getting GRUB to show a quick menu. Seems to work ok every time now......

But still, it would be nice if it were prettier?

---

### Post by eugenesan on 2007-05-01
I have same issue on 6.10 with ReFit 0.8 and 7.04 on ReFit 0.9.
Any Ideas why?

---

### Post by bazzer on 2007-05-01
Actually I've noticed that if I have a LAN connection it barfs, if the port is empty it's ok..... VERY odd. I wonder if it's a hardware bug?

---

### Post by eugenesan on 2007-05-01
ReFit  in text mode helps, but doesn't solve the problem.
I have filling that issue related to ReFit video controller initialization and inability of GRUB to take over video controller after that. Issue appeared after grub update.
I will try to install old version of grub to see if the grub is the one to blame.

---

