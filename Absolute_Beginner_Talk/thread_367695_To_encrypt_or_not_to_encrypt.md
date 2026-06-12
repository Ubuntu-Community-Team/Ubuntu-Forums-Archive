---
title: "To encrypt or not to encrypt?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by joshier on 2007-02-22
Hey guys.

I do a lot of online shopping, so I use ubuntu primarily for this to avoid trojans etc.

Well, as of yet, I've not given HD encryption much thought, though I'd love to know if it is a wise choice to go with for my usage.

Anyone know?

Cheers!

---

### Post by nereid on 2007-02-22
Uh, why do you want to encrypt your harddrive? Just because you're online shopping?

---

### Post by joshier on 2007-02-22
> **nereid said:**
> Uh, why do you want to encrypt your harddrive? Just because you're online shopping?

hackers?

---

### Post by Zzl1xndd on 2007-02-22
> **joshier said:**
> hackers?

Wont help you really, If your logged in and they hi-jack your comp then they have full access. Your better off with a good Firewall if your worried about it. Although if your using a router I wouldn't even worry about that.

---

### Post by nereid on 2007-02-22
If somebody hacked your system then is everything to late. In this case you should create a private key and store this one on an usb stick or something like that. But this is really unnecessary and, excuse me, real paranoid. Did you do this with Windows?

Not that it is really complicated to encrypt your harddrive, but why take these extreme measures on a home pc?

---

### Post by joshier on 2007-02-22
> **nereid said:**
> If somebody hacked your system then is everything to late. In this case you should create a private key and store this one on an usb stick or something like that. But this is really unnecessary and, excuse me, real paranoid. Did you do this with Windows?

Not that it is really complicated to encrypt your harddrive, but why take these extreme measures on a home pc?

I don't want to be subjected to someone stealing my credit card info when I'm making expensive purchases.

---

### Post by nereid on 2007-02-23
But this has not to do anything with encrypting your harddisk. This means you want a secure encrypted connection to the internet which is most of the time the duty of the shop provider. You want a secure SSL connection to your online shop of choice. You can't do anything here, the shop owner has to establish this connection.

---

### Post by Jadd on 2007-12-14
Encyrpting hard drives is good from keeping the data on your physical computer from physical people with physical access to your computer, like thieves who steal laptops. It doesn't protect you from hackers, spyware or viruses.

---

### Post by saj0577 on 2007-12-14
If you have a few sensitive files on your computer just shred them when you get rid of them. Unless you got any thing top secret on your computer i would not really bother encrypting the whole hard drive, if your worried about hackers no need to be, linux is safer, it is not completely safe but it is enough for day to day online shopping.

Saj

---

### Post by Odd-rationale on 2007-12-14
Encrypting your hard drive only provides security when your computer is OFF. Once you boot up and type in the encyption phrase, your computer is now "unencrypted" so to speak. So it would not really help you for the online shopping issue.

The good thing about encrypting your hard drive is that if someone stole your laptop - or your hard drive - all your data on the disk is safe. You probably know that without encryption, someone can just pop a LiveCD into the disk, boot from it, and then be able to view and edit your system files. Sometimes that person could be yourself, i.e. you messed up your installation and trying to fix it. :)

---

### Post by niteshifter on 2007-12-14
> The good thing about encrypting your hard drive is that if someone stole your laptop - or your hard drive - all your data on the disk is safe. You probably know that without encryption, someone can just pop a LiveCD into the disk, boot from it, and then be able to view and edit your system files. Sometimes that person could be yourself, i.e. you messed up your installation and trying to fix it.


Thank You! I was going to point that out as the best, soundest argument against using FDE (Full Disk Encrypttion) for most folks. That and the sibling issue of FDE: Key Management. Makes system repair a royal b**ch at best, frequently makes it not possible at all. Also affects backup methods - obviously using a file archiver (like tar) renders any FDE null and void, one has to image the partition(s).

That's not to say that FDE doesn't have it uses - it does. Just not appropriate for common destop usage. Where it is useful, even needed: Medical or Legal office where patiient or client information is stored. Stuff like that. But Joe Average User: No.

If one is worried about physical theft and the discovery of private information then look into Truecrypt and keep such info in a TC volume.

---

