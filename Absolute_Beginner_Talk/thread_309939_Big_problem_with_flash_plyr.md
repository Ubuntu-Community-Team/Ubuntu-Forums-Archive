---
title: "Big problem with flash plyr"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by tradesman on 2006-11-30
Hi I seem to have got myself in a bit of a mess whilst trying to install flash player using terminal got the following message    "dpkg --configure -a" and not sure what to do next, HELP!

---

### Post by deadgobby on 2006-11-30
There easy way is to install flash player that is either Easyubuntu or Automatix. As of now Automatix is down for some maint for while. Most Ubie fans love Automatix. It depend on what Ubie version you are using. If Drapper, you and use either or, If Eft, then you may wait for Beerorkid get the web site up and running. 
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Now to you know that flash player can be really annoying, Most you get is adds and that is a way to stop that.
[http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)

Gobby

---

### Post by tradesman on 2006-11-30
It's when I try to use Automatix that I get the error.

---

### Post by deadgobby on 2006-11-30
As I said, Automatix is down for a while. Try it again in a while. If you want just go to [http://www.getautomatix.com/](http://www.getautomatix.com/) and you get
"Apologies everyone, our Joomla website appears to be down. We're working on getting it fixed, but in the mean time, go check out the other parts of the site."
 The site is down and try in about an hour. This why I gave the link for the other.
Gobby

---

### Post by deadgobby on 2006-11-30
As I said, Automatix is down for a while. Try it again in a while. If you want just go to [http://www.getautomatix.com/](http://www.getautomatix.com/) and you get
"Apologies everyone, our Joomla website appears to be down. We're working on getting it fixed, but in the mean time, go check out the other parts of the site."
 The site is down and try in about an hour. This why I gave the link for the other.
 Or try 
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=restricted+formats&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=restricted+formats&titlesearch=Titles)

Gobby

---

### Post by nofrak on 2006-11-30
"dpkg --configure -a" is not an error, it's a command.  Is it telling you that you need to run that from the terminal?

---

### Post by tradesman on 2006-11-30
Have included a screenshot of the result when I type the command in terminal

---

### Post by shin on 2006-11-30
Remove j2sdk1.4-doc package to get rid of it.
Or just follow instructions.

Go to [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

Download j2sdk-1_4_2-doc.zip
Move it to /tmp
Change ownership to root:root
```
sudo chown root:root /tmp/j2sdk-1_4_2-doc.zip

```

and try again
```
sudo dpkg --configure -a
```

About flash player - my 2 cents, add this repo to source.list
deb [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) edgy 3v1n0
```

echo deb http://download.tuxfamily.org/3v1deb/ edgy 3v1n0 | sudo tee -a /etc/apt/sources.list
```

then

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree flashplayer-nonfree
```

I dont really like automatix. With this repo you get newest flash 9 beta plugin and standalone player.

---

### Post by tradesman on 2006-11-30
Need the command to move file to /tmp please

---

