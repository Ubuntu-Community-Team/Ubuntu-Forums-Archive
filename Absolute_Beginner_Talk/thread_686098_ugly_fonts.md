---
title: "ugly fonts"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-02
No offense, but the fonts are kinda ugly, especially in firefox, is there a way to fix it.  I have heard that the fedora fonts package is nice, and that MINT uses them are they available for ubuntu?  If so how do you get\install?

However, if I can just improve the appearance of the current ones that would be great as well.  I am staring at a 15.4 lcd laptop

---

### Post by RomeReactor on 2008-02-02
Hi. To improve the fonts in Firefox, search for **msttcorefonts** in Synaptic (System->Administration->Synaptic); or to install them from the terminal (Applications->Accessories->Terminal):
```
sudo aptitude install msttcorefonts
```

Also, instead of installing msttcorefonts you might want to install **ubuntu-restricted-extras**; this is a metapackage--an empty package that calls other packages for installation--that will provide you with multimedia codecs, Java, and the fonts. Search for it in Synaptic; or, form the terminal:
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by TechDragon on 2008-02-02
wow, thanks alot!

---

### Post by TechDragon on 2008-02-02
Once installed how do I select them?

---

### Post by RomeReactor on 2008-02-02
In Firefox go to 'Edit->Preferences', go to the 'Content' tab, and press the 'Advanced' button in the 'Fonts & Colors' section. Make sure the **Allow pages to choose their own fonts...** box is checked.

---

