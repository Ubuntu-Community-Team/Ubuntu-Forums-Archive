---
title: "macbook + Ubuntu 7.04 BT won't work"
date: 2007-05-20
forum: Apple Intel Users
---

### Post by bendrops on 2007-05-20
Hey, I've installed ubuntu 7.04 on my macbook
Now, I got almost everything to work perfectly except for two things:
Bluetooth
Touchpad - two finger scrolling

Now Iv'e installed all the bluetooth packeges and I have the little Bt symbol but I can't scan for devices, I don't even have that option. This means I can't connect my Mighty mouse to my Mac. Now i'm a novice linux user so be gentle, I'm just starting out so be gentle.

Also is there a possible way to get two finger scrolling and two finger right click?

thenks a lot, Ben

---

### Post by James_M on 2007-05-20
I can't answer the part about bluetooth because I haven't bothered to get it working in Ubuntu (i can use OS X for that), but your trackpad issues can be solved by downloading either qsynaptics or Gsynaptics (Gsynaptics got closer to working for me, so I recommend that one.).  Once you've got one of those installed (you can get them from the synaptic package manager repos), you need to edit your xorg.conf file.  type this into a command prompt:
```
sudo gedit /etc/X11/xorg.conf
```

add this line to the "synaptics" touchpad section.

```
Option "SHMConfig" "true"
```

now there is a slight chance you won't be able to edit that section beccause it's not there.  This was the case for me.  I haven't quite figured it out yet, but if I come across anything, i'll stick it in this thread.  If you do have a "synaptics" section in there, this method will work perfectly for you.

---

### Post by bendrops on 2007-05-20
installed Gsynaptics and I added the line but nothing happens  ](*,)
It just added a touchpad section to system prefrences but I can't control right click or two finger scrolling from there

---

### Post by bendrops on 2007-05-21
Okay got the touchpad working by adding the right commands in the xorg.conf file
Had to figure that one out myself, assume I know nothing....
still waiting on how to pair the mighty mouse....

---

### Post by nicfagn on 2007-06-01
> **bendrops said:**
> still waiting on how to pair the mighty mouse....
I paired my mighty mouse following the instructions on this [page.]("https://help.ubuntu.com/community/BluetoothSetup")

Before doing so, I had to disable the bluetooth service to get my wireless mouse and keyboard to work, but in that way the scroll wheel didn't work.
Letting the bluetooth service manage the mouse allows to use all its capabilities.

Based on my experimentation, a simpler way to find the mouse and/or keyboard bluetooth addresses is to use the System Profiler application on Mac OS X.

Bye
Nicola

---

