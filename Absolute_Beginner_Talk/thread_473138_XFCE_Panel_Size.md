---
title: "XFCE Panel Size"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-13
Why is it that the panel size on XFCE is larger than the GNOME panel size even if I set i tto the same height?
I try and shrink the panel size, so I bring it down to 16. When I shrink it down to 16 I get these REALLY small quick launch(?) icons such as the show desktop icon.

How do I fix this?

---

### Post by diatribe on 2007-06-13
if your iconset is by .png and not by .svg I dont think they will resize correctly; just guessing though

---

### Post by dannymichel on 2007-06-13
I tried an svg
It didnt work

---

### Post by dannymichel on 2007-06-14
This has GOT to be a common issue.
I just cant find it on the forums anywhere.

---

### Post by dannymichel on 2007-06-15
I want to bump this cause it's been almost 24 hours.
Do you see that?
What's up with that?*(see attachment)*

---

### Post by Foxray on 2007-08-28
I actually have the same problem, I'm not exactly sure what it is. My toolbar is also at 16 and my Xfce icons are microscopic.

---

### Post by maxamillion on 2007-08-28
It has to do with the scaling and the padding on the buttons in the Xfce panel. Its not so much an "issue" or a bug as it is just that the Xfce developers prefer padding between the icon and the edge of the button where as gnome doesn't appear to. There was a bug a while back that had to do with .png instead of .svg but that doesn't appear to apply. Its also possible that this is in fact a bug that i haven't heard of and it was fixed in the 4.4.1 release (4.4.0 is what is in the feisty repos).

Hope that helped or at least cleared some stuff up.

---

### Post by Foxray on 2007-08-28
I've actually solved this problem. The problem was because I had some applets that prevented the bar from resizing correctly. So if you remove them and just have icons on there it works how xfce should work. As usual xubuntu pwns my gnome unbuntu desktop.

---

