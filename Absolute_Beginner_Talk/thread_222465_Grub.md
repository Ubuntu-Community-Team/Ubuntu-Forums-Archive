---
title: "Grub"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2006-07-25
Does grub (i love that name.  it was my nickname as a kid) have to write to the Windows MBR thingie or can opt not to do that?  Is it possible that grub is corrupting my Windows so that when I install Ubuntu makes it go all screwy?  Forgive me if I sound like I don't know what I'm talking about, but that could be because I don't know what I'm talking about.  Actually, I know what I'm trying to ask but I'm not familuar enough with this system to know the correct terminology.  One more quick question.  If I don't do the grub/MBR thing, how would I boot Ubuntu?

---

### Post by Sef on 2006-07-25
So to understand your problem, it is this:

When you installed Ubuntu, you could not access Windows, correct?

---

### Post by magnoliablossom on 2006-07-25
> **Sef said:**
> So to understand your problem, it is this:

When you installed Ubuntu, you could not access Windows, correct?

Exactly...And I've done it 4 times and every time the same results.  I have to reformt my hard drive, reinstall windows, then install Ubuntu...Ubuntu does beautifully but Windows craps out with the dreaded "blue screen".  I wouldn't even put Windows back on if it wasn't for the fact I can't get my modem to work in Ubuntu.  I like it much better than Windows.

---

### Post by Sef on 2006-07-25
> I wouldn't even put Windows back on if it wasn't for the fact I can't get my modem to work in Ubuntu.

What are computer specs including the modem?

> I've done it 4 times and every time the same results. I have to reformt my hard drive, reinstall windows, then install Ubuntu...Ubuntu does beautifully but Windows craps out with the dreaded "blue screen".

If you downloaded Ubuntu, did you do an md5sum?  Did you order the disks from ship-it?  In either case you may have a bad download or a bad cd.

> I like it much better than Windows.

So do I.

---

### Post by magnoliablossom on 2006-07-25
the specs that i know are:

160 gig hard drive (western digital)
lucent winmodem
52x cd-rw (memorex)
512 ram
intel pent 4

as for the cds, i've tried two different ones and they both are fine...i've tried the livecd and the alternate cd.  they're both dapper.  i read and tried every thing i've found through searches that i thought might apply to my machine, but it doesn't work.  :(

---

### Post by Lord Illidan on 2006-07-25
Can you give us your /boot/grub/menu.lst ?

I had Windows and Ubuntu sitting peacefully together for months with no problems, on the same partition or on different ones.

Grub does overwrite your MBR, but it should not touch Windows itself.

---

### Post by magnoliablossom on 2006-07-25
> **Lord Illidan said:**
> Can you give us your /boot/grub/menu.lst ?

I had Windows and Ubuntu sitting peacefully together for months with no problems, on the same partition or on different ones.

Grub does overwrite your MBR, but it should not touch Windows itself.

well, i could but...i don't have ubuntu on here anymore and if i put it on i won't be able to get back on the internet for another 2 or 3 hours. lol

---

### Post by Sef on 2006-07-25
For your modem problems, check out [linmodems.org]("http://linmodems.org/").

---

