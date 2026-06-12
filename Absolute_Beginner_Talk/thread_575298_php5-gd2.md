---
title: "php5-gd2"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-10-13
Greetings, I will try to be as exact and explanatory as possible, in hopes of getting a few suggestions as to what I should do to solve my problem.

I just setup Apache2, Php5, MySQL and PhpAdminPanel, all from the repositories, following this tutorial:
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

This is my first time to setup a webserver in this fasion, as I normally use XAMPP, but I decided to try it from the repositories this time.

I *have* installed php5-gd from the repositories, restarted apache2 with:
```
sudo /etc/init.d/apache2 restart
```

Created a file to use gd2 functions in Php, taken from Php.net that looks identical to this:
```
<?php
header("Content-type: image/png");
$im = @imagecreate(110, 20)
    or die("Cannot Initialize new GD image stream");
$background_color = imagecolorallocate($im, 0, 0, 0);
$text_color = imagecolorallocate($im, 233, 14, 91);
imagestring($im, 1, 5, 5,  "A Simple Text String", $text_color);
imagepng($im);
imagedestroy($im);
?> 
```

And ran it in the browser, and I get this:
> [http://localhost/gd.php](http://localhost/gd.php)

I have no idea what else to do, so any help would be most appreciated!

Dr Small

---

### Post by [S|G] on 2007-10-15
We can't really help you if you provide a url pointing to localhost ;)

---

### Post by Dr Small on 2007-10-15
I wasn't posting a link to localhost. I was posting the output of gd.php.
That in the quote is exactly what I see in my browser. Letting you be able to access the file on my pc would do no good, as you would get the same output.

---

