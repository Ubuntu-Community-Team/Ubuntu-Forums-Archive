---
title: "fonts problem firefox"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2008-01-12
Hi,

my firefox browser seems to have a font problem. The screen is generally readable, but some parts of it are almost impossible to read (see the top right part where the search's time and "Showing results 1to 25.." I think the spacing between characters is off...

Thinking beyond Firefox (the whole OS) could you tell me, 1) how to re-step the fonts specification to the default Ubuntu 7.10, b) how to set fonts to mimic (I am afraid I would have to say it) Windows' ?. I think having the same fonts as Windows, could be a good starting point to start customizing....

Thanks,
D.

---

### Post by polmir on 2008-01-12
```
sudo apt-get install msttcorefonts
```

after instalation go to Preference of Firefox

---

### Post by RomeReactor on 2008-01-12
Hi. Also, in Firefox try going to 'Edit->Preferences' and in 'Fonts & Colors' press the 'Advanced...' button; make sure the box labeled "Allow pages to choose their own font..." is checked.

If this doesn't ehlp, try deleting Firefox's preferences: Close Firefox, open a terminal (Applications->Accessories->Terminal) and run the following:
```
rm ~/.mozilla/firefox/*.default/prefs.js
```
Then open Firefox again and see if the problem persists.

---

