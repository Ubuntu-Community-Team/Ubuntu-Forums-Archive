---
title: "[SOLVED] newbie needs help"
date: 2008-07-04
forum: Art &amp; Design
---

### Post by majikhotline on 2008-07-04
Hello ubuntu country,

i just installed lamp and put my web pages on the ubuntu machine from a windows machine.  not my background, photos, and links will not work.  my file are in /var/www

Thanks

---

### Post by Xfcn on 2008-07-04
First, we need more information. Are you specifically getting the broken-image icons or are the sizes of the pictures showing up but just not properly loading? Like it's failing to render?

In general, make sure that all your file-paths are correct. Remember that /var/www is now your root folder (for Apache2), so if you had [http://localhost/images/myimage.jpg](http://localhost/images/myimage.jpg) before, it's actual location on the server SHOULD be /var/www/images/myimage.jpg

Other than that, make sure you're actually linking to a relative file-path and not an absolute file-path. Meaning, if you've got the images set as "http://www.myroamingdomain.dyndns.org/images/myimage.jpg", you might try taking that to a relative file-path: "images/myimage.jpg" to see what happens.

Beyond that, can you be perhaps slightly more descriptive?

---

### Post by majikhotline on 2008-07-05
i put all my pictures in /var/www/images files and still none of the pictures will show up, but all the links work.

this is very strange

any suggestions anyone?

---

