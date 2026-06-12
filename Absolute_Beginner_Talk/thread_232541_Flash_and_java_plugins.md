---
title: "Flash and java plugins"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by kvalenza on 2006-08-08
I installed Ubuntu 6.06 to my desktop.  The installation went well, and this flavor of Linux is one of the best I have seen.  I do have a couple of questions:

1.  How can I install the flash player and the java plugins for Firefox?  I read somewhere that it can be done, but I was unable to figure out how.

2.  I am thinking about installing Ubuntu onto my laptop.  Does it recognize the wireless network, or will it have to be configured manually?  I had an awful time trying to get my laptop to work with Xandros; in fact, the wireless never did work with it.

Keith

---

### Post by Bragador on 2006-08-08
Well I just installed flash so I can help you.

System>Administration>Synaptic Package Manager

then select **flashplugin-nonfree** in the "all" list 

I have a problem with flash because it doesn't play any sound though...

---

### Post by Drakkor on 2006-08-08
Automatix,or EasyUbuntu !

---

### Post by Bragador on 2006-08-08
does automatix make the flash player work with sound ?

---

### Post by eKlipSe on 2006-08-08
[COLOR="Blue"]Hi, how do i get online video to play in Ubuntu ... such as Google, You Tube, MySpace.  Also I inserted a CD into the cd player and its not playing ... i dont hear any sound ???   thanX[/COLOR]

---

### Post by kvalenza on 2006-08-08
I went to the synaptic package manager, and flashplugin-nonfree was not even listed.  Now what do I do?

Keith

---

### Post by eKlipSe on 2006-08-08
[COLOR="Blue"]you clicked 'all' on the left side of Synaptic Package Manager, and then scrolled thru all entries on right side which are listed in alphabetical order ... i found it in mine, i have downloaded 'Automatix' maybe thats why its in mine. If you have'nt downloaded that yet you may need to do so in order to have the 'nonfree flashplugins'. [/COLOR]

---

### Post by powder on 2006-08-09
> **kvalenza said:**
> I went to the synaptic package manager, and flashplugin-nonfree was not even listed.  Now what do I do?

Keith

Flashplugin-nonfree is in multiverse.  You need to edit /etc/apt/sources.list and enable the multiverse repositories.

---

### Post by magnoliablossom on 2006-08-09
Use Easy Ubuntu....it was the easiest way for me...It'll install your java and your flash as well as your codecs for your multimedia stuff as well.  Here's the code you need, just cut and paste:

> wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz)
tar -zxf easyubuntu-3.021.tar.gz
cd easyubuntu
sudo python easyubuntu.in


You can get more how to help here and it's almost all cut and paste:
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

I keep that in my favorites.

---

### Post by kvalenza on 2006-08-11
What is multiverse?  And how do I do this?  edit /etc/apt/sources.list and enable the multiverse repositories.

---

### Post by alainsamoun on 2006-08-11
> **magnoliablossom said:**
> Use Easy Ubuntu....it was the easiest way for me...It'll install your java and your flash as well as your codecs for your multimedia stuff as well.  Here's the code you need, just cut and paste:




You can get more how to help here and it's almost all cut and paste:
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

I keep that in my favorites.

I try:
 wget [http://easyubuntu.freecontrib.org/fi...u-3.021.tar.gz](http://easyubuntu.freecontrib.org/fi...u-3.021.tar.gz)
I get:
--17:21:26--  [http://easyubuntu.freecontrib.org/fi...u-3.021.tar.gz](http://easyubuntu.freecontrib.org/fi...u-3.021.tar.gz)
           => `fi...u-3.021.tar.gz'
Resolving easyubuntu.freecontrib.org... 213.246.58.132
Connecting to easyubuntu.freecontrib.org|213.246.58.132|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:21:28 ERROR 404: Not Found.

What else??

---

### Post by alainsamoun on 2006-08-11
The script is:
wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz)
tar -zxf easyubuntu-3.021.tar.gz
cd easyubuntu
sudo python easyubuntu.in

---

### Post by bukwirm on 2006-08-11
> **kvalenza said:**
> 2.  I am thinking about installing Ubuntu onto my laptop.  Does it recognize the wireless network, or will it have to be configured manually?  I had an awful time trying to get my laptop to work with Xandros; in fact, the wireless never did work with it.
Keith

What wireless card do you have?

---

### Post by alainsamoun on 2006-08-11
Ah, I understand what happened, my font size, too big for the script, added the pesty dots... So the original script from magnoliablossom worked, sorry :oops:

---

