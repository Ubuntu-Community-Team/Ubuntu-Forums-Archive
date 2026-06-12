---
title: "kubuntu crashed, failed to boot. Please help"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by ssharish on 2007-06-05
Hi,

I just swiched on my linux mahicne. It runs kubuntu 6.10 Edgy version. It comes and hags up 

```

Starting up...

```

nothing happenes after this. How do I solve this problem. Do I need to reinstall the OS now :(

Please help.

Thank you

ssharish

---

### Post by MikeDX on 2007-06-05
Try hitting escape at the grub screen and picking the second option down, you may be able to get into recovery mode and run an x session from there.

i wouldnt reinstall the os just yet!

---

### Post by ssharish on 2007-06-05
> **MikeDX said:**
> Try hitting escape at the grub screen and picking the second option down, you may be able to get into recovery mode and run an x session from there.

i wouldnt reinstall the os just yet!


Thanks Mike, I did enter the recovery console. B ut still it comes and hags up there saying as 

```

Starting up

```

It just donst show anything else. I have entered the grud console window. Can I do something there. What is grub? What does it do?

Thanks very much

ssharish

---

### Post by MikeDX on 2007-06-08
You could boot from the live cd, backup your /home to a usb stick and then reinstall. this way you wouldnt (should not) lose anything except maybe some installed software. I've done this before.

Make sure you back up EVERYTHING in /home/your_user. I would use a terminal and tar everything up such as:

tar zcvf backup.tar.gz /home/myuser 

this should backup everything for your user, then you can almost certainly reinstall without a problem. of course you'll need any drivers and whatnot if you needed them first time round..

good luck!

---

