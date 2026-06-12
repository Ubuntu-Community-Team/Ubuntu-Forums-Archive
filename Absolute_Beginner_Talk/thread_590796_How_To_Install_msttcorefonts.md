---
title: "How To Install msttcorefonts?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by dswhite85 on 2007-10-25
How exactly do I do that so I can view websites more accurately? I've downloaded the Ubuntu Restricted Extras from Add/Remove program, but what exactly do I do now so I know they are installed and working properly?

---

### Post by yabbadabbadont on 2007-10-25
In Firefox.  Edit->Preferences->Content (tab)->Fonts & Colors (section)->Advanced (button).

Look in the font drop-down boxes to see if the MS fonts are there.  Arial, Times New Roman, ...

Edit: or just open a terminal window and run
```
sudo apt-get install msttcorefonts
```

---

### Post by Sef on 2007-10-25
> ```
sudo apt-get install msttcorefonts
```


Do an update of the repositories first:

```
sudo apt-get update
```

---

### Post by dswhite85 on 2007-10-25
Thanks very much, I got it to work after I logged off and back on again.
But is there any other way out there that I could make the fonts look even nicer (more pleasing to the eye) with ClearType or something of the like? Thanks

---

### Post by macogw on 2007-10-25
I don't know what ClearType is, but in System > Preferences > Appearance, there are font settings.  People say the "anti-aliased" font settings are good.  I say the "best contrast" setting is the one that make me feel least like I need to go get new glasses.

---

