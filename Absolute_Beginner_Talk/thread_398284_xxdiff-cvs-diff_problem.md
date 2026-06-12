---
title: "xxdiff-cvs-diff problem"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Boffin13 on 2007-03-31
Hello. I'm using xxdiff-cvs-diff to compare my current version of file with one that I have in CVS, but nothing works :(

I have config.php file that I recently added two strings. But when I write:
xxdiff-cvs-diff config.php

I got window as if my config.php is absolutely the same (with same text at the left side where CVS has to be).

Also I get following messages in konsole window:
```
****************************************
Index: config.php
===================================================================
RCS file: /usr/local/cvsroot/bthumber/_includes/config.php,v
retrieving revision 1.1
diff -u -r1.1 config.php
--- config.php  31 Mar 2007 23:46:05 -0000      1.1
+++ config.php  31 Mar 2007 23:58:59 -0000
@@ -20,4 +20,9 @@
 $url['menu.js'] = $url['ADMIN'].'Menu/libjs/layersmenu.js';

 $url['categories.php'] = $url['ADMIN'].'categories.php';
+$url['paysites.php'] = $url['ADMIN'].'paysites.php';
+$url['bulk_add.php'] = $url['ADMIN'].'bulk_add.php';
+$url['manage_gals.php'] = $url['ADMIN'].'manage_gals.php';
+$url['settings.php'] = $url['ADMIN'].'settings.php';
+$url['logout.php'] = $url['ADMIN'].'logout.php';
 ?>
****************************************
patching file config.php
patch unexpectedly ends in middle of line
Hunk #1 FAILED at 20.
1 out of 1 hunk FAILED -- saving rejects to file /tmp/xxdiff-cvs-diff.WiGWXe.rej
```

How can I fix it?

---

