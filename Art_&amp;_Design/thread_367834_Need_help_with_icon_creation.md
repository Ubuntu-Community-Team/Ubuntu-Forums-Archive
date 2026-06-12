---
title: "Need help with icon creation"
date: 2007-02-22
forum: Art &amp; Design
---

### Post by jozmak on 2007-02-22
Hi,

I would need a bit of help with icon creation. I am remaking the tango icons. Currently most of the folder icons are done. However the new icons are not updating everywhere. The large icons on the desktop are updating nicely but not the small ones in file-manager. Could anyone who is experienced in icon issues give me some ideas what could be the problem?

Thanks,
jmak

---

### Post by ComplexNumber on 2007-02-22
there are some areas to investigate:
a)  for some reason, different distros seem to use different names. for example, one distro may use the icon name stock_volume-0 for the volume applet to show a muted state. some distros may use the icon name audio-volume-muted (this is what ubuntu uses)
b) the index.theme file.

i suspect the problem may lie in b)

---

### Post by jozmak on 2007-02-22
Thanks for the suggestion. I looked up the index.theme file but there i couldn't find the source of the problem. In the meantime, I deleted the original icons and replaced them with my icons, and the weirdest thing is that the non-existing icons still show up. How is this possible.

---

