---
title: "Ubuntu Won't boot  2 HDD Desktop"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by JosephBus on 2007-08-14
Ubuntu Won't boot  2 HDD Desktop

HDD0 - (Primary on SATA0 ) Ubuntu 7.04, Live CD installs,
             Installed to HDD0, removed Live CD, Won't Boot.

HDD1 - (Secondary on SATA1 ), XP Pro OK

Tried:

PC boots only to HDD1 / XP with both HDDs connected,
     regardless of SATA 0/1 configuration.

Only with SATA1 / XP disconnected, & with Live CD,
     does HDD0 boot.

When live CD is installed on HDD0, power down / restart,
Bios cannot find bootable HDD0. 

Master Boot Record corrupted ??

Appreciate any ideas,  JosephBus

---

### Post by alienexplorers on 2007-08-14
I found out on my system XP does not like being on the second drive, only the primary.

---

### Post by gimpguy2000 on 2007-08-14
> **JosephBus said:**
> Ubuntu Won't boot  2 HDD Desktop

HDD0 - (Primary on SATA0 ) Ubuntu 7.04, Live CD installs,
             Installed to HDD0, removed Live CD, Won't Boot.

HDD1 - (Secondary on SATA1 ), XP Pro OK

Tried:

PC boots only to HDD1 / XP with both HDDs connected,
     regardless of SATA 0/1 configuration.

Only with SATA1 / XP disconnected, & with Live CD,
     does HDD0 boot.

When live CD is installed on HDD0, power down / restart,
Bios cannot find bootable HDD0. 

Master Boot Record corrupted ??

Appreciate any ideas,  JosephBus


Try to go into Bios and do an "typically" F6 to set settings to default. This is what I have to do with every Ubuntu install else I get the same errors as you, or can't boot etc...make sure your drives are connected the way you had them during install though. 

Paul

---

### Post by JosephBus on 2007-08-16
Thank You ! I needed to know if I was the only one suffering from the insanity...

I was directed by past forum messages to have Ubuntu primary (SATA0),but I'm open
to ANYTHING that works...my intuition (I'm not an Avatar) tells me it will be worth it to
survive the microsoft pain.

---

### Post by gimpguy2000 on 2007-08-18
From my experience I have to have Windows as primary boot or no Windows on the system, else everything is wrong. It says grub error, or ntldr not found or no operating system, etc... Basically  adding to alienexplorer's post and off my other, this should get you your correct booting order and it should theoretically work. When I first encountered this, I installed 10 times < exaggeration but at least 4 and removed drives, set orders manually, etc..for hours and nothing. Finally, I just F6'd the bios and viola! All was working. 

I guess we'll see and hope it works for you.

Paul

---

