---
title: "Panel behind windows?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by swayer_77 on 2007-03-09
Is there a way to make the panel on the top (the one with firefox) so that it goes behind windows instead of taking up space (see screenshot)

I saw the option where it hides it, but whenever I move my mouse up the panel pops out and its annoying. Also, the panel is still a little bit visible on the screen, which is also annoying :P

---

### Post by aidanr on 2007-03-09
theres an option in gconf to make the panel completely hidden

gconf-editor
/apps/panel/toplevels/top_panel_screen0/auto_hide_size <- change to 0

i don't know if there is a way to set the panel below windows

---

