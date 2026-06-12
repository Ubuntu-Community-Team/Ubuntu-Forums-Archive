---
title: "Making EPS with preview from in the Gimp?"
date: 2007-03-22
forum: Art &amp; Design
---

### Post by jazzgossen on 2007-03-22
I need to make save a few images as EPS files with previews. There is an option to create a preview in the Gimp's save dialog, but it doesn't seem to work. I can save ordinary EPS files allright, but when I have the "preview" box checked, the plugin fails to save the file. Does anybody know of a workaround?

---

### Post by rossdh on 2007-03-27
I get this problem as well. I could not find a workaround for it. Seems they need to fix the plugin.

EDIT: Here is a way to add the preview manually. 

1. Install EPS tool using synaptic package manager.
2. Save your EPS without the preview.
3. At the command line type: epstool -t6p file.eps file.eps
4. Your image should now have a preview.

---

