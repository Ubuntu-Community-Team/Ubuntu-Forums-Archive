---
title: "RAID support in UBUNTU?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by gsnider@nyc.rr.com on 2006-06-10
Does UBUNTU (any version) support/allow on a 64 bit machine which uses RAID 0 ?? If possible, please respond via e-mail. [email]gsnider@nyc.rr.com[/email]
Thank you all.

---

### Post by newhpzzw on 2006-06-11
I am so sorry to say that the Ubuntu support the HARD RAID only,you will find your raid display two disk when you install the Ubuntu if you just have the BIOS raid or fakeraid such as INTEL&#12289;NForce and VIA.and you can not install if your raid like this.

---

### Post by wombat20 on 2006-06-18
Not true.

I'm not sure about the 64-bit kernel, but if you use the i386 one (which will work on AMD64) then it should support softRAID.
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

That said, I'm still battling to work out how to partition it correctly, I'm wondering if I'm not supposed to create partitions on the new RAID0 device that appears, but on the two primary drives I made it from... should be simple...

---

### Post by blkish on 2006-06-18
i'm not sure of the specifics of x64 support on this (though i would expect it to be included) but you should find software RAID works fine for your situation.

you might like to post in Server Talk where there will be more people who can clarify this.

---

