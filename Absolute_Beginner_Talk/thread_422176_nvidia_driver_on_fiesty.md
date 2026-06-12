---
title: "nvidia driver on fiesty"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by seanmbarrett on 2007-04-24
i wouls like to activate the nvidia driver on my desktop, but it says it is restricted and  do not want ubuntu to crash. it is the ndvidia gforce fx 5200 video card. should it work with fiesty? i would like to play with beryl on my desktop, on my laptop it works great. my desktop is a dell 8100 p4 1.8 thanks for the help. sean

---

### Post by tchoklat on 2007-04-24
try this  

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by seanmbarrett on 2007-04-25
hi i tried it and my screen turned black after reboot. how can i switch back my drivers to the old thanks sean

---

### Post by Wee Nyaff on 2007-04-25
> **seanmbarrett said:**
> hi i tried it and my screen turned black after reboot. how can i switch back my drivers to the old thanks sean

Sean,

The way I do it is as follows:

On reboot hit the ESC button as soon as the GRUB appears.
Select the recovery mode option.
When it gets to the end of its thing, I type login which allows me to do just that with my name and then password.
Once it offers you the $ sign you could try this  "sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf"
minus the " "
reboot and hopefully you have your machine up and running.
Alan

---

