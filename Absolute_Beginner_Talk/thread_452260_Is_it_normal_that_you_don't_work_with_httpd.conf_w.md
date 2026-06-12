---
title: "Is it normal that you don't work with httpd.conf when using Linux Apache?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-05-23
I have always learnt how to configure Apache on Windows by editing the **httpd.conf **file.
This file no longer look like how it used to is this normal?

I installed my LAMP on Ubuntu Desktop with this method:
```
sudo aptitude install php5 apache2 mysql-server
```

This guide tells one to use **/etc/apache2/apache2.conf** file it won't accept the extra lines I'm used to when working in **httpd.conf**.  Help, plz!!
[https://help.ubuntu.com/community/ApacheMySQLPHP#head-6aac570a36ae91754513949f6b2d1df5e61fe5ac](https://help.ubuntu.com/community/ApacheMySQLPHP#head-6aac570a36ae91754513949f6b2d1df5e61fe5ac)

[COLOR="Red"]What I want is to add this line to my httpd.conf file.  But doing so for the file and to the apache2.conf file does nothing.[/COLOR]
> AddType application/x-httpd.php .html

---

### Post by Viskovitz on 2007-05-23
Hi jingo, apache2.conf **is** the file to edit to change apache config settings. Last week I installed wordpress in my edgy and so had to install apache+mysql+php. I added this line to that file:

<code>
AddType application/x-httpd-php .php .phtml
</code>

and also made a symlink from /etc/apache2/mods-available/php5.load to /etc/apache2/mods-enabled/php5.load

This will effectively load php module into apache. Also, remember to restart apache!!
<code>
sudo /etc/init.d/apache2 restart
</code>

Hope that helps :)

---

### Post by jingo811 on 2007-05-23
what's a symlink and how do I make a symlink?

---

### Post by darkworld on 2007-05-23
I didnt have to do any of that stuff. I used too but apache2 php module does it all for you. Up and running with very little to do. Change php.ini for php.ini-recommended maybe. that was about it.



> Apache2ctl start is another difference!!!!

---

### Post by jingo811 on 2007-05-23
Yeah my basic Apache+PHP files worked also right away when I started the web server.
But the line change which usually goes into httpd.conf is to make all *.html files go through the PHP interpretator.  So I don't have to name my PHP script files with an *.php extension.

That's what I want to accomplish.  Man I thought LAMP would be easier than WAMP since active Linux servers are in majority in the world ~70%.  But boy am I wrong :( LAMP is more complicated.

---

### Post by Wim Sturkenboom on 2007-05-23
Your '*it won't accept the extra line*' is not a very clear dexcription of the error. Does apache give an error when you start it or can't you save the file after editing (I need root permission on my slackware system to save the file).

---

### Post by jingo811 on 2007-05-23
I don't really understand your question?  But this is the situation.

**1.)** I install LAMP the aptitude way.
**2.)** I test a PHP script I made earlier called multiplication.php - It works!
**3.)** Now I want to configure my apache2.conf so that my renamed multiplication.html can recognize and process the PHP script.
**4.)** Adding that extra line to my httpd.conf and apache2.conf files does nothing compared to when I did that in WAMP.  Instead of printing a multiplication table in the web browser I get this instead:

> "; /*------------------------------*/ // Kolumn rubriker /*------------------------------*/ print "" . ""; for ($col=1; $col<=10; $col++) { print "" . $col . ""; } print ""; /*------------------------------*/ // Rad rubriker /*------------------------------*/ for ($row=1; $row<=25; $row++) { print "" . "" . $row . ""; /*------------------------------*/ // Varannan färgat /*------------------------------*/ if ($row%2) { $color_row = "lightgray"; } else { $color_row = "olive"; } /*------------------------------*/ // Tabellen /*------------------------------*/ for ($col=1; $col<=10; $col++) { print"" . $row*$col . ""; } print ""; } print ""; ?>

**5.)** Apache doesn't really complain but I can see something doesn't compute.  Understand me now?

---

### Post by Viskovitz on 2007-05-23
Make sure it's not a spelling mistake!

You said you wrote this:

AddType application/**x-httpd.php** .html

when you have to write this:

AddType application/**x-httpd-php** .php .html .htm

Make this changes, restart apache and see if it works, please :)

---

### Post by jingo811 on 2007-05-23
You were right I misstyped and I saw it already had such a line #commented out however.  I played around with a bunch of combinations and restarted all the time.  It didn't take :(

I think something is messed up with my Linux equivalence for this whatever that is....
LoadModule php5_module "C:\\Program Files\PHP\php5apache2_2.dll"

I don't know where to go from here, I found some additional probelms with my MySQL regarding having 2 folders php4 and php5 when I only chose to install one. :(
Maybe I need to do a full cleansing of LAMPP since I had XAMPP before which screws things up now.

---

