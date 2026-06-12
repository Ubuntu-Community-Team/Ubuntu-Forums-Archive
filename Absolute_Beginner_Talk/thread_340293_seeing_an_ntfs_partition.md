---
title: "seeing an ntfs partition"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by saltyscott on 2007-01-17
hi i have two questions. i don't like any icons on my desktop so i got rid of them all. when i got rid of the icon for my ntfs partition it doesn't show up in my Computer folder anymore. i would like that icon and my ipod one to show up there but not on my desktop. how do i get back my ntfs one and how can i get rid of the ipod one from the desktop?

---

### Post by Ecthelion on 2007-01-17
> **saltyscott said:**
> hi i have two questions. i don't like any icons on my desktop so i got rid of them all. when i got rid of the icon for my ntfs partition it doesn't show up in my Computer folder anymore. i would like that icon and my ipod one to show up there but not on my desktop. how do i get back my ntfs one and how can i get rid of the ipod one from the desktop?
Euhm...
Could you post the output if this command?
```
cat /etc/fstab
```

> it doesn't show up in my Computer folder anymore
I can help you to mount your ntfs somewhere else.
That won't be in the 'my computer' folder, since this is a somewhat special location and I don't know how to mount something to there.
But any other location is good.
And if you bookmark that location it will show up in the 'locations' menu.

For your ipod...
Best is to leave it like it is...
You could try to add some lines in your fstab to have it automount at another location each time.

If that's what you want I can try to help :-)

Anyway, first thing I need is the output the command I requested earlier :-)

---

