---
title: "imac alsa overdrive"
date: 2004-10-17
forum: Apple PPC Users
---

### Post by stereo on 2004-10-17
it's much too loud. even if its one singel point over zero. any ideas?

---

### Post by stereo on 2004-10-18
i looked a bit around and found this.
setmixer -V 
gives
root@ubu:/home/stereo # setmixer -V
    vol - 0,0
speaker - 0,0
   line - 100
    mic - 100
     cd - 100
  igain - 0,0

but i can't change the line-output down to 50. the mixer seems dead in that position 
setmixer vol -50
does it, but
setmixer line -50
does nothing

it's a pitty, anybody with similar problems?
i have an imac 350 slot-loading blueberry

thanks
stereo

---

