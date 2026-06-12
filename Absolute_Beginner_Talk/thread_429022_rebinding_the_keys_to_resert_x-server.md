---
title: "rebinding the keys to resert x-server"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Spreggo on 2007-04-30
I want to rebind the keys (shift+backspace) to something else. It isn't under the keyboard shortcut options, so how might I go about changing it? Thanks.

---

### Post by Pobega on 2007-04-30
I think the keybind you're talking about is Ctrl+Alt+Backspace, not Shift+Backspace. And I don't think it can be changed, as far as I know it's something that's built directly into X.

---

### Post by Spreggo on 2007-04-30
well, my copy of feisty definitely dumps and returns to the login screen when you hit shift+backspace. I reall want to change it because I accidentally hit it all the time (Don't ask how)

---

### Post by Spreggo on 2007-04-30
[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/32857](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/32857)

okay this was the problem, anyone else with this issue follow the instructions on adding that bit to the startup apps. It cured me anyways.

---

