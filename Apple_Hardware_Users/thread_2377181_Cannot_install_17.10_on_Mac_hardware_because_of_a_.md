---
title: "Cannot install 17.10 on Mac hardware because of a UEFI issue"
date: 2017-11-10
forum: Apple Hardware Users
---

### Post by jim-4 on 2017-11-10
I believe this is linked to the Linux kernel 4.13 rather than Ubuntu specifically (I have seen people with the same issue on Fedora running 4.11).

Trying to run the Ubuntu installer (and presumably the OS) gives the following error on my 2009 MacBook Pro 17" and my 2015 MacBook Pro 13" retina:

```

[COLOR=#000000][FONT=verdana]Couldn't get size: 0x800000000000000e[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]MODSIGN: Couldn't get UEFI db list[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Couldn't get size: 0x800000000000000e
[/FONT][/COLOR]
```[COLOR=#000000][FONT=verdana]

Does anyone know a workaround for this?
I believe others have disabled Secure Boot on non-Apple hardware, is there some similar trick that will work on a MacBook Pro?


[/FONT][/COLOR]

---

### Post by oldfred on 2017-11-13
May want to see this, lots of issues, settings, work arounds required:
 Apple's Late-2016 MacBook Pro Is Still A Wreck With Linux
[https://www.phoronix.com/scan.php?page=article&item=mbp2016-linux-wreck&num=1](https://www.phoronix.com/scan.php?page=article&item=mbp2016-linux-wreck&num=1)

---

### Post by jim-4 on 2017-11-13
> **oldfred said:**
> May want to see this, lots of issues, settings, work arounds required:
 Apple's Late-2016 MacBook Pro Is Still A Wreck With Linux
[https://www.phoronix.com/scan.php?page=article&item=mbp2016-linux-wreck&num=1](https://www.phoronix.com/scan.php?page=article&item=mbp2016-linux-wreck&num=1)

Thank you oldfred!

My MacBooks are the older models that used to work OK with various Linux flavours. I've had Mint running on them for example. 
The problem seems to be specific to the 4.11+ kernels. I see that the 4.14 contains [some improvements to EFI support]("http://lkml.iu.edu/hypermail/linux/kernel/1709.0/01667.html"). 

I guess I'll need to opt for an older kernel for now and wait until the 18.04 release of Ubuntu which I believe will ship with 4.14.

---

### Post by kevin160 on 2017-11-29
Have you tried "noefi" on the grub kernel command line?  That is what I needed for my old macpro1,1 when I upgraded from 16.04 (4.4 kernel) to 17.04 (4.10 kernel).

---

### Post by jim-4 on 2017-12-03
> **kevin160 said:**
> Have you tried "noefi" on the grub kernel command line?  That is what I needed for my old macpro1,1 when I upgraded from 16.04 (4.4 kernel) to 17.04 (4.10 kernel).

Thank you for the tip!
I've actually given up and sold my 2011 MBP 17". I might attempt this again with my 2015 model - I'll post back here with my results if so.

---

### Post by hotsalad on 2018-03-13
I had the same issue until I burned the iso to a disc. Then I re-inserted it and hit restart before it can reject it as unreadable. After the start up chime, hold down option. 

**Choose "Windows" **instead of any of the EFI boots. That launched the installer for me.

[This article]("http://www.rodsbooks.com/ubuntu-efi/") mentioned in its lengthy, but helpful, paragraphs that, "(It may be mis-labelled as "Windows.")"

---

### Post by shaynepollard1987 on 2018-11-17
For anyone in the future that may come across this issue with old macbooks i found a solution. After you are able to get into the grubloader by holding down the option key, highlight "install ubuntu" and press "e". In the line that begins with "Linux" you need to add "nomodeset" and "noefi" to the kernel command line.... you will enter these two before the "---" at the end and after the last word which is usually splash something make sure you have a space between nomodeset and noefi.. Furthermore, dont connect to the internet until after its successful to avoid any further headaches.

---

### Post by awstest on 2019-08-05
> **shaynepollard1987 said:**
> For anyone in the future that may come across this issue with old macbooks i found a solution. After you are able to get into the grubloader by holding down the option key, highlight "install ubuntu" and press "e". In the line that begins with "Linux" you need to add "nomodeset" and "noefi" to the kernel command line.... you will enter these two before the "---" at the end and after the last word which is usually splash something make sure you have a space between nomodeset and noefi.. Furthermore, dont connect to the internet until after its successful to avoid any further headaches.

Man...you are awesome! It worked for me!

---

