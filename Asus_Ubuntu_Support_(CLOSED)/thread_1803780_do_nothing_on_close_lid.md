---
title: "do nothing on close lid"
date: 2011-07-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by oldarney on 2011-07-13
Every time I close my lid, my system crashes. I used the i8042 workaround to fix my sleep problems. But I can't find a way to make the system do nothing when I close my lid. The best I get is blank screen, which crashes my system. Sleeping it kills my music, I don't want to do that.

I have an Asus UL30A-X4 presumably with a i8042 board.

I'm running with an SU7200 core duo, 4G's of ddr2 and an up to date  11.04 ubuntu.

Thanks in advance.

EDIT EDIT EDIT

In a terminal (Applications-->Accessories-->Terminal), type: gconf-editor

Navigate to apps-->gnome-power-manager-->buttons and set lid_ac and/or lid_battery to "nothing" (without the quotes).

---

### Post by mike0042 on 2012-02-28
For newer versions of Ubuntu (like 11.10) simply go to System Settings -> Power and adjust accordingly.

---

