---
title: "Small and Big Problems..."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by 4Real on 2007-07-26
Yay i got ubuntu but heres a couple i things i cant do or dont have...

1. No sound 
2. Screen Resolution Is Big 
3. When I turn on the computer it asks me several different options for loading screens... How do i get rid of that... I hear people say its called GRUB...

---

### Post by sailor2001 on 2007-07-26
1st 2 things.. go to system / preferences.......for speedier startup..........

sudo gedit /boot/grub/menu.lst  and you will see a timing setup for starting. reduce the seconds to what you want.

---

### Post by 4Real on 2007-07-26
sudo gedit /boot/grub/menu.lst  - where do i get that

---

### Post by fredj on 2007-07-26
Open a terminal from the Applications->Accessories Menu. Then type your sudo gedit ... command.

---

