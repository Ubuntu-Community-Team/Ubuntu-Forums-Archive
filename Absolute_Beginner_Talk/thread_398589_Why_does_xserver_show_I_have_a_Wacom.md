---
title: "Why does xserver show I have a Wacom"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-04-01
When I don't have one of these?

---

### Post by pppetter on 2007-04-01
Where does xserver tell you that?

---

### Post by captgadget on 2007-04-01
when I do a sudo nano -r /etc/X11/org.conf and go through it it shows as a device in there.

---

### Post by tseliot on 2007-04-01
That section of your xorg.conf will be used if you plug a Wacom tablet into your computer, otherwise it won't do anything.

---

### Post by captgadget on 2007-04-01
OK, thanks

---

