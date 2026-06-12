---
title: "CLI: sudo nano and editing/viewing directorires"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by RavUn on 2007-08-07
I'm going through one of the ubuntu tutorials and trying to setup Apache and it says:
> then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to edit

```
/etc/apache2/apache2.conf
```

I type sudo nano /etc/apache2/apache2.conf and it says "sudo: nano: command not found"
Am I doing something wrong?

Also, I've seen places say to look in /etc/blahblahblah/... but how do I get there?  I type that in the command line and it says -bash /etc/blahblahblah/...: Permission Denied.  Am I supposed to type something before that?

How do I look in directories or manage stuff in directories, like /var/www/html and all of that also? 

Please help with links or comments.  I've been searching all night to get everything setup and it's exhausting since everything isn't in one place.

---

### Post by Inxsible on 2007-08-07
you probably dont have nano  installed. did you try ```
gksudo gedit /etc/apache2/apache2.conf
```

to navigate to a directory from a terminal you need to put cd command before the path. like so

```
cd /etc/blah/blah
```

---

### Post by Kingsley on 2007-08-07
Type cd to go into directories. Type ls to see what's in the directories.

---

### Post by bikeboy on 2007-08-07
Nano is installed by default, so I would find it hard to believe it isn't installed. Check the capitalisation and that you don't put quotation marks in. Of course if gksudo gedit works then use it for now, it's easier to work out.

---

### Post by Dr Small on 2007-08-07
You could always use the substitute of nano, which is pico, and it will do the same thing, incase you don't have GUI to run gedit.

Dr Small

---

### Post by RavUn on 2007-08-08
I'm doing it from a virtual appliance so perhaps it's not installed, but it's the ubuntu 7.04 LAMP server.  I don't have a GUI so no gedit and neither sudo nano nor sudo pico work.  It says:
```
sudo: pico: command not found
```
and I typed exactly:
```
sudo pico /etc/apache2/apache2.conf
```
```
sudo nano /etc/apache2/apache2.conf
```
Is there a way to install nano?

---

### Post by bikeboy on 2007-08-08
```
sudo apt-get install nano
```

---

### Post by RavUn on 2007-08-08
man, linux makes me feel small.

Thanks.  I will give it all another shot when I get home.

---

### Post by RavUn on 2007-08-08
what about creating a directory?  I cannot restart apache since /home/user/public_html does not exist but I don't know how to create it.  

Also, how to I go to a website.  It says to go to [http://localhost](http://localhost), but how do I do this?

Sorry for the dumb questions but I can't find anywhere that has dumb answers.  They include all the commands for the harder stuff but not stuff most people already know.

---

### Post by ThrobbingBrain66 on 2007-08-08
To make a directory:
```
mkdir /home/user/public_html
```

Lynx is a text-only browser
```
sudo apt-get install lynx
```
I've never used it before so I don't know the exact syntax, but that should be a good start for you.

---

### Post by kerry_s on 2007-08-08
sudo apt-get install mc gpm

will make your life in command much easier, i also would reccomend links2.

sudo apt-get install links2

mc is a file manager, editor, all around fantastic tool.
links2 is a web browser, it does not require X
running straight links2 will put it in text mode.
useing links2 -g google.com is way better.

---

