---
title: "how to load GD extensions"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by liangtp on 2006-10-08
hi, i wish to upload images, have it resized and displayed. I downloaded some source from the internet and when i run my code (contains extension_loaded('gd') checking), i get the message "The GD extension isn't loaded". Question, how do i load the GD extensions.

Thanks

---

### Post by grundleflyDOTcom on 2008-01-14
I had a similar problem installing Expose4 into Joomla and it reported 'GD extension unavailable' ... eventually solved it with the advice posted below:


Install GD support php5-gd in Ubuntu
--------------------------------------------
Just type following command to install this module:

$ sudo apt-get install php5-gd

Restart Apache
# sudo /etc/init.d/apache2 restart

---

