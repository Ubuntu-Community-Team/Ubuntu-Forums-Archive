---
title: "php files are trying to save or download vs open"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by solsie on 2007-01-19
I have a wierd situation here.  I have installed LAMP Server and all the configurations.  I try to open a php file and it tries to save or download vs open up.  How can i confirm PHP is started ?  

Scott

---

### Post by JamieC on 2007-01-19
How do you mean "confirm PHP is started?"? The PHP engine (assuming CGI binary) will process PHP files (providing you have set up the handler properly) as you request them.

Do you mean to say when you request the PHP file through your browser, instead of being parsed and output, a download is forced?

---

### Post by solsie on 2007-01-19
exactly, i am used to running this in windows, but wanted to implement a linux box instead.  Where should i go to look to make sure that php is handling the appropriate extensions?

---

### Post by JamieC on 2007-01-19
Is the file in the correct directory used by the server software and are requests for HTML files served properly?

If so, attach your httpd.conf file and I'll take a look for you.

---

### Post by solsie on 2007-01-19
where can i confirm that this is set up correctly.  I apologize for being a newbie on this. 

I am sure that i dont have this set up correctly.

Scott

--------------------------------------------------------------------------------

Is the file in the correct directory used by the server software and are requests for HTML files served properly?

If so, attach your httpd.conf file and I'll take a look for you.

---

### Post by JamieC on 2007-01-19
Is the server software running? Are you on the machine you've installed the server software? If so, point your browser to [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) and you should see a page informing you that the installation was successful...

---

### Post by solsie on 2007-01-19
ok not able to connect.  how can i make sure that this is configured to run

---

