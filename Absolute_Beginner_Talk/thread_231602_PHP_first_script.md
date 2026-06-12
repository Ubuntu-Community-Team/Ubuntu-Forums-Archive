---
title: "PHP: first script"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-08-07
I've installed Xampp; and everything is ok. I've got Php, mysql and Apache working. I've written my first php script and i've tried to have it run writing in the address bar: [http://localhost/php1.php](http://localhost/php1.php)

But i've got this message back:

Not Found

The requested URL /php1.php was not found on this server.
Apache/2.2.2 (Unix) DAV/2 mod_ssl/2.2.2 OpenSSL/0.9.8b PHP/5.1.4 mod_apreq2-20051231/2.5.7 mod_perl/2.0.2 Perl/v5.8.7 Server at 127.0.0.1 Port 80

I've tried [http://localhost/127.0.0.1](http://localhost/127.0.0.1)  Nothing.

Maybe php1.php should be stored in a specific directory: I put in in the Desktop. 

Any hint?

:confused: :confused: 

Thanks in advance.

---

### Post by kebes on 2006-08-07
When you go to:
[http://localhost/](http://localhost/)
(or equivalently to "http://127.0.0.1/")
you are really going to your web-directory. You need to put your file "php1.php" into your web folder. Its location depends somewhat on configuration, but it is usually:
/var/www/html/

If you put your file in there, you should be able to see it in your browser.

---

### Post by Klaidas on 2006-08-07
Yes, your files that you want to be accessible from the web should be stored in /var/www , which is the default Apache's directory.
Here's some helpful info about web development under Linux (PHP, Apache): 
[http://www.linux.org/lessons/interm/c1685.html](http://www.linux.org/lessons/interm/c1685.html)
[http://www.linux.org/lessons/interm/x2305.html#PHP-INTRO](http://www.linux.org/lessons/interm/x2305.html#PHP-INTRO)

---

### Post by kebes on 2006-08-07
Oh, it looks like Xampp works a bit different from Apache (which would normally store things in "/var/www/html/"). According to this thread:
[http://www.ubuntuforums.org/showthread.php?p=1311529](http://www.ubuntuforums.org/showthread.php?p=1311529)

It stores the web-files in:
/opt/lampp/htdocs/
(or a user directory within there...)

Refer to the thread above for tricks, like making a symlink in your home directory so that it is easier to update the files in the Xampp web folder.

Hope that helps.

---

### Post by mithras86 on 2006-08-07
The root for Apache is a folder specially configured. I don't know sure how it's configured with Xampp, but I think it's the same. 
Probably the folder is /var/www/, but with xampp, it could also called htdocs. Look over in /etc/apache2/apache.conf where the folder is located.

That folder is the root for your webserver to look in for. So look up this folder and you know where you have to store your documents.

Furthermore: 127.0.0.1 is the ip for your localhost, if apache (or another server) is running. So [http://localhost](http://localhost) and 127.0.0.1 are the same, don't use them together ;)

/edit: as above seen: look over for /opt/lampp/htdocs/

---

### Post by helphope on 2006-08-07
Thank you very much for teh very precious help. It helped a lot, and gave me some good references which I was unable to discover.

I managed to follow the path

 /opt/lampp/htdocs/

but when it comes that I want to save the file I've got a message that I can't write it.

:confused: :confused: 

Any more hint? Thanks in advance

---

### Post by mithras86 on 2006-08-07
> **helphope said:**
> but when it comes that I want to save the file I've got a message that I can't write it.The folder is probably owned by root, with 644 permission. It means that you are not allowed to write in that folder. You have 2 options:
1)copy or move your files as root to the folder
2)change the ownership to your own user

NB. 1)it's the safest solution, 2) is easier to use, but i don't know if lampp will crash on it. Try it out, and if it doesn't work, you have to move your files with root permission to that folder.

---

### Post by helphope on 2006-08-08
Great. Thanks to you all once again. Eventually I managed to write into the htdocs directory and have the php files running.
Thanks again

:-({|= :-({|= :)

---

