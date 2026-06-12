---
title: "XAMPP install problems..."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jbrevik on 2007-12-08
I seem to be having problems starting xampp....

1. Downloaded **xampp-linux-1.6.4.tar.gz**
2. Ran the following command to extract
```
$sudo tar xvfz xampp-linux-1.6.4.tar.gz -C /opt
```
3. Ran the next command
```
$sudo /opt/lampp/lampp start
```
------------------------------------------------------------------
Result:
```
sudo: lampp: command not found
```

Here is the lampp directory listing

drwxr-xr-x 20 root   root  4096 2007-10-07 02:07 .
drwxr-xr-x  3 root   root  4096 2007-12-08 15:29 ..
drwx------  2 root   root  4096 2004-02-10 22:43 backup
drwxr-xr-x  3 root   root 12288 2007-10-07 02:28 bin
drwxr-xr-x  2 root   root  4096 2004-07-14 07:04 cgi-bin
drwxr-xr-x  3 root   root  4096 2005-10-16 05:43 error
drwxr-xr-x  9 root   root  4096 2007-09-30 02:11 etc
drwxr-xr-x  4 nobody root  4096 2007-05-11 05:40 htdocs
drwxr-xr-x  3 root   root  4096 2003-05-30 16:38 icons
**-rwxr-xr-x  1 root   root 14866 2007-08-31 06:44 lampp**
drwxr-xr-x 10 root   root  4096 2007-10-07 02:28 lib
drwxr-xr-x  2 root   root  4096 2006-04-26 10:46 libexec
drwxr-xr-x 37 root   root  4096 2006-03-14 09:06 licenses
drwxr-xr-x  2 root   root  4096 2007-09-07 07:28 logs
drwxr-xr-x  2 root   root  4096 2007-10-07 02:28 modules
drwxr-xr-x 10 root   root  4096 2007-09-30 04:04 phpmyadmin
drwxrwxrwx  2 root   root  4096 2007-07-15 09:20 phpsqliteadmin
-rw-rw-r--  1 root   root 49555 2007-10-07 01:55 RELEASENOTES
drwxr-xr-x  2 root   root  4096 2007-10-07 02:28 sbin
drwxr-xr-x 15 root   root  4096 2007-10-07 02:07 share
drwxr-xr-x  3 root   root  4096 2005-01-18 13:21 tmp
drwxr-xr-x  5 root   root  4096 2007-09-07 07:28 var
------------------------------------------------------------------------

Any Ideas???

---

### Post by Presto123 on 2007-12-08
For one...you downloaded "Xampp" and you have there "Lamp". I don't know this program, but it looks like incorrect directories.

---

### Post by Dr Small on 2007-12-08
Edit. Just saw that you had already did that...

The only suggestion I can give, for you to try, would be this:
```
sudo su
cd /opt/lampp/
./lampp
```

And see what happens. Maybe something is wrong from Xampp. I haven't tried 1.6.4 yet, so maybe that is a problem...

Dr Small

---

### Post by jbrevik on 2007-12-08
For some reason when the xampp package is untar'ed it creates the lampp directory. I followed the xampp install directions to a tee.

---

### Post by Presto123 on 2007-12-08
Just looking here, try this:

```
cd opt/xampp/lampp
```

Try the code there and see.

OR you could find the file and drag and drop it onto the terminal and it will auto fill the directory...other than that...I don't know.

---

### Post by Presto123 on 2007-12-08
> **Dr Small said:**
> Edit. Just saw that you had already did that...

The only suggestion I can give, for you to try, would be this:
```
sudo su
cd /opt/lampp/
./lampp
```

And see what happens. Maybe something is wrong from Xampp. I haven't tried 1.6.4 yet, so maybe that is a problem...

Dr Small

I think Dr. Smalls Idea trumps mine.

---

### Post by Dr Small on 2007-12-08
Xampp installs to the directory /opt/lampp
I have Xampp 1.6.3 installed and it worked perfectly, by following the instructions on their website. I have not tried 1.6.4, so there may be some problem with their software, which if this is the case, they should be notified as to this problem.

Dr Small

---

### Post by louieb on 2007-12-08
I used xampp in the past nice how to here [HOWTO: (XAMPP) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=223410")

---

### Post by Dr Small on 2007-12-08
Also, my Howto:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

