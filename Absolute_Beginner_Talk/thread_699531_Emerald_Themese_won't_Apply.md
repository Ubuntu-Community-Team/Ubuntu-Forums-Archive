---
title: "Emerald Themese won't Apply"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by kittykatmeowmeow on 2008-02-17
I am trying to apply an emerald theme and it doesn't give me an option to apply.  I have already installed the CCSM...but anything I choose on there...it doesn't do anything.  I am so new to this and spending so much time on trying to figure it out by myself...Please help.

Thanks

---

### Post by jan quark on 2008-02-17
asking pre-cautiously

you have installed emerald, do you?

---

### Post by kittykatmeowmeow on 2008-02-17
As far as I know yes...I installed it from the SPM

---

### Post by jan quark on 2008-02-17
Near the upper-right corner of the Emerald Theme Manager window, there's an Import button. Click on that, then select a theme you've downloaded. The new theme should show up at the bottom of the themes list.

---

### Post by kittykatmeowmeow on 2008-02-17
Yep!  I've done that and I see the themes I have downloaded.  now....how to I apply it?  There isn't an apply button.

---

### Post by gotee12 on 2008-02-17
All you have to do is click on the theme and it (should) apply automatically.

Though my Emerald install is borked up and the only way for me to apply the new theme is to fully restart X.

Have you tried selecting a theme, closing the Emerald manager, and then logging out and back in to your machine?

---

### Post by kittykatmeowmeow on 2008-02-17
I clicked on the theme in Emerald Theme Manager, exited it, logged out and logged back in.  I still see the fabulous brown UBUNTU theme.

---

### Post by gotee12 on 2008-02-17
open a command line and type

```
sudo emerald --replace
```

---

### Post by Tuning_In on 2008-02-17
Hi:)

I'm no expert, but this procedure works for me. 

1. After installing compizConfig settings manager go to preferences and set the "backend" section to "Flat-file configuration Backend".Then create a new profile. Do that by clicking the "+" icon and type a profile name(call it whatever you want) in the "profile" section.

2. Next click "back" and go to "window decoration" in the "effects" section. Then type "emerald" in the "Command" section. Click "back" and close the manager.

3. Open the emerald theme manger and select the theme you want. Then close.

4. Then click ALT+F2 and type "emerald --replace". 

I don't know if this is the best way to do it or the right way, but maybe it can help you get things working. Excuse my poor English.

---

### Post by kittykatmeowmeow on 2008-02-17
I did all of those steps and it still didn't work :( Any other suggestions??

---

### Post by Tuning_In on 2008-02-17
As mention earlier in the thread, try to log out and then back in. After that ALT+F2 and type
emerald --replace

Edit: Also you can read this great [ blog]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty") by Forlong for troubleshooting and configureing.

---

### Post by kittykatmeowmeow on 2008-02-18
Thank you!

---

