---
title: "Unable to start Ubuntu Live CD"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by manoharp on 2007-08-18
I am unable to start the Live CD, my problem is pretty strange than others.. 

When I click on the start or install Ubuntu.. it says

Loading  /casper/vimlinuz...................
Loading  /casper/initrd.gz.......................

A popup appeared stating

Starting.. 
Loading Linux Kernel

Status bar goes to 100% and then it hangs.. 

I got the ISO file from PCWORLD magazine and wrote the image into a CD. I am not sure the problem is with burning, so I even tried with "Check CD for Defects" again it goes there and hangs. 

Please guide me through the ways I should check my CD,  also install Ubuntu

My Laptop configuration.. 

HP laptop dv6355 
AMD Turion 64X2 1.8Gh
2GB Ram
nVIDIA GEFeroce 6150 graphics card

Do you require any more information?

I eargely waiting to explore Ubuntu.. so I awaiting for your response.

thanks,
Pravin

[P.S: I am pretty newbie to Linux and its installation]

---

### Post by mysticmatrix on 2007-08-18
Pravin, Although I can't tell you exact nature of your problem, I guess HP laptops have problems when trying to boot from live CD of certain distro.(I had one during booting SABAYON). The problem is something to do with acpi flag at boot time which even I don't understand.

Guess you can try WUBI ( [http://wubi-installer.org/](http://wubi-installer.org/)) to start with Ubuntu. That would be less hassle for you.

---

### Post by manoharp on 2007-08-18
Thanks for the explanation.. I digged bit in Google and found many state the problem is due to ACPI. 

Is there anyways to turn off ACPI, while booting/installing?

How can we install through text mode, if you think the text mode could solve this problem?

Why does ACPI brings in a issue?

Is there any ways I can check the CD I burnt is perfect, or is there any issues with the CD?

Does Ubuntu support NVDIA GEForce 6150 graphics card and AMD turionx2 processor?

FYI, I am going to use this a dual boot, with VISTA, the OS I hate the most, but I have nooption to keep it as a backup for some of official applications.. 

I would be very delighted to use a 64bit os on my 64 bit processor, I dont
really like it to be used in VMWare, which wont allow me to experince the power of 64bit..

I would reallly appreciate your help in this...

---

### Post by mysticmatrix on 2007-08-18
Assuming that you are using Windows, a utility to find whether your disk is corrupt or not is to use this software [found here]("http://advanced-checksum-verifier.irnis-i-haliullin.qarchive.org/")

You can find correct MD5 sums of Ubuntu disk on the disk itself, or on the website of Ubuntu.

---

### Post by sailor2001 on 2007-08-18
might I suggest you download the alternate ubuntu 7.04...... it is text based and installs quite easy.

---

### Post by manoharp on 2007-08-28
How do I get a text based installer.. I have now got a new Live CD from my friend it started fine and loaded everything.. Finally it showed 

"Starting GNome terminal"

It turned to black screen nothing is visible not sure what should I do now.. can you please help me.

---

### Post by alienexplorers on 2007-08-28
Try running this in terminal:
> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Marat Galiev on 2007-08-28
Then you boot from live-cd press F1....F2 and read about boot methods.

---

### Post by manoharp on 2007-08-28
How do I start text based booting

---

