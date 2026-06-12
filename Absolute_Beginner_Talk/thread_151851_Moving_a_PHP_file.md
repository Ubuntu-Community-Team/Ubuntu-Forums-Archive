---
title: "Moving a PHP file"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by truNWA on 2006-03-28
I am relativly new to Ubuntu, but i do alot of programing. I have a php file on my desktop that I want to move to /etc/var/www. I've tried many things in terminal like, but i can't seem to get the command right. Any thoughts?

BTW the file name is Take

---

### Post by trent dillman on 2006-03-28
sudo cp ~/Desktop/Take.php /etc/var/www

---

### Post by truNWA on 2006-03-28
cp: cannot stat `/home/johnathan/Desktop/Take.php': No such file or directory

---

### Post by RedKnight on 2006-03-28
Firstly on your desktop does Take.php appears as:

Take.php
or
take.php

Ubuntu like most linux's is case sensative on files.

Secondly check to make sure its just .php and not got further extensions on it....

It has to be a fault with the "File Naming".

Hope this helps

Stuart.

---

### Post by truNWA on 2006-04-01
ok 

on my desktop the file appears as Take

---

### Post by plord on 2006-04-01
sudo cp ~/Desktop/Take.php /etc/var/www should work

however try  opening a terminal 

and typing 'pwd'  to show where you are. It should display something like 
/home/username

you then need to go into the desktop 'cd Desktop' or 'cd D tabbutton'
then type 'ls' to see files
you should see your file Take.php so you can copy it or move it to where you want.

sudo cp Take.php /etc/var/www/
This is a long way to do as I suspect your trying to cp to /var/www which is the default webroot therefore 

sudo cp ~/Desktop/Take.php /var/www should work

---

### Post by truNWA on 2006-04-02
srry I don't know why i can't seem to get it.... this is what i put in the terminal after going the cd Desktop route.....


sudo cp Take.php /var/www/


I keeps saying missing file destination.

---

### Post by Zeroangel on 2006-04-02
[quote=truNWA]srry I don't know why i can't seem to get it.... this is what i put in the terminal after going the cd Desktop route.....


sudo cp Take.php /var/www/


I keeps saying missing file destination.[/quote]It will usually say that if you forgot to add a space between Take.php and /var/www. Otherwise, it would be very odd for this error to happen, as it 'should' work. Anyways, try running these commands:
```
sudo chown -R $USER /var/www
```to make the /var/www directory writable by you (so you dont have to use sudo every time you want to write to it), then create a symbolic link to it on the desktop:```
ln -s /var/www/ ~/Desktop
``` Then simply drag Take.php into the www 'folder' on your desktop. You can even rename it, move it into your home folder, delete it or whatever else since it's not a real folder, its just a file pretends its the /var/www folder.

---

### Post by dvarsam on 2006-04-02
Hello!

What the people answering to you, DO NOT understand is the following:

YOUR filename is "Take".

THEY Think YOUR file name is "Take.php".

So they are suggesting to you to use this:

cp Take.php /var/www/

The above should NOT work simply because THEY have got your filename wrong...

Try this:

cp Take /var/www/Take.php

The above command should copy the file "Take" into the "/var/www" destination directory _and_ RENAME it at the SAME time to "Take.php".

IF YOU WANT YOUR ".php" FILE TO WORK, YOU MUST RENAME IT, TO END WITH A ".php" extension...

IF YOU DO NOT RENAME IT, DO NOT EXPECT YOUR ".php" TO BE BROWSABLE!!!

Good Luck!

---

### Post by truNWA on 2006-04-04
[QUOTE=Zeroangel]
```
sudo chown -R $USER /var/www
```[/QUOTE]



ok.... i do that but it says too few arguments.](*,)



EDIT:

nevermind, i got it.... thanx for the help

---

### Post by aysiu on 2006-04-04
[QUOTE=dvarsam]
What the people answering to you, DO NOT understand is the following:

YOUR filename is "Take".

THEY Think YOUR file name is "Take.php".[/quote] People are probably under that impression based on the fact the thread is titled "Moving a PHP file."

---

