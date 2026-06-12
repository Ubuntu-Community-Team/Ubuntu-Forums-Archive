---
title: "Music Player hangs PC"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by theking2 on 2006-05-01
Was listening to internet radio with out a problem all day without a problem. 

After an update my pc required a reboot (linux nerds let me believe I *never* have to reboot anymore ) After the reboot the Media Player froze my system (again, I thought hanging was a thing of the microsoft-past)

Well I stop whining now. 

How do I revive my musicplayer? Im using a snd-sb16 driver. And ALSA, or OOS. Not sure anymore.

---

### Post by theking2 on 2006-05-01
OK, it was esd and I had to redo modprobe snd-sb16. So this is what I did:
 open Terminal (Command Line)
 do a ```
sudo modprobe snd-sb16
```
 do a ```
esd
```
 close the Terminal
set the Multimedia Input Selector to use "ESD - Enlightenment Sound Deamon" as "default input sink". 
And Rythmbox Media Player rocks and rolls again.

When I touch the "Default Source" Test button my system "freezes" again and I have to do a hard reset, so I don't do that anymore.

---

