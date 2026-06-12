---
title: "[SOLVED] Slightly marred images, how to downgrade libmagick9?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-07-11
I updated Feisty yesterday and ever since then there's been some image distortion (only within Firefox, rendering certain images) and I think it's related to the libmagick9 patch yesterday.

How do I downgrade libmagick9?  I tried to remove it but there are some dependencies (rss-glx, ubuntu-desktop) that would also need to be removed.

Edit: I've included a screenshot comparing Firefox (left) and Opera (right) where you can see how the image doesn't line up.

---

### Post by AncientPC on 2007-07-11
Never mind I found the source of the problem by running Firefox in safe mode.  The Add-On Image Zoom was working fine until libmagick9 was updated.  Uninstalling the Add-On has fixed everything.

---

