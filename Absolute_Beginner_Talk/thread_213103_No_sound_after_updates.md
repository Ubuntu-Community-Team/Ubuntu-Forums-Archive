---
title: "No sound after updates"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by crossev on 2006-07-10
All,


I awoke today to having lost my sound on my Ubuntu dapper installation.  I believe it happened when I installed some dapper updates.  

I tries the following link: [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
and that did not work.

When I typed in aplay -l it showed that my nvidia sound card. 

card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I checked alasmixer and unmuted everything and still no sound.  Not sure what else to try.  Any help or links will be great.



Peace,

---

### Post by crossev on 2006-07-11
I am pretty sure that the updates are the reason why my sound is no longer working.  Is it possible to roll back my system to pre updating.  If so how would I go about doing this.  I was thinking of looking in the /var/log folder but I am unsure of which file to look at to determine what the updates were.




Thanks,

---

### Post by inf0c0m on 2006-07-11
> **crossev said:**
> I am pretty sure that the updates are the reason why my sound is no longer working.  Is it possible to roll back my system to pre updating.  If so how would I go about doing this.  I was thinking of looking in the /var/log folder but I am unsure of which file to look at to determine what the updates were.




Thanks,

id check to see if esd is running (if your in gnome). just do a 

> ps aux |grep esd

this is the gnome sound controller software. it was running on my pc, and i just had to stop it.

---

### Post by crossev on 2006-07-12
Thanks for the reply.  I finally got my sound working again following these instructions.


"Finally, I found the answer here:

[http://www.ubuntuforums.org/showthread.php?t=153752&highlight=touchpad+sony](http://www.ubuntuforums.org/showthread.php?t=153752&highlight=touchpad+sony).

The crucial thing is to enable everything in alsamixer EXCEPT "external amplifier." (I had to turn off microphone too, to stop feedback)."


Thanks

---

