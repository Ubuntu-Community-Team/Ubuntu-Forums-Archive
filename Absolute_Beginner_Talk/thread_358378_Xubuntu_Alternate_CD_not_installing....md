---
title: "Xubuntu Alternate CD not installing..."
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by gatman_32 on 2007-02-10
I have a P3 730mhz with 128 RAM.  I downloaded and burned the image iso of the alternative cd and did the text install.  When it tries to install on the hd, I get a bootstrap warning and it says files are corrupt?  I also tried the original cd.  128 RAM can run the live cd, but doesn't seem to be able to install it.  Any suggestions?

---

### Post by meng on 2007-02-10
Try reburning the Alternate CD at lower speed. Even before that, check the md5sum of the iso file to make sure the download was not corrupted.

---

### Post by SoloSalsa on 2007-02-10
OMG I had the SAME problem...  Well I think.  Tell us how you tried to install it.  Once upon a time, I reported an error with the Edgy beta cd, about it not capable of manipulating JFS partitions (at all).  Then, when Edgy was official, I had the SAME debootstrap hubub when trying to install to JFS (, though it was *possible* to make such partitions... without installing to them).  And it was quite frustrating, that I had to start all over just because it did not want to install to JFS...

Anyway, is that your problem, attempting installation to a JFS partition?  Because it just won't work (to my very limited tech-manipulative capacity; though I'm sure someone smart could get past the warning...).

---

### Post by gatman_32 on 2007-02-10
I just tried the text install option.  I reburned the cd at 8X and it has gotten past installing on the base.  It's still installing right now but everything is running smoothly and no bootstrap warnings have come up.  Knock on wood.

---

### Post by nickoli_02 on 2007-02-10
Yea, I think I had the same issue a little while ago. My CD burner is garbage. If you run the option to check the CD for errors when it first boots the CD, you'll most likely find it has defects.

---

### Post by pasi.meri on 2007-02-11
> **meng said:**
> Try reburning the Alternate CD at lower speed. Even before that, check the md5sum of the iso file to make sure the download was not corrupted.

Hi, there ..
I have this same issue (i.e. Debootstrap -warning / problem) ongoing at the moment and I don't know how to proceed an installation of Xubuntu 6.06.1 Alternate i386 installation :-(

I'm going to try install a Xubuntu to my old IBM ThinkPad 600 and I'm not sure do I have too old PC/Laptop for Xubuntu .. ?

The problem what exists now on my Laptop is a warning:
file:///cdrom/pool/main/o/openssl/libss10.9.8_0.9.8a-7build1_i386.deb was corrupt

Q: If look at your comments of solution, I need to have reburn my CD again .. to check also the checksum with 'md5sum' application?

Any help is more than great, hope to get that :)

---

### Post by SoloSalsa on 2007-02-12
Using Windows, right?
Google tells me [this]("http://www.freedownloadscenter.com/Multimedia_and_Graphics/Misc__Graphics_Tools/MD5_Checker.html").
Unzip it, and paste [this]("http://ftp.wustl.edu/pub/linux/distributions/ubuntu/ubuntu-6.06.1-alternate-i386.iso.md5") in the field.

---

