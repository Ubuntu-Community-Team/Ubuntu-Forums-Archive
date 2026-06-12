---
title: "apache, php problem..."
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-03-27
I have a problem. Every time that I try to load a php file with my browser I get a prompt that asks me if I want to download the file. Why does it do this. I installed everything correctly and I get no errors. html files work perfectly but when I run the php files I get  a download prompt. Does anyone know what is going on and how I can fix it. It was working perfectly before but this happened when I tried to uninstall php5 and reinstall php4. I have no clue on what could have happened. Another thing, when I try to browse into the /var/www directory it does not show the directory structure. I get  a prompt to download a file that does not exist in the directory. I even deleted the directory and then created a new www directory and I still get the same problem. It is just some mysterious file. Thank you for any help that you can give me.

---

### Post by dvarsam on 2006-03-27
Can you please tell me how did you manage to make ".html" files work in your PHP?

Thanks.

---

### Post by dvarsam on 2006-03-27
What "apt-get install" packages did you install to make it work?

Can you please tell me?

Thanks!

I am desperate man, lets compare what you did & what I did, because I have ".php" files working perfectly, but NOT ".html" files working...

& you have ".html" files working but NOT ".php"...

What an irony, heh....????

---

### Post by simon_is_learning on 2006-03-27
I remeber once that I had the sam issue, but it worked when I typed 127.0.0.1 
instead of localhost.

Maybe it's your configuration but try that first =)

---

### Post by Ginger The Cat on 2006-03-27
This thread is very similar and they seemed to resolve the problem

[http://www.ubuntuforums.org/showthread.php?t=147063](http://www.ubuntuforums.org/showthread.php?t=147063)

Cheers

Mike

---

### Post by adamkane on 2006-03-27
You may have inadvertantly installed apache1.3 along with apache2 files. Which version of Apache shows up when you browse to localhost?

You have to make sure that you only install apache2 files and do not install any apache1.3 files, otherwise you will end up with a mixed configuration. It is difficult to completely uninstall apache1.3, and get apache2 working.

Pick one of these combinations, and stick with it.

apache2 + php5 + mysql4.1
apache2 + php5 + mysql4
apache2 + php4 + mysql4.1
apache2 + php4 + mysql4

You can start with something like this:

```

sudo apt-get install apache2 php5 mysql-client-4.1 mysql-server-4.1 libapache2-mod-auth-mysql libapache-mod-php5 php5-mysql

```

---

### Post by dvarsam on 2006-03-27
> 
apache2 + php5 + mysql4.1
apache2 + php5 + mysql4
apache2 + php4 + mysql4.1
apache2 + php4 + mysql4

apt-get install apache2
apt-get install php5
apt-get install mysql-client-4.1
apt-get mysql-server-4.1
apt-get install libapache2-mod-auth-mysql
apt-get install libapache-mod-php5
apt-get install php5-mysql


I have installed ALL the above & in addition:

1. apt-get install phpmyadmin
7. apt-get install mysql-admin

But, unfortunately, I do NOT get to run ".html" files....

ONLY ".php" ones...

Any ideas?

---

### Post by grim918 on 2006-03-27
ok, I got it working. Thank you Ginger The Cat. That thread was very helpful and solved my problem. If anyone else is having similar problems they should go read the thread.

[http://www.ubuntuforums.org/showthread.php?t=147063]("http://www.ubuntuforums.org/showthread.php?t=147063")

---

### Post by grim918 on 2006-03-27
To dvarsam:

htm and html files should work on any web browser (from what I know). 
Here are the packages that I installed:
> 
sudo apt-get install apache2
sudo apt-get install php4
sudo apt-get install php4-gd

If you are still having problems then you should take a look at the link I posted above (thanks to Ginger the Cat). It solved my problems.

---

### Post by adamkane on 2006-03-27
Have you tried what is described in thread 147063?

---

### Post by dvarsam on 2006-03-27
[QUOTE=adamkane]Have you tried what is described in thread 147063?[/QUOTE]

Yes, I have tried it out...

Still, got nothing...

What I did NOT have installed compared to "grim918", were:

sudo apt-get install php4
sudo apt-get install php4-gd

I just did & Restarted apache again,...to get NOTHING...

I am trying to run the following:

<html>
<head>
<title>PHP Test</title>
</head>
<body>
<?php echo '<p>Hello World</p>'; ?>
</body>
</html>

Can you guys please try save the above as "test.php" & place it to your "/var/www" folders to see it if it runs?

What if it is the case that the above "code" is wrong?

Thanks.

---

### Post by dvarsam on 2006-03-27
[QUOTE=grim918]I have a problem:
Every time that I try to load a php file with my browser I get a prompt that asks me if I want to download the file.
Why does it do this?
I installed everything correctly and I get no errors. html files work perfectly but when I run the php files I get  a download prompt...
Does anyone know what is going on and how I can fix it?
It was working perfectly before but this happened when I tried to uninstall php5 and reinstall php4.
I have no clue on what could have happened...
[/QUOTE]

When I edited the "/etc/apache2/mods-available/php5.conf" file, to add the ".html" pages to open in the end of the follwing line:

Before:
AddType application/x-httpd-php .php .phtml .php3

After:
AddType application/x-httpd-php .php .phtml .php3

And then Restarted my Ubuntu, I got the same proble like you just described...(the save-as dialog appeared...)

_Question 1_:
Did you put things back to normal?

Because I then went & removed the ".html" part from that line...

_Question 2_:
Why do I have to add the ".html" part to both files:

1. Inside "/etc/apache2/mods-available/php5.conf"
2. Inside "/etc/apache2/apache2.conf"

Why?

Am I doing something wrong here?
Because it doesn't look good to me, to double-declare the SAME thing, in 2 separate files...?

I have installed php5, NOT php4 if that makes a difference...

Thanks.

P.S. Can somebody give me provide a copy of your above 2 files: 1 & 2?
       Hopefully it might help me work things out...

---

### Post by dvarsam on 2006-03-27
Sorry, made a typo:

After:
AddType application/x-httpd-php .php .phtml .php3 .html

---

