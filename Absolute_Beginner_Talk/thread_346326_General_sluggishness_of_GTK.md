---
title: "General sluggishness of GTK"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by occams_beard on 2007-01-25
I really like Gnome, but one major let down is the sluggish performance of GTK. For instance, scrolling in tree components leaves little trails behind, resizing windows feels laggy, and moving a window on top of another leaves gray rectangles behind. It's like someone spilled molasses all over my desktop. Applications with a complex layout, such as Eclipse, are a real pain to use because of this.

From what I understand, this is due to the way GTK implements double buffering within the widgets. 

Is there any way to remedy this, or at least improve it a little bit?

---

### Post by Duppy on 2007-01-25
Have you got the latest drivers for your graphics card?

---

### Post by occams_beard on 2007-01-25
Yes I do. I'm running the NVida 1.0-9746 drivers on a GeForce FX 5200

---

### Post by Tenicus on 2007-01-25
I had this problem as well
do:
sudo dpkg-reconfigre -xserver-xorg
when it asks for "use kernel framebuffer interface?"
say YES

this worked for me at least.

---

### Post by occams_beard on 2007-01-25
Tenicus,

Thanks for the suggestion. I gave it a try, but didn't notice any appreciable difference. Sadly, it still seemed just as sluggish with the UseFBDev flag set to true.

---

