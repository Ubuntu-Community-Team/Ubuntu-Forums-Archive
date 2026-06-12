---
title: "place icons in Computer location"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-29
is there a way to add icons for hard drive volumes to the Computer location?  i want to be able to see two new volumes that i have added to my /etc/fstab file under Computer- they were visible there before i added entries for them to fstab.  can this be done?  thanks.

---

### Post by stalker145 on 2008-01-29
> **Matt26 said:**
> is there a way to add icons for hard drive volumes to the Computer location?  i want to be able to see two new volumes that i have added to my /etc/fstab file under Computer- they were visible there before i added entries for them to fstab.  can this be done?  thanks.

I'm not quite sure about doing it the way you ask, but another option is to open Nautilus and drag the folder in question over to the lower half of your navigation tree (on the left) and rename the shortcut to one of your choosing.

---

### Post by legend2440 on 2008-01-29
Perhaps this will help
In terminal type
gconf-editor

Then go to apps >> nautilus >> desktop and put check next to volumes_visible

This will put icons on desktop and perhaps also in Places and or Computer
Hope that helps

---

