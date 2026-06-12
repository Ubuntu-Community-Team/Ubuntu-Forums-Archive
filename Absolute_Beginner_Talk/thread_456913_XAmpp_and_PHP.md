---
title: "XAmpp and PHP"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by kjelle392 on 2007-05-28
Hello again

Today I installed XAmpp on my Ubuntu-box. No errors. 

When I try to open my newly written php-script in the browser, absolutely nothing happens... "View source" from the browser produces just a empty page, but when I do a "cat test.php" in the console, the script is there.

Why don't XAmpp parse the php-file, and why is the source-code empty in FireFox?

---

### Post by ep2011 on 2007-05-28
Are you viewing the php-file through your home folder? Or are you using the correct folder specified by Xampp? You must put your php files in /opt/lampp/htdocs/ and then view them by typing localhost://Name_of_file.php in your favorite web browser (Firefox, etc)

---

### Post by kjelle392 on 2007-05-28
> **ep2011 said:**
> Are you viewing the php-file through your home folder? Or are you using the correct folder specified by Xampp? You must put your php files in /opt/lampp/htdocs/ and then view them by typing localhost://Name_of_file.php in your favorite web browser (Firefox, etc)

Yes I've put the file in the htdocs-folder. I have also chown'ed the folder (and files) to my user.

---

### Post by kjelle392 on 2007-05-29
No-one that can help?

Help me remove ALL off XAmpp, old installation of Apache, PHP and MySQL - and then guide me through a complete install of Apache, PHP and MySQL then :p

---

### Post by SoulinEther on 2007-05-29
> **kjelle392 said:**
> No-one that can help?

Help me remove ALL off XAmpp, old installation of Apache, PHP and MySQL - and then guide me through a complete install of Apache, PHP and MySQL then :p

Good job on the removal of XAmpp thing, that's just about what I was going to tell you!

If I recall correctly.... if you go to Synaptic... you should be able to find some choice in the stuff to ... automatically install AMP. ...

Yes! Go to Edit > Mark Packages by Task, Select LAMP Server.

Should help.

---

### Post by ukripper on 2007-05-29
i am running XAMPP with no problem on EDGY and aslo removed all LAMP stack I had which was creating panick among my services. Now it is much easy to manage. but i would prefer LAMP stack down the line when I finish with my webapps and finally put it on my Webserver till then XAMPP is fine for testing.

---

### Post by kjelle392 on 2007-05-29
> **SoulinEther said:**
> Good job on the removal of XAmpp thing, that's just about what I was going to tell you!

If I recall correctly.... if you go to Synaptic... you should be able to find some choice in the stuff to ... automatically install AMP. ...

Yes! Go to Edit > Mark Packages by Task, Select LAMP Server.

Should help.

Wow that's easy :p

Thank you very much!

But still I have problems with parsing of the PHP-files... FF just want to download them...

---

