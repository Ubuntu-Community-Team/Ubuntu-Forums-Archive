---
title: "[SOLVED] No boot logo at startup"
date: 2008-12-15
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-12-15
For some weird reason, I no longer get the sweet framebuffer boot logo (No. I'm not talking about bootsplash image). You know, the boot logo that appears on top left. It just appears momentarily and then disappears.

---

### Post by ajgreeny on 2008-12-15
I'm still not quite sure which boot logo you mean, I'm afraid.  The grub menu could be the first graphic item you see unless there is a manufacturer's logo at boot, eg Acer or Asus or Dell or similar, which I don't see as my machine was built for me a long time ago.  After that it is the grub menu and then the usplash graphic of the growing orange band, then the login screen.  What are you expecting to see?

---

### Post by kpkeerthi on 2008-12-15
By boot logo, I mean the framebuffer image that appears when Arch begins to boot (after you choose the GRUB kernel entry).

Sorry, the below is the closest I could google. In Arch, the Arch logo appears at the top left instead of Tux. But for me, it just appears for a split seconds and goes away.

[IMG]http://www.gavare.se/gxemul/gxemul-stable/doc/debian-1.png[/IMG]

---

### Post by handy on 2008-12-15
On my 24" screen I get 2, if I work out how to get one off, I'll email it to you. :-)

---

### Post by kpkeerthi on 2008-12-15
> **handy said:**
> On my 24" screen I get 2, if I work out how to get one off, I'll email it to you. :-)

That would be great. Thanks Handy.

---

### Post by mips on 2008-12-15
> **handy said:**
> On my 24" screen I get 2, if I work out how to get one off, I'll email it to you. :-)

lol

Not something I pay much attention to and I actually don't even know if I have one.

---

### Post by MisfitI38 on 2008-12-15
> **handy said:**
> On my 24" screen I get 2, if I work out how to get one off, I'll email it to you. :-)

That's because you have a dual core CPU. ;)
FWIW, the logo is in or around the kernel PKGBUILD under /var/abs

---

### Post by handy on 2008-12-15
> **MisfitI38 said:**
> That's because you have a dual core CPU. ;)
FWIW, the logo is in or around the kernel PKGBUILD under /var/abs

So I just have to turn off one core to get rid of the 2nd one. No prob's. :-)

---

### Post by crimesaucer on 2008-12-15
The way I make my 2 images show (2 zen signs). is I add this to my kernel line in the /boot/grub/menu.lst:

```
vga=773
```


This adds the framebuffer. I usually put after the "resume=/dev/sda5" part.

From the menu.lst:

```
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
```

---

### Post by kpkeerthi on 2008-12-16
Yes. I have framebuffer turned on. Mine is vga=795 for the resolution I have. Like I said in my first post, the logo does appear, but shorty after, it disappears.

---

### Post by crimesaucer on 2008-12-16
> **kpkeerthi said:**
> Yes. I have framebuffer turned on. Mine is vga=795 for the resolution I have. Like I said in my first post, the logo does appear, but shorty after, it disappears.

Oh, I misread it. EDIT: after rebooting I see that mine stays fixed at the top while everything else scrolls up.

---

### Post by kpkeerthi on 2008-12-18
I chose to disable the framebuffer boot logo completely. Much better than annoying sudden disappearance.

---

