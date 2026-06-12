---
title: "Creating a server environment: XAMPP or not?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Verminox on 2006-11-28
I have Kubuntu 6.06 installed (not the server version) and I want to create a server environment to be able to execute PHP and run MySQL. Basically, I need Apache.

Instead of downloading Apache, PHP and MySQL separately, I was thinking of using [XAMPP for Linux](http://www.apachefriends.org/en/xampp-linux.html) (a.k.a LAMPP).I've used XAMPP on Windows before and it seemed good enough.

Should I go ahead with XAMPP or are there any advantages in getting everything separately? 

If XAMPP, some more questions:

The site recommends an install in /opt. What is /opt used for? And where does one usually install applications that are downloaded in tar form? I have only used Adept-installed apps till now.... but I always thought /usr/local/bin was the place to install apps.... so what is /opt ?

Also, to start the server I would have to manually call the command:
/opt/lampp/lampp start
each time I need it. How would I get this done automatically at boot? Or is it better to do this at runtime to save resources?

Thanks for your help :)

---

### Post by Verminox on 2006-11-28
*cheap bump*




Sorry... but it's been 8 hours without a reply.... perhaps there are more users online at this hour of the day...

---

### Post by Bachstelze on 2006-11-28
Just install the Apache/PHP/MySQL packages from apt, it's just one command to type.

---

### Post by Verminox on 2006-11-28
yeah but xampp also gives me phpmyadmin, extra php libraries, perl modules also i think... in all it sounds like a good package.... 

does it have any disadvantages in particular?

---

### Post by Bachstelze on 2006-11-28
I couldn't tell you since I never used it but it's genrerally better to stick with the Ubuntu packages, it will be easier to install and maintain. And I think you can get everyhing you need that way, too (there's an Ubuntu package for phpmyadmin, too).

---

