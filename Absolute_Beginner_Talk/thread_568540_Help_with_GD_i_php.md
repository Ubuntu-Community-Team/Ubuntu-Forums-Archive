---
title: "Help with GD i php"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by djknorr75 on 2007-10-05
I am trying to enable GD in PHP5 (I installed PHP with LAMP, and then installed GD with 'sudo apt-get install php5-gd), but even after restarting my server I still get an error when trying to upload a picture:

```
Fatal error: Call to undefined function imagecreatefromjpeg() in /var/www/snapshots/check_image.php on line 114
```

I have a book here that says I need to enable GD with the '--with-gd' configure option.  However, I have not figured out how to do that.  Does anybody know how?  Or, better yet, does anybody know if that will solve my problem?

Thanks

---

### Post by Maxtorm on 2007-10-06
Is GD enabled in php.ini? There should be a line that reads ```
extension=php_gd.dll
```
Make sure there is no ; in front of the line commenting it out. I don't recall the exact location of php.ini off the top of my head (/etc?) but a "locate php.ini" should find it for you.

---

### Post by djknorr75 on 2007-10-06
Apparently, I'm a moron....Upon making the recommended change (even with .so instead of .dll), and restarting my server it still didn't work.  I decided to reboot my computer, and then it magically did.  This was after I reverted the php.ini file back to its original state.

Apparently, when I thought I was restarting my server, I really wasn't doing anything at all.  I was using the 'apache2 restart' command.  Is there something I missed there?  It seems logical to me that calling that would reboot the server, but apparently it takes something else.....

Thanks for your help, though, Maxtorm.

---

