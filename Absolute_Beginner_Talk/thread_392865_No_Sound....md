---
title: "No Sound..."
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Tyscorp on 2007-03-25
When I first used the Live CD, the sound worked perfectly. I thought "Ooo I like it" so I installed Ubuntu 6.06. I have had it installed for a while now and ever since I installed it, the sound has not worked. I have two sound cards. An on-board and a PCI one. (Intel 82801BA-ICH2 and C-Media PCI CMI8738-MC6) None of them work, and when I try to change the default one from the Intel to the C-Media, it always swiches back to the Intel. Please help as I have no idea what to do...

Edit: Its not on mute either :P

Edit: Dont worry... It randomly started working...

---

### Post by lamalex on 2007-03-25
add this to /etc/asound.conf

```

pcm.!default {
        type hw
        card 0
        }

        ctl.!default {
        type hw           
        card 0
        }

```
where card 0 is the corresponding card you want from [code]cat /proc/asound/cards

---

