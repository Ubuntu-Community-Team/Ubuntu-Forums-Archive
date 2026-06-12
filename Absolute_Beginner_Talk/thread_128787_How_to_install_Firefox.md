---
title: "How to install Firefox"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by Settler on 2006-02-12
hello guys,

I have the gnome version of ubuntu and I am a real newbie in linux...

I would like to ask how can I install firefox and how can I easily switch languages...

Thanks a lot
Kostas

---

### Post by simon_is_learning on 2006-02-12
Isn't Firefox installed by default?

Otherwise it's easy:
sudo apt-get install firefox.
Then you'll have english as language.
Or you want your native tounge, as In my case
sudo apt-get install mozilla-firefox-locale-sv-se 

If you recently Installed maybe your sources.list isn't set up properly.
read: [http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

after you've got your repositories in order

type apt-cache search firefox 

then find your language, and sudo apt-get install "your language package"

---

### Post by cotcot on 2006-02-12
Install guide for Firefox 1.5 : [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
1.5 is not in the repositoriies.

---

### Post by Bartender on 2006-02-12
What version does Automatix install?  I thought it delivered 1.5 when I ran it just a coupla days ago....

---

### Post by alfonz on 2006-02-12
just use the link above it works like a charm its not hard to follow.

---

### Post by atoponce on 2006-02-12
[quote=cotcot]Install guide for Firefox 1.5 : [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")
1.5 is not in the repositoriies.[/quote] It should be too.  How long has it been out?

---

### Post by alfonz on 2006-02-12
problem is Breezy still uses the 1.0.7 Gecko engine its not as easy to update it. 
Dapper uses the 1.5 so it comes with FF1.5

---

### Post by patrick295767 on 2006-02-12
```
apt-get -f -y install mozilla-firefox
```
  
or just have a look on their website... 
then u can type:
```
dpkg -i debianubuntu_package.deb
```

Greetz

---

### Post by Settler on 2006-02-12
Hello again guys...

I just did what in [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
said but nothing happened..Instead I have not internet browser now so I'm on windows again....

Any idea?..
Should I reinstall ubuntu?..

---

### Post by Settler on 2006-02-15
[QUOTE=cotcot]Install guide for Firefox 1.5 : [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
[/QUOTE]

When I am trying to do 

      mkdir /usr/local/firefox32

      cp -r -p ./* /usr/local/firefox32/

it says...
**mkdir: cannot create directory `/usr/local/firefox32': Permission denied**

What can I do pls...

Thanks

---

### Post by weasel fierce on 2006-02-15
Try it with 
"sudo  mkdir /usr/local/firefox32"

---

### Post by WolfJay_83 on 2006-02-15
Eith type sudo before your command, or begin by typing 
sudo -s   

either way you will be prompted for your password, and commands will be executed with administrator (root) priviges.  (the first just makes one command root, versus the second makes any subsiquent commands root)

This provides a layer of security that prevents any normal programs (or users) from damaging anything system related.

---

