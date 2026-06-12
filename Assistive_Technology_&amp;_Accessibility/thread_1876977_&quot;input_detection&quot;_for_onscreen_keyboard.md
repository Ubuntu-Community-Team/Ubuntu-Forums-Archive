---
title: "&quot;input detection&quot; for onscreen keyboard"
date: 2011-11-07
forum: Assistive Technology &amp; Accessibility
---

### Post by dekkelkamp on 2011-11-07
> Hello all,

I had Ubuntu 11.10 with gnome shell installed on my WeTab tablet, it worked really well with the onscreen keyboard (Caribou). Wherever i could input text the onscreen keyboard showed. But because the full Ubuntu desktop with gnome shell was too heavy for use on my tablet i used the minimal installation of Ubuntu to create a lighter installation. I installed only gnome-core for the gnome desktop and some other applications.

The problem now is that the onscreen keyboard does not always show when i click in a textbox. With the full installation the OSK even showed when i entered a textbox on a webpage. Now the keyboard only shows when i enter a textbox in a GTK3 application.

My question is: Wich package should i install to get the 'input detection' for the onscreen keyboard?

ANSWER: I found the answer after comparing installed packages on my laptop (full installation of ubuntu) and my tablet (minimal installation), and found out that the package libatk-adaptor was needed for the keyboard to show up with all textboxes.

---

