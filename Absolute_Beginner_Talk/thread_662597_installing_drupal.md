---
title: "installing drupal"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by synistics on 2008-01-09
All installed up to the point of making the web databases.

I head to the drupal install and it does what it needs to do, but is stopped by a permission issue.  It needs R/W for the file settings.php

I change the settings and the message persists. I tried it in the GUI I tried from the command line  *chmod a+w settings.php*

file reference

sites/default/settings.php 

site reference:

[http://www.howtoforge.com/multisite_drupal_installation_ubuntu](http://www.howtoforge.com/multisite_drupal_installation_ubuntu)

Some guidance would be appreciated.

TIA

---

### Post by shareMenaPeace on 2008-01-09
Hi, 
you chmoded to 777?

YOu can also use a script moment

---

### Post by shareMenaPeace on 2008-01-09
If this still not function create a file and past this

```

<?php
chmod ("/somedir/somefile", 755);   
?>

```
upload it and run it - do not forget to delete it afterwards (wait till after install procedure).

Cheers


ps.
I installed drupal yesterday :D


:popcorn:

---

### Post by stalker145 on 2008-01-09
I just reinstalled my Drupal last night after moving everything over to a dedicated web server and off of my desktop. I ran into a similar problem with permissions and ended up throwing a tantrum and simply 777'ing the entire Drupal directory. 

OK, probably not the most secure thing I've ever done, but eh...

Anyway, did you guys know Drupal is in the Ubuntu repos now? I stumbled across that *somewhere* on the forums last night when I was working through my install. It's a bit behind on all the updates, but it makes me all warm and fuzzy-feeling to know that my Drupal install is blessed by the programmers here :D

---

### Post by synistics on 2008-01-09
what is 

***chmoded to 777***

 or

777ing

---

### Post by taurus on 2008-01-09
> **synistics said:**
> what is 

***chmoded to 777***

 or

777ing

```
man chmod
```
Would give you the manpage for chmod command and its options.

---

### Post by synistics on 2008-01-09
found a better chmod explanation page

[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

that was the good news.

I re-set through the GUI, I chmod through the command, I am still getting the same issue

***The Drupal installer requires write permissions to ./sites/default/settings.php during the installation process.***


Currently searching HD to see if there are more than one instance of settings.php

---

### Post by stalker145 on 2008-01-10
> **synistics said:**
> ***The Drupal installer requires write permissions to ./sites/default/settings.php during the installation process.***

OK, I'm *definitely* not the CLI pro here, so someone chime in if I dork this up...

Assuming that your site is, in fact, installed to the above directory, you have already entered```
chmod 777 ./sites/default/settings.php
```into the terminal and are still coming up with the same problem?

Maybe toss sudo in for good measure if it sontinues to give you grief.

---

### Post by synistics on 2008-01-10
the ultimate issue was that there were multiple settings.php and I was resetting all but the correct one.

When I got to the correct one I was able to move on to the next issue. 

The drupal that installed from Synaptics went into the etc/ folder

The settings it was looking for was in the var/www/drupal/sites/ folder

so all the chmod in the world will not work when you are doing the wrong file!

---

### Post by stalker145 on 2008-01-10
> **synistics said:**
> the ultimate issue was that there were multiple settings.php and I was resetting all but the correct one.

When I got to the correct one I was able to move on to the next issue. 

The drupal that installed from Synaptics went into the etc/ folder

The settings it was looking for was in the var/www/drupal/sites/ folder

so all the chmod in the world will not work when you are doing the wrong file!

It's good to hear that you found the right one and got moving. How are you liking Drupal so far? I've been using it for about the last three months and am amazed with the amount of add-ons and cool things that you can do with it.

Well, enjoy :D

---

### Post by noiseordinance on 2008-05-14
I got the write permissions enabled through terminal via help from a tutorial using the command:

sudo chmod o+w sites/default

However, I'm at a point now where I need to remove write privileges but I'm not sure how to do it (and the tutorial doesn't say).

Anyone know?

---

### Post by noiseordinance on 2008-05-14
No love? Someone out there has to know about chmoding...

---

### Post by stalker145 on 2008-05-16
> **noiseordinance said:**
> No love? Someone out there has to know about chmoding...

Maybe ```
sudo chmod o-w sites/default
```It would be logical (to me, anyway) that if one gives write permissions with +w that one could remove said permission with -o. ;)

```
man chmod
```

---

### Post by Yfrwlf on 2008-06-10
> **stalker145 said:**
> Maybe ```
sudo chmod o-w sites/default
```It would be logical (to me, anyway) that if one gives write permissions with +w that one could remove said permission with -o. ;)

```
man chmod
```

Correct.  If you want, you can simply use Nautilus or another file manager and go to file properties and change the permissions there using the GUI method.  If you don't own those files, you will not be able to change them.  To change another's files, you can launch a root/administrator nautilus session by installing the nautilus-admin plugin (and the restarting nautilus or logging out and back in), or by opening a terminal and typing in:
```
gksu nautilus
or
sudo nautilus
```

To use the command line method though:

You have [1st letter(s)][symbol][lastletter(s)]

For the first letter:

u=user
g=group
o=other
a=all three

Then the symbol:

+ add
- subtract

Then the last letter:

w=write
r=read
x=execute

So to allow anyone and everyone to be able to do anything they want to the settings.php file, while in that directory, you'd run:

```
chmod a+rwx settings.php
```

In Drupal's case, it wants you to allow the [www.-data](www.-data) user to modify the settings.php file and also that ./sites/default directory I think, so you can do this by making the files be o+wxr or whatnot, or you can change the owner of those files to the www-data owner with the chown command.

To see the ownership and file permissions of a file or subdirectory in your current directory, you could use the following command:

```
ls -l
```

You may see something like: drwxrwxr-x

The first bit is a "d" if it's a directory.  The second three bits are for permissions for the user, the next three are group, and the final three is for "all other users", and in the above case other users do not have write access.

If you install Drupal from the repos, you'll have to track down the files yourself, but if you install it from their downloadable package you'll be able to put everything where you want (/var/www by Apache's default), but you'll need to install Apache and MySQL in that case.

---

### Post by jmendez2 on 2008-06-10
Hi all,

I just finished installing Drupal and want to see its capabilities.  I was wondering if anyone has a Drupal website that I could look and see what could be achieved?

Thanks!

---

### Post by Yfrwlf on 2008-06-11
> **jmendez2 said:**
> Hi all,

I just finished installing Drupal and want to see its capabilities.  I was wondering if anyone has a Drupal website that I could look and see what could be achieved?

Thanks!

Teh Googly provides. ^^

[http://highervisibilitywebsites.com/node/42](http://highervisibilitywebsites.com/node/42)

---

### Post by jmendez2 on 2008-06-11
great, this is exactly what I was looking for!

Thanks!

---

