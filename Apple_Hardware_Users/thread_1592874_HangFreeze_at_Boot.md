---
title: "Hang/Freeze at Boot"
date: 2010-10-11
forum: Apple Hardware Users
---

### Post by tosehee on 2010-10-11
Hello.

I am trying to install the latest Ubuntu 10.10 on the first generation Mac Pro, and it stucks at boot up.

I am using the 64bit linux and my Mac Pro, from what I read, has the 32bit EFI.

is there any way I can install 64 bit Ubuntu on my machine?

I have OSX/W7 installed already, but I don't really care about the triple boot. If I have to get rid of one, I would do so to install ubuntu on this  machine in 64bit.

Any help is greatly appreciated.

Cheers

---

### Post by zeroti on 2010-10-11
The following article mentions a "fakebios" option for GRUB2. Maybe you could try it out. The rest of the article isn't related to what you need to do though.

[http://blog.christophersmart.com/2009/12/22/does-your-mac-have-64bit-efi/](http://blog.christophersmart.com/2009/12/22/does-your-mac-have-64bit-efi/)

---

### Post by tosehee on 2010-10-11
Thanks for the links!

I have something to try now.  I will report back here if it works.

Cheers.

---

### Post by tpievila on 2010-10-12
> **tosehee said:**
> Hello.

I am trying to install the latest Ubuntu 10.10 on the first generation Mac Pro, and it stucks at boot up.

I am using the 64bit linux and my Mac Pro, from what I read, has the 32bit EFI.

is there any way I can install 64 bit Ubuntu on my machine?

I have OSX/W7 installed already, but I don't really care about the triple boot. If I have to get rid of one, I would do so to install ubuntu on this  machine in 64bit.

Any help is greatly appreciated.

Cheers

This is the first time I heard that some 64 bit Core CPU macs have a 32 bit EFI. Googling didn't give much info regarding Linux either...

What do you mean by getting stuck? Does the bootloader work? Does the kernel load?

---

### Post by tosehee on 2010-10-12
> **tpievila said:**
> This is the first time I heard that some 64 bit Core CPU macs have a 32 bit EFI. Googling didn't give much info regarding Linux either...

What do you mean by getting stuck? Does the bootloader work? Does the kernel load?

It basically hangs/freezes at the boot. I can't even get pass the initial grub loading screen.

---

### Post by linuxopjemac on 2010-10-12
Did you try this?
[http://ubuntuforums.org/showthread.php?t=1593445#4](http://ubuntuforums.org/showthread.php?t=1593445#4)

---

### Post by tosehee on 2010-10-12
> **linuxopjemac said:**
> Did you try this?
[http://ubuntuforums.org/showthread.php?t=1593445#4](http://ubuntuforums.org/showthread.php?t=1593445#4)

I can't even get it to show "Try Ubuntu".

It hangs at Booting from DVD.

---

### Post by tosehee on 2010-10-14
> **linuxopjemac said:**
> Did you try this?
[http://ubuntuforums.org/showthread.php?t=1593445#4](http://ubuntuforums.org/showthread.php?t=1593445#4)

I can boot to usb... 

now, what can I do to install from CD once booted in usb?

---

### Post by obast on 2010-10-14
Do you have the mac version of the 10.10 64-bit CD-ROM? The regular release doesn't work, so you need the mac specific one. You have to navigate around cdimage.ubuntu.com to find it.

---

### Post by tosehee on 2010-10-14
> **obast said:**
> Do you have the mac version of the 10.10 64-bit CD-ROM? The regular release doesn't work, so you need the mac specific one. You have to navigate around cdimage.ubuntu.com to find it.

You are absolutely right.

I just found it on another thread and was about to update this thread with the findings.

I can boot up with the +mac version fine now.

Thanks everyone for suggestions and inputs.

Cheers

---

