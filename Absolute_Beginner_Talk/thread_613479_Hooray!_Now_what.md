---
title: "Hooray! Now what?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Brandon! on 2007-11-15
So I got Ubuntu installed with very minimal problems.  Now I have my Vista PC and Linux distro sharing the same desk and they aren't even fighting!  Now that I have this up an running though, I want to know what I should do next.
I would like to use this computer as a dedicated web server for testing etc., and I also want to use it to experiment and learn linux as time goes on.  Is there a good web server application for Ubuntu (preferably a full fledged server with ModRewrite, PHP, MySQL, etc. etc.)?
Also, I saw a couple videos of Beryl installed, and that looked really cool.  Their wiki is currently down, so I didn't see a newbie tutorial for installing it (this will be my first linux package to install).  Is there a good backup source?

I really can't wait to get some free time to dive in to this new operating system.  Besides the web server (that I only use for testing a few times a month), I don't have any real use for this computer, so I'm open to ideas.  It only has a 80gb hard drive so it won't be a media server or HTPC or anything really fun, but it is fast and can handle some work if it needs to, so I'm open to ideas! :D

:popcorn:

---

### Post by Inxsible on 2007-11-15
Beryl is old and no longer supported. If you installed the latest version i.e. 7.10, then you already have Compiz Fusion installed. Look for tutorials on enabling your restricted drivers for the graphics card that you have. Then you can enable compiz fusion and play around with it

---

### Post by kpkeerthi on 2007-11-15
Check out [this ]("http://www.ubuntugeek.com/") to learn cool things to keep you busy.

---

### Post by Brandon! on 2007-11-15
> **kpkeerthi said:**
> Check out [this ]("http://www.ubuntugeek.com/") to learn cool things to keep you busy.
Thank you for the link -- that's exactly the type of thing I'm looking for I think.  I know that Ubuntu is sweet, I just don't know what all it *can* do.

However, this is where I run in to problems with Linux.  I have no idea how everything works so I want to jump in an experiment (I have nothing on this machine so I can format and re-install at a moment's notice).  I went to this page: [http://www.ubuntugeek.com/installing-lamp-using-taskeldesktop-edition.html](http://www.ubuntugeek.com/installing-lamp-using-taskeldesktop-edition.html) to install LAMP.  I used the first command he posted
```
sudo apt-get install apache2 mysql-server php5 libapache2-mod-php5 php5-xsl php5-gd php-pear libapache2-mod-auth-mysql php5-mysql
```Now I have no idea how, but what I understand from this is that it will be installing the following:
Apache2, MySQL server and PHP 5 (with a bunch of extras like XSL, GD2 and)... perfect, no?  I get this error when I run it in the terminal:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2Now I don't know what that means, I don't know if something was partially installed that I need to remove, and I don't know how to fix it so that I can install it.

I also tried the sudo taskel method (sudo: taskel: command not found), and the GUI method lead me to a dead end too.

I'll keep reading through the site tomorrow though.

---

### Post by Brandon! on 2007-11-15
> **Inxsible said:**
> Beryl is old and no longer supported. If you installed the latest version i.e. 7.10, then you already have Compiz Fusion installed. Look for tutorials on enabling your restricted drivers for the graphics card that you have. Then you can enable compiz fusion and play around with it
I didn't realize Beryl was old.  I saw a video on YouTube and it made me want to give Ubuntu a shot.  I'll have to check out Compiz Fusion tomorrow.
I don't believe my graphics card is installed properly yet.  How do I figure it out?  If I look in the Device Manager, I see Radeon 9600 (I have a Radeon 9600 All-in-Wonder).  Does that mean it is installed?  If I go to Restricted Drivers and try to enable my card (which shows up) I get "The software source for the package xorg-driver-fdlrx is not enabled".  I'll so a search tomorrow to figure that out...

EDIT: Scratch that.  I got it to work with a simple Google search.  The only thing that sucks is I had to restart.  I didn't think Linux had that problem, but I guess drivers are hard to swap on the fly :D

---

### Post by Inxsible on 2007-11-15
you might have to install xgl```
sudo aptitude install xserver-xgl
```

---

### Post by TadH on 2007-11-15
yea u need xgl

---

### Post by Brandon! on 2007-11-15
Okay, thanks!  That worked and it's all installing now.

Now what does that mean?  What does aptitude mean and what is xserver-xgl?

EDIT: haha, good joke.  Now where is it in stalled at? lol.  I can go to 127.0.0.1 and see the default files. If I try to do a search for the folder, I come up empty.  I looked in /bin and /usr/bin and saw nothing.  Normally my *nix web servers have a path like /home/httpd/vhosts/.... I did find the apache2 install directory under /usr/lib, but that's not what I'm looking for.

Thanks guys, you are very helpful -- just bare with me :D

---

### Post by Inxsible on 2007-11-15
> **Brandon! said:**
> Okay, thanks!  That worked and it's all installing now.

Now what does that mean?  What does aptitude mean and what is xserver-xgl?aptitude is a command line package manager for Ubuntu. Synaptic behind the scenes does the same thing. 

you will probably not need xgl after Hardy Heron is released in April. At least that's what I have heard. That's because ATI is going to provide better support for Linux users and are going to provide a better driver for their cards.

Hopefully that will all come true. :)

---

### Post by hyper_ch on 2007-11-15
for setting up a server you could start here:

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p4](http://www.howtoforge.com/perfect_server_ubuntu7.10_p4)

---

### Post by Brandon! on 2007-11-15
So I found that the files are located in /var/www (thanks to the link that hyper_ch posted), but I can't write them.  I can log in as root and edit/create all I want, but I don't believe that is the correct way to do it -- is it?  I know that I don't want to chmod 0777 everything either...

---

### Post by hyper_ch on 2007-11-16
depends on how you want to set it up... if you plan only on one 1 site, then I'd rather change ownership of the www folder to your user... if you plan on multiple sites then it probably would be better to install some kind of config panel that will take care for you of users/folders and stuff.

---

### Post by Brandon! on 2007-11-16
Would it be possible to get more information about the cpanel?  Would I need to install software like plesk or cpanel?  I do want more than one site, but I don't anticipate anyone but myself to work on the sites.  The way I work is that I may have more than one open projects (different .coms), but I would only have a single user (myself) accessing them.

In a best case scenario though, I would have this computer set up like a *real* host so that I can get experience with how a server is typically set up.

---

### Post by hyper_ch on 2007-11-16
cpanel and plesk are payware... 

if you want to host multiple sites I recommend to install ISPConfig... it will do what you want on quite a simple way and it's FOSS ;)

I already gave you the link for preparing the server for ISPConfig (well, for setting up apache, php, mysql, postfix etc.). Based upon that howto you can then also easily install ISPConfig.

Or you could install a vmware appliance (never done that):  [http://www.vmware.com/vmtn/appliances/directory/342](http://www.vmware.com/vmtn/appliances/directory/342)

A demo can be found here:  [http://www.ispconfig.org/demo.htm](http://www.ispconfig.org/demo.htm)

Well, that would be a complete solution... you could, of course, also write your own virtual hosts in the apache config. It's not "that" difficult.

---

