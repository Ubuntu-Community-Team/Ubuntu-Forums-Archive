---
title: "How to create scripts"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by merrameu on 2005-10-05
Hello,

I'm new in Linux. I have a simple question:

How can I create scripts? For example create a script to reset the gnome panel. I don't want to open a terminal window, write "kill....." every time I need to reset the gnome panel. I want to create a script and to execute this script from desktop. Is this posible?

Thanks

---

### Post by Perfect Storm on 2005-10-05
make a new file eg. my_script.sh
open it and then: 

**#!/bin/bash**
**killall gnome-panel**

save it and **chmod +x** it

---

### Post by merrameu on 2005-10-05
Ok,

Thanks Artificial Intelligence. Do you know any web were I can learn about scripts?

Thanks

---

### Post by Perfect Storm on 2005-10-05
Well there some books: [http://www.intuitive.com/linux/index.shtml](http://www.intuitive.com/linux/index.shtml)

Some guides etc.
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)
[http://linux.about.com/od/commands/l/blcmdl_na.htm](http://linux.about.com/od/commands/l/blcmdl_na.htm)

---

### Post by merrameu on 2005-10-05
Ok,, thanks  :D

---

### Post by davmac on 2005-10-05
I've found [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) to be really useful getting started.

HTH,

Dave Mac

---

