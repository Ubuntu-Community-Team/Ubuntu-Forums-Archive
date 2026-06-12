---
title: "/var/www Permissions"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by icio on 2007-01-20
I've just installed apache, php and mysql. Everything is ok with the installation but the only way that I can do anything in the web root /var/www/ is by using sudo in terminal because chmod on the directory doesn't seem to work 
- is there something special about that directory or am I just using the command wrong? Thanks for any insight you can provide.

---

### Post by ComplexNumber on 2007-01-20
> **icio said:**
> I've just installed apache, php and mysql. Everything is ok with the installation but the only way that I can do anything in the web root /var/www/ is by using sudo in terminal because chmod on the directory doesn't seem to work 
- is there something special about that directory or am I just using the command wrong? Thanks for any insight you can provide.
leave the permissions as they are. 

why do you want to change the permissions anyway? then people may be able to help.

---

### Post by melancholeric on 2007-01-20
sudo chown [your username here] /var/www

should do the trick.

---

### Post by nsleiman on 2007-01-20
did u try sudo chmod 755 /var/www/* ?

post the output here if u want!

---

### Post by ComplexNumber on 2007-01-20
> **melancholeric said:**
> sudo chown [your username here] /var/www

should do the trick.
that won't do the trick.

> 
did u try sudo chmod 755 /var/www/* ?
neither will that.

---

### Post by konst88 on 2007-01-20
You should add the -R otion to the commands listen above, like this:
```
sudo chmod -R 755 /var/www/
```
But this still forbids to write to this directory.
You may choose 777 instead, but i think it is not so secure...

---

### Post by mcduck on 2007-01-20
I recommend just running 'gksudo nautilus' to open file manager as root whenever you need to copy files to /var/www..

---

### Post by ComplexNumber on 2007-01-20
> **mcduck said:**
> I recommend just running 'gksudo nautilus' to open file manager as root whenever you need to copy files to /var/www..
me too.

**icio**
honestly, you really shouldn't go around changing permissions. its bad practice. as mcduck says, if you need to write to or edit a file, use 'gksudo gedit <filename>'. if you need to do any moving/copying to that area, either use the command line with sudo or use 'gksudo nautilus', although i would tend to prefer the former.

---

### Post by icio on 2007-01-21
The server that I'm running is purely for local development, so security of that directory really isn't much of an issue and definately not enough of an issue for me to have to use work-arounds to edit the directory's contents, so I guess that the best thing to do here is create a launcher for nautilus that will run it as root.

Thanks for all of the suggestions, though.

What is the reason that chmod and chown wouldn't work for the directory /var/www/ ?

---

### Post by Bachstelze on 2007-01-21
sudo chown -R username /var/www
sudo chmod -R 755 /var/www

definitely should do the trick. If it doesn't, please paste the output of  *ls -l /var*. It's definitely a bad idea to have nautilus running as root.

---

### Post by ComplexNumber on 2007-01-21
[quote=icio] What is the reason that chmod and chown wouldn't work for the directory /var/www/ ?[/quote]the reason why the the info in posts 3 & 4 is because sudo "chown [your username here] /var/www" merely changes the permissions of the directory, not the contents of it. "sudo chmod 755 /var/www/*"  won't worl because it only changes the permssions of the directories a level directly below /var/www, and not the contents that they hold.

---

### Post by FyreBrand on 2007-01-29
icio you can make /var/www your own by (replace $user with your user name):
```
$ sudo chown -R $USER:$USER /var/www
```
Since you are using this as a development server it is a very convenient thing to do.  This way I can use Quanta and Kate to directly work in /var/www/foo/bar and not have to sudo my way through life or worse yet use gksudo and nautilus which I think is a very bad idea especially when you're copying files a lot.  A small mistake can create big problems when you run your file manager as root.

I aksed a very similar question in the "Servers and Security" section not long ago.  There were a few really good answers and some sound advice. I would recommend reading that thread (and it's nice and short too).
Here it is: [**Ubuntu Forums - Web Development Security**]("http://ubuntuforums.org/showthread.php?t=326737").  In my first post I also linked to the ApacheMySQLPHP article.  It's a good article to read as well and is fairly short too.

---

