---
title: "How did they do that!?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Jshaw on 2007-11-12
Please visit the following youtube vid:
[http://www.youtube.com/watch?v=dPqJWE1DEoI]("http://www.youtube.com/watch?v=dPqJWE1DEoI")

Now when the user opens and closes windows, they sparkle when they come up, and turn into some sort of pane, or blind when they close. How is this done?

---

### Post by geirha on 2007-11-12
```
sudo aptitude install compizconfig-settings-manager
```

Then System->Preferences->Apperance and try out the options under Visual Effects.

---

### Post by santiagoward2000 on 2007-11-12
It's just the "Burn" animation using randomly colored fire.

---

### Post by ErusGuleilmus on 2007-11-12
I am not seeing this "Burn" option anywhere.

---

### Post by santiagoward2000 on 2007-11-12
> **ErusGuleilmus said:**
> I am not seeing this "Burn" option anywhere.

Open CompizConfig Settings Manager, go to "Animations" and under the "Close Animation" tab, select the first one from the list (type=normal), click on "Edit" and select "Burn" in the "Close Effect" dropdown menu. Repeat the same under the "Open Animation" tab.
Then, to get those colors, go to the "Effect Settings" tab. Under "Fire", check the "Randomly Colored Fire" box.
That should do it. Just ask if not!

---

