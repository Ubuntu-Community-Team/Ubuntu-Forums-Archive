---
title: "Warning messages when booting up Live CD"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Sini on 2007-06-27
Hi everyone,

A few days ago I bought myself a laptop (Toshiba A200-196), which unfortunately came with Windows Vista. Because I don't think Vista and I are going to be friends, I'd like to put Ubuntu on it instead. (Bear in mind that I'm entirely new to Linux.)

Now, I've downloaded and burned the CD (version 6.06), and it boots up okay -- except that there's a couple of error messages while it's loading. Before I actually go ahead and install the whole thing, I wanted to check if these are something serious.

The first one is this:
```
mount: Function not implemented
```

Then:
```
Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
```

And finally:
```
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
```

Once it's actually booted up, everything seems to be working fine.

If anyone could shed any light on any of these, I'd be grateful. I have googled them, but I'm not entirely sure I understand the results.

Many thanks,
Sini

---

### Post by Inxsible on 2007-06-27
Did you check the CD for errors? Did you burn the iso at the slowest available burn speed? 
 
Recommended burn speeds are less than 4x. These are the only things that I can think of. Maybe I am completely off !

---

### Post by Cypher on 2007-06-27
First, you should try out Feisty Fawn 7.04 as opposed to 6.06, but anyway, as long the Live CD does boot fully up and is usable you can ignore the error/warning messages that come up during boot.

The Live CD is designed to work with a very large variety of computers with a large variety of peripherals, and as such you will get those random errors for things that don't exist or aren't behaving properly.

---

### Post by Sini on 2007-06-27
Thanks for the quick replies, both of you!

I did check the CD for errors after downloading and again before booting, and it seemed to be fine, although I think I probably burned it at 8x (couldn't work out how to change the speed on Toshiba's inbuilt widget -- might try again with Nero).

> as long the Live CD does boot fully up and is usable you can ignore the error/warning messages that come up during boot
I'm glad to hear that -- it's sort of what I figured, but it's better to be sure!

So, if the CD boots up fine, can I assume that it'll probably run fine once installed, too...?

Thanks again for your help,
Sini

---

### Post by Inxsible on 2007-06-27
> **Sini said:**
> Thanks for the quick replies, both of you!
 
I did check the CD for errors after downloading and again before booting, and it seemed to be fine, although I think I probably burned it at 8x (couldn't work out how to change the speed on Toshiba's inbuilt widget -- might try again with Nero).
 
 
I'm glad to hear that -- it's sort of what I figured, but it's better to be sure!
 
So, if the CD boots up fine, can I assume that it'll probably run fine once installed, too...?
 
Thanks again for your help,
Sini
From the Live CD:
 
Make sure you can change the resolution higher or lower. Make sure your internet works. These are the peeves some users get into. So if that works for you on LiveCD, chances are that they will work on install too.

---

### Post by Sini on 2007-06-27
Got internet, will check the resolution changing... and perhaps I'll dual boot it to start with, just to make sure.

Thanks very much for your help!

Sini

---

### Post by mjwhitfield on 2007-06-27
just from a personal view point on burning CDs and DVDs... it's suicide burning at x4 on a CD, you're as likley to get a bad burn as you at at x52.  Aim for x24.

---

