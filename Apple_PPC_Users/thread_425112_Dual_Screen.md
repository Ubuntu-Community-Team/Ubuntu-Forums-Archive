---
title: "Dual Screen"
date: 2007-04-27
forum: Apple PPC Users
---

### Post by fergie4000` on 2007-04-27
Ok, first off, hi. Very nice OS. I have been using it for a few weeks. I have recently tried to use my iBook G4 1.2GHz with an external screen and have found no way to set it up. Is it even possible? And if is then how would I go about setting it up?

Thanks,

---

### Post by ssam on 2007-04-28
on the iBooks video out port is limited to mirroring the main display by the firmware. I think it might be possible to change the firmware, but it could break the video card, and i dont know where you get a unofficial  firmware from.

if mirroring is ok for you then it should be possible to do. currently it requires that you manually edit the X configuration. (soon X will auto configure).

what graphics card do you have? the command

```

lspci

```

should tell you

---

### Post by fergie4000` on 2007-05-01
i don't have access to it at the moment but the chip on the mainboard is a radeon 9200 or 9250 if memory (and google) serve me correctly

*EDIT*
mirroring is fine as i just intend to use the external display as the only display so a mirror would suit that well

---

### Post by stmiller on 2007-05-01
Check this out. I just got mirroring to work on my TiBook. You might have to alter the modes that you want to use.

[http://ubuntuforums.org/showpost.php?p=2576099&postcount=34](http://ubuntuforums.org/showpost.php?p=2576099&postcount=34)

---

