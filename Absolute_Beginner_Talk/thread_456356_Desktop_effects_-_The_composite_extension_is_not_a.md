---
title: "Desktop effects - The composite extension is not available"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-05-27
When trying to access desktop effects, it gives me the error message (The composite extension is not available). I googled through these forums and found a solution saying to edit one of the last lines of xorg.conf from

Section "Extensions"
	Option		"Composite"	"0"
EndSection

to

Section "Extensions"
	Option		"Composite"	"1"
EndSection


I did so and saved it but it seems to have had no effect.

I am using 7.04 ubuntu.

---

### Post by homergreg on 2007-05-27
do you happen to have an ATI video chipset?

---

### Post by virgilnilson on 2007-05-27
> **homergreg said:**
> do you happen to have an ATI video chipset?

Uh oh, yes. =[

x850

Is that it for any chance at getting this to work then?

---

### Post by homergreg on 2007-05-27
Yes, you want to keep the composite set to off, then you need to login to a  Gnome with XGL session.  At least that is what did the trick for me on my Radeon Xpress 200M.  I'll see if I can find you a howto link.

---

### Post by virgilnilson on 2007-05-27
> **homergreg said:**
> Yes, you want to keep the composite set to off, then you need to login to a  Gnome with XGL session.  At least that is what did the trick for me on my Radeon Xpress 200M.  I'll see if I can find you a howto link.

Thank you, I googled gnome with xgl session and successfully installed xgl and am now using it as my default session and the desktop effects work now. =]

---

### Post by homergreg on 2007-05-27
Great!   Have fun with it!

---

### Post by skylornova on 2007-05-29
What instructions did you use?  Is there a HOWTO available?  The ones I found seemed pretty complicated.

---

### Post by virgilnilson on 2007-05-29
> **skylornova said:**
> What instructions did you use?  Is there a HOWTO available?  The ones I found seemed pretty complicated.

These instructions were very simple. Just follow it until it gets to the part until installing beryl.

[http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty]("http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty")

---

### Post by skylornova on 2007-05-30
Thanks for the link.  I tried it and XGL seems to load, however when i try to use the "cube" effect and switch to another desktop, all I see is the background (no menu bars, etc.).  The wobble works now, though.

Any idea what I can do?

---

### Post by jsblackmaro on 2007-12-26
I had this issue as well.  I installed the 2 files I saw in another post.  I restarted, and logged in.  I see Running local boot scripts in a full screen terminal, it goes black, and brings me back to the login screen.  So now I cant get in at all!! any ideas???  Can I get a terminal from the login window?

---

### Post by colecampbell666 on 2008-02-01
I'm having trouble - the same error message - in Gutsy.

---

### Post by elecompte on 2008-02-21
Hey....I tried all of the steps on this post, and it still says"he composite extension is not available"

---

