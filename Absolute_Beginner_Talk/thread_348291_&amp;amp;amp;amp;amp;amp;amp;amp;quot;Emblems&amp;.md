---
title: "&amp;amp;amp;amp;amp;amp;amp;amp;quot;Emblems&amp;amp;amp; amp;amp; amp;amp; amp;quot ; how to get rid"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-28
Can someone please tell me how to get rid of the little orange emblems

Thanks :)

---

### Post by riven0 on 2007-01-28
If you're talking about those orange applications icons, you have to change it manually. Right click on the icon, choose Properties, then click on the pic box to the left and change it to what you want.

---

### Post by squrl on 2007-01-28
You must be referring to the icon. I'm interested in the orange "emblem" at least thats what they are named in the properties box but it doesn't give a way to remove them

---

### Post by kevinlyfellow on 2007-02-18
I want to change that too.  I located all directories that was related to emblems but I cam up short (I did find the ones I wanted to use though).  I can't find the orange ones, and when I try to add the good ones, I get an error message saying that its not usable.

---

### Post by kevinlyfellow on 2007-02-18
Aha.. I found those ugly little... anyways
/usr/share/icons/Human/scalable/emblems
I wonder why it doesn't let me import svg... oh well, time to replace those little devils

---

### Post by kevinlyfellow on 2007-02-18
This is what I did and now I have the standard gnome emblem set

```

sudo mv /usr/share/icons/Human/emblems /usr/share/icons/Human/emblems_standard
sudo cp /usr/share/icons/gnome/emblems /usr/share/icons/Human/emblems
killall nautilus

```

---

