---
title: "Installation failed on PII"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by deepseeker on 2005-12-05
New to the forum and would like to say hi to you all and ask a quick question.;) 

The CD's arrived at the weekend :razz: and being very new to linux I tried the live cd. 

It works fine in the laptop but fails to load on a pentum II 260Mhz desktop computer (is there a minimum spec for the system to work) - Question is if the live CD fails to work will the full install fail as well.

many thanks from deepseeker

---

### Post by markr on 2005-12-05
What errors is it giving you?

---

### Post by Adrian on 2005-12-05
[QUOTE=deepseeker]is there a minimum spec for the system to work[/QUOTE]

According to my x86 Hoary CDs (I haven't received the Breezy CDs yet), the live cd requires at least 128MB of RAM in order to work, while 32 MB is enough for a hard drive install.

However, it is not a good idea to run Ubunutu as a desktop system with less than 128MB RAM.

Recommended minimum requirements for Breezy:
([https://wiki.ubuntu.com/BreezyReleaseNotes](https://wiki.ubuntu.com/BreezyReleaseNotes) under "Downloading and Installing")

Install Type: Desktop
RAM: 128 megabytes
Hard Drive Space: 2 gigabytes

Install Type: Server
RAM: 64 megabytes
Hard Drive Space: 500 megabytes

---

### Post by deepseeker on 2005-12-06
Thanks for the reply's.

Answering from work so will try to explain as best I can (do not have the machine in front of me).

Memory is no problem as there is over 300 MB on the machine with no internet connection (reading other posts this seems to be needed on full install).

The disc will run and prepair everything but fails to go any further than this, the next step that I see on the laptop is where the system starts to detect the computer and configuer it with the desktop this fails to happen and always at the same place!

---

### Post by deepseeker on 2005-12-07
The line the install stops at is:

(4294669.445000)ACPI: using PIC for interrupt routing


hope this will help someone to spot what the problem is and hot to work around it.

---

### Post by Adrian on 2005-12-09
[QUOTE=deepseeker]The line the install stops at is:

(4294669.445000)ACPI: using PIC for interrupt routing


hope this will help someone to spot what the problem is and hot to work around it.[/QUOTE]

I got a similar error when I tried to install Ubuntu 4.10 (Warty) many months ago. The problem was the 2.6.8 kernel, and I got the same error when I installed it (the kernel) in Debian. I guess the reason was that the ACPI implementation in the kernel and my laptop (an old Compaq Armada 110, probably very "non-standard") were not compatible.

More recent kernels work fine, and so do the older ones (except that the ACPI functions don't work when using them).

You can try typing this at the live cd's initial "boot:" prompt:
```
live acpi=off
```
and see if it boots.

---

