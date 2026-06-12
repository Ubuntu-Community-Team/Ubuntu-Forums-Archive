---
title: "installed, but not showing up in menu"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by jmilane on 2006-07-23
I installed phpmyadmin so that I can get into Mambo, but it is not showing up in my applications menu. 

I did it from the terminal... do I have to do something else?

---

### Post by orb9220 on 2006-07-23
Try going to applications>accesories>ala carte menu and if there is an entry in one of those menu's then just check it to make it appear.

---

### Post by jimmygoon on 2006-07-23
> **jmilane said:**
> I installed phpmyadmin so that I can get into Mambo, but it is not showing up in my applications menu. 

I did it from the terminal... do I have to do something else?
phpmyadmin is accessed through your browser, if I knew, I would tell you how to access it :)

---

### Post by paddy1978 on 2006-07-24
Yes, phpmyadmin is accessed through a browser, so you have to have a web server (Apache) running on the machine. To use it you would go to, e.g. [http://localhost/]("http://localhost/")

You would also need mysql and php installing too for it to work. Try looking at this page for how to do all this: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

I actually installed phpmyadmin manually by just downloading and unpacking it into /var/www - which is where Apache looks for pages by default. It pretty much just worked straight away, I just needed to set permissions properly I think - i.e. make it readable by 'others'. Sounds like you're talking about installing from repositories but I imagine it sets itself up in /var/www so you would see it from [http://localhost/]("http://localhost/").

Hope this helps! :-)

---

### Post by elemental666 on 2006-07-24
For clarity, apache makes a /var/www directory that is your web root by default.  If you installed phpMyAdmin via the repositories, then all the files for phpMyAdmin live in /var/www/phpmyadmin and to access them via your web browser you need to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

