---
title: "How do I determine an apps version number?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by bdemers on 2007-04-06
Is there some way for me to determine an apps version number using command line?

Secondly, is there some way to see if Apache, Mysql and PHP (LAMP) are successfully installed on my op sys?  Is there an interface for each that I can launch?

---

### Post by kh4nh on 2007-04-06
you can use dpkg


dpkg -l name_of_the_app
# the option is an el, not one

---

### Post by bdemers on 2007-04-06
So, in my case I am looking for the version numbers for Apache2, mysql, and php5.

I would use :
dpkg -l apache2 as an example?  Or do I need to determine the executables name?

---

