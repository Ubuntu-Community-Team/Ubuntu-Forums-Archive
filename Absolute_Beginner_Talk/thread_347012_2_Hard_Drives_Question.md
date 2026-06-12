---
title: "2 Hard Drives Question"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by AdyE on 2007-01-26
Hello, I have a question about setting up 2 disc drives but i will explain something first :-)
I had a disc drive with windows xp home on it (Maxtor 200GB SATA II) which had to be re-installed after it got hit by a virus. I had problems doing this so I took out the drive and gave it to a friend to sort out for me.
Meanwhile, I bought a new hard drive (Hitachi 250GB SATA II) and installed Ubuntu 6.06 as I wanted to try a linux O/S.
My friend has fixed and returned the original drive and I now want to put it back in my comp.
My questions are,
1) Can I just put the windows drive back in and boot up.
2) Do I leave the ubuntu drive in Sata 1 or move it to Sata 2 on the motherboard.

Any help will be appreciated :-)
Take care,
AdyE.

---

### Post by lyceum on 2007-01-26
If you load XP after Ubuntu there will be no boot to let you chose which one you want. If you do XP first, then Ubuntu, Ubuntu will set one up for you. Hope that helps. :)

---

### Post by AdyE on 2007-01-26
> **lyceum said:**
> If you load XP after Ubuntu there will be no boot to let you chose which one you want. If you do XP first, then Ubuntu, Ubuntu will set one up for you. Hope that helps. :)

Does that mean I will have to re-install ubuntu after I have sorted the windows drive?
Thanx for the reply :-)

---

### Post by lyceum on 2007-01-26
> **AdyE said:**
> Does that mean I will have to re-install ubuntu after I have sorted the windows drive?
Thanx for the reply :-)

Sorry, but yes. :(  You will have to start over with a new Ubuntu install.

---

### Post by jkeyes0 on 2007-01-26
> **AdyE said:**
> Hello, I have a question about setting up 2 disc drives but i will explain something first :-)
I had a disc drive with windows xp home on it (Maxtor 200GB SATA II) which had to be re-installed after it got hit by a virus. I had problems doing this so I took out the drive and gave it to a friend to sort out for me.
Meanwhile, I bought a new hard drive (Hitachi 250GB SATA II) and installed Ubuntu 6.06 as I wanted to try a linux O/S.
My friend has fixed and returned the original drive and I now want to put it back in my comp.
My questions are,
1) Can I just put the windows drive back in and boot up.
2) Do I leave the ubuntu drive in Sata 1 or move it to Sata 2 on the motherboard.

Any help will be appreciated :-)
Take care,
AdyE.

This actually sounds similar to my dual-boot situation. If you disconnect the ubuntu drive and reconnect the windows drive, it should boot to windows with little-to-no problems (unless your friend changed somethign on the drive).

If you know how to change boot options in the bios, it might be possible to have both drives in the system, and dual boot by changing the "default boot device" in the bios (yes, I did this for a while, but I was going between an IDE drive and a SATA drive).

---

### Post by hellocharlie on 2007-01-26
This all depends on your BIOS settings. I have a similar setup because Windows tends to bork ext partitions inexplicably from time to time. Since my system's set up to boot from SATA 1, I can simply swap HDs to choose an OS... this isn't exactly graceful but I prefer leaving the XP disk completely out of the loop at most times (I've had too many troublesome issues with dual booting).

Additionally, it may interest you to know that XP cannot boot from a secondary drive... it's selfish enough to require installation on the primary.

Therefore, if you want to dual boot, I'd suggest installing the Ubuntu disk on SATA 2, then setting up the XP disk to manage your OS selection process (there are a number of options out there).

Hope this helps. ^^

---

### Post by AdyE on 2007-01-26
> **lyceum said:**
> Sorry, but yes. :(  You will have to start over with a new Ubuntu install.

Ahhhh, a pain but worth doing. I will do this later on after a cup of coffee.
Again, thank you for your help lyceum :-)

---

### Post by hellocharlie on 2007-01-26
You shouldn't need to reinstall to get this going.

If you're up to the challenge, you can try this solution:

[http://ask.metafilter.com/mefi/47609](http://ask.metafilter.com/mefi/47609)

which I've successfully managed on a couple of occasions.

---

### Post by AdyE on 2007-01-26
Thank you to all who have answered. It has certainly helped :-)
I will do a bit more reading before I continue.
Take care all :-)
AdyE

---

