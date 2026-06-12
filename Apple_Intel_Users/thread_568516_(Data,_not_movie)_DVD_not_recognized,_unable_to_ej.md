---
title: "(Data, not movie) DVD not recognized, unable to eject"
date: 2007-10-05
forum: Apple Intel Users
---

### Post by oneoverzero on 2007-10-05
I am single booting Ubuntu Gutsy on my gen 2 Macbook, overall i've been able to get everything to work, even if it needed some persuading.  

However, about a half hour ago I put a DVD-R in that had some backed up data on it, and the computer did nothing.  
I hit the eject button, nothing.  
I went into the command line and tried eject, and got the following errors : 
[FONT="Courier New"]eject: tried to use `/dev/scd0' as device name but it is no block device
eject: unable to find or open device for: `cdrom'[/FONT]
I then thought maybe it was somehow mounted despite it not being listed anywhere that I can find, so I did umount /dev/cdrom, and umount /dev/scd0.  it told me that neither were mounted, (mount told me nether existed). 

I've tried sudo all of these, just in the off chance that it's really a permssions issue and its not telling me.... I've also tried several times after restarting...

I don't so much care that it's not being recognized, more that its not ejecting (thats one issue with slot-loaders, i cant manually do it when the comp is off)... (though help for both is appreciated)

I love linux, but this has got me stumped.

---

### Post by alephsmith on 2007-10-05
```
sudo modprobe ide_generic
```

---

