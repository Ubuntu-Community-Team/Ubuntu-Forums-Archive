---
title: "lock-up then wont boot"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-05-29
I was in the middle of an email when my screen suddenly locked up and the hard drive light came on and stayed on. alt+ctrl+backspace wouldn't reset.  I powered down manually but now I can't boot at all from the HD.  I can't even boot into Windows.  I'm running Feisty and everything has been fine.  I'm operating off of the live CD right now.

I'm in deep right now.  Please help.

---

### Post by Kobalt on 2007-05-29
What exactly is happening when you try to boot : do you get error messages ? Does it lock up in the middle of something ?

---

### Post by djen9999 on 2007-05-29
If I try to boot into Ubuntu I just get a flashing cursor.  If I try to boot into Windows I get a long error message about improperly installed software.  The other thing that bothers me is that the light for the HD comes on and stays on.

This can't be good.

---

### Post by djen9999 on 2007-05-29
This is interesting; I just did sudo fdisk -l and it returned nothing at all.  Do I have a hard drive problem?

---

### Post by Kobalt on 2007-05-30
Hmm... It does seem like a hardware HD problem. Do you get something out of ```
sudo lshw -C disk
```

---

### Post by djen9999 on 2007-05-30
Don't ask me why, but I noticed that whenever I tried to boot from the hard drive, it would get stuck at the prompt that said, "Booting from CD." (That's with the CD drive empty)  So I changed my boot sequence to boot from the HD first and everything has been fine.  This actually sounds like a BIOS problem but BIOS is in ROM and can't get corrupted.  Or can it?

If anything, it's running faster and better than it has.

---

