---
title: "getting gimp to use real inches"
date: 2010-07-28
forum: Art &amp; Design
---

### Post by guine on 2010-07-28
I think I've had this same problem in the past before, but when I tried to make a picture a set number of inches in gimp and then insert into a word document gimps idea of what an inch is is smaller than what word programs think an inch is.(I tried multiple word programs on multiple computers using multiple operating systems so Im pretty certain its gimp)  Is there any plugin or anything like that to fix gimps measurement scale?  Thanks.

---

### Post by qamelian on 2010-07-28
> **guine said:**
> I think I've had this same problem in the past before, but when I tried to make a picture a set number of inches in gimp and then insert into a word document gimps idea of what an inch is is smaller than what word programs think an inch is.(I tried multiple word programs on multiple computers using multiple operating systems so Im pretty certain its gimp)  Is there any plugin or anything like that to fix gimps measurement scale?  Thanks.
GIMP defaults to assuming 72 pixels per inch, according to Edit > Preferences > Default Image > Advanced Options. If your final document is going to print at higher resolution (which it more than likely is!), you'll need to adjust the resolution in this section accordingly. For example, if the document is meant to print to a 300 dpi laser printer, to keep the image to scale, you'll want to set the resolution here to 300 as well.

---

### Post by guine on 2010-07-28
Thanks, that fixed it and explains why the image didnt look as good in a word document too.

---

