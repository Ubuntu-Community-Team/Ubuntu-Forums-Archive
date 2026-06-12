---
title: "Questions about xmcm"
date: 2006-07-12
forum: Assistive Technology &amp; Accessibility
---

### Post by linbetwin on 2006-07-12
I have downloaded xmcm 0.1.5 from sourceforge.net. Now...

1) Can I install it on Dapper ?
2) Do I need xgl + compiz ?
3) Do I install xmcm by issuing the commands listed in the INSTALL file ?

---

### Post by jasongrieves on 2006-07-12
Hi,

XMCM currently runs on Dapper but has a big bug where the root window is "poking" through the magnifier.

I will try to build a deb in the future but you can build it on dapper.

1) yes it builds on dapper
2) you do not need xgl and you can't have compiz manager running
   You DO need the composite extension enabled (assuming your card can handle it)

sudo vi /etc/X11/xorg.conf and add

```

Section "Extensions"
    Option "Composite" "true"
EndSection

```

3) yeah run the stuff in INSTALL, you can look at my bugs on sourceforge that I listed if you want to see how I got around the ubuntu build problems

---

### Post by Henrik on 2006-07-13
Hi Jason,

That's very cool! Would you be able to make a package for Ubuntu? Perhaps you can get Luke or one of the MOTUs to help you?

---

### Post by jasongrieves on 2006-07-13
yeah i have made a couple .debs I'll look into it and prob post to Luke/You to see if I made it correctly.

---

