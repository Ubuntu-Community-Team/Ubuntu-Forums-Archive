---
title: "Urgent Help ASAP Please Ubuntu boot hangs!!!!!"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by c0reyf on 2007-05-22
I was working on configuring VNC and trying to get it to work on my laptop and my desktop. I made some edits under the

System->Administration->Login Screen Setup

I was reading on the forums here and tweaking different settings on both boxes to make them the same and now I get a constant spinning cursor and neither box will boot. My laptop is my main machine and I need to get it up ASAP. I can get a root command line but I don't know what to do or check for. Any help is greatly appreciated.

Please let me know If this is best suited for another Subforum or even site.

---

### Post by Kobalt on 2007-05-22
If you can access a command line then you could try to reconfigure the gdm for example (if that's what you tweaked) : ```
sudo dpkg-reconfigure gdm
```

---

### Post by c0reyf on 2007-05-22
sudo dpkg-reconfigure gdm
* Reloading GNOME Display Manager configuration...
* Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

shutdown -r now

No change yet, still hanging. Anymore ideas.

---

### Post by Kobalt on 2007-05-22
> **c0reyf said:**
> invoke-rc.d: initscript gdm, action "reload" failed.
It doesn't seem that good... Can you remember what you actually changed in the GDM to get to this point ?
Additionaly I'd try to purge gdm then reinstall it : ```
sudo /etc/init.d/gdm stop
sudo apt-get remove --purge gdm
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

---

### Post by c0reyf on 2007-05-22
WOW!!! Worked instantly, both of my boxes are back to normal. I very much do appreciate your thoughts on this Kobalt. 

Thanks again

---

