---
title: "Where is gstreamer0.10-plugins-ugly ???"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by johnnyboy on 2006-06-14
I just updated, online, from breezy to dapper.  With dapper, I am attempting to convert to mp3 and listen to non-free formats, can't find the right plugins : gstreamer0.10-plugins-ugly-multiverse or gstreamer0.10-plugins-ugly (same thing I assume).

I checked my repositories, and there is no "settings" button to click "show hidden repositories".  So I just went ahead and changed all 'universe' repositories to both 'universe multiverse'.  Even now I cannot find the required plugins.  Does anyone know what is up?

---

### Post by Jagot on 2006-06-14
gstreamer0.10-plugins-ugly is in the universe repo.  Are you sure you have enabled it correctly?  When you go Synaptic, and to the settings for the repos you need to click 'Add' then make sure you select the universe and multiverse at the bottom as well a just making sure all the repos ar ticked.

---

### Post by FyreBrand on 2006-06-14
make sure you have the repository enabled.  i just installed them so they are there.  i used the search button to filter down the extra content so it was easier to read.

---

### Post by johnnyboy on 2006-06-14
[QUOTE=Jagot]gstreamer0.10-plugins-ugly is in the universe repo.  Are you sure you have enabled it correctly?  When you go Synaptic, and to the settings for the repos you need to click 'Add' then make sure you select the universe and multiverse at the bottom as well a just making sure all the repos ar ticked.[/QUOTE]


Thanks guys.  It was a complete brainfart on my part.  I forgot to add the 6.06 backports repositories.

---

### Post by mostwanted on 2006-06-14
[QUOTE=johnnyboy]Thanks guys.  It was a complete brainfart on my part.  I forgot to add the 6.06 backports repositories.[/QUOTE]

It's in multiverse and universe not backports.

And the two packages you mentioned aren't the same thing, one has material suitable for universe, the other suitable for multiverse.

---

