---
title: "dyal bootin help"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by tadada on 2007-08-12
Ok I am writin this from MS windows because of the following problem.](*,)

I have 2 comps this one my windows(this one) and my 4 year old one used for Ubuntu. Ok i've been running ubuntu on the older one for about a week now but I decided I was going to customize it using a tutorial that tells you how to use a command line system to make and choose your apps yourself.

anyways I go install the command line. I shrink the existing partition by 10 gig and I thinkin cool I getting it set up so they can accsess each others partition. It installs and asks where to put the grub boot loader. I say to put it on the first partition (my existing install's partition (hd0) is the command) and it finishes. I reboot and it has 3 options recovery normal and memtest. I choose option 1 normal boot. And it goes into the command line system. I try all and it won't boot into the old one. 

Is there any way to recover the old os?

and when I reinstall the command line os should I isntall the boot lloader on something like my 32 meg usb drive?

---

### Post by Arthur Archnix on 2007-08-12
This is a bit confusing. Let's simplify it a bit and not talk about your computer with Windows on it. So you've got one computer with Ubuntu, and you want to install a second version of Ubuntu starting with a CLI and building it up from there?

Second, I've never understood why people are afraid to put grub in the MBR. In fact, unless you really know what you're doing you should always put it on the MBR, otherwise you may run into issues like this, which sounds like you may need to edit grub from the CLI partition and manually add the location of the kernel for your old system.

I'm not too sure how to do that, so me, I'd reinstall the command-line version and let it install Grub to MBR. It will automatically detect your Ubuntu desktop partition and put an option in grub to boot into it.

---

### Post by tadada on 2007-08-12
ok thnks I thought I was installing to the MRB but being new and was going a bit fast (qoucldn't wait to get started) I musta skipped that

---

### Post by tadada on 2007-08-12
um I at the boot loader and I don't see a option for the MRB other then (hd0) which is what I used but is the same thing /dev/hda 

I orginally used (hd0) which geave me the problem but it says that goes to the MRB... but further up it says stuff about the notian soemthing like "you can install it using the notiation (hdn,m) or as a /dev" 

but originally I didn't use anything that had an "m". Is that my problem do I have to add the m and the comma?

---

### Post by tadada on 2007-08-12
a little bit of help with my above post please...

---

### Post by Arthur Archnix on 2007-08-12
Ubuntu has a number of IRC channels available for instant support.

Best,

---

