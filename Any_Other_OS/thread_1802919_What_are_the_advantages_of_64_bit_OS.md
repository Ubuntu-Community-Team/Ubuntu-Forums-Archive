---
title: "What are the advantages of 64 bit OS?"
date: 2011-07-12
forum: Any Other OS
---

### Post by ssreddy555 on 2011-07-12
I have installed an Ubuntu variant (Mint) both 32 bit & 64 bit versions in two different partitions.

I don't find much difference in performance, though I don't use it much for memory intensive apps like 3D games or Photoshop.

Can any one enlighten me  what are the pros & cons of 64 Bit vis a vis 32 Bit OS?

My Processor supports 64 Bit OS.

Thank u.

---

### Post by Rex Bouwense on 2011-07-12
If you are not using any memory intensive programs, I doubt that you will notice much of a difference.

---

### Post by mips on 2011-07-12
Test it archiving or encrypting largish files, do some video/audio encoding atc and you will notice the difference.

---

### Post by handy on 2011-07-12
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=9](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=9)

---

### Post by BrokenKingpin on 2011-07-12
If you have a 64-bit CPU there is very little reason not to run a 64-bit OS.

---

### Post by Plumtreed on 2011-07-13
@handy

.....thanks for those links!

---

### Post by ssreddy555 on 2011-07-13
Thanks for the replies. 

As I have already mentioned, I have already installed 64 bit Mint. Will there be much of a performance difference between this & 64 bit Ubuntu to download  & install it? 

I know it's Ubuntu forums; but still I asked the question hoping to get an answer. I already run 32 bit Ubuntu on the same system.

---

### Post by BrokenKingpin on 2011-07-13
> **ssreddy555 said:**
> As I have already mentioned, I have already installed 64 bit Mint. Will there be much of a performance difference between this & 64 bit Ubuntu to download  & install it? 

Not really, they are basically the same OS. Mint64 might run a bit lighter just because it uses Gnome2 over Unity, but this has nothing to do with 64 bit or not.

---

### Post by ssreddy555 on 2011-07-13
> **BrokenKingpin said:**
> Not really, they are basically the same OS. Mint64 might run a bit lighter just because it uses Gnome2 over Unity, but this has nothing to do with 64 bit or not.

Thank u so much.

---

### Post by bcschmerker on 2011-07-14
I have run both 32- and 64-bit versions of Ubuntu® 10.04.*-LTS Lucid Lynx&#8482; on my hybrid Everex® mid-tower (Gigabyte® MA78GM-S2HP system board, Advance Micro Devices® Athlon 64&#8482; 5600+, Creative Laboratories® SB0350 PCI audio), and 64-bit both has advantages from a performance standpoint and drawbacks in commercial support and to a lesser extent compatibility with 32-bit software.

If my experience proves out across distros, judging from known performance on the Advance Micro Devices® Athlon 64&#8482; family in 32-bit mode, 64-bit LinUX in general will run 2x to 3x as fast as 32-bit on the Athlon 64&#8482; family for the same CPU part, potentially up to 5x as fast for the same core count and clock speed on the Intel® Core&#8482; i-Series (due to the Hyper-Threading internal architecture).  Be advised that 64-bit programming has some fundamental differences, as Adobe Systems learned the hard way:

In the summer of 2010, Adobe® discovered multiple critical bugs in Flash Platform 10.0.45.2, which they were too time-constrained to fix in the 64-bit version at the time.  As I noted in "[Adobe Flash install information for AMD64 (December 2009 update)](http://ubuntuforums.org/showthread.php?t=1358591)" on 9 August 2010: 

> **bcschmerker said:**
> The actual [Security Bulletin for Flash Platform](http://www.adobe.com/support/security/bulletins/apsb10-14.html) identifies multiple critical bugs. At this point, I have to go on the assumption that Adobe Systems has pushed 64-bit support to the in-development (as of August 2010) Flash Platform 11; testing 64-bit fixes is a relatively new art in the commercial-software business. Adobe *did* patch Flash Player 9, as Version 9.0.277.0.

I found that 64-bit applications in LinUX do not support certain 32-bit libraries very efficiently, as Flash&#8482; 10.1 failed to handle certain SWF's from over-the-Web properly in 64-bit Mozilla® Firefox&#8482; 3.6.  Hopefully both nVIDIA® and Advance Micro Devices® are doing a better job on 64-bit than Adobe®, as their closed-source X-servers for the GeForce® and Radeon HD® GPU's, respectively, are mission-critical regardless of operating system.

---

### Post by wolfen69 on 2011-07-15
> **bcschmerker said:**
> I have run both 32- and 64-bit versions of Ubuntu® 10.04.*-LTS Lucid Lynx™ on my hybrid Everex® mid-tower (Gigabyte® MA78GM-S2HP system board, Advance Micro Devices® Athlon 64™ 5600+, Creative Laboratories® SB0350 PCI audio), and 64-bit both has advantages from a performance standpoint and drawbacks in commercial support and to a lesser extent compatibility with 32-bit software.

If my experience proves out across distros, judging from known performance on the Advance Micro Devices® Athlon 64™ family in 32-bit mode, 64-bit LinUX in general will run 2x to 3x as fast as 32-bit on the Athlon 64™ family for the same CPU part, potentially up to 5x as fast for the same core count and clock speed on the Intel® Core™ i-Series (due to the Hyper-Threading internal architecture).  Be advised that 64-bit programming has some fundamental differences, as Adobe Systems learned the hard way:

In the summer of 2010, Adobe® discovered multiple critical bugs in Flash Platform 10.0.45.2, which they were too time-constrained to fix in the 64-bit version at the time.  As I noted in "[Adobe Flash install information for AMD64 (December 2009 update)](http://ubuntuforums.org/showthread.php?t=1358591)" on 9 August 2010: 



I found that 64-bit applications in LinUX do not support certain 32-bit libraries very efficiently, as Flash™ 10.1 failed to handle certain SWF's from over-the-Web properly in 64-bit Mozilla® Firefox™ 3.6.  Hopefully both nVIDIA® and Advance Micro Devices® are doing a better job on 64-bit than Adobe®, as their closed-source X-servers for the GeForce® and Radeon HD® GPU's, respectively, are mission-critical regardless of operating system.

Your use of ® and other characters are distracting and unnecessary.

I find 64bit to be slightly faster and more memory efficient. If I have a 64bit cpu, I use a 64bit OS. (provided I have enough memory)

---

### Post by ssreddy555 on 2011-07-16
[QUOTE=wolfen69]I find 64bit to be slightly faster and more memory efficient. If I have a 64bit cpu, I use a 64bit OS. (provided I have enough memory)[/QUOTE]

My system has a 2 gb memory. Is it enough to run 64 bit Mint or I 
may have some problems running some programs? As of now, it's running ok.

---

### Post by NightwishFan on 2011-07-16
> **ssreddy555 said:**
> My system has a 2 gb memory. Is it enough to run 64 bit Mint or I 
may have some problems running some programs? As of now, it's running ok.

That is plenty. :)

---

### Post by Dlambert on 2011-07-17
More than plenty in fact, for me, i cannot install a 32 bit OS knowing my cpu supports 64. So no 64 bit version = no install

---

