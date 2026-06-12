---
title: "Apache2 Installed - need help to configure"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-02-19
I have installed Apache2, but I am having trouble configuring it. I tested it by going to a browser page and entering ... [http://localhost/](http://localhost/)

I get a directory, which includes... apache2-default/ 

If I add append apache2-default/ to [http://localhost](http://localhost), I get the standard Apache Test page.

Because I am new to Linux, I don't know if Apache2 installations spread the files across the file system, instead of being in one folder on windows. I was looking throughout the filesystem for the file that I can configure Apache2 on, and then I was looking for [http://localhost](http://localhost) within the filesystem. I would appreciate help on this.

Also, I downloaded user documentation, but I have no idea where it got installed.

I am wondering if most of my problems are related to my little understanding of Linux (in general).

Thank you!

---

### Post by colyn on 2007-02-19
The folder you are looking for is in /var/www/  This is the default folder for web files.

---

### Post by Bachstelze on 2007-02-19
Just put your HTML files in /var/www, you can then browse them from [http://127.0.0.1](http://127.0.0.1) - or [http://localhost](http://localhost), it's the same thing.

---

### Post by rbradshaw on 2007-02-19
Thanks for the quick replies.

Question - One would think the Apache Test page (html file) would be in var/www. Where should the Apache test page be?

---

### Post by Bachstelze on 2007-02-19
/var/www/apache2-default

You're automagically redirected there if there's no index file in /var/www

---

### Post by n8bounds on 2007-02-19
btw, the config files for apache2 are in 
```
 /etc/apache2/ 
```
like all well behaved debian packages, it keeps its configs in the /etc/ folder

---

### Post by nick.inspiron6400 on 2007-02-20
Good advice, also how do other people see my web pages?

Nick.

---

### Post by rbradshaw on 2007-02-20
After installing Apache2, I created an index.html file and wanted to save it in /var/www, but I received file permissions. Is it typical on Linux to have file permissions preventing users from saving files in a folder? Did Apache2 installation protect the folders so nothing would be copied into them? Doesn't make a lot of sense because the /var/www folder is there to copy html files into it.

I have been looking on how to change folder permissions. I assume there is a GUI in addition to the command. Any advice would be appreciated. Thanks.

---

### Post by jbeamer on 2007-02-20
I am having the exact same issue with permissions in /var/www.  I installed Apache2 under my user ID and not Root and I think this is the issue.  I have not had any luck finding the command to grant permissions to my ID

Still very new to Ubuntu,
John

---

### Post by Bachstelze on 2007-02-20
What do you mean, you didn't install Apache as root ?

---

### Post by jbeamer on 2007-02-20
Sorry for the confusion my post was not very clear. 
I installed Apache2 usint the sudo command but I still can't create files in the /var/www folder

---

### Post by Obor on 2007-02-20
i think /var is owned by root so you will need root privileges to do things there. If you want GUI then open nautilus as root i.e Alt-F2 and gksudo nautilus

To change permissions for the www you should:
chmod -R 755 /var/www

---

### Post by rbradshaw on 2007-02-20
I installed Apache2 from Synaptic GUI, thus the installation probably did not ask me about root.

When I log onto Ubuntu, is through the GUI interface / login screen. I have always been logged in as rbradshaw. I am going to see if I can log in as root from the GUI. If I log into rbradshaw through the GUI, can I change to root from the command line? How? I am going to try to log into root from the GUI. If I can do this, my guess is I should de-install Apache2 (not sure how to do this yet) as rbradshaw, and re-install it as root.

Your thoughts?

---

