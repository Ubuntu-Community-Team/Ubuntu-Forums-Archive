---
title: "Logon Screen Resolution"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Cannonade on 2007-03-08
I was wondering if there is any way to change the logon screen resolution. On my system it automatically defaults to 1280x1024, which my monitor cannot display properly so I get a big 'Out of Range' message bang in the middle of the screen.

My monitor is a 14" Widescreen and can only handle 1280x768 or 1280x800. Is there a way I can change the logon screen to this resolution?

---

### Post by moshuptrail on 2007-03-08
have you tried messing with xorg.conf?

---

### Post by Cannonade on 2007-03-09
I've looked at the file by opening it to edit from terminal. Being a noob to Linux, well, it looks a little scary and I'm concerned about changing too much!

But at the end of it, in Section "Screen" is has lists for my graphics card and my monitor. This bit reads:

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"

And after this, it reads different screen resolutions at different depths: 1, 4, 8, 15, 16 and 24. The modes for each of these are exactly the same, starting with 1280x1024. I have no idea what to do here, but my guess would be to remove the 1280x1024 line. I don't really want to risk messing with it just yet whilst I'm still having boot issues!:redface:

---

### Post by srt4play on 2007-03-09
If the resolution you want is there after the 1280x1024 line, then just remove the 1280x1024 line.

If not, then replace the 1280x1024 line with the resolution you want.

---

### Post by Cannonade on 2007-03-09
Yes, that did the trick!

Thank you very much!

---

