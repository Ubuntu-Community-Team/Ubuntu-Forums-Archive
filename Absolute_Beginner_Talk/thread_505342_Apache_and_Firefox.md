---
title: "Apache and Firefox"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by skao on 2007-07-20
Hi

I am using Ubuntu 7.04 and just install Apache2, and got some small problem

1. I am unable to find the config file for Apache2,  is the /etc/apache2/apache2.conf I should modify.

2. Not quite sure this is a FireFox problem for Apache2 problem. When I try to open the index.html for Apache2 documentation (copying the manual directory into my documentroot directory and by using File / Open File) it fail to redirect to the correct page, it just show the contain of the index.html page

The following is part of what I get when I try to open the index.html
URI: configuring.html.de Content-Language: de Content-type: text/html; charset=ISO-8859-1 ...

What should I do so it can redirect to the correct page

Thanks for the help
Stephen

---

### Post by anubhavrocks on 2007-07-20
can  you try  
```
sudo /etc/init.d/apache2 restart
``` 

and give it a shot,i also think that apache2 wasn't correctly installed in the first place.To install apache2 use the following command

```
sudo apt-get install apache2
```

---

### Post by skao on 2007-07-20
> **skao said:**
> Hi

I am using Ubuntu 7.04 and just install Apache2, and got some small problem

1. I am unable to find the config file for Apache2,  is the /etc/apache2/apache2.conf I should modify.

2. Not quite sure this is a FireFox problem for Apache2 problem. When I try to open the index.html for Apache2 documentation (copying the manual directory into my documentroot directory and by using File / Open File) it fail to redirect to the correct page, it just show the contain of the index.html page

The following is part of what I get when I try to open the index.html
URI: configuring.html.de Content-Language: de Content-type: text/html; charset=ISO-8859-1 ...

What should I do so it can redirect to the correct page

anubhavrocks Thanks for the help
Stephen

Hi after some search I found the answer  
the /etc/apache2/apache2.conf is the right file, but it also include the httpd.conf file

about the index.html, look like it is a Apache bug, the main html file should be with the extension of .var

---

