---
title: "General Linux Question"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by Glass Casket on 2006-05-18
If I share my NTFS partition to linux for my all my music. Does that put more strain on my hardrive?

Thanks!

---

### Post by Rinzwind on 2006-05-18
[QUOTE=Glass Casket]If I share my NTFS partition to linux for my all my music. Does that put more strain on my hardrive?

Thanks![/QUOTE]

No. 

A disc more or less spins at a rate of 7200 r(otations)p(er)m(inute) (or 5400, 4500 if it's a slower disc) and WHEN a disc spins your NTFS spins with it ;)

---

### Post by Sef on 2006-05-18
> If I share my NTFS partition to linux for my all my music. Does that put more strain on my hardrive?

It shouldn't, but I don't know how well that would work.  GNU/Linux can read files, but not write to them.  Am not sure if GNU/Linux would be able to read your music files though.  How are your music files saved?  If they are saved in a proprietary Microsoft format then you would not be able to play them, except maybe under wine.

---

### Post by Glass Casket on 2006-05-18
[QUOTE=Sef]It shouldn't, but I don't know how well that would work.  GNU/Linux can read files, but not write to them.  Am not sure if GNU/Linux would be able to read your music files though.  How are your music files saved?  If they are saved in a proprietary Microsoft format then you would not be able to play them, except maybe under wine.[/QUOTE]

They're .mp3 so I'm sure they'll work under AmaroK..

And I know that I won't be able to write on that drive, only read, which is fine.

Thanks!

---

### Post by matthew on 2006-05-18
Back in my dual-boot days I did the same thing. It will work fine.

---

### Post by johnnymac on 2006-05-18
You will have no performance degradation with reading from the NTFS - as long as you aren't attempting to write to it.

---

### Post by nolan- on 2006-05-18
Yeah I do that, I have loads of MP3 on windows drive and Amarok reads the NTFS mounted drive no problems.

NoL

---

### Post by Glass Casket on 2006-05-18
Thanks guys!

---

### Post by towsonu2003 on 2006-05-18
[QUOTE=Glass Casket]They're .mp3 so I'm sure they'll work under AmaroK.[/QUOTE]
just in case: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by joseph956 on 2007-04-09
Sorry to butt in here, but is it possible to reverse that?  To be able to play your mp3's that you have saved on your Ubuntu partition in XP for instance?

If so, could you point me in the direction of a FAQ or a post?  

Thank you!

---

### Post by mac.ryan on 2007-04-09
> **joseph956 said:**
> Sorry to butt in here, but is it possible to reverse that?  To be able to play your mp3's that you have saved on your Ubuntu partition in XP for instance?

You can, if you install [drivers for EXT3 partitions]("http://www.fs-driver.org/") for windows. I would recommend to have an ubuntu partition only for data (songs) then, as with windows you will access to your EXT3 partition with full r/w access to all of it...

---

