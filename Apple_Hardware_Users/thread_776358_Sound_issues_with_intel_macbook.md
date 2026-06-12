---
title: "Sound issues with intel macbook"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by jake.keyes on 2008-04-30
Hi,

The sound on my macbook is very quiet and distorted, even when I plug the computer into external speakers. I know [others]("http://ubuntuforums.org/showthread.php?t=760875") have the same issue as well. I'm relatively new to Ubuntu and would appreciate any help.

Thanks,
Jake

---

### Post by cyberdork33 on 2008-04-30
> **jake.keyes said:**
> Hi,

The sound on my macbook is very quiet and distorted, even when I plug the computer into external speakers. I know [others]("http://ubuntuforums.org/showthread.php?t=760875") have the same issue as well. I'm relatively new to Ubuntu and would appreciate any help.

Thanks,
Jake
first, please run 'alsamixer' and try adjusting several channel levels.

---

### Post by jake.keyes on 2008-05-02
alsamixer did the trick. I unchecked the mute box under the 'surround' slider. Sound is loud and clear, as far as i can tell on these earbuds.

many thanks.

---

### Post by Jeratt on 2008-06-24
Perfect. Sound on my MacBook was not working at all as soon as I plugged it a speaker; The sound would just stop and not come out of either the internal or external speaker. Now it works perfectly. Here's instructions, for noobs (even though I'm one :) ).
> Open up a terminal window, under "Accessories" in the "Applications" menu. After it launches, type "alsamixer", and press enter. The display should change to a mixer interface. Use the right and left arrow keys to navagate to an item called "Surround". Now press "M". Press the escape key, and then close the terminal window. No need to restart, it should be working already if you have a speaker plugged in.

---

