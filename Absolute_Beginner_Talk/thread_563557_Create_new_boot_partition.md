---
title: "Create new boot partition"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-09-30
Hi!
I want to increase the size of my /boot partition, but I'm not able to since there's no free space after it. So I just wonder if I can create a new, larger /boot, copy the contents of the old boot and then remove the old partition. Would this work, or would I f**k up the whole thing?

Thanks! Joakim

---

### Post by indytim on 2007-09-30
Why don't you just shrink the adjoinging partition size?  Use the newly created unallocated space to "grow" your boot partition.  Advisory : if you go this route do it in discreet steps (don't do it all in one chained operation).

IndyTim

---

### Post by Joakim Stokland on 2007-09-30
Thanks, I will try that next time ;) I presumed it would break my system, but I had to try. I thought of upgrading to Gutsy you see, but I figured I would rather wipe out my drive and start fresh :)
Thanks anyway :) Oh, and just for the record - I tried, and yes, it DID break my system! ;)

---

