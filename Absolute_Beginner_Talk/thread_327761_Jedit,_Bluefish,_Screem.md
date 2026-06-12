---
title: "Jedit, Bluefish, Screem"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by laforge on 2006-12-29
Ok, I am hopefully hosting a webserver on this machine here but I have a few problems.

I installed apache, and php and mysql (I think), so when I go to [http://localhost](http://localhost) I get a FTP style page.  Probably because I don't have an index file.

I tried to create one with jEdit but the problem is that wont open.

Then I tried Bluefish, I wrote a simple php script just an echo "message".  I tried to save it to /var/www/ but I get an error. "File save error: Cannot write to /var/www/"

I tried Screem next and pretty much got the same error except it said, "Access denied"

I am guess it has something to do with sudo or administration password.  I am fairly new to linux so any help would be appreciated.

Thanks in advance.

---

### Post by angkor on 2006-12-29
Try to save the file to your home folder in Bluefish. After that copy the file to your /var/www/ with sudo:

Open a terminal:

```
sudo cp [file_you_created] /var/www/index.html
```

You will be prompted for your user password.

---

### Post by Gerard Barberi on 2006-12-29
[http://localhost/apache2-default/](http://localhost/apache2-default/)

The index.html file is here.  It used to be located outside this directory in apache's root.

/var/www/apache2-default/ in nautilus.

If you want to

sudo cp /var/www/apache2-default/apache_pb.gif /var/www/
sudo cp /var/www/apache2-default/index.html.en /var/www/

will copy it into the root.  Then you can see it at [http://localhost](http://localhost)

---

### Post by qalimas on 2006-12-29
To be able to write to /var/www run the following:
```
sudo chmod -R 777 /var/www/
```

---

### Post by laforge on 2006-12-29
Ok cool that work thanks guys.

Do I have to save and copy over every time I want to save a file to var/www or is there a way to give bluefish the permisison to do it?

---

### Post by angkor on 2006-12-30
> **laforge said:**
> Ok cool that work thanks guys.

Do I have to save and copy over every time I want to save a file to var/www or is there a way to give bluefish the permisison to do it?

If you do what qalimas suggested bluefish should be able to save files to /var/www.

---

