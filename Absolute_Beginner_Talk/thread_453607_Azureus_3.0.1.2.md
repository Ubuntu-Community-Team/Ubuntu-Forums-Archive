---
title: "Azureus 3.0.1.2"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by servvs on 2007-05-24
I was wondering if anyone has figured out how to run this on linux? I am not good at installing from source or anything like that, so if someone can post a how-to I would be forever grateful.

---

### Post by Happy_Man on 2007-05-24
First off... open a terminal. It's your new best friend. System -- Accessories -- Terminal.

```
sudo apt-get install build-essential
```

Extract the source onto your Desktop however you want, just make sure those extracted files are on there. Go back to the terminal.

```
cd Desktop/<name of folder on Deskop with files>
./configure
make
sudo make install
```

And you're set!

---

### Post by shirilover on 2007-05-24
Firstly, there is no Azureus 3, it is known as Vuze. Which is an attempt to sell content using bittorrent as the distribution method.
However, while it is based upon Azureus 2.5, it does not correctly identify itself as Vuze 3.0.1.2.

As far as I can tell, even clicking on the Download button will get you Azureus 2.5.0.4

---

### Post by servvs on 2007-05-24
I understand how to install from source, but Azureus doesn't have a makefile or anything. So I am at a loss. Is it because it is written in java? IT has a bui

---

### Post by iomegaz on 2007-06-11
Pour installer Vuze, veuillez tout d'abord télécharger le fichier suivant :
For installing Vuze, download this file:

[http://www.divshare.com/download/915120-816](http://www.divshare.com/download/915120-816)

Il faut extraire le fichier:
Extract File:

tar xvzf Vuze.bin.tar.gz

Puis xecutez-le grace à la commande suivante :
Execute with this command :


./vuze.bin

(Ou alors double cliquer dessus)
Or Double Clic

Suivez les instructions !!
Follow instructions


Bon séjour avec Vuze Powered By Azureus 3.0  
Bye and good week with Azureus 3


;)

---

### Post by incripshin on 2007-06-14
Don't worry about the new version.  I can't see any improvements at all.  But if you insist...

Do yourself a big favor and do not install that thing from iomegaz.  It is far from being official.  Here is how to install azureus-3.0.1.2:

1. Download the old azureus-2.5.0.4 tarball from the [main site]("http://azureus.sourceforge.net/download.php")
2. Download the new azureus-3.0.1.4.jar from the same place
3. Untar and copy azureus-3.0.1.4.jar into the azureus directory as Azureus2.jar (replacing the old)
4. Run azureus, downloading the swt update (and keep seeding it!!)

If you already have azureus installed, you can probably skip step 1.  Just know that if you don't have write access to the azureus directory, the update won't work smoothly.  I was able to grab the swt-?.jar file out of ~/.azureus/updates/?/swt-?.jar and copy it manually into the place I have azureus installed, overwriting the old swt jar.

Mark

---

### Post by brainkilla on 2007-06-21
Mark's how-to is actually very good and works as advertised. However, I would recommend going to this address
 [http://www.azureuswiki.com/index.php/Azureus_2_and_Vuze]("http://www.azureuswiki.com/index.php/Azureus_2_and_Vuze")
and getting the alternative Vuze start-up script.

---

### Post by Obeleh on 2007-06-21
Theres also an easy way    [www.getautomatix.com](www.getautomatix.com)

It has some other nice stuff too

---

### Post by brainkilla on 2007-06-21
> **Obeleh said:**
> Theres also an easy way    [www.getautomatix.com](www.getautomatix.com)

It has some other nice stuff too


As far as I could see it only offers Azureus proper, not the Vuze thingie. And Automatix is for n00bs, not real men ;)

---

### Post by NeoLithium on 2007-06-21
> **brainkilla said:**
> As far as I could see it only offers Azureus proper, not the Vuze thingie. And Automatix is for n00bs, not real men ;)

There's no need to insult the developers of the program. Some people prefer automatix, though using a guide like [http://www.ubuntuguide.org](http://www.ubuntuguide.org) or [http://www.psychocats.net](http://www.psychocats.net) is the preferred methods.  They have great walkthroughs that will help install it.

---

### Post by brainkilla on 2007-06-22
> **NeoLithium said:**
> There's no need to insult the developers of the program. Some people prefer automatix, though using a guide like [http://www.ubuntuguide.org](http://www.ubuntuguide.org) or [http://www.psychocats.net](http://www.psychocats.net) is the preferred methods.  They have great walkthroughs that will help install it.

Come on, it was a jocular way of stating an opinion, it wasn't meant to be an insult. Everyone is free to use what he or she likes, even Windows :o

---

