---
title: "MD5SUM or SHA1SUM for &quot;Breezy Badger&quot;, i386"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by rbronson1976 on 2005-09-13
Hello everyone,

I did not see anywhere on the Ubuntu site where either an MD5 or SHA1 sum is listed for the Breezy Badger i386 release. Specifically, I am referring to the file, "ubuntu-5.10-preview-install-i386.iso".

I am a little nervous about burning the ISO without being sure of its integrity. Could two or three people please reply with either the MD5SUM and/SHA1 sums? I would appreciate,

Thank you very much.

---

### Post by Emerzen on 2005-09-13
If, by chance, you are already using Ubuntu and have K3B installed, when you burn the ISO it automatically performs a sum check.  Also, if you download w/ Bittorrent, it's unlikely to have any errors.

---

### Post by Emerzen on 2005-09-13
I just looked at my ISO of the preview, and one of the files inside is a MD5 sumcheck text file...I'm guessing this is where K3B get's the values to check.

---

### Post by rbronson1976 on 2005-09-13
[QUOTE=Emerzen]If, by chance, you are already using Ubuntu and have K3B installed, when you burn the ISO it automatically performs a sum check.  Also, if you download w/ Bittorrent, it's unlikely to have any errors.[/QUOTE]
 Thank you, but as I alluded to in my post, I have not yet burned the CD. The ISO is downloading as I type. I'm not using Bittorrent, BTW. If you still have teh original ISO can yod a sha1 or md5 for me?

Thanks

---

### Post by rbronson1976 on 2005-09-13
[QUOTE=Emerzen]I just looked at my ISO of the preview, and one of the files inside is a MD5 sumcheck text file...I'm guessing this is where K3B get's the values to check.[/QUOTE]
 So the MD5 sum in *inside* the ISO? That's interesting. I guess the MD5 value must be based on the ISO minus the MD5 text file. Could you run an MD5 over the original ISO (which, I guess, includes the MD5 file)?

Thank you.

---

### Post by Emerzen on 2005-09-13
The MD5 that K3B comes up w/ on my ISO is:

**88c0d18ee3dfee3fb2e2651c75044db3**

and it puts a green checkmark next to it.  I'm assuming, I understand the risk w/ that word, that it is comparing what it comes up w/ to the values inside the ISO and, hence, the green check.  However, when I look at the MD5 file inside the ISO there are hundreds of sums listed next to different files inside the package.  I don't know the ins-and-outs of MD5's, but my CD has installed flawlessly (Breezy Preview has been a charm BTW).  Hope that helps.

---

### Post by rbronson1976 on 2005-09-13
[QUOTE=Emerzen]The MD5 that K3B comes up w/ on my ISO is:

**88c0d18ee3dfee3fb2e2651c75044db3**

and it puts a green checkmark next to it.  I'm assuming, I understand the risk w/ that word, that it is comparing what it comes up w/ to the values inside the ISO and, hence, the green check.  However, when I look at the MD5 file inside the ISO there are hundreds of sums listed next to different files inside the package.  I don't know the ins-and-outs of MD5's, but my CD has installed flawlessly (Breezy Preview has been a charm BTW).  Hope that helps.[/QUOTE]
 Yes, that helps! Thank you very much. My ISO is fine and I will burn tonight. Thanks again for going through the trouble.

---

### Post by ScoobyDan on 2005-09-13
Hi,

As far as I am aware, the MD5 file in the ISO lists the MD5 sums for the files within that ISO, so you can identify whether a certain file passes or fails the MD5 check.

Daniel

---

### Post by Emerzen on 2005-09-13
Happy to help, as lots of people have helped me.

---

