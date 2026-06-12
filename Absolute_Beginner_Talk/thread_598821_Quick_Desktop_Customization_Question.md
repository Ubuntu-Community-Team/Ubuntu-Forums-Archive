---
title: "Quick Desktop Customization Question"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-10-31
How would I change it so there is no CD-ROM icon on my desktop? Thanks for your help.

---

### Post by ThrobbingBrain66 on 2007-10-31
Hit Alt+F2

Navigate to apps > nautilus > desktop

Uncheck the 'volumes_visible' key

---

### Post by 449 on 2007-10-31
> **ThrobbingBrain66 said:**
> Hit Alt+F2

Navigate to apps > nautilus > desktop

Uncheck the 'volumes_visible' key

I'm still very new to Linux/Ubuntu and still not very familiar with navigating. Could you "spell it out" for me? Thanks again.

---

### Post by spec-chum on 2007-10-31
ThrobbingBrain66 missed off a line from his post.

1. Hit Alt+F2

2. Type gconf-editor in the Run Application dialog that pops up.

3. Navigate in the editor to apps > nautilus > desktop

4. Untick the volumes_visible checkbox

---

### Post by alwiap on 2007-10-31
1. click alt+F2 
2. type in 'gconf-editor' and click enter, the "Configuration Editor" will come up
3. in the left panel, click the 'apps' folder to expand 
4. find nautilus there and expand nautilus
5. click the folder 'desktop' in nautilus
6. look at the right panel, and click on the lowest value, 'volumes_visible', and uncheck the box.

:)

---

### Post by ThrobbingBrain66 on 2007-10-31
> **spec-chum said:**
> ThrobbingBrain66 missed off a line from his post.

1. Hit Alt+F2

2. Type gconf-editor in the Run Application dialog that pops up.

3. Navigate in the editor to apps > nautilus > desktop

4. Untick the volumes_visible checkbox

Thanks for catching that for me :)

---

