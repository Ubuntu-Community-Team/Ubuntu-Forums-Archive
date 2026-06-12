---
title: "No Sound - SB Live EMU10k1"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by cpharvey on 2005-12-08
So here's the wierd thing. When the login screen comes up I hear the drumbeat sound. Also when I use the Live CD I get sound perfectly. When I login as me to the system I have no sound and a red x up in the top right for the sound system. In fact it complains about volume control not finding any elements to control.

If I go to Multi-Media systems selector and try any of the options I get an error "Failed to construct test pipepline for xxx etc"

If I go to prefs/sound, there is no Default sound card and I can't select one.

But.. all this and I hear sound when the login screen comes up! weird.... anyone have the same?

---

### Post by tay on 2005-12-09
i hav'nt even got that drum beat on my emachine yet.

---

### Post by cpharvey on 2005-12-09
Sorry to hear that. To me it says that the system knows about the card and can use it, but something about my profile says I can't.

---

### Post by cpharvey on 2005-12-09
Fixed it.. I needed to add my users to the 'audio' group under /etc/group

---

