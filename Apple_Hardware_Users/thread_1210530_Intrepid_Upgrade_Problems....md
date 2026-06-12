---
title: "Intrepid Upgrade Problems..."
date: 2009-07-11
forum: Apple Hardware Users
---

### Post by Breath! on 2009-07-11
Hello, everyone! 

After trying many a times to upgrade to Intrepid, I always get the same error. After the intial restart Intrepid fails to find my root partition. 

The error is along the lines of:Timed out waiting for root partition. /dev/hda3 doesn't exist.

I tried loading in using a Dapper live cd, but when I tried to mount the /dev/hda3, Nautilus  wouldn't mount it. 

I'm going to try to upgrade again later today so I will  be able to post the specific error- if it happens- then.

---

### Post by Breath! on 2009-07-11
Oh, and by the way, I'm on an iBook g3 @ 600mhz w/ 384MB of RAM using Yaboot 1.3.13

---

### Post by j.stam.84 on 2009-07-14
what does 'sudo fdisk -l /dev/hda' give you ? Another possibility is that this is related to a change in the kernel. I don't know when exactly, but at some point they changed to libata for HD access. If that's the case, your drive should be accesible through /dev/sda instead of /dev/hda (if the Dapper version doesn't work, scratch this last comment ;))

---

