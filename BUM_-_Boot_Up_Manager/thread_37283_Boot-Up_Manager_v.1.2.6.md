---
title: "Boot-Up Manager v.1.2.6"
date: 2005-05-26
forum: BUM - Boot Up Manager
---

### Post by saltydog on 2005-05-26
New version is out!! The name is changed to "Boot-Up Manager" (BUM) and you can download from this page:

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

New version includes localization for italian, spanish, german, french and dutch, and other features. See the Changelog on the home page.

**Update May 27th** 
New v. 1.2.7 si online. Fixed localization bugs.

**Update May 31st** 
BUM is on LinuxJournal: [http://www.linuxjournal.com/article/8322](http://www.linuxjournal.com/article/8322)

**Update June 16th** 
New v.1.3.0 is online! Please read changelog on the site:
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by 23meg on 2005-05-27
downloading the new version now; thanks for this very useful app. have you tested it on debian unstable?

---

### Post by Knome_fan on 2005-05-27
Works great.
However, something seems to have gone wrong with the German localization, as it doesn't show Umlauts correctly.

---

### Post by saltydog on 2005-05-27
[QUOTE=23meg]downloading the new version now; thanks for this very useful app. have you tested it on debian unstable?[/QUOTE]

No. Could you do it for me please?

---

### Post by saltydog on 2005-05-27
[QUOTE=Knome_fan]Works great.
However, something seems to have gone wrong with the German localization, as it doesn't show Umlauts correctly.[/QUOTE]

The german Umlauts look nice on my PC. I will double-check, thanks.

---

### Post by pdk001 on 2005-05-27
thanks a bunch for useful application

---

### Post by 23meg on 2005-05-27
[QUOTE=saltydog]No. Could you do it for me please?[/QUOTE]

i shouldn't promise since i don't have it set up at the moment. as soon as i can i'll let you know.

---

### Post by josuealcalde on 2005-05-27
Spanish localization is broken.
Every á é í ó ú ñ appears as strange characters.

---

### Post by saltydog on 2005-05-27
[QUOTE=josuealcalde]Spanish localization is broken.
Every á é í ó ú ñ appears as strange characters.[/QUOTE]

I know. Sorry. I'm working on it.
For the time being, if you want the english text back, just do this:

sudo rm /usr/share/locale/es/LC_MESSAGES/bim.mo

---

### Post by Fab on 2005-05-27
[QUOTE=Knome_fan]Works great.
However, something seems to have gone wrong with the German localization, as it doesn't show Umlauts correctly.[/QUOTE]
 its encoded in utf 8, if that helps (maybe you try to view / use them with iso encoding?)

---

### Post by saltydog on 2005-05-27
New version 1.2.7 is online. Please provide feedback on fixed localizations.

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by Stemp on 2005-05-27
French localization work fine with the new version ;)
Thanks a lot

---

### Post by Knome_fan on 2005-05-27
Wow, that was fast. 

Thanks a lot, works like a charm now.  :grin:

---

### Post by saltydog on 2005-05-28
TO ALL RUSSIAN-LANGUAGE USERS:

if you want to have bum localized in russian language, without waiting for next release, you can download bum.mo file from this link:

[http://www.marzocca.net/linux/downloads/bum.mo](http://www.marzocca.net/linux/downloads/bum.mo)

Then, type this command:

sudo cp bum.mo /usr/share/locale/ru/LC_MESSAGES/bum.mo

---

### Post by saltydog on 2005-05-31
BUM is on Linux-Journal:
[http://www.linuxjournal.com/article/8322](http://www.linuxjournal.com/article/8322)

---

### Post by Jergar on 2005-06-01
[QUOTE=saltydog]New version 1.2.7 is online. Please provide feedback on fixed localizations.

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)[/QUOTE]
 German localisation works fine

Thanks for another fine job
Jergar

---

### Post by rwabel on 2005-06-13
Is it on my system only or does BUM take a long time to startup up?
Might it be, that some special service delays it?
How long does it take for u guys?

thanks

---

### Post by saltydog on 2005-06-14
[QUOTE=rwabel]Is it on my system only or does BUM take a long time to startup up?
Might it be, that some special service delays it?
How long does it take for u guys?

thanks[/QUOTE]


As stated on the docs ([http://www.marzocca.net/linux/bumdocs.html)](http://www.marzocca.net/linux/bumdocs.html)), BUM has a delay only on FIRST start, in order to build the cache. If you are continuing experiencing delays at start, it means that you have one or more init scripts that are not recognized as a package, so it take long to search a description for them.

Look at the list. If there is any package with no description, post here the name of the script.

---

### Post by rwabel on 2005-06-14
I've found 2 old vmware scripts which I've now deleted. Starts up much faster. There is one more which I don't know: discover
can I delete that one and what is it and where does it come from?

thanks

---

### Post by saltydog on 2005-06-14
[QUOTE=rwabel]I've found 2 old vmware scripts which I've now deleted. Starts up much faster. There is one more which I don't know: discover
can I delete that one and what is it and where does it come from?

thanks[/QUOTE]


I have deletd /etc/init.d/discover as it has no symlink anywhere, so it is never started at boot. That file will greatly delay BUM start has it doesn't appear to be an official file of the discover1 package.

---

### Post by rwabel on 2005-06-14
great! works fine now
thanks

---

### Post by saltydog on 2005-06-14
[QUOTE=rwabel]great! works fine now
thanks[/QUOTE]

I have better investigated on this. The file /etc/init.d/discover is not removed when the package "discover" is uninstalled from the system,  and this could probably happen in all Hoary distributions that have been upgraded from Warty.

If you experience an abnormal delay at BUM start, please check if you have a script named "discover" in /etc/init.d.  Then type:

dpkg -L discover

If the result of this command is:

package "discover" is not installed

you can safely delete the file /etc/init.d/discover and you BUM will then start very fast..

---

### Post by rwabel on 2005-06-14
good to know. When I check my system I've installed discover1, so I assume that in warty the hardware identification system was discover. Now under hoary it's discover1.

---

