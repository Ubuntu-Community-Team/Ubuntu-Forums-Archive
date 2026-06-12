---
title: "title bars go away ?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Faud on 2007-11-08
Is there a way to make the title bars go away from windows ?

---

### Post by inversekinetix on 2007-11-08
If you're using compiz fusion, just disable the window decorations it ccsm.

---

### Post by Faud on 2007-11-08
Im trying to do it w/o using compiz

---

### Post by Faud on 2007-11-09
any ideas guys ?

---

### Post by Faud on 2007-11-11
Ive been trying for days and cannot find a setting in gnome to do this. Easy enough with compiz fusion. I keep think there as has got to be a way to do it though

---

### Post by FuturePilot on 2007-11-11
You would probably have to remove Metacity or prevent it from starting. But without a window manager running you won't be able to move your windows around the screen.

---

### Post by DutyDuty on 2007-11-11
Typically, this is type of thing people try to *avoid.* You could delete all the theme from Emerald and then use ```
emerald --replace
``` which may or may not do something.

---

### Post by chamberlain2006 on 2007-11-11
Are you talking from a functional standpoint or are you programming an application?  May I ask why you need to do this?

---

### Post by Blutack on 2007-11-11
Hmm...have a rummage in your .themes folder...
I found a chunk like this in the metacity-theme xml

<!--
    Window Title
-->

<draw_ops name="draw_title_text_normal">
    <title x="0" y="(height - title_height) / 2" color="#ffffff"/>
</draw_ops>

<draw_ops name="draw_title_text_inactive">
    <title x="0" y="(height - title_height) / 2" color="gtk:text[INSENSITIVE]"/>
</draw_ops>

Just set the active text colour the same as your window bar colour.

---

