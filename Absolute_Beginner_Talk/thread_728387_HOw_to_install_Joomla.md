---
title: "HOw to install Joomla?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-03-18
Hi,

could anybody tell me how to install Joomal, I downloaded the files but don't know what to do with it?

thanls

ANdreas

---

### Post by thewho? on 2008-03-18
Joomla is a web application.  You need to have apache Running.  It also uses MySql as its database.  You need to install that.  Once all that is done, follow the directions in this wiki:

[http://edutechwiki.unige.ch/en/Joomla_installation_and_configuration](http://edutechwiki.unige.ch/en/Joomla_installation_and_configuration)

---

### Post by Djalmahal on 2008-03-19
Hey,

thanks,
i got it running, at least to the point where i filed in the name of database etc, now if i go to localhost/joomla i get this message

 For your security please completely remove the installation directory including all files and sub-folders - then refresh this page. 

I didn't find the installation directory. I thought as well that now there would be a program installed on my computer called joomla but nothing like that, maybe I am just mistaken and it all works over the web.

One last question, i the web site I am about to generate hosted from this computer or will i have to enlist the service of a proper server.

Thnaks so much for your reply, I guess those question sound rather stupid, but I don't know better.

ANdreas

---

### Post by deandude on 2008-04-26
> **thewho? said:**
> Joomla is a web application.  You need to have apache Running.  It also uses MySql as its database.  You need to install that.  Once all that is done, follow the directions in this wiki:

[http://edutechwiki.unige.ch/en/Joomla_installation_and_configuration](http://edutechwiki.unige.ch/en/Joomla_installation_and_configuration)

I need help. Can u message me and we can chat at some point so u can help me?:(:(:(

---

### Post by deandude on 2008-04-26
> **deandude said:**
> I need help. Can u message me and we can chat at some point so u can help me?:(:(:(

Or someone who is willing to help and knows how.:)

---

### Post by thewho? on 2008-05-21
THe install directory is in the actual www directory.  Wherever you put the website is were the install directory is.  In there you will find a directory named install.  Just move it somewhere where you'll remember and you're good to go.

---

### Post by totoro21 on 2008-05-23
> **thewho? said:**
> THe install directory is in the actual www directory.  Wherever you put the website is were the install directory is.  In there you will find a directory named install.  Just move it somewhere where you'll remember and you're good to go.

hi thewho, following the instructions listed here : 

[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

Now this is what has happened. In the pre-installation check screen configuration.php had no written across it. A bit of search and I have come to know it would be taken care at the end of the steps. Apart from that I also had 'Custom Errors' in the Recommended Settings sections to 'On'. 

At the end of installation I got a step where it asked me to create configuration.php file with the data it showed in the listbox which i did and removed 'installation' directory from /var/www/joomla directory. I refreshed my page after doing that and I find index/install.php not found error in the screen.

Can someone help me how to fix this? I have also seen that this command :
sudo chown -R www-data:www-data /var/www/joomla
was not allowing me to make any changes with permission denied error in the steps that followed, so again after searching replaced www-data:www-data with my root name. Did i do something wrong?


Also how are the rules defined here and how come I not able to create a 'new post'?

---

### Post by subverso on 2008-07-02
> **totoro21 said:**
> hi thewho, following the instructions listed here : 
[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)


[FONT=Lucida Sans Unicode][SIZE=2]**Hello totoro21, wassup!?**
man, what version of Ubuntu r u using?
I'd like to know if this tutor   :arrow:([https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla))  u posted here works with Ubuntu 8.04.
Thanks in advance[/SIZE][/FONT]

---

