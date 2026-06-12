---
title: "Problem configuring 915resolution"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by Christiaan on 2006-07-24
I'm getting this in the Terminal:

> sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Unknown chipset type and unrecognized bios.
915resolution only works with Intel 800/900 series graphic chipsets.
Chipset Id: ffffffff

I'm using Parallels Desktop on a MacBook. Any idea why I'm not getting a normal mode list?

---

### Post by hajk on 2006-07-24
> **Christiaan said:**
> 
I'm using Parallels Desktop on a MacBook.


You don't have access to the hardware in a Parallels VM, instead you must address the virtual PC that (I believe) provides (in software) for the Intel i810 chipset. So the error message you're getting is right.

---

### Post by Christiaan on 2006-07-24
> **hajk said:**
> You don't have access to the hardware in a Parallels VM, instead you must address the virtual PC that (I believe) provides (in software) for the Intel i810 chipset. So the error message you're getting is right.

Oh I see, thanks. So what do you mean by "you must address"?

---

### Post by hajk on 2006-07-24
> **Christiaan said:**
> Oh I see, thanks. So what do you mean by "you must address"?

From the COD:
"address... transitive verb  meaning ... 4. direct one's attention to."

As follows:
1. Check Parallels configuration for the best available resolution.

2. After starting Ubuntu, run "sudo dpkg-reconfigure xserver-xorg" and then choose the i810 driver and that 'best available resolution'.

Good luck!

---

### Post by Christiaan on 2006-07-24
Okay cool, I'll try that. I thought "address" in this context might have been some sort of unix jargon.

---

