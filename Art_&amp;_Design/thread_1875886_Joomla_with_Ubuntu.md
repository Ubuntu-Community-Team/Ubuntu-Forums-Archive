---
title: "Joomla with Ubuntu"
date: 2011-11-05
forum: Art &amp; Design
---

### Post by naksuli on 2011-11-05
Hi all

Im wondering how Ubuntu works with web development?
Im at the moment building websites with Joomla with my windows for example [http://www.netsome.fi]("http://www.netsome.fi/"), but my laptop is getting slow, and im interested in switching to Ubuntu. Just wondering how difficult it is to make testing setup for XAMPP with Ubuntu?

Any other decent web developing tools for Ubuntu?

---

### Post by alex.rayu on 2011-11-07
If your laptop is getting slow for windows, it will for Ubuntu. But as per question:

Ubuntu has all you need and some things that are limited in Windows, but has one significant limitation - you can't run Photoshop cs4 or cs5 unless you know the system well enough as to install WINE and configure it. Then you have Photoshop - but not Fireworks not Flash (who needs Flash?)

If you switch, you will have a native apache, php, mysql - which will be harder to configure than xammp, especialy for mod_rewrite and virtual hosts. You will have to learn some server administration. Thats a negative.

Positives are - you are using native system, you can use git and subversion natively, use ssh natively, use netbeans or Aptana or Eclipse or some other tool for development (Linux has that). 

Another down side - how will you test in ie? (You can install IE7 under WINE if you learn how).

So if you know NOTHING of linux control, WINE, or editing apache or PHP config files - then don't switch at once. You will be helpless if you do.

---

### Post by Dry Lips on 2011-11-08
Installing Xampp should be pretty straight forward... See the installation notices:
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

The only thing that you'll have to keep in mind, is that you use sudo instead of su
in Ubuntu (see **step 2**). ```
sudo tar xvfz xampp-linux-1.7.7.tar.gz -C /opt
```

A good alternative to Xampp, is to set up your own Ubuntu lamp server. It isn't that
hard for a noob, and is a ***great*** learning experience. If you have an old desktop
computer that you don't use, that is what I would have done if I were you...

Just my 0.02£. Good luck!

---

