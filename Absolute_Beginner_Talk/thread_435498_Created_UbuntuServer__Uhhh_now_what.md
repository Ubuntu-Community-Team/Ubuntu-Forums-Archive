---
title: "Created UbuntuServer / Uhhh now what?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by wh33t on 2007-05-07
Ok so I got the 6.10 Iso and installed the LAMP version onto an old P3-450 I have kicking around the house. Apparently it already has Apache Mysql and PHP running on it. 

How do I now administer each of these servers? I am used to doing it through some sort of web based panel. Is it possible to set something like this up? Webmin or something maybe?

Can someone also please tell me what firewall UbuntuServer uses by default.

Thanks so much in advance.

---

### Post by Nythain on 2007-05-07
webmin would be a GREAT solution to your situation. it is available for linux on thier website, and handles just about every server you can think of... from a nice web interface, but im sure you already know that since you brought it up :)
unfortunately its not available in the repos for some reason, so you will have to download from thier site and install yourself... also if its a headless machine, setting up ssh would be a good idea

the firewall ubuntu comes with is iptables... im not the most familiar with how to use it in terminal, but there is a gui for it called firestarter

---

### Post by wh33t on 2007-05-07
Hrm... well there is a monitor and keyboard connected to it. I just tried to FTP into it with my username but I dont think FTP is running. How would i get webmin on there? There isn't any graphical desktop :(

---

### Post by wh33t on 2007-05-07
Ok well i installed Lynx (text web browser) I will download the Webmin.deb file. but how do install it?

---

### Post by Nythain on 2007-05-07
you could download the source from thier site on another machine, burn to cd, extract on your server somewhere, and install manaully... im not to familiar with web browsing from command line and the wget command or i would help more that way...

as far as ftp'ing to the server, its not gonna work default out of the box, i think its gonna take a little bit of installing (if not already) and configuring proftp, or whatever ftp deamon you like best... 

if you arent familiar with command line administration of linux you CAN install a desktop gui ontop of your server install... sudo apt-get ubuntu-desktop, or xubuntu-desktop, or kubuntu-desktop... or just install the base desktop environment like sudo apt-get install kde-core or gnome-core if you dont want all the extra desktop software

---

### Post by bikeboy on 2007-05-07
wget [http://website.address](http://website.address) will download a file.

sudo dpkg-i file.deb will install a deb file.

Pretty sure that webmin is a simple tar.gz install though, check their readme and you should get everything you need.

---

### Post by wh33t on 2007-05-07
I think I hate linux. Why is it so difficult to do anything? Is there a rant section on these forums?

---

### Post by Nythain on 2007-05-07
so im taking it sudo dpkg -i /path/to/webmin.deb didnt work for you???

---

### Post by wh33t on 2007-05-07
I did manage to download webmin using lynx

I then typed in dpkg --isntall webmin.deb, and it tells me its missing some dependecies... Isn't the point of the package manager to handle dependecies?

Furthermore, the webmin website does not tell me if after i install webmin if it will be running or not. I assume its not, and I try to go in over the web and port 10000 and it doesn't appear to be running.

So after searching it Google it says to try /etc/webmin/start , no file found...

Ok so I assume it never got installed. 

So I try to apt-get install the dependecies files that webmin requires. They aren't found. YAY!

---

### Post by Wiebelhaus on 2007-05-07
> **wh33t said:**
> I think I hate linux. Why is it so difficult to do anything? Is there a rant section on these forums?

edited , nm.

---

### Post by wh33t on 2007-05-07
I dont have a graphical interface. The machine is fairly old and I'm tyring to do the server thing. And I have read that documentation, and I have Ubuntu running on my laptop quite nicely graphically.

---

### Post by Nythain on 2007-05-07
the problem with installing things outside of the actuall package manager (aptitude) is the fact that YOU have to take care of dependencies... did you make sure to enable all the repositories in your /etc/apt/sources.list by uncommenting the ones starting with #... what depencies are unment... and yeah, dpkg wont install software if you dont meet the dependencies because the software wont run without them.

when dpkg actually installs it, it should set it up in the process and automatically start it... as for testing it... point your browser to [http://your.ip.address:10000](http://your.ip.address:10000) or [http://localhost:10000](http://localhost:10000)

the appropriate command google should have told you is something like
```

sudo /etc/init.d/webmin start

```
[http://doxfer.com/Webmin](http://doxfer.com/Webmin) might give you a bit more info and help... if you havent already visisted there yet

---

### Post by wh33t on 2007-05-07
Ill try uncommenting the sources list. 
Thanks for your help so far man. I appreciate it.
Also, when I'm installing something using apt-get (should i be using aptitude instead?) do I have to say apt-get install somelibr-xx.xx or can i just say apt-get install somelib? do I require the version numbers?

---

### Post by wh33t on 2007-05-07
Ok I am missing

libauthen-pam-perl
libmd5-perl

So how would I install those?

---

### Post by Nythain on 2007-05-07
ok, both of those are in my repositories... im running feisty...

ummm... lets seee... you can use sudo aptitude install or sudo apt-get install, wichever one you prefer
make sure you sudo it.
no you dont need the version numbers usually, unless they are part of the deb package name.

sudo aptitude search packagename will show you wether or not its available in the repos you have in your sources.list file

to install the files you mentioned just try
```

sudo apt-get  libauthen-pam-perl  libmd5-perl

```
that should do it as long as you have all your repositories available in your /etc/apt/sources.list file

i know everything can seem complicated at first, but once you learn how to use a few key commands linux actually becomes easier than windows in ways

---

### Post by bikeboy on 2007-05-07
```
sudo aptitude install libauthen-pam-perl libmd5-perl
``` 

apt-get vs aptitude is sort of personal preference so don't worry too much. Apt-get is now "smarter" than it used to be so there's less difference.

I understand your frustration, most software you will ever need is in the repositories, especially on a server. In the case of webmin, I think it was removed from the repos because it had a bad security history.

Remember that you've never used a non-gui linux system before, of course it won't be easy. You can use a desktop install as a server while you learn your way around, but you wouldn't have much luck with that on an old machine, regardless of OS.

Another couple of options you might want to look at is phpmyadmin (web interface to administer mysql), it's available through the repos with ```
sudo aptitude install phpmyadmin
```. You won't have dependency troubles, but it's only for the mysql part of your server.

Another server distro that is simpler for someone new to Linux is the other thing I might suggest. CentOS, ClarkConnect or SMEserver might be worth a look. As a desktop Ubuntu is simple, but as a headless server it requires a little bit of knowledge to get up and running or configure. Those other ones I mention are ready to go with a web interface straight away.

---

### Post by wh33t on 2007-05-07
Ok well using apt-get install didn not work for me.
aptitude did. So I know which one ill be using from now on.

Thanks for your help guys. And which Web interface does CentOS and those others come with?

---

### Post by wh33t on 2007-05-07
Ahh *sigh* Another issue.

So Aptitude seemed to work to install, ran the dpkg -i webmin.deb ... apparently its still missing those libraries.

---

### Post by wh33t on 2007-05-07
Ahh nevermind, apparently aptitude never installed them.

Instead it tells me that there is unsolved dependecy issues, webmin is missing the two files I'm telling it to download and install, so it tells me its solution is to remove webmin.... I dont get it..

---

### Post by bikeboy on 2007-05-07
Ok lets approach this a little differently. What are you intending to do with your server? Many things are easy to setup with a few changes to a text file configuration that's there for you already.

CentOS I think is a normal GUI by default but I don't know much about it really, excpet that there are quite a few GUI server config tools in it and it's based on RedHat Enterprise server. Not sure on the web interfaces of the other, they might be custom, no doubt there are screenshots on their pages.

---

### Post by wh33t on 2007-05-07
I was hoping for an easier way of managing apache mysql and php through webmin, and I want to use it as a test server for a website I'm building. I wanted to test it here on a server in my house and then if all is good, try it on the real dedicated server.

More Updates
Apparently the files I need to download weren't found in the repository and about 50 files needed to be upgraded. I'm thinking maybe they needed to be updated first? So I'm doing the UPGRADE and then DIST-UPRGADE and then I'll try again.

---

### Post by bikeboy on 2007-05-07
Yep updating is good, helps keep things secure and stable.

Ah of course (brainwave), you need to do apt-get/aptitude update after making changes to your /etc/apt/sources.list or it won't know of new software you've enables access to. That could include those libraries you tried to install.

---

### Post by wh33t on 2007-05-07
Ok can u do me a favour and tell me if you have

libmd5-perl
libauthen-pam-perl

in your reposistories. Cause I do not.

I have uncommented the lines in sources.list and saved it. I have also done the upgrade and dist-upgrade, and update on both aptitude and apt-get and still its not found.

---

### Post by Nythain on 2007-05-07
can you show us what your sources.list looks like??? if you are using edgy they might be contained in a third party repo... ill look and see if they should be in your base repos and possibly find you a link to download the debs yourself and install them, but that could open up a whole new can of dependency issues....

i really wish they would have left webmin in the repos

---

### Post by bikeboy on 2007-05-07
Just checked, I have both. Can you post your sources.list so we can take a look.

```
cat /etc/apt/sources.list
```


edit: mine is Dapper, older than Edgy, while another poster said they're in Feisty. So it looks like they should be available once we get your sources.list sorted.

---

### Post by Nythain on 2007-05-07
ok, you said you are running edgy (6.10) right... here we go
[libmd5-perl]("http://packages.ubuntu.com/edgy/perl/libmd5-perl") (2.03-1) [universe]backwards-compatible wrapper for Digest::MD5
[libauthen-pam-perl]("http://packages.ubuntu.com/edgy/perl/libauthen-pam-perl") (0.16-1) [universe]Perl interface to PAM library
links for both:
[U][http://packages.ubuntu.com/edgy/perl/libauthen-pam-perl](http://packages.ubuntu.com/edgy/perl/libauthen-pam-perl)
[http://packages.ubuntu.com/edgy/perl/libmd5-perl](http://packages.ubuntu.com/edgy/perl/libmd5-perl)

the libauthen-pam-perl is ging to have a few deps i dont know if you meet, but libmd5-perl just requires perl
[/U]

---

### Post by Kissack on 2007-05-07
I get the same missing dependancies (with Kubuntu 7.04).  Is there a dkpg switch liek apt-get -f that fixes things without the difficulty of trying to install all dependencies individually?

---

### Post by Tomosaur on 2007-05-07
> **wh33t said:**
> Ok can u do me a favour and tell me if you have

libmd5-perl
libauthen-pam-perl

in your reposistories. Cause I do not.

I have uncommented the lines in sources.list and saved it. I have also done the upgrade and dist-upgrade, and update on both aptitude and apt-get and still its not found.

```
sudo aptitude upgrade
``` and ```
sudo aptitude dist-upgrade
``` are for downloading updates to your packages.

The command you need to use is:
```

sudo aptitude update

```

This is to update the list of available packages. You need to do this after you edit your sources.list file.

If you're new to Linux - heading straight into the command line is not such a good idea. You can get a graphical desktop by taking your pick of:
```

sudo aptitude install ubuntu-desktop

```

```

sudo aptitude install kubuntu-desktop

```

```

sudo aptitude install xubuntu-desktop

```

Each of those will give you a GUI - but xubuntu-desktop is considered the most lightweight. Alternatively you can just build up your GUI from scratch, and installing a REAL lightweight environment like fluxbox. You can then use this machine to configure everything, and can teach yourself how to do stuff via the command line, while keeping a more 'friendly' browser open to read tutorials / documentation and such.

---

### Post by hyper_ch on 2007-05-07
You could try this:

[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

---

### Post by Kissack on 2007-05-07
Ok, decided just to use the apt package gui to install dependancies (x5).  Then used dpkg and webmin 1.34 is insalled and working

---

