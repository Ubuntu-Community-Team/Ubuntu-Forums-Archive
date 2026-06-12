---
title: "Apache installation and use help"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by The Pinny Parlour on 2006-01-20
Hello

I have installed apache as I want to use ubuntu as a file server amongst other things.  I'm not sure how to start it or where it is on the pc though.  Any help would be great

Thank You

---

### Post by hen3rz on 2006-01-20
Hello,

I think I can help.

To access your files simply go to /var/www/ all files inside the www folder can be viewed from [http://localhost/](http://localhost/) and so on.

To start the apache server it really depends on what version you are running. 

**To start apache2** type the following command in the terminal:

```
sudo apache2 -k start
```

**To restart apache2** type the following command in the terminal:
```
sudo apache2 -k restart
```

**To stop apache2** type the following command in the terminal:
```
sudo apache2 -k stop
```

**For more information you can type:**
```
sudo apache2
```

Unfortunately I do not know how to start, stop or restart apache1.3 or any other version but version 2.

> I want to use ubuntu as a file server
As I side note I wouldnt recommend Apache as a "file server" unless you know what your doing because all your files can be viewed by anyone on the internet at [http://yourip/](http://yourip/)

---

### Post by hen3rz on 2006-01-20
> As I side note I wouldnt recommend Apache as a "file server" unless you know what your doing because all your files can be viewed by anyone on the internet at [http://yourip/](http://yourip/)

I forgot to add. Apache can be great as a "file server" if u use .htaccess files to password protect any directory that you wish to keep sensitive information. A tutorial on this can be found in the **apache2** documentation:

[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

for **apache1.3** you can check this out:

[http://httpd.apache.org/docs/1.3/howto/auth.html](http://httpd.apache.org/docs/1.3/howto/auth.html)

---

### Post by The Pinny Parlour on 2006-01-20
Many thanks

I will uninstall apache and install apache 2

---

### Post by The Pinny Parlour on 2006-01-20
Trying to move data into the var.[www.apache2-default](www.apache2-default) and it says I don't have permission.  Any ideas on what I'm doing incorrectly?

---

### Post by bartbes on 2006-01-20
2 things:
1. Place it in /var/www/ not /var/www/apache2-default
2. You have no rights in the /var/www/ dir, use sudo or do sudo chmod -R 777 /var/www/ and maybe, sudo chown -R <username>:<username> /var/www/

---

### Post by The Pinny Parlour on 2006-01-20
ok thanks for your help

I tried drop n drag to /var/www/ but it says I have no permission.

any ideas on what I'm doing wrong?

thanks

---

### Post by bartbes on 2006-01-20
[QUOTE=bartbes]You have no rights in the /var/www/ dir, use sudo or do sudo chmod -R 777 /var/www/ and maybe, sudo chown -R <username>:<username> /var/www/[/QUOTE]

Read this part again....

---

### Post by The Pinny Parlour on 2006-01-20
[QUOTE=bartbes]Read this part again....[/QUOTE]


Thanks for the help

I have read that but I have to say, I don't understand what the heck that means.

---

### Post by The Pinny Parlour on 2006-01-20
It seems I'm getting in way over my head with this.  I really thought it would be easy.   I'm going to go back to windows on this particular machine as it seems that everything I want to do is hard and difficult and needs lots of learning.  I really don't want to, but for the sack of speed and ease I think I'm going to have to.

---

### Post by bartbes on 2006-01-20
have you tried what I said? If yes, what's going wrong then?  give some output

---

### Post by jon_z on 2006-01-20
c'mon, its not that hard.  You have a few options.. You're first one is to move the files in the terminal example:
Terminal moving, basic commands are:
dir  - directory listing
cd - to move to a directory i.e. cd /var/www/
cp - copy cp index.html index.html.bak  (dir would show now that you have index.html and index.html.bak)
mv - move 
to get any help with any command type:
man <command> i.e.  man mv
```
sudo mv whatever_file_you_want /var/www/
```
sudo gives you the root privledge to move things into the folder /var/www/

another possibility is to do in a terminal:
```
sudo chown -R <username>:<username> /var/www/
```
the chown gives you <username>:<username> ownership of that folder, and allows you to do many things to it. this will allow you to always drag and drop

and at last we can open a root browser:

```
sudo konqueror
```
if you are using the KDE user interface (drag and drop)
OR
```
sudo nautilus
```
if you are using GNOME user interface (drag and drop)

don't give up, remember Windows was foriegn once too, but look at this excellent tech support. we are a growing community willing to help each other.

---

### Post by The Pinny Parlour on 2006-01-20
[QUOTE=bartbes]have you tried what I said? If yes, what's going wrong then?  give some output[/QUOTE]


Have I tried what you said?  No.  I don't know what it means or what it does.

Whats going wrong?  alot.  I wish it was easier.

I thank you for your help, but I'm over dealing with code at this point, to much to learn and not easy enough for newbies like myself.  Same old thing linux people hear all the time I'm sure.

I am trying to set up a firewall/gateway for a windows machine .. web server  .. file server .. and network to a windows machine to transfer data to the nix box and vice versa.  All in one box.  For a newbie, it seems way too much.  :)  I had high hopes that I could pull it off but I'm just to new at this Linux.  I was dreaming  lol


Just getting a Primary Slave to recognise was a nightmare, and I still can't write to it. 
[http://www.ubuntuforums.org/showthread.php?t=119351](http://www.ubuntuforums.org/showthread.php?t=119351)

---

### Post by The Pinny Parlour on 2006-01-20
[QUOTE=jon_z]c'mon, its not that hard.  You have a few options.. You're first one is to move the files in the terminal example:
Terminal moving, basic commands are:
dir  - directory listing
cd - to move to a directory i.e. dir /var/www/
cp - copy
mv - move
to get any help with any command type:
man <command> i.e.  man mv
```
sudo mv whatever_file_you_want /var/www/
```
sudo gives you the root privledge to move things into the folder /var/www/

another possibility is to do in a terminal:
```
sudo chown -R <username>:<username> /var/www/
```
the chown gives you <username>:<username> ownership of that folder, and allows you to do many things to it. this will allow you to always drag and drop

and at last we can open a root browser:

```
sudo konqueror
```
if you are using the KDE user interface (drag and drop)
OR
```
sudo nautilus
```
if you are using GNOME user interface (drag and drop)

don't give up, remember Windows was foriegn once too, but look at this excellent tech support. we are a growing community willing to help each other.[/QUOTE]



Thanks you.  That was helpful and worked and explained it to me.

I don't even really know why I want to drag my web site over to /var/www/   I'm trying to get apache going but know I really don't know what to do.  The next step, *shrug* I'm not sure now  lol  I'm such a newbie at this.  

Cheers

---

### Post by jon_z on 2006-01-20
Glad to help, sometimes we assume that everyone understands what we are talking about, glad I was able to break it down for you.  And I'm glad to keep you aboard :)

I touched up the explantion of the commands a bit and fixed my typo

---

### Post by The Pinny Parlour on 2006-01-20
This doesn't work with my HDD primary slave issues though

@ubuntuserver:~$ sudo chown -R server:server computer:///hdb1
chown: cannot access `computer:///hdb1': No such file or directory


I just want to be able to drop and drag files to the slave.  Oh why oh why is it so difficult?

---

### Post by The Pinny Parlour on 2006-01-20
[QUOTE=jon_z]Glad to help, sometimes we assume that everyone understands what we are talking about, glad I was able to break it down for you.  And I'm glad to keep you aboard :)

I touched up the explantion of the commands a bit and fixed my typo[/QUOTE]


Yes thank you.

I will be keeping ubuntu on my personal box but this attempted server box I'm trying to build is going to be ANOTHER crappy windows box on the www.  It's to hard to do what I want with linux.  It's just not easy enough to use and I just don't know what I'm doing.

Thank you all for your help.

---

### Post by Jolva on 2006-01-20
mods please delete this reply

---

### Post by bartbes on 2006-01-20
[QUOTE=The Pinny Parlour]
@ubuntuserver:~$ sudo chown -R server:server computer:///hdb1
chown: cannot access `computer:///hdb1': No such file or directory
[/QUOTE]

Is hdb1 your root drive or a windows/mac/extra/etc. drive?

if it's 2 the path is most likely /media/hdb1 instead of computer:///hdb1
if it's 1 then the path is / but I don't know if it works...
BUT: if it's a NTFS drive you can't change ownership

---

### Post by jon_z on 2006-01-20
NTFS = Windows 2000/XP unless you strictly specified when you installed to use Fat32

---

### Post by The Pinny Parlour on 2006-01-27
Slave drive was  created using win98 boot disc and making it fat32

---

### Post by encompass on 2006-01-29
Bummer... your missing out... you just run those commands at the terminal.
Don't be afraid to ask here.  We can help you.

---

### Post by TomH on 2006-02-06
tom@TomLinux:~$ sudo apache2
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

Any ideas :confused: 

Im stuck lol



[QUOTE=hen3rz]Hello,

I think I can help.

To access your files simply go to /var/www/ all files inside the www folder can be viewed from [http://localhost/](http://localhost/) and so on.

To start the apache server it really depends on what version you are running. 

**To start apache2** type the following command in the terminal:

```
sudo apache2 -k start
```

**To restart apache2** type the following command in the terminal:
```
sudo apache2 -k restart
```

**To stop apache2** type the following command in the terminal:
```
sudo apache2 -k stop
```

**For more information you can type:**
```
sudo apache2
```

Unfortunately I do not know how to start, stop or restart apache1.3 or any other version but version 2.


As I side note I wouldnt recommend Apache as a "file server" unless you know what your doing because all your files can be viewed by anyone on the internet at [http://yourip/](http://yourip/)[/QUOTE]

---

### Post by encompass on 2006-02-06
Did you run the command shown above?  That is how you start and stop apache... it is not too hard.  I set mine up in about 30 seconds.  The hardest part about it all is just the firewall... it that is dead simple.

---

