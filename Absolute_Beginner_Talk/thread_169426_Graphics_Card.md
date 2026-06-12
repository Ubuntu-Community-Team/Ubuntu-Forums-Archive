---
title: "Graphics Card"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-05-02
Hi,

I need advice/help :D 

What is the best graphics card for my system?

My spec is: Intel(R) Pentium(R) 4 CPU 3.00GHz on an Asus Barebonde Vintage-PE1 motherboard. The board comes with integrated graphics card on-board.

I believe it is pci-slot i have. Anyone, by chance have the same motherboard? Seems, generally-speaking, that NVidia cards work best with GNU/Linux os, but i recall vaguely hearing the vendor name a different card, but not with Linux in mind. So....

Due to budget i had been happy to rely on and carry on with the on-board integrated graphics card, but increasingly i want to get a proper and separate graphics card; thus conserving my ram for other utilities and not getting sucked by the onboard integrated graphics card. there is a connection with the processor too?

Anyway, hardware is always getting cheaper. I saw an Invidia GEforce 7300TC for £49.99 at Maplins. Anyways...

Any opinions, advice, comments? much appreciated,

thanking you in advance,

--
sophtpaw

---

### Post by christhemonkey on 2006-05-02
Nvidia FX5500 seems to work very very nicely here.
(although still missing the whole glx_texture_from_pixmap thing for Xgl)

---

### Post by jazzmuzik on 2006-05-02
Yeah, it seems lots of people say nvidia based cards are better suited to Linux than ATI cards (which is what I've got).

---

### Post by sophtpaw on 2006-05-02
[QUOTE=jazzmuzik]Yeah, it seems lots of people say nvidia based cards are better suited to Linux than ATI cards (which is what I've got).[/QUOTE]

But your ATI card works fine too; is that what you're saying?

thx,

--
sophtpaw

---

### Post by r4ik on 2006-05-02
I have got both, Nvidia (SuSE) and ATI (Ubuntu)
No problems.

Just in case you need it,

[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

---

### Post by Chuck_W on 2006-05-02
My first try with Ubuntu was on a Dell tower that had onboard video. The problem I had was that the onboard video was going flaky (a known issue with that model). I tried using a PCI video card but I couldn't get Ubuntu to ignore the onboard and use the PCI card. I've since replaced the Dell as I got tired of the lines and streaks on the screen. Maybe that won't be an issue for you.

---

### Post by jazzmuzik on 2006-05-02
My ATI card works fine. I meant that the accelerated drivers are better supported by nvidia than ati. I've abandoned using the fglrx video driver. Too many problems. What's the point?

---

### Post by sophtpaw on 2006-05-03
[QUOTE=Chuck_W]My first try with Ubuntu was on a Dell tower that had onboard video. The problem I had was that the onboard video was going flaky (a known issue with that model). I tried using a PCI video card but I couldn't get Ubuntu to ignore the onboard and use the PCI card. I've since replaced the Dell as I got tired of the lines and streaks on the screen. Maybe that won't be an issue for you.[/QUOTE]

Thx for that. I know about the lines & streaks too. I thought once a PCI card is introduced the os picks up on that and bypasses the onboard/integrated graphics, which is of course the whole point. But i hear that wasn't the case for you. What card didyou get?
Aguess, its worth a try but it is good to know that may be an issue. How or where does one check what the os is using? Is it System Information (hardinfo) under Applications/System Tools?

thx again,

--
sophtpaw

---

