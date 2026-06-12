---
title: "Encrypting Hard Drive Without Formatting"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by kiplingw on 2008-03-23
The alternative discs for gutsy and hardy both have a feature to format the drive encrypted so that it prompts for a password at boot. I would like this feature on my system, but do not want to format my whole system to do this. Is there a way to set it up on a system that already has a standard unencrypted ext3 partition?

Kip

---

### Post by Jadd on 2008-03-26
If you want just part of your system to be encypted, use Truecryt, encfs or pam-encfs. There are quite a few guides out there, you should be able to find them in no time.

I doubt there's an easy way to convert an entire ext3 partition into an encrypted one. The only way I can think of is to shrink your current ext3 partition with GNOME partiton editor (gparted), use a the text installer Ubuntu CD to install another Ubuntu installation, but encrypted (like in [this guide](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)), transfer all your data and setting from your old home on the old partition to home on your new encrypted partition, make sure everything is working after installing your programs, then wipe your old partition.

---

### Post by wieman01 on 2008-03-26
I am not aware of any method in Linux that allows your to convert a file system into an encrypted one without formating and removing all data in the first place. Windows can do it using Truecrypt for instance, but in Linux I don't think it is.

---

### Post by kiplingw on 2008-03-26
Thank you. What type of encryption does the LVM encrypted install use on the alternative disc?

Kip

---

