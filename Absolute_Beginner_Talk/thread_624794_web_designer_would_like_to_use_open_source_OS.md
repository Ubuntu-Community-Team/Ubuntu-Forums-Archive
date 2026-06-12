---
title: "web designer would like to use open source OS"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by dsiembab on 2007-11-27
Good morning,
Hi I have three personal websites and would like to use ubuntu, basically like it's security,.
Now be patient. I would like to test my websites on many ( basically all ) browsers. I have gotten my flash 8 to work flawlessly thanks to wine and even my html-kit by chami. I have heard of Konqueror and was wondering if it does render like IE. I'm sure this is not the first time this question has been asked and I am sure it will not be the last. Without installing the dreaded money sucking, no support, i like blue just not a whole screen windows, is this possible?
 Basically I want to use ubuntu because it is linux and all of my websites are hosted with a linux server, basically because I like php programming.
Well anyways, If you guys (or ladies) can help I would greatly appreciate it. Thank you for your time.](*,)

---

### Post by Breepee on 2007-11-27
Konqueror does not render like IE at all. More like Safari (they basically the same).

You can get IE6 to work in wine though, maybe try that.

Or, Microsoft has an image available with Windows and IE6/IE7 that you can download for free and run in VMware. I don't know if it runs in Virtualbox.

---

### Post by edm1 on 2007-11-27
[IEs4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") may be of help.

---

### Post by dsiembab on 2007-11-27
Damn that was fast thanks

---

### Post by dsiembab on 2007-11-27
hey edm1 put your hand up because there is a big high 5 coming your way

---

### Post by asmiller-ke6seh on 2007-11-27
> **dsiembab said:**
> Good morning,
Hi I have three personal websites and would like to use ubuntu, basically like it's security,.
Now be patient. I would like to test my websites on many ( basically all ) browsers. I have gotten my flash 8 to work flawlessly thanks to wine and even my html-kit by chami. I have heard of Konqueror and was wondering if it does render like IE. I'm sure this is not the first time this question has been asked and I am sure it will not be the last. Without installing the dreaded money sucking, no support, i like blue just not a whole screen windows, is this possible?
 Basically I want to use ubuntu because it is linux and all of my websites are hosted with a linux server, basically because I like php programming.
Well anyways, If you guys (or ladies) can help I would greatly appreciate it. Thank you for your time.](*,)

Based on what you said, above, you might want to look at [Joomla!]("http://demo.joomla.org") From what I understand, it makes real nice web sites that are highly compatible across multiple browsers - check out the demo. It's Open Source (of course).

---

### Post by MystaMax on 2007-11-27
I don't think he was looking for a content management system (CMS), although its a good idea if you want an easy way to update your site.

I also use joomla for personal sites and business. I highly recommend it as well. It has tons of [extensions]("http://extensions.joomla.org") and is pretty easy to install and setup.

[http://www.opensourcecms.com/](http://www.opensourcecms.com/) has what seems like every OS CMS system known to man available for testing, check it out.

[http://browsershots.org/](http://browsershots.org/) is a website which tests your web design in different browsers. Another great resource....

good luck.

---

### Post by michaelzap on 2007-11-27
I do web design professionally on Ubuntu, and although I can't quite say that it's the ideal platform for my work I'm gonna stick with it. I use Geany for coding (and the [MODx CMS]("http://modxcms.com/") for the vast majority of our websites), which I like about as much as the program that I used in XP, and there are a ton of Dreamweaver-like options in Ubuntu for those who want them. I'm also relatively content with the GIMP for most web graphics, although to be completely honest most of the initial design is done by my partner in Photoshop on an XP machine.

I develop and test in Swiftfox first with the Web Developer extension and then use IEs4Linux to test in IE6. I have an XP VirtualBox machine with IE7 for testing designs there. And I also love browsershots.org, which can alert you to potential design problems in older Safari browsers in particular (although it doesn't flag usability issues).

Where I've had the biggest problems are:
[LIST]
[*]getting Ubuntu to display fonts the same as XP, which is still the standard we need to match (it's never quite right, so I always need to check layouts in Windows)
[*]lack of transparency in Flash for Linux
[*]inability to create Flash movies in Linux (I have to dual boot to do this)
[/LIST]

This is a pretty short list of complaints, really. In general I've been extremely happy with Ubuntu since I switched, and I only boot into XP once or twice a month for some specific task. As usual most of the design difficulties stem from Windows and Internet Explorer being the standard system and browser used by the vast majority of people who would view our sites and not from any deficiency in Ubuntu or Firefox.

---

### Post by dsiembab on 2007-11-27
One more question if I want to test my php I used to use wamp on windows what is the alternative here? I know a silly question.
on the cms I use an easy php template system. something small and simple with my own scripts.

---

### Post by MystaMax on 2007-11-27
I use [aptana]("http://www.aptana.com") for all my css/html/javascript needs. It also plays nice w/ RoR, but I use netbeans for that.

To test things, I actually have a separate server (Ubuntu-server) to mimic my production environment, but if you want to do local testing check this out:

[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

---

### Post by siciliancasanova on 2007-11-27
> **MystaMax said:**
> I use [aptana]("http://www.aptana.com") for all my css/html/javascript needs. It also plays nice w/ RoR, but I use netbeans for that.

To test things, I actually have a separate server (Ubuntu-server) to mimic my production environment, but if you want to do local testing check this out:

[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

I am also a web developer and I use Aptana Studio on Gutsy.

I actually prefer a text editor like Notepad++ but the nice thing about Aptana is the ability to change a file and upload it without changing windows.  That is of course if you are using FTP.

If you use ROR, I believe there is an entire Ruby plugin set for Aptana.  There was for Aptana IDE I haven't checked to see if it's updated for Aptana Studio.

EDIT:  This reply sounds like its to the guy above me, really I'm just agreeing with him on everything he said.

---

### Post by siciliancasanova on 2007-11-27
> **dsiembab said:**
> One more question if I want to test my php I used to use wamp on windows what is the alternative here? I know a silly question.
on the cms I use an easy php template system. something small and simple with my own scripts.

It would be LAMP.

---

### Post by dsiembab on 2007-11-27
Yeah i use a lamp to view my keyboard. I did upload Apache Mysql and Php5. everytime I tried to drag a php file into the var/www it said i didn't have permision??? I am the only one using this computer do I need the creator of ubunto to upload it for me? just kidding what gives?

---

### Post by MystaMax on 2007-11-28
the permissions on /var/www/ are probably set to root. You need to either changes permissions on that folder, or add yourself to the group that has write-access.

If you want to add files right away use the sudo command infront of cp. For example:

```

sudo cp /home/dsiembab/myfirstscript.php /var/www/
```

---

### Post by dsiembab on 2007-11-28
thanks I did try to change permissions on that folder. but I decided to do a dual boot of xp and ubuntu so the apache php and mysql were vaporized. I'm pretty new as in huh to OSOS ( Open Source Operating Systems ) and I figure I'll just keep the dual boot for now and then I will see if ubuntu seduces me. thanks again you people are great.

---

