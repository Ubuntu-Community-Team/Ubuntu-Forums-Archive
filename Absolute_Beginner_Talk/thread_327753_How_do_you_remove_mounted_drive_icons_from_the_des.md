---
title: "How do you remove mounted drive icons from the desktop?"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by mrdeeno on 2006-12-29
I just got Ubuntu 6.06 working the way I want it to on my Sony Vaio laptop.

I have a memory stick in my computer (Sony Vaio) and an external drive where I keep all my data and media, and I also have a Windows XP partition on my hard drive, all of which shows as icons on the desktop since they are all mounted.

Does anyone know how I can remove the icons from the desktop in 6.06 but keep the drives mounted so my desktop is "clear"?

---

### Post by angkor on 2006-12-29
Open up gconf-editor and go to: Apps -> Nautilus -> Desktop

Untick volumes_visible, home_icon_visible and computer_icon_visible. You desktop should be empty after that.

---

### Post by mrdeeno on 2006-12-29
That worked.  Thanks

---

### Post by skiddly on 2007-03-02
Hi how do i find gconfig-editor

---

### Post by 23meg on 2007-03-02
> **skiddly said:**
> Hi how do i find gconfig-editor

Hit Alt + F2 and type "gconf-editor".

---

### Post by skiddly on 2007-03-02
Right opened up gconf-editor nautilus etc but box to right is empty with no options or anything:(

---

### Post by skiddly on 2007-03-02
The desktop folder wont actually open

---

### Post by 23meg on 2007-03-02
Click "apps" on the left; the tree will expand, and under apps you should choose "nautilus", and under that, "desktop". You'll then get the menu options in the box.

Alternatively, click Edit / Find and do a search for the key name to get straight to it.

---

### Post by skiddly on 2007-03-02
Ive done all that but once i get to desktop theres no little arrow to expand and if i click on it nothing happens

---

### Post by 23meg on 2007-03-02
That's very strange. See if this works:

```
 gconftool-2 --type boolean -s /apps/nautilus/desktop/volumes_visible false
```

---

### Post by skiddly on 2007-03-02
[SIZE="5"][/SIZE]Still no luck tried doing the last option no joy did manage to get the volumes visible box but it was already unticked and yes icons still on desk top

---

### Post by 23meg on 2007-03-02
Is anything else malfunctioning in GNOME? Can you post a screenshot of the gconf-editor window with the "desktop" folder selected?

---

