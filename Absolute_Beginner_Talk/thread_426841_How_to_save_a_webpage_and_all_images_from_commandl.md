---
title: "How to save a webpage and all images from commandline?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by wrybread on 2007-04-28
I need a way to save ebay auction pages, including all images, to the harddrive. Using Firefox's Save feature works great, but I need to automate it.

Can anyone think of a way to do this? I'm guessing the answer is in wget somewhere, but I can't get it to work.

For example:

[edsel]$ wget --page-requisites -erobots=off -r [http://cgi.ebay.com/ebaymotors/DAIHATSU-MIDGET-MINI-HIJET-RARE-VEHICLE-CUSHMAN_W0QQcmdZViewItemQQcategoryZ10076QQihZ003QQitemZ130106511761QQrdZ1](http://cgi.ebay.com/ebaymotors/DAIHATSU-MIDGET-MINI-HIJET-RARE-VEHICLE-CUSHMAN_W0QQcmdZViewItemQQcategoryZ10076QQihZ003QQitemZ130106511761QQrdZ1)

Anyone?

---

### Post by aysiu on 2007-04-28
Will this work? ```
wget -c -m http://cgi.ebay.com/ebaymotors/DAIHATSU-MIDGET-MINI-HIJET-RARE-VEHICLE-CUSHMAN_W0QQcmdZViewItemQQcategoryZ10076QQihZ003QQitemZ130106511761QQrdZ1
```

---

### Post by wrybread on 2007-04-30
Did that wget command work for you? It's not working for me.

I wound up writing a Python script, works nicely, it's here:

[http://forums.devshed.com/python-programming-11/download-a-webpage-and-all-images-440976.html](http://forums.devshed.com/python-programming-11/download-a-webpage-and-all-images-440976.html)

---

