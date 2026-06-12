---
title: "Still haven't been able to import former Firefox settings"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-11
Hey folks. I've tried and tried and tried, but I still can't figure out what to do with the settings I backed up from my former Firefox when I upgraded to 2.0 . . .now I have 2.0.1, still have the folder with the settings, and I want them back! ~LOL~ I've tried replacing the actual files in the .mozilla/firefox folder with the same file in backup, but that does nothing . . .any thoughts?

---

### Post by tweedledee on 2007-01-13
> **CheshireMac said:**
> Hey folks. I've tried and tried and tried, but I still can't figure out what to do with the settings I backed up from my former Firefox when I upgraded to 2.0 . . .now I have 2.0.1, still have the folder with the settings, and I want them back! ~LOL~ I've tried replacing the actual files in the .mozilla/firefox folder with the same file in backup, but that does nothing . . .any thoughts?

What works for me is to complete delete the ~/.mozilla folder, and just copy in the old one.  Firefox then seems to find the old settings.

---

### Post by ComplexNumber on 2007-01-13
> **tweedledee said:**
> What works for me is to complete delete the ~/.mozilla folder, and just copy in the old one.  Firefox then seems to find the old settings.
thats what i've done for the last 8-10 reinstalls. 

**CheshireCat**
BEFORE you run the new firefox, get your old settings and put them in your home directory. the settings are always stored in .mozilla irectory. the reason i emphasise "before" is because when you run firefox for the first time it creates the .mozilla directory.
actually, you don't need to move your settings anywhere. 
you need to restart firefox for any changes to come into effect.

---

### Post by CheshireMac on 2007-01-13
> **ComplexNumber said:**
> thats what i've done for the last 8-10 reinstalls. 

**CheshireCat**
BEFORE you run the new firefox, get your old settings and put them in your home directory. the settings are always stored in .mozilla irectory. the reason i emphasise "before" is because when you run firefox for the first time it creates the .mozilla directory.
actually, you don't need to move your settings anywhere. 
you need to restart firefox for any changes to come into effect.

It was already upgraded . . .It told me to backup the settings, but didn't tell me what to do with them . . .now I have the new Firefox, and no clue what to do with the old folder. ~LOL~ I'll try the first reply and see what happens.

---

### Post by ComplexNumber on 2007-01-13
> **CheshireMac said:**
> It was already upgraded . . .It told me to backup the settings, but didn't tell me what to do with them . . .now I have the new Firefox, and no clue what to do with the old folder. ~LOL~ I'll try the first reply and see what happens.
just create a directory in your home folder such as 'Backups' or 'Documents'. then before you run the new firefox, copy(not move) your old settings to .mozilla.

---

