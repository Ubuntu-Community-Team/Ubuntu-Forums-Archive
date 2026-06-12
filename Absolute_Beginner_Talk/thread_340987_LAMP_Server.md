---
title: "LAMP Server"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Ic3y on 2007-01-18
Hi there just curious as to whether you can run a LAMP server on Ubuntu 6.10 Edgy Desktop edition if so could someone please tell me where I can go for the tutorial.

It would be much appreciated.

---

### Post by riven0 on 2007-01-18
Have you checked out[ this howto yet]("http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html")?

Oh, yeah:[ here's another]("http://news.linux.com/article.pl?sid=06/11/09/2016247&tid=96").

---

### Post by Ic3y on 2007-01-18
yeah I checked them both they both need the Server edition I only have the desktop edition doesnt have the features to install LAMP server on the boot disk

Thanks for your reply 8) 

I am assuming it is only available on the server edition may have to look at downloading that.

Thanks,
Ic3y :mrgreen:

---

### Post by irish_flu on 2007-01-18
Nah, the desktop edition can have everything the server edition has.  LAMP is (to me) Linux, Apache, MySQL, and PHP (and/or Python).

Here's how (I'm assuming you use Gnome):
Open up "synaptic Package Manager" under the "Administration" menu.  It's your best friend.

Click "Search" and type apache2.  Mark the "apache2" package for installation.
While you're there, I think you should also get the package called "libapache2-mod-php5"

Search for "PHP5".  Mark the "PHP5" package for installation.

search for "mysql-server".  Mark the "mysql-server" package for installation.

Hit "apply".

You're now the proud owner of a LAMP server!  Happy computing, and feel free to post here and rake me over the coals if I've forgotten anything.  :D

---

### Post by Ic3y on 2007-01-18
Thanks again for the guide I went looking for all the packages and was at a loss again is there anyway I can download these packages if there is I am more than willing to look at downloading them

BIG thanks
Ic3y :mrgreen:

---

### Post by irish_flu on 2007-01-18
The "Synaptic Package Manager" I mentioned *is* how you download them (and it installs them, too).  :D 

Holler if what I'm saying doesn't make sense.

---

### Post by Ic3y on 2007-01-18
I tried to use the search and it returns nothing for me mind you there is a drop down bar named 'look in' that has a few options on what to look for which may play an effect on the search
I am currently awaiting the reload which I have clicked which seems to be downloading package information and at the same time I have found this site with all the packages for download which could prove interesting as long as I can work out how to install them

> [http://packages.ubuntu.com/edgy/](http://packages.ubuntu.com/edgy/)

Ic3y :mrgreen:

---

### Post by riven0 on 2007-01-18
Don't go through all that trouble. Just do it through the terminal

> sudo apt-get install php5 mysql-server apache2 libapache2-mod-php5

And you'll be set!

---

### Post by irish_flu on 2007-01-18
> **Ic3y said:**
> I tried to use the search and it returns nothing for me mind you there is a drop down bar named 'look in' that has a few options on what to look for which may play an effect on the search
I am currently awaiting the reload which I have clicked which seems to be downloading package information and at the same time I have found this site with all the packages for download which could prove interesting as long as I can work out how to install them

Sorry to hear that homie, maybe they're part of the extra repositories I've added over time or something (in other words, I'm losing it heh).  My "look in" box is set to "description and name".

To get the rest of the repositories (I hope you're using the same software version that I am), open up Synaptic, then go to "Settings" and then "Repositories".  Under the first tab, under the "Internet" heading, check the boxes next to "Community Maintained Open Source Software (Universe)", "Canonical supported Open Source Software", and you might as well check "Software restricted by copyright or legal issues (multiverse)".

Once all three of those are checked, close the box and try the search again.  Sorry it didn't work for you the first time!

---

### Post by Ic3y on 2007-01-18
Didnt work for me Riven0 from what I believe is that your terminal command access the packages that are kept under the Synaptic Package Manager as such it didnt find the packages but all in all I am still downloading the packages on the Synaptic Package Manager and see how we go with that  Thanks for the update on what I should do to gain access to the latest packages irish_flu I am currently reloading the Synaptic Package Manager at the moment and it seems to be downloading 21 new packages so what you advised has been great so far :-D 

Thanks to the both of you to this point
Ic3y :mrgreen:

---

### Post by Ic3y on 2007-01-18
Irish_Flu your resolution worked a treat I found the packages and are now downloading them and thanks to you Riven0 your terminal command worked a treat as well it shortened the time of having to search for the packages and I was able to automatically  download the packages from the one command saved alot of hassle your both a credit to this community \\:D/

---

### Post by irish_flu on 2007-01-18
Glad we could help, I hope they work out for you!

---

### Post by riven0 on 2007-01-18
Yeah, and good luck with the server! :KS

---

