---
title: "[SOLVED] Encrypted Partition"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-09
I am looking to create an encrypted partition to keep all my journal files. Right now, the only encryption program that I have, is GPG, however, I have not been able to find a function to let me create an encrypted partition  I want to be able to drag files in and out of my encrypted partition.

---

### Post by indytim on 2007-12-09
Why don't you just encrypt the file (to what end??) and be done with it.  <opinion>Sounds like you're really trying to make things much harder than they need to be </opinion> :).

IndyTim

---

### Post by fmbugdadi on 2007-12-09
Well, I could encrypt the file, however, I have multiple files. Why can't I just create an encrypted partition, and drag my files into it, which should automatically encrypt? I think that would be more efficient, rather than trying to encrypt and decrypt multiple files everyday. That, just does not make any sense to me....

---

### Post by akopacsi on 2007-12-09
You need TrueCrypt. It's very easy to use and it's very secure. Actually it doesn't create an encrypted partition, but it makes a file (with a given size) that you can mount to your filesystem and then you can use it as it was a normal folder.
[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by fmbugdadi on 2007-12-09
Is there a way to install truecrypt from terminal or synaptic, or do I have to download a tar.gz package and compile it myself? If there is a way to install from terminal, what is the exact command? thanks....

---

### Post by ggaaron on 2007-12-09
You can also try encfs.

---

### Post by akopacsi on 2007-12-09
No need to compile. Simply go to this page:
[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)
Select your version from the drop-down menu. You get a tar.gz file,
unzip it to any folder. It contains a truecrypt(xyz version).deb package. Double clicking on this .deb file will launch an installer, you have to click on the install button, enter your password and the program will be installed in a few second.

Once installed, you can run truecrypt from the terminal. It'll be very easy to set a up a big file that will contain your encrypted data, but it'd be useful for you to take a quick look at this how-to:
[http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/)
Scroll down to the section "The virtual volume creation".

---

### Post by fmbugdadi on 2007-12-10
O.k. the installation of Truecrypt worked without a hitch it seems. Now, I am working on creating a file to store all my files in..... thanks for the info....

---

