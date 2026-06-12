---
title: "Another Question On Ati cards"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by faerydae on 2008-04-19
So I have installed ubuntu 7.10 on a Formerly Vista Basic system gateway laptop. after sorting out the graphic issues i have run into a sound issue if anyone knows about Ati sound cards Please drop me a line 

blessings
:confused:

---

### Post by BaffledMollusc on 2008-04-19
Are you sure it's an ATI sound card? As far as I know, ATI only makes graphics cards, not sound card.

---

### Post by master5o1 on 2008-04-19
ATI sound card? Wow I thought they only did GFX.

Wana post the output of the command lspci? That will help anyone who knows more than I do figure out what card it is exactly and give you more detailed help.

---

### Post by faerydae on 2008-04-19
It's listed by ubuntu as

Vendor : Ati tech inc.
Device : SB450 HDA Audio
Status : Status
Bus : PCI
Device Type : unknown
Capabilities : unknown

---

### Post by master5o1 on 2008-04-19
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

Read through that maybe. Searching on google I found launchpad bugs relating to that card as late as may 2007. In a few days Ubuntu 8.04 will be out and I believe that switches from alsa to pulse audio and that may indeed solve the problem. I would recommend trying to fix it in 7.10 first (which I presume you are using) and if that seems to hard trying 8.04 and trying to fix it from there (which might well be easier with 6 months newer drivers/kernel/etc.

---

