---
title: "apache2 and php4"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by tgone on 2006-04-17
Hello,

1. I installed Apache2 and it works fine. However, I cannot find the correct httpd.conf file. I tried edting one located in my /etc/apache2 dir but it is read-only. I tried changing the permissions but that didn't work. Am I edting the right httpd.conf file? Keep in mind that I'm used to developing LAMP on Windows where everything for Apache is in one directory. 

2. I installed PHP4 from the package manager. It didn't give me any error messages and Apache shows that it's installed. I can't find it on my system though. the command "which php" doesn't return any results. Any ideas?

Thanks for any help!

---

### Post by bitoiu on 2006-04-17
Hi,

See if the problem is the file you're using. In apache2 it's usually **apache2.conf** instead of the old httpd.conf.

Hope it helps

---

### Post by echo $USER on 2006-04-17
And for question number two, your php.ini file is under the /etc directory.  Save this:
<?
phpinfo();
?>
as test.php in your /var/www directory and pull it up with firefox.  If you get an error php is not installed.

---

### Post by tgone on 2006-04-17
[QUOTE=bitoiu]Hi,

See if the problem is the file you're using. In apache2 it's usually **apache2.conf** instead of the old httpd.conf.

Hope it helps[/QUOTE]

I opened /etc/apache2/apache2.conf - but it's read-only.

I don't think this is the right conf file because I don't see a default directory defined anywhere, and Apache appears to be serving files from /var/www - I don't see this dir referenced in the conf file...

---

### Post by echo $USER on 2006-04-17
It's split up because that's the way debian installs it.  It's broken down into like four files: apache2.conf, httpd.conf, maybe something called port.conf, and other files like sites-enabled, etc.

You can change the default directory in the sites-enabled.conf, but I could be wrong.  Just search the forums for more answer; I'm at work using windows so I don't know off the top of my head.  Just make sure you copy all the original .conf files before you edit them.

Oh and to open a read only file to edit it enter this into the terminal:
sudo gedit /path/to/file
Then it ask for the root passwd.

---

### Post by tgone on 2006-04-17
[QUOTE=echo $USER]It's split up because that's the way debian installs it.  It's broken down into like four files: apache2.conf, httpd.conf, maybe something called port.conf, and other files like sites-enabled, etc.

You can change the default directory in the sites-enabled.conf, but I could be wrong.  Just search the forums for more answer; I'm at work using windows so I don't know off the top of my head.  Just make sure you copy all the original .conf files before you edit them.

Oh and to open a read only file to edit it enter this into the terminal:
sudo gedit /path/to/file
Then it ask for the root passwd.[/QUOTE]

/etc/apache2/sites-enabled/000-default.conf is right. But what about PHP? I can run PHP scripts via Apache but I can't find where it's installed on my computer. I noticed that phpinfo() says that the Server API is "Apache 2.0 Handler" - which is different from my Windows installation. This seems very weird to me.

Thanks for the help. Much appreciated.

---

### Post by tgone on 2006-04-17
nevermind, I didn't realize that you have install the php-cli package to access php from the command line.

---

