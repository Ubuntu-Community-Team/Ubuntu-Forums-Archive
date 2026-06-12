---
title: "Amarok Songs listed twice"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2007-08-07
I have every song listed in my library twice.  How can I erase my entire library from Amarok and start over.

I have tried rescan and update as well as changing the location of my library.

---

### Post by forestpixie on 2007-08-07
there's a hidden folder which contains the database and album covers

in nautilus show hidden files - look in homew for .kde - in there share/app/amarok

hope that helps

---

### Post by gentlemanmasher on 2007-08-07
How do I show hidden files?

---

### Post by forestpixie on 2007-08-07
once you're in nautilus - either view - show hidden files or Ctrl H

---

### Post by deadlikeoscar on 2007-08-07
I just had this problem and fixed it. Yeah, as was suggested navigate to your home directory and then hit CTRL + H. Then click on the .kde folder and then on share and then apps and finally amarok. Delete collection.db, collection_scan.files, and collection_scan.log. Then when you open Amarok, it will rebuild the database.

---

### Post by gentlemanmasher on 2007-08-07
Thanks both.  I will try this when I get home.

---

