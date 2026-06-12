---
title: "Slow browser"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by lengguard on 2006-02-14
Have just installed ubuntu .Most seems well so far The first thing I noticed is the default firefox browsr is dead slow.icould not get opera through automatix.how do I upgrade firefox to 1.5 and install another gnome browser.Thank you for your patience.Through this forum I am getting there .

---

### Post by xXx 0wn3d xXx on 2006-02-14
Use automatix. There is a sticky in every forum about it. It will install all the most popular and needed packages. Including Firefox 1.5 :)

---

### Post by stalefries on 2006-02-14
I would suggest searching the forums, as you will find a howto for Firefox 1.5 in here. Also, the defauolt GNOME browser is epiphany, installable by typing "sudo apt-get install epiphany" in a terminal.

---

### Post by bored2k on 2006-02-14
The manual way:
First install *libstdc++5* (search for libstdc, I might myspelled it).
Download it. [http://www.mozilla.org/](http://www.mozilla.org/) 
Extract it. Run firefox inside the firefox directory. 
Note: Installing Opera would be similar.

---

### Post by Qrk on 2006-02-14
Try epiphany as well. I love it and its a straight:

sudo apt-get install epiphany

away.


Its even available through the nifty add-applications app at the bottom of the menu. Very painless, and I like it better than firefox because the close tab button is on the tab, not off to one side.

---

### Post by Packard Dell on 2006-02-15
[QUOTE=lengguard]Have just installed ubuntu .Most seems well so far The first thing I noticed is the default firefox browsr is dead slow.icould not get opera through automatix.how do I upgrade firefox to 1.5 and install another gnome browser.Thank you for your patience.Through this forum I am getting there .[/QUOTE]

To upgrade firefox, follow this: [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")
and if you want your firefox loads webpages a bit faster, do this: 

1. Open **firefox**

2. Go to the address bar and enter: **about:config** hit enter.

3. Go to the filter box **Filter Box**

4. In filter box go to or type in: **network.dns.disableIPv6** double click to change it to be: **true**

5. In filter box go to or type in: **network.http.pipelining double **click to change it to be: **true**

6. In filter box go to or type in: **network.http.pipelining.maxrequests** double click it to change to **8** click OK when done.

7. In filter box go to or type in:** network.http.proxy.pipelining **double click to change it to be: **true**

8. **Restart firefox! **

---

### Post by kingsidy on 2006-02-15
[QUOTE=Packard Dell]To upgrade firefox, follow this: [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")
and if you want your firefox loads webpages a bit faster, do this: 

1. Open **firefox**

2. Go to the address bar and enter: **about:config** hit enter.

3. Go to the filter box **Filter Box**

4. In filter box go to or type in: **network.dns.disableIPv6** double click to change it to be: **true**

5. In filter box go to or type in: **network.http.pipelining double **click to change it to be: **true**

6. In filter box go to or type in: **network.http.pipelining.maxrequests** double click it to change to **8** click OK when done.

7. In filter box go to or type in:** network.http.proxy.pipelining **double click to change it to be: **true**

8. **Restart firefox! **[/QUOTE]

Ever heard of fasterfox (ff extension)

instead of all of this, just download an extension called fasterfox. It does about everything listed above except disable ipv6

---

### Post by bored2k on 2006-02-15
[QUOTE=Qrk]Try epiphany as well. I love it and its a straight:

sudo apt-get install epiphany

away.


Its even available through the nifty add-applications app at the bottom of the menu. Very painless, and I like it better than firefox because the close tab button is on the tab, not off to one side.[/QUOTE]
Correction: epiphany-browser.

---

