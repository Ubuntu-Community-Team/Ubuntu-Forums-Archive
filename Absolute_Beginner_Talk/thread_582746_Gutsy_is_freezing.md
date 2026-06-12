---
title: "Gutsy is freezing"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Danyl on 2007-10-20
Well it appears the same unidentifiable problem that plauged Feisty is plauging Gutsy...ie the random hard freeze.

Anyone else experiencing this?

---

### Post by HW_Hack on 2007-10-20
You'll need to post info on your system components and other details 

Freezes usually boil down to
- memory issues  (test each stick separately by removing all but one and rebooting - repeat as needed.)
- video card / driver / video memory issues  (switch to onboard video )

- A long shot is to upgrade your MB BIOS

---

### Post by stijngysemans on 2007-10-20
When my pc was freezing (both under Xp and feisty), i removed the dust from my video card: that helped.

Another pc was freezing when i recovered from hibernate, maybe that's what you're doing?

---

### Post by nudnik on 2007-10-20
> **Danyl said:**
> Well it appears the same unidentifiable problem that plauged Feisty is plauging Gutsy...ie the random hard freeze.

Anyone else experiencing this?

Yes. In my case it was an issue with K3b that developed somehow when upgrading from  BETA to Gutsy Final. Things went south after the new KDE components were installed. My system would freeze, utterly, on cue, like clockwork at the very end of a DVD burn. I backed up my data using nautilus and wiped the HD (a hobby of mine) before performing a fresh, clean install of Gutsy from the final release cd. All has been well since.

---

### Post by Danyl on 2007-10-20
> **stijngysemans said:**
> When my pc was freezing (both under Xp and feisty), i removed the dust from my video card: that helped.

Another pc was freezing when i recovered from hibernate, maybe that's what you're doing?

My PC has only frozen under Feisty and Gutsy. XP is fine as is PCLinuxOS. I haven't tried Kubuntu Gutsy but will be soon.

---

### Post by pyrforos on 2007-10-22
Same here..
Gutsy(clean install), Kubuntu ,Ati

Something i found:
I made a shortcut for ksysguard and if i manage to clik that, after 10-15 sec when the window of the  ksysguard appeared the system unfreezes!

---

### Post by Danyl on 2007-10-22
I think I've diagnosed my problem and I have no idea why this is but it works!

I was running my machine with 1 gig of DDR Ram (2x 512mb chips). When I remove one (it doesn't matter which one) my comp runs fine! Its not the RAM because I've interchanged (ie only run 512 at a time with each chip) the 2 pieces.

Weird huh? Its as if Ubuntu and my motherboard don't like working with each other when I crank up the RAM to 1 gig and as I said above, other OS's haven't had this problem, only Ubuntu.

---

### Post by pyrforos on 2007-10-23
Doesn't working for me..2gb --> 510Mb+512Bb+1gb..

---

### Post by gecko_gp on 2007-10-23
> **HW_Hack said:**
> You'll need to post info on your system components and other details 

Freezes usually boil down to
- memory issues  (test each stick separately by removing all but one and rebooting - repeat as needed.)
- video card / driver / video memory issues  (switch to onboard video )

- A long shot is to upgrade your MB BIOS

How i do it????

---

