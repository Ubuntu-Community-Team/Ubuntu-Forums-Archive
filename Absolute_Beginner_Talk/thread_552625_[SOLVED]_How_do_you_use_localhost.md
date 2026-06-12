---
title: "[SOLVED] How do you use localhost"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by New Boy on 2007-09-16
I have installed LAMP and all seems to be OK.
I've also installed phpmyadmin and I've got that working.

Now, before I start working on my database (previously used ASP and MS Access on XP), I thought I would try a simple HTML test page.

My /var/www directory contains:
apache2-default (a folder)
phpmyadmin (a link to /usr/share/phpmyadmin)
testphp.php (a php file)

When I enter localhost in Firefox the above three are listed and clicking on any of them gives the expected result.

Now, noticing that phpmyadmin is a link I created a link (called test) linked to /home/david/internet/test. This folder has a simple html file index.html

When I now enter localhost in Firefox test is not listed.  If I enter localhost/test I get the response:

Forbidden
You don't have permission to access /test on this server.
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at localhost Port 80

I've tried changing the owner of the test link file from my user name to root and that hasn't made any difference.

Where am I going wrong?


----------------------------

Problem now solved - see my final post [below]("http://ubuntuforums.org/showpost.php?p=3383713&postcount=11")

---

### Post by Bachstelze on 2007-09-16
Please do a

```
ls -ld /home/david/internet/test
```

and post the results.

---

### Post by louieb on 2007-09-16
I believe you are going to have to set up a virtual server. Haven't quite figured out all the in and out of apache. But I did install Webmin to give me a GUI. I followed this guide.   [Installing Webmin On Ubuntu Feisty Fawn (7.04) | HowtoForge - Linux Howtos and Tutorials]("http://www.howtoforge.com/installing_webmin_ubuntu_feisty")

---

### Post by Bachstelze on 2007-09-16
What do Virtual Hosts have to do with anything ? This is purely a permissions problem...

---

### Post by louieb on 2007-09-16
> **HymnToLife said:**
> What do Virtual Hosts have to do with anything ? This is purely a permissions problem...
Just a wild guess based on experience. I defer to your expertise. Alway a pleasure to see what you have to say about how to do something.

---

### Post by New Boy on 2007-09-17
> **HymnToLife said:**
> Please do a

```
ls -ld /home/david/internet/test
```

and post the results.

Thanks for your reply - sorry for the delay - I've had a good nights sleep since then.

Results of your code:

drwxr-xr-x 2 david david 4096 2007-09-17 09:16 /home/david/internet/test

---

### Post by Bachstelze on 2007-09-17
And how about this ?

```
ls -l /home/david/internet/test/
```

---

### Post by New Boy on 2007-09-17
> **HymnToLife said:**
> And how about this ?

```
ls -l /home/david/internet/test/
```

That gives the result:

david@david-laptop:~$ ls -l /home/david/internet/test/
total 4
-rw-r--r-- 1 david david 26 2007-09-16 08:10 index.html
david@david-laptop:~$

---

### Post by Bachstelze on 2007-09-17
Permissions are okay. Your Apache must be configured not to allow symlinks following... Anyway, there's a much more elegantway to do this (using aliases) but I can't help you with that, I'm not familiar with Apache configuration in Ubuntu...

---

### Post by New Boy on 2007-09-17
> **HymnToLife said:**
> Permissions are okay. Your Apache must be configured not to allow symlinks following... Anyway, there's a much more elegantway to do this (using aliases) but I can't help you with that, I'm not familiar with Apache configuration in Ubuntu...

I don't know the answer to that: I'll have to do some more Forum searching on Apache configuration.

David

---

### Post by New Boy on 2007-09-18
I've now sorted it.

After spending hours searching the forums, I decided to completely remove LAMP and its componants by following the instructions [here]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-17bb23065563de1df51561a0248d29008a42234f"), and starting over again by installing LAMP afresh.

This still came up with the same problem. :(

Then I noticed [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031"). I didn't even have a file /etc/apache2/httpd.conf, so I created one with 'ServerName localhost' as the only line.  IT NOW WORKS :)

Thanks to everyone to helped.

David

---

