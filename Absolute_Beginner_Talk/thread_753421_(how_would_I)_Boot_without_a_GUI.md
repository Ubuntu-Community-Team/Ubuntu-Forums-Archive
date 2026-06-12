---
title: "(how would I) Boot without a GUI?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Taters on 2008-04-12
Ever since I've built my new machine, Debian based distros don't like to play nicely with me. Ubuntu attempts to work in low graphics mode (freezes up after a while,) Sabayon actually gives me a command line, then whenever I try to run something a I get an error. Same thing with Mint and Etch.

The alternate install works until  I try and use the thing. Then it encounters the same error. All I'm asking is if there is a key or configuration I have to do to get Ubuntu just to boot into a command line. From that point I'm competent enough to pull the nvidia drivers off of a USB drive and to install it.

So, is there a key combo that I have to press? Or would I have to tinker with something in grub? 

System specs:
Intel C2D E6750
DFI Blood Shot, no integrated graphics card (Which is what I believe is the source of the problem)
Nvidia 8800gt 512mb 256bit

and the rest really shouldn't be dealing with this....

Hopefully someone can help.

---

### Post by llamakc on 2008-04-12
Even if you boot into safe graphics mode you can get to a TTY login by pressing the CTL-ALT-F2 (F3, etc) key combo. From there you may login and have full access to the system (sans the GUI).

Otherwise you could install BUM (boot up manager) and disable GDM from starting at boot.

---

### Post by Kingsley on 2008-04-12
I'm sure selecting the recovery mode of Ubuntu when GRUB pops up should do what you want.

---

