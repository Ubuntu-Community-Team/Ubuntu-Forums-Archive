---
title: "CD ROM won't mount media. ????"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Chasmo on 2008-02-28
Hi. I have a dell Inspiron 7000 that I put ubuntu on this week. all is going pretty well except for not being able to mount media in my cd rom. I burned a cd using my desktop box also running ubuntu thinking there should be no conflicts, but still no go. Any Ideas???  I want to copy a bunch of pics to this computer. I used this drive to install ubuntu.

---

### Post by brettg on 2008-02-28
try putting acpi=off on the appropriate kernel line in grub.conf

I have a similar problem on my non-Dell laptop and it appears to be some sort of problem between grub and the acpi in the bios. If that fixes it then you can try updating the bios or in my case I can turn on RAID support in the bios and the problem goes away. I can't explain why.

---

### Post by Chasmo on 2008-02-28
> **brettg said:**
> try putting acpi=off on the appropriate kernel line in grub.conf

I have a similar problem on m y non-Dell laptop and it appears to be some sort of problem between grub and the acpi in the bios. If that fixes it then you can try updating the bios or in my case I can turn on RAID support in the bios and the problem goes away. I can't explain why.

Thanks for the advise. I would follow it if I could. My ignorance holds me back. I fear I will need someone to hold my hand through this.  I am new to linux and wasn't very good with windows, just stumbling by.

---

### Post by oedha on 2008-02-28
have you mark the boxes in system - preferences - removable storage.....

---

### Post by Chasmo on 2008-02-28
> **oedha said:**
> have you mark the boxes in system - preferences - removable storage.....

I did just do that. All are marked. still not reading media. Thanks

---

### Post by Chasmo on 2008-02-28
I will check in tomarrow. Things to do for now.

---

