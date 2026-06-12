---
title: "localhost redirecti to xampp"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by InternetDominus on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=553567&amp;highlight=remove+xampp](http://ubuntuforums.org/showthread.php?t=553567&amp;highlight=remove+xampp) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I installed xampp first, but since I could not start mysql because I could not find it at /etc/int.d/mysql , I figured it would be easier to uninstall xammp , and intall it agin using instruction on this [thread]("http://ubuntuforums.org/showthread.php?t=553567&highlight=remove+xampp")

Well, I have installed as per instructions, and mysql starts fine, but can't run phpmyadmin, I don't see at /etc although I see php5, perl, and others...and when I go to [http://localhost](http://localhost) it automatically redirects me to [http://localhost/xammp](http://localhost/xammp), and of course it is empty...

Where could I modify the redirect? so that the browser stays at localhost, and where is myphpadmin installed if not at /etc/ nor /var where I think usually should be installed?

Thanks!

---

### Post by haldean on 2007-11-03
The redirect might be located in /var/www, although I'm not sure what kind of file it would be in. That's where the document root of Apache is located by default. 

phpMyAdmin is installed to /usr/share/phpmyadmin by default.

---

### Post by kellemes on 2008-03-11
I know this is an old thread.. but for anyone having this issue this may be interesting.
Don't forget about your browser-cache. I simply wiped the firefox-cache and this issue is solved.

---

### Post by TuxWithoutPants on 2008-05-14
> **kellemes said:**
> I know this is an old thread.. but for anyone having this issue this may be interesting.
Don't forget about your browser-cache. I simply wiped the firefox-cache and this issue is solved.

LOL! Thanks kellemes! I uninstalled xampp to install LAMP from Synaptic and was getting really frustrated that localhost still points to localhost/xampp. I went as far as opening the host file to see if it was redirected there. Then I found your post and realized that all I had to do was clear cache LOL! Thanks man!

---

