---
title: "recovery mode / root console shell for Mac / PPC?"
date: 2007-02-28
forum: Apple PPC Users
---

### Post by Dave / Mosaic on 2007-02-28
New to Ubuntu here as of a couple weeks ago, on a PowerMac G3.  (So far it works great, though troubles installing...)

A question though:  On the PC platform, the GRUB bootloader gives you a choice before booting (so I have read) to boot into recovery mode, by pressing escape and selecting different boot modes from a menu.

I haven't been able to figure out any corresponding option on my G3/PPC platform here, in the normal yaboot booting sequence.

Is there a way to do this that I am missing?

--dave

---

### Post by ssam on 2007-03-01
at the second part of the yaboot, press tab. you should be give a list of boot options. I get
```
Linux
old
hda13-Linux
hda13-old
```

then try typing
```
Linux single
```
and pressing enter.

(I have not tested this, but i think it is how it should work)

---

### Post by Dave / Mosaic on 2007-03-01
REALLY....!!??  Hey, thanks...

Well now, I'll have to try that...  I can't right now, being in the middle of a reinstallation, but that's what I want, for sure.

Do you know, is that documented somewhere, where I could have found out this answer myself, if only I had known where to look?  I've searched around a lot, actually,,,

Also, while I'm thinking of it... do you know what the 'old' in that list is about?  I tried typing it once, and only got a message that the bootloader couldn't find a kernel with that name to load...

--dave

---

### Post by Dave / Mosaic on 2007-03-01
BTW -- I just tried the "Linux single" thing and it works exactly right, booting into a root shell without X...

Many thanks,

--dave

> **ssam said:**
> at the second part of the yaboot, press tab. you should be give a list of boot options. I get
```
Linux
old
hda13-Linux
hda13-old
```

then try typing
```
Linux single
```
and pressing enter.

(I have not tested this, but i think it is how it should work)

---

