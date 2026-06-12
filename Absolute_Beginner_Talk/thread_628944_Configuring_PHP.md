---
title: "Configuring PHP"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by kenboyles72 on 2007-12-01
I have downloaded all required packages for php, but don't know how to config it. I have php installed on my windoze box and it already had a recommended php.ini to use, so i didn't have to edit anything. Is there a similar ini file for ubuntu, or what do I need to edit in the ini. Which there are three folders that have php.ini in em; cli, apache2 and cgi. I'm trying to get this to work with Abyss web server, the same that I have installed on my other pc. Abyss configs to run php as cgi/isapi. I got Abyss cofig'd for perl, but can't get php to work.

---

### Post by Dr Small on 2007-12-01
Did you try installing Php from the repositories ?
Also, there is another method (which I use, and works very well), from here:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

Dr Small

---

### Post by kenboyles72 on 2007-12-01
yeah, i installed it through synaptic.

---

### Post by kenboyles72 on 2007-12-01
I looked at your link and I did have xampp installed, but removed it, because I wanted to use Abyss. If I reinstall xampp, can I choose not to start it and use just php, then config abyss to point to php installed by xampp?

---

### Post by Dr Small on 2007-12-01
It should be possible, I guess, but I can not confirm that I have tried it.
You could try it though ;)

---

### Post by p_quarles on 2007-12-01
Your php.ini file is located in:
```
/etc/php5/apache2/
```

---

### Post by kenboyles72 on 2007-12-01
> **p_quarles said:**
> Your php.ini file is located in:
```
/etc/php5/apache2/
```

ok, what do i need to edit in the ini file?

---

### Post by p_quarles on 2007-12-01
Well, I'm not sure how to get it working with Abyss, since I've never used that. My suspicion, though, is that that would involve configuring Abyss, and not PHP.

---

### Post by kenboyles72 on 2007-12-01
well, i setup it up just like my other installation on windoze , except the path to php is different. I configed abyss to point to "/usr/bin/php", which is the path that displayed when I ran "which php" in console. But when I run a php file from a browser, I get a 500 error and in my cgi log for abyss it says "CGI: [/usr/bin/php  ]	URI: /test.php	Broken pipe".

---

