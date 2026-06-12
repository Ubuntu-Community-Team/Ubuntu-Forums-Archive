---
title: "Samba uses disk space on local disk?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by reldruH on 2006-10-01
I just configured a samba server on my network and got it to auto-mount with fstab. I then went into my filesystem and saw that everything I had automounted was being counted towards how much space I'm using on my local hard drive. I know samba can't have transferred all that information over (it took over an hour to do it once), so is this just a mistake? Instead of only having 10 GB's left, do I actually have 30 (20GB share)?

---

### Post by ola on 2006-10-01
Hi,

when you mount a share via samba on you local computer, the local computer will access that share as a local hard drive and therefore you should see the disk space of them both on your computer (10+20=30gb).

Hopefully did that answer you question. Best regards,

Ola

---

### Post by reldruH on 2006-10-01
> **ola said:**
> Hi,

when you mount a share via samba on you local computer, the local computer will access that share as a local hard drive and therefore you should see the disk space of them both on your computer (10+20=30gb).

Hopefully did that answer you question. Best regards,

Ola

Does that mean that I can store more than what kde says is the maximum amount of space on my hard drive? It currently says I'm using 50 of 60 GB's when it's really only 30. Can I store 30 more GB's (so that it would look like I'm using 80 out of 60? Or is kde supposed to be adding the size of both my local drive and samba share? It doesn't look like it's doing that. Thanks for your help.

---

