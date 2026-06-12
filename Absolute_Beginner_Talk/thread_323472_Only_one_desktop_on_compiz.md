---
title: "Only one desktop on compiz"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by arochester on 2006-12-22
I installed compiz following the  "Unofficial Ubuntu 6.10 (Edgy Eft) Starter Guide" using "How to install compiz-freedesktop without XGL / AIGLX utilising the latest Nvidia BETA drivers"

When I activate GL desktop I only have one desktop available, no cube, no transition. When I turn off the GL desktop I have four desktops available.  

Am I doing something wrong?

---

### Post by darrenm on 2006-12-22
I didn't realise Compiz was even still developed. Everyones using Beryl these days.

Just add ```
deb http://ubuntu.beryl-project.org/ edgy main-edgy
``` to your /etc/apt/sources.list then
```
sudo apt-get update && sudo apt-get install beryl* emerald*
beryl-manager
```

---

### Post by arochester on 2006-12-22
Thanks for the reply. Had Beryll. Too many whistles and bells!

Found solution. In Compiz Preferences >Workspaces just push image to edge of screen Compiz only has one visible desktop on the bar, but can change anyway

---

