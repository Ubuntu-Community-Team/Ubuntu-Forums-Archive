---
title: "Encrypt my HDD"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by takuhii on 2007-12-06
How do I encrypt my HDD in Ubuntu 7.10? It never gave me the option on install?

Cheers
Darren

---

### Post by wieman01 on 2007-12-06
I think it's on the Alternate Install CD, not the regular one.

---

### Post by WorldTripping on 2007-12-06
Here's a little light reading.

[http://www.howtoforge.com/ubuntu_dm_crypt_luks]("http://www.howtoforge.com/ubuntu_dm_crypt_luks")

[http://ubuntuforums.org/showthread.php?t=293299]("http://ubuntuforums.org/showthread.php?t=293299")

[http://ubuntuforums.org/showthread.php?t=420182]("http://ubuntuforums.org/showthread.php?t=420182")

[https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto")

Hope some of this helps.

---

### Post by hyper_ch on 2007-12-06
I can also recommend the howtoforge one *ggg*

If you want to fully encrypt your system it's the best if you get the alternate install cd. You'll have there an option to fully encrypt your system.

---

### Post by KhaaL on 2007-12-06
Just a question, a bit off topic... Once a FS is encrypted, how can the file system be accessed if there is a system failure?

---

### Post by wieman01 on 2007-12-06
> **KhaaL said:**
> Just a question, a bit off topic... Once a FS is encrypted, how can the file system be accessed if there is a system failure?
What sort of system failure?

---

### Post by KhaaL on 2007-12-06
The sort where you can't boot up but would still be able to access your filed through a LiveCD, for example.

---

### Post by wieman01 on 2007-12-06
> **KhaaL said:**
> The sort where you can't boot up but would still be able to access your filed through a LiveCD, for example.
I reckon in that case you are in a bit of a trouble... That's why I would never encrypt my entire HD, but only parts of it (e.g. personal data).

---

### Post by hyper_ch on 2007-12-06
> **wieman01 said:**
> I reckon in that case you are in a bit of a trouble... That's why I would never encrypt my entire HD, but only parts of it (e.g. personal data).

That's why you should have decentralized backups ;)

---

### Post by wieman01 on 2007-12-06
> **hyper_ch said:**
> That's why you should have decentralized backups ;)
True indeed... makes sense. :-)

---

### Post by hyper_ch on 2007-12-06
(and have them also encrypted)

---

### Post by tageiru on 2007-12-06
> **wieman01 said:**
> I reckon in that case you are in a bit of a trouble... That's why I would never encrypt my entire HD, but only parts of it (e.g. personal data).

Nonsense!

Just use cryptsetup from the livecd to open the encrypted partition.

---

### Post by codfather on 2007-12-06
Have a look at the work that Steve Harper is doing on this forum with Easy crypt.

This will give you an easy method to have an encrypted volume.

[http://ubuntuforums.org/showthread.php?t=585578](http://ubuntuforums.org/showthread.php?t=585578)

Cod

---

### Post by wieman01 on 2007-12-06
> **tageiru said:**
> Nonsense!

Just use cryptsetup from the livecd to open the encrypted partition.
What your language, buddy. Nice & easy although you could be right, ok?

---

### Post by hyper_ch on 2007-12-06
> **tageiru said:**
> Nonsense!

It depends on what part of the harddisk is damaged ;)

---

### Post by wieman01 on 2007-12-06
> **hyper_ch said:**
> It depends on what part of the harddisk is damaged ;)
Could you shed some light on the issue? What part would be critical? And what happend if the MBR got corrupted?

---

### Post by KhaaL on 2007-12-06
Uh... sounds like encrypting the whole partition (or at least /home) means hasse. In this case it's better to just use a encrypted volume a la truecrypt, no?

btw, what is decentralized backups?

---

