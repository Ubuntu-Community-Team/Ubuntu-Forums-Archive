---
title: "Help me with installing wine please"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Edje on 2006-08-18
I have downloaded some package and  saved it on my desktop.
[INDENT]wine_0.9.12-winehq2-ubuntu-6.06-1.dsc
wine-dev_0.9.12-winehq2-ubuntu-6.06-1_i386.deb
wine_0.9.12-winehq2-ubuntu-6.06.orig.tar.gz
wine_0.9.12-winehq2-ubuntu-6.06-1_i386.deb
wine_0.9.12-winehq2-ubuntu-6.06-1.diff.gz[/INDENT]
I opened "terminalvenster" and typed: sudo apt-get install wine

And this is what I get
> Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Pakket wine is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
E: Pakket wine heeft geen installeerbare kandidaat


I don't know what i'm doing wrong or what is going wrong.
Help me out please.

---

### Post by waldschm on 2006-08-18
That error message is really bizarre, is English not your system language or is that something with terminalvenster? Anyway, I installed wine by adding the wine repository and installing it from synaptic. The Wine website has these instructions:

To install Wine from the WineHQ APT repository, you need to configure APT to look in the right place for the Wine packages. On Ubuntu systems, and those using the Synaptic Package Manager, this can be done easily by opening up Synaptic (System->Administration->Synaptic Package Manager) and selecting Settings->Repositories. Then click add, select custom, and enter one of the following:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Then you can simply download from Synaptic, this installed without any errors on my machine and I would recommend attempting the installation in this manner.

---

### Post by moma on 2006-08-18
>E: Pakket wine heeft geen installeerbare kandidaat

I think you must enable the Universe repository in /etc/apt/sources.list 
Do as instructed in this guide
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

You can also add this wine repository to /etc/apt/sources.list 
```
deb http://wine.sourceforge.net/apt/ binary/
```

Then do 
$ [COLOR="Green"]sudo apt-get update[/COLOR] 
and install wine

---

### Post by waldschm on 2006-08-18
Ubuntu's repository has an outdated version of wine, I'm not sure about the sourceforge one, but I know the one directly from the wine website gives you wine 0.9.19 at this point.

---

### Post by moma on 2006-08-18
> **waldschm said:**
> Ubuntu's repository has an outdated version of wine, I'm not sure about the sourceforge one, but I know the one directly from the wine website gives you wine 0.9.19 at this point.

Oops.  Agree:
Replaced the wine-repo with 
```
deb http://wine.budgetdedicated.com/apt dapper main
```
(Ref: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) )

$ [COLOR="Green"]sudo apt-get update [/COLOR]
$ [COLOR="Green"] sudo apt-get install --reinstall wine[/COLOR]

And it said:
Get: 1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main wine 0.9.19~winehq0~ubuntu~6.06-2 [8854kB]
Setting up wine (0.9.19~winehq0~ubuntu~6.06-2) ...

$ [COLOR="Green"]wine --version[/COLOR]
Wine 0.9.19
------------------------------------------------------------------

@Edje: Do you wanna see the messages in English? Do:
$ [COLOR="Green"]LANGUAGE=en_EN sudo apt-get install wine [/COLOR]

---

### Post by Edje on 2006-08-18
Thanks this helps me a lot, WINE is working now.

And by the way the language of my system is Dutch because I live in the Netherlands, sorry about that.

---

