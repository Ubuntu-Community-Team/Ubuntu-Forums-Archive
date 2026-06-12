---
title: "Mighty Mouse scroll doesn't work after suspend/resume"
date: 2008-03-07
forum: Apple Intel Users
---

### Post by Joel Duckworth on 2008-03-07
Hi I've got an Apple Mighty Mouse that I'm using with my MacBook (Santa Rosa). After I suspend and resume the mouse scroll stops working. 

I've tried to switch off and on the mouse but that doesn't help either. Has anyone got any ideas?

My xorg.conf show's this
```
Section "InputDevice"
        Identifier  "Apple Mouse"
        Driver      "evdev"
        Option     "SendCoreEvents" "true"
        Option "Name" "Apple Computer, Inc. Mighty Mouse"
        Option "HWHEELRelativeAxisButtons" "6 7"
        Option "Buttons" "8"
EndSection
```

---

### Post by cyberdork33 on 2008-03-08
Is this a bluetooth mouse?

---

### Post by Joel Duckworth on 2008-03-09
yep, it's bluetooth. The trackpad scrolling still works after resuming however.

---

### Post by cyberdork33 on 2008-03-09
for some reason the bluetooth stack doesn't resume properly. There is a bug report in launchpad about this. try restarting bluetooth and see if it works then:
```
sudo /etc/init.d/bluetooth restart
```

---

### Post by Joel Duckworth on 2008-03-09
thanks for the reply but unfortunately that didn't fix the issue. It's also interesting that the bluetooth manager doesn't list any devices but the mouse is working to a degree. It does sound like something with the bluetooth subsystem I agree. Got any other hints?

---

### Post by cyberdork33 on 2008-03-09
> **Joel Duckworth said:**
> thanks for the reply but unfortunately that didn't fix the issue. It's also interesting that the bluetooth manager doesn't list any devices but the mouse is working to a degree. It does sound like something with the bluetooth subsystem I agree. Got any other hints?
Nope, sorry. There was no resolution to this that I have seen. I would check for bug reports, or file a new one.

---

### Post by nicfagn on 2008-03-10
When bluetooth input is not screwed up as it is now for me in Hardy, the following command works for me:
```
sudo hid2hci --tohci
```

---

### Post by davidc73 on 2008-03-25
> **nicfagn said:**
> When bluetooth input is not screwed up as it is now for me in Hardy, the following command works for me:
```
sudo hid2hci --tohci
```

It worked for me. Thank you!

---

