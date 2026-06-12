---
title: "shut down glitches"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by chang3andrew on 2008-03-01
Hey everyone,

I've been having issues with ubuntu shutting down. When I am finished doing a lot of work with the computer, and when I order it to shut down, it gets stuck with a blank screen and a roaring hard drive. How can I fix this, and will hardy heron make something change so i won't have to face these issues again?

---

### Post by forrestcupp on 2008-03-01
Do you happen to have an ATI card and be using drivers before the latest 8.2 ones?  If so, uninstall those ATI drivers and install the latest ones via [Envy](http://albertomilone.com/nvidia_scripts1.html).  The latest ATI drivers take care of that problem.

If that is not your problem, you may need to give more info.

---

### Post by chang3andrew on 2008-03-02
I'm on a Dell 700 m, integrated graphics. I think when I unplug my notebook and when there isn't so many things in operation, the computer won't have so much to worry about, but when it's busy with things it has trouble shutting down.

---

### Post by erginemr on 2008-03-02
It seems a memory / swap issue to me. How much memory do you have? What is the outcome of:
```
sudo fdisk -l
```
and 
```
free
```

Can you please write "top" in a terminal and post its screenshot here?

---

