---
title: "Failing to boot"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by webler707 on 2007-12-06
I know this is probably a very noobish question, but after searching these forums for hours I can't seem to find out what is going wrong, if there is a link to a thread that has this information it would be greatly appreciated. 

I am running an hp Pavilion tx1220us(tx1000 series) and I am trying to run the live disk(7.10), which works on my desktop, and I am assuming it is done with a lot of the booting procedures and about to dump me to the desktop when the screen suddenly just goes white and fades away. It looks like clouds drifting off to the side of the computer until the screen goes completely black but with the backlight still on. Also, every moving part stops moving and the system goes completely quite... Wish I knew what was going on here...

---

### Post by Shinbu-Otaku on 2007-12-07
have you checked to make sure that the cd works correctly? Do the 'check CD for defects' option the next time that you load the live CD. If there are errors on it, then this is most probably your problem. If not, it could be that your CD drive could be on the way out, so you may need to buy a new one.

Unfortunatly, i am not 100% sure though, it sounds quite odd though...

---

### Post by bumanie on 2007-12-07
You could also check the md5checksum of your iso (if you still have it) to ensure you got a clean download.

---

### Post by cubeist on 2007-12-07
lots of hp laptops require booting with noapic.  Just edit your grub linux boot item and add noapic at the end...
Here, try this tutorial...
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

cheers

---

