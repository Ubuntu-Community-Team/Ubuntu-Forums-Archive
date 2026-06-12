---
title: "weird touchpad issue - Edgy"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by osouji on 2007-03-22
Ok, so I have this really weird issue that I don't know how to resolve.

It all started with my desire to disable mouse tapping on the touchpad of my sony vaio vgn-c190g in Edgy.

I have installed gsynaptics and added gsynaptics-init to my startup. SHMConfig "true" is set on in xorg.conf

Fine, fine fine. Hit ctrl-alt-backspace and everything works..

Great right? Except for how upon restart of the computer - everything doesn't work again. Tapping is on, synclient allegedly still works, gsynaptics-init is in startup, gsynaptics starts up ok and notes that tapping should be disabled.

Also, manually doing synclient tapbutton1=0 or maxtaptime=0 or whatever else doesn't seem to affect anything.

Then magically - by doing ctrl-alt-backspace, everything works again, just as it should and tapping is disabled.

Has anyone else had this problem? I really don't want to have to restart X every single time I reboot. Granted I don't reboot that often but still. It's almost as if a reboot loads a different xorg.conf or loads different settings or something.... I didn't have this problem with Dapper.

Thanks. I apologize if this discussion exists in a thread elsewhere that I haven't found.

---

