---
title: "Appearance preference dialog taking 100% CPU"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by DCboi on 2007-10-19
Hello, 

I upgraded from Feisty to Gutsy today and now the "Appearance preference" dialog is taking 100% CPU. It is also not possible to select different items on the dialog. 

Is it just me or can anyone else reproduce it ?

Update : 100% CPU seems to be bit of exaggeration but still the dialog takes up fair share of CPU. And the particular process causing it is gnome-appearance-properties.

---

### Post by DCboi on 2007-10-19
Problem solved after removing gtk-qt-engine package.

---

### Post by marriedman on 2007-12-25
I know this is late, but I can confirm this fixed mine as well. Thanks for posting your solution!

---

### Post by Shuri on 2008-02-25
Even later still...

This fixed my problem as well.Many thanks to the OP for sharing the solution. :)

---

### Post by jfernyhough on 2008-03-27
I found the same problem just recently with Hardy (after setting the GTK theme with switch2 in fluxbox). I needed to delete the .gtkrc* files in my home; apparently appearance manager keeps the settings somewhere else and it conflicts.

---

### Post by Che.SSL on 2008-06-06
These solutions didn't work for me, unfortunately...

---

