---
title: "Keep Ubuntu in Safe Graphics Mode"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by drworm01 on 2008-03-08
Is there a way to make Ubuntu always start in Safe Graphics mode? I have an old computer with a semi-fragged video card. Anything that stinks of mild effort causes it to kill the entire system--unless I'm using one of the tty screens or booting into safe graphics mode (I guess a parallel question would be should I give up on using Ubuntu on this computer and switch instead to Xubuntu or some other low-use distro?). I'm trying to turn it into a headless box but my Linux-fu isn't at the point where I feel comfortable never adjusting the system via a gui.

Is what I'm trying to do possible?

Thanks for you time.
D-

---

### Post by forestpixie on 2008-03-08
is it a seperate card ? - if it is wouldn't you be better of using the onboard one, or reconfigure X to use vesa instead.

I would have thought that regardless of the distro i fthe card is saying bye slowly - it'll do it regardless

---

### Post by drworm01 on 2008-03-08
No second card, this is the only one on the computer. And I don't know what vesa is though I'll do some Googling on that.

Like I said, the LiveCD works in safe graphics mode but in normal mode (or after an install) it'll freeze the entire system up as soon as I try to open a menu. But no crashes from a tty screen, with a text-based installer or, like I said, LiveCD in safe graphics mode.

Yeah, there's no making the card un-die, but I'm one of those people who tries to squeeze every last drop he can out of everything. I'm donating the whole computer to a charity to use for spare parts eventually. I'm just trying to get this one last thing to work.

D-

---

### Post by forestpixie on 2008-03-08
vesa is the basic driver - if you reconfigure when you get to the driver part instead of nvidia, nv, ati - vesa instead try that 

of course you might already be using that check you xorg.conf

cat /etc/X11/xorg.conf 

and see what driver it's using

---

