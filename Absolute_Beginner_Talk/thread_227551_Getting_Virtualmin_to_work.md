---
title: "Getting Virtualmin to work"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by rawoo on 2006-08-01
Okay, I've switched to Ubuntu and now want Virtualmin to assist with virtual domains. One problem...Virtualmin requires Apache to be compiled with suexec pointing to / home. Has anyone done this? Detailed help is appreciated.:p 

Thanks,
Richard

---

### Post by Mistraal on 2006-08-23
Anybody?

I would also like to know how to change the default suexec settings.

As ubuntu follows the debian trend of modules maybe there is a switch or something to a2enmod. Dunno.

---

### Post by andydread on 2006-09-28
> **Mistraal said:**
> Anybody?

I would also like to know how to change the default suexec settings.

As ubuntu follows the debian trend of modules maybe there is a switch or something to a2enmod. Dunno.

you have to :-

Open a terminal

$sudo apt-get install fakeroot
$sudo apt-get install build-essential 
$apt-get source apache2
$sudo apt-get build-dep apache2

change to the apache2-2.0.x/debian folder  
$cd apache2-2.0.X/debian 
edit the rules file
$gedit rules
change the following line from
--with-suexec-docroot=/var/www
to
--with-suexec-docroot=/home
save.
cdup one level to the apache2-2.0.x folder
$cd ..
then type 
$dpkg-buildpackage -rfakeroot -b
$sudo dpkg -i ../apache2-2.0.x_i386.deb
then edit the /etc/apache2/apache2.conf file
$gedit /etc/apache2/apache2.conf
uncomment the following line
#AddHandler cgi-script .cgi 
and make it look like this 
AddHandler cgi-script .php .cgi .sh .pl

Hope this helps.

---

### Post by uguwoo on 2008-04-02
In my opinion Virtualmin is the one that needs an overhaul.
If I have to recompile apache (and good luck with that by the way) to make it work with that suexec junk then it is junk too.
I tried Virtualmin and tried to recompile apache on ubuntu and just got a bunch of fatal errors.

The only way you can use Virtualmin with /home is to buy their product and then download their custom apache. (Or do it yourself if you're debian compiler guru).

That's the same with ALL of those control panels. Almost ALL of them require you to download their custom cans of worms so you are then stuck with their proprietary junk.

I am now doing my own sites manually and may even develop my own control panel because all of those existing control panels are just junk for you to BUY! BUY! BUY!

Get it? If you don't know better then BUY IT!

---

### Post by uguwoo on 2008-04-02
Actually the bottom line on that is that SUEXEC is the outdated piece of junk that needs to be upgraded.

I just delete the suexec line because it's a dinosaur invented by paranoid security freaks.

---

### Post by bradmurmz on 2008-07-09
Wow... I went throught the whole recompile precess and it worked... But when I updated my apache a month later from the repository, of coarse the problem was back again. Instead of trying to go through the whole recompile process again I just decided to try a little "hack" that WORKED! I move my site from /home/mysite to /var/www/mysite and then simply added a symbolic link from /var/www/mysite to /home/mysite

> ln -s /var/www/mysite /home/mysite

Worked like a charm!

---

