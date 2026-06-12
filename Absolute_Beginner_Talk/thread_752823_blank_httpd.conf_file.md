---
title: "blank httpd.conf file"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by goldenbough on 2008-04-12
Basically I want to change a few things in this file.  Apache, as it is right now, is running perfectly fine.  Now when I open this file in gedit I get a blank file.  Something is obviously in there. I even placed an x in the page, saved it, and then cleared the x to create a blank page again saved it again, and after having done it renders Apache inoperative.  What's up?

---

### Post by KMuchane on 2008-04-12
goldenbough,
Hi... 
The file httpd.conf is actually empty. If you read apache2 README you will see that. 
What you should be editing is the file /etc/apache2 /sites-enabled/000-default or the file in that folder which contains your configurations. 
The reason why putting anything in httpd.conf renders it inoperative is because there is a line in the main configuration file /etc/apache2 /apache2 .conf which tells Apache2 to include the configurations in httpd.conf, so when you write an x it sees a syntax error! 
 I hope this helps. Good luck !

---

