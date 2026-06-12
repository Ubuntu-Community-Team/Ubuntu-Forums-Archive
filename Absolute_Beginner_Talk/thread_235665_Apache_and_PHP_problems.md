---
title: "Apache and PHP problems"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-08-13
Hey all! Trying to install php and apache. I've downloaded, but having some problems setting them up. When I type in localhost into my browser it comes up with a page like you see when you type a ftp address into firefox, saying index of /, which then has a link taking me to the apache test page (the one i was expecting to see!). I managed to fix that by editing /etc/apache2/sites-available/000-default and uncommenting a line, but in the address bar it says localhost/apache2-default/, instead of just localhost. Is that normal?

Then, I'm having some problems with PHP. Once installed, should I be able to open .php files in my webbrowser from anywhere on my computer? Because it won't. The odd thing is, when I move a .php file to the directory that the Apache page is in (/var/www/apache2-default) it opens no problem.For example, a page called phpinfo.php won't display off my desktop, but when I move it to that folder and type localhost/phpinfo.php it displays no problem!

Help!!!

---

### Post by kebes on 2006-08-13
> in the address bar it says [http://localhost/apache2-default/](http://localhost/apache2-default/), instead of just localhost. Is that normal?

Yes that's normal on a fresh install. If you put a real webpage in the root web folder (i.e.: make a "index.html" file in "/var/www/") you'll see that page instead of the default "your have apached installed"-type page.

> Once installed, should I be able to open .php files in my webbrowser? Because it won't. The odd thing is, when I move a .php file to the directory that the Apache page is in (/var/www/apache2-default) it opens no problem (i.e. a page put in there called phpinfo.php, won't display off my desktop, but when I move it to that folder and type localhost/phpinfo.php it displays no problem!)

That's exactly how it should be. If you try to open a .php file anywhere on your filesystem, you'll simply be opening a text file. Inside it you'll see all the PHP code, which you'll be able to edit.

The only way to get the .php file to be converted into a web-document is to have your web-server (apache) parse it. So you need to put the document inside your web-folder (/var/www/ or any sub-directory thereof) and open the document in a web-browser using "http://localhost/".

So if you make a file called "index.php" and copy it to "/var/www/mypage/" then you can edit it with a text editor, by opening the file "/var/www/mypage/index.php" and you can "preview" it by opening a web-browser and going to:
[http://localhost/mypage/](http://localhost/mypage/)

The apache web-browser can only parse php files (convert them into HTML web documents) if they are in the web-folder.


It sounds like your installation is working fine.

---

### Post by tartarian on 2006-08-13
Yay! Thanks for that! Wasn't sure!

---

