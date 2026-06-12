---
title: "Error with Mozilla Firefox"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2005-08-21
When clicking on a link in Mozilla Firefox to download something, I get this popup window with the following error message:

"xml parsing error: not well formed..."

anyone know how to fix this?

EDIT>> I also get such xml errors when trying to bookmark a site

---

### Post by heimo on 2005-08-21
This may be a working workaround (but you'll have to make your settings again): Exit firefox, open terminal and type:
 ```
mv  ~/.mozilla/firefox ~/.mozilla/firefox_old 
``` 
Open firefox and try again. If you don't use any other mozilla products, you may try to mv (move, rename) the whole .mozilla directory.

---

