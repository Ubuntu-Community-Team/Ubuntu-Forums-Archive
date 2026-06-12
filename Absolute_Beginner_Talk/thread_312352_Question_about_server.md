---
title: "Question about server"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by old_newbie on 2006-12-04
Ok, I got it all installed, I think, but when I try to reach a php-page from localhost it won't understand. I have restarted the apache server, but the browser can not understand the page, nor any php at all. What is worng, then? Please? :confused: :confused:

---

### Post by Tomosaur on 2006-12-04
Could be a number of things really. First and most obvious is to check your code is correct. Secondly, you may need to configure apache so it knows where your page is. You should normally be putting your web-stuff in '/var/www', because that's where Apache will look.

If it's still now working, you may need to set the permissions of the stuff in /var/www.

---

### Post by old_newbie on 2006-12-05
Nothing worked, the system will not execute php, only html. And the pre-defined web directory is in /var/www/apache2-default

Maybe I shouldn't have installed the ubuntu 6.10, but the server edition 6.06? My only purpose is to develop and test php on a local machine without the network. Maybe I should make a fresh new installation with 6.06, will it overwrite 6.10, then?

---

