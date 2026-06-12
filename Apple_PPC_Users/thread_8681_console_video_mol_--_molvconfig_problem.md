---
title: "console video mol -- molvconfig problem"
date: 2004-12-20
forum: Apple PPC Users
---

### Post by cosmo on 2004-12-20
Hi there,

I have a problem running console video. Well, it is not possible for me to use molvconfig. I only get a black screen on vt8. (G3 Desktop, G4 Sonnet PCI Upgrade, Radeon 7000, Sony CPD-203). Mol runs fine in a X window, however I would prefer running it fullscreen on console. At the moment I have no clue what I could try to "see" what molvconfig is doing. The only remedy is to switch back to vt7 and ctrl-c molvconfig.

Any hints and suggestions are most welcome !
Cheers Cosmo

---

### Post by procdan on 2005-01-05
Hello!
Just tonight, I had run molvconfig several times fruitlessly. Then, as a lark, I ran it from a failsafe terminal session, and it worked! I think that my gnome settings were getting in the way. From the failsafe terminal, there's only xterm and X to get in the way.

 Also, remember that you've gotta run it as root (I changed to su in the terminal, rather than sudo). Sudo wasn't working for me. YMMV, of course.

Best of luck, Dan

---

