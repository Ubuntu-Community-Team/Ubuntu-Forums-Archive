---
title: "LAMP Apache DirectoryIndex problem"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by GaFFy on 2006-05-08
I have Apache PHP MySQL installed and everthing works great...
Well almost everything, if i go to just localhost with no page name then it comes up with the download file dialog and the filename is ~

/etc/apache2/apache2.conf has my index.php listed under DefaultIndex

if I goto to index.php directly (or any other page) then it works correctly.

What would cause this and how do I fix it? ](*,) 

Thanks

I am using Apache/2.0.55 (Ubuntu) PHP/5.1.2-1ubuntu2
also MySQL 5.0.19

---

### Post by Kurt` on 2006-05-08
I am also interested in the solution to this problem. :)

I had this same problem... I ended up compiling apache2 manually (from the sources on the apache site) for my server. :(

---

### Post by Daremo on 2006-05-08
If it is a default Ubuntu Apache install then you might want to try this page:
[http://localhost/apache2-default](http://localhost/apache2-default) in your browser, as this is the default web server directory when installed from Synaptic Package Manager. 

If you just use localhost then you'll end up just getting a directory listing.

Unless you redirect Apache with a directory alias, then be sure to use the localhost/apache2-default location or you'll end up with the Not Found error.

Using Webmin is an easy way to configure Apache.

---

### Post by guitarded on 2006-05-09
i used synaptic to install webmin...  how do i launch the application?  an icon or menu selection was not created and i am not sure where the executable is located.

---

### Post by Daremo on 2006-05-09
open your browser and go to the page "https://localhost:10000" (without the "")
Webmin should display. It is a browser based app

---

### Post by GaFFy on 2006-05-09
Well I dont know what changed but Dapper updated several things this morning and asked to reboot and now apache is working correctly.  I am not sure if the updates did it or just the reboot (which I had tried already). :rolleyes: 

Anyway thanks for all the help.
I dont think I need webmin now which is good because it wont install.
 Package webmin has no installation candidate ](*,)

---

