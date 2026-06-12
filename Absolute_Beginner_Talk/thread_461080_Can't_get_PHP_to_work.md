---
title: "Can't get PHP to work"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by intrepid_geek on 2007-06-01
I simply cannot get php to work on my server. Apache2 works fine. I've installed:

php5 mysql-server 

I've been all over these forums, I've done this: [http://ubuntuforums.org/showpost.php?p=2638509&postcount=5]("http://ubuntuforums.org/showpost.php?p=2638509&postcount=5")

And I've added AddType application/x-httpd-php .php to apache2.conf and I've restarted apache.


I wasn't able to download libapache2-mod-php5 because it said it no longer existed and there were no candidates for it. I suspect thats my problem, any ideas?

Also, I do not see php in "/etc/apache2/mods-enabled".


here is my php code:

[B]<html>
<body>

<?php
echo "Hello World";
?>

</body>
</html>[/B]

---

### Post by Cypher on 2007-06-01
Indeed, without the "libapache2-mod-php5", what I did in the post you mentioned will not work. Are you using Feisty? I can see the package listed [here]("http://packages.ubuntu.com/feisty/web/libapache2-mod-php5"). So not sure why you got that error.

Also, PHP code doesn't need to be surrounded by HTML tags, it can stand alone..

---

### Post by S29K on 2007-06-01
NM: I'm a moron.

---

### Post by S29K on 2007-06-01
Another thought, did you save your code as an 'htm' or 'html' file?.....in my experience you need to give the file a 'php' extension for the server to recognize it as having php code in it.

---

### Post by Cypher on 2007-06-01
> **S29K said:**
> Another thought, did you save your code as an 'htm' or 'html' file?.....in my experience you need to give the file a 'php' extension for the server to recognize it as having php code in it.
That's a valid point, but with the libapache2-php-mod, Firefox will just prompt you to download the file. With the  module, PHP has to be configured as a CGI script using ScriptAlias/AddScript/AddHandler..

---

### Post by intrepid_geek on 2007-06-01
ooooooooook.. i put "apache" instead of "apache2" in that package when i first tried to download it.

also, you're right, you must have a file extension of php for that to work. So basically, when I want to "<a href...", instead of pointing to an htm/l file ill just point to a php. blah blah...

ok i got some learning to do. 

thanks x 100!

---

