---
title: "Installing Second hard drive"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by bluewagon on 2007-04-13
just wanted to ask a quick question, while installing the second hard drive and putting ubuntu on it, is their anywhere that i could harm my first hard drive with XP on it?

---

### Post by phr0ze on 2007-04-13
I believe a little will be changed in the MBR of the first drive to tell the system how to start. (You will end up with a menu to choose windows or Ubuntu.)  Even if this goes horribly wrong, I've never heard of someone not recovering. And in any case the data should still be accessable.

I would go ahead and install. If you are really paranoid, turn off hard drive one in the BIOS, install ubuntu to drive 2, then turn drive one back on. Use the bios boot device selector to pick which drive to boot.

---

### Post by alexlex on 2007-04-13
i have done this myself.... grub(linux boot loader) will install on hd0 regardless of what other hard drive you have (unless you tell it not to) so make sure your second hard drive is a slave in the bios. if you want grub to install on your second hard drive that is fine but after words you need to change your boot order in bios to boot from slave first..... do you have any other partitions on your primary drive (example. windows backup) or just ntfs C:

---

### Post by alexlex on 2007-04-13
if you have any questions or want more info let me know. i have done this myself many times.

---

### Post by bluewagon on 2007-04-13
i ran into a problem :|
is there anyway to install a STA hard drive with an IDE hard drive in place? i bought [http://www.newegg.com/Product/Product.asp?Item=N82E16822148144](http://www.newegg.com/Product/Product.asp?Item=N82E16822148144)
and i didnt realize that it didnt come with cords or anything( yea im extremely stupid when it comes to hardware) so can i just buy the sata power and data cord and still install it with an ide hard drive?

---

### Post by sewercake on 2007-04-13
Does your computer have IDE slots? Or SATA? or both? From what I know, SATA is a singly cord, with no slave. IDE is something different, it is a wide cord that has two plugs on it. So, the short answer is no, you cannot install an IDE hdd on a SATA  adapter, and you cannot install a SATA drive on an IDE adapter. But, if you have an IDE adapter, and a SATA adapter, you can install both. 
hope this helps



-Sewercake

---

### Post by bluewagon on 2007-04-13
would this work with ubuntu?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812206001](http://www.newegg.com/Product/Product.aspx?Item=N82E16812206001)
and it means that my SATA hd will work with IDE plugs right? ive run into many and they all have almost the same wording, two will have SATA to IDE converter and one will mean an IDE hd for an SATA mb and vice versa so now im all confused

---

