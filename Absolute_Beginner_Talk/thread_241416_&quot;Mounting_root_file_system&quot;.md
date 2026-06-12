---
title: "&quot;Mounting root file system&quot;"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Imma Krout on 2006-08-22
When I'm booting up, it loads the kernel fast then when it gets to this it litterally takes like 4-5 minuites for it to finally mount and continue. I've search but all I see is people who just plain cannot get past this. I really don't think it should take this long so somthing has got to be up.. Thanks for help.

---

### Post by TrendyDark on 2006-08-22
I think this has something to do with your hardware. I know when I boot sometimes it lags at this part and sometimes it doesn't lag at all.

---

### Post by Lord Illidan on 2006-08-22
I guess it will be checking your partitions. Does it do this every boot?

Try running a failsafe boot from Grub, it should tell you where it is lagging?

Also, are your partitions ext3 or reiserfs?

---

### Post by wpshooter on 2006-08-22
> **Imma Krout said:**
> When I'm booting up, it loads the kernel fast then when it gets to this it litterally takes like 4-5 minuites for it to finally mount and continue. I've search but all I see is people who just plain cannot get past this. I really don't think it should take this long so somthing has got to be up.. Thanks for help.

I have one computer that does this same thing, although I don't think mine takes 5 minutes.  The things that are different about this particular machine of mine is that it is using a SCSI 15K/RPM drive and is an AMD processor machine while my other 3 machines all use SATA drives and are Intel processor machines.  My other machines do NOT do what you are talking about, so I am quite sure it is hardware related.

P. S. - I have asked about this same question myself before and I never got any really specific answer to it.

---

### Post by adam0509 on 2007-01-27
add irqpoll in GRUB

Thanks to answer if it works for you

---

### Post by Paloseco on 2007-02-09
> **adam0509 said:**
> add irqpoll in GRUB

Thanks to answer if it works for you

How do you do that?

---

