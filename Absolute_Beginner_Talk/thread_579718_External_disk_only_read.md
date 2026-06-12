---
title: "External disk only read?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-10-18
Hi

I want to move some files from a laptop(using Ubuntu) to an external hard drive(witch are using ntfs). The ntfs-3g driver is installed, but when I try to paste the files the &#8220;paste&#8221; option is missing. I have tried to start nautilus as root(gksu nautilus) and changed the permissions of the external hard drive, but I always get the result &#8220;can only read the disk(or something)&#8221;, and I cant change it. Any tips for me?

---

### Post by _sAm_ on 2007-10-19
No one:)

---

### Post by Paqman on 2007-10-19
Sounds like ntfs-3g isn't doing what it should for you. What version are you using? Gutsy handles ntfs write permissons automatically.

---

### Post by _sAm_ on 2007-10-19
I am using Feisty; I will do a clean install with the latest version and see if it works, and if not I will come back and whine:)

---

### Post by Paqman on 2007-10-19
Well, a full install might be a bit drastic if it's just ntfs-3g you want. Have you tried reinstalling it?

---

### Post by _sAm_ on 2007-10-19
Yes; in synaptic.

---

### Post by Paqman on 2007-10-19
Hmm. I'm just guessing here, but what happens when you manually unmount your external drive and then mount it with:

```

mount -t ntfs-3g /dev/*location_of_your_external drive* /mnt/external

```

---

