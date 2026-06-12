---
title: "Is ubuntu for them?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Danilo Leon on 2007-04-19
I come from a country where only 10% of the population uses and are connected to the internet (I'm luck enough to be part of that 10%).  I want to recommend ubuntu to my friends but unlike me they do not have internet access.  since in my very short experience with ubuntu, most updates were done through the internet, with the pc directly connecting to the web.

is it posibble and/or feasible for my friends to use ubuntu even though they do not have net access?

can they have security updates by going to an internet shop and download the file to a flash drive, bring it back home and install the update?

thanks.

---

### Post by hyper_ch on 2007-04-19
If they don't have internet, what do they need security patches for?

And I tend to say "yes" - Ubuntu is a good choice. Download the DVD which has a lot more appz for them to work with as dvd-repository :)

---

### Post by Danilo Leon on 2007-04-19
I was thinking that maybe viruses designed for linux can be transferred via removable drives so there is a need for security updates.

Is it possible to download specific programs (e.g. restricted formats) using Windows OS (coz most internet shops uses Windows) and then save it in removable drives then go back home and install the upgrades?

---

### Post by meborc on 2007-04-19
you really don't need upgrades when you are not connected to net... the probability to get a linux virus in a country where internet is not widespread is marginal... i would not worry... 

to suggest ubuntu or not... well... if they are gamers, then probably not... not all windows games can be run under wine...

if they use the computer just for office/graphical designing/or they are willing to try linux games then why not :)

the lack of internet is the only problem, as most of the stuff you need to install after the base installation needs internet (multimedia codecs, special programs not included in the base install)

---

### Post by Danilo Leon on 2007-04-19
> **meborc said:**
> the lack of internet is the only problem, as most of the stuff you need to install after the base installation needs internet (multimedia codecs, special programs not included in the base install)

yup, that is precisely what deters them from using ubuntu.  So is there a work-around for this?  Getting updates from a different pc and then installing the downloaded files in their pc?

---

### Post by meborc on 2007-04-19
you can access the archives with ubuntu/windows and download the sourcecodes/deb.files and then install them in your friends computers... but you will run into problems as most of the packages in the archives need some dependencies... which need dependencies... etc...

what i would do is through a LAN party at your house... bring your friends with your computers to your place and install all you need from your net cable... it is way better then to run back and forth with your usb drive :)

---

### Post by omeng on 2007-04-19
I am also from the Philippines as Danilo, although there are few percentage of the population who has internet access this few percentage is equivalent to around 8 million and there are many viruses (affects windows system, not sure if there are for linux) encountered especially on removable storage devices. Is there any free antivirus designed for linux?

---

### Post by Danilo Leon on 2007-04-19
> **meborc said:**
> what i would do is through a LAN party at your house... bring your friends with your computers to your place and install all you need from your net cable... it is way better then to run back and forth with your usb drive :)

this is a great idea :D.  making ubuntu work for others while having fun

---

### Post by Danilo Leon on 2007-04-19
> **omeng said:**
> I am also from the Philippines as Danilo, although there are few percentage of the population who has internet access this few percentage is equivalent to around 8 million and there are many viruses (affects windows system, not sure if there are for linux) encountered especially on removable storage devices. Is there any free antivirus designed for linux?

have you tried to google it?  it might provide the answers

---

### Post by meborc on 2007-04-19
> **omeng said:**
> I am also from the Philippines as Danilo, although there are few percentage of the population who has internet access this few percentage is equivalent to around 8 million and there are many viruses (affects windows system, not sure if there are for linux) encountered especially on removable storage devices. Is there any free antivirus designed for linux?

you sound like you just converted from windows :D ... there are SO few linux viruses that you probably should not worry about that... if you ARE still worried, try this page - [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

the only real reason why a linux user installs antivirus software is to protect their windows partitions and to prevent from spreading windows viruses... which by the way have NO affect on linux

also read this for more info - (this is not 100% accurate though) [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#Do_I_need_firewall.2C_antivirus.2C_disk_defragmentation.2C_on_Linux.3F](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#Do_I_need_firewall.2C_antivirus.2C_disk_defragmentation.2C_on_Linux.3F)

this old article might also help [http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)

edit: this is good read also - [http://librenix.com/?inode=21](http://librenix.com/?inode=21)

---

### Post by jvc26 on 2007-04-19
I'd just point you to [here]("http://www.psychocats.net/ubuntu/security") which will explain something towards the virus situation. There arent very many for linux, and those that are dont widely distribute (at present) you cannot be infected by Windows viruses at the moment (though there was an interesting article a while back of someone trying to run windows viruses in wine to see if they worked - they pretty much didnt). You can download the .deb files (and as long as you get their corresponding dependencies) you can then take them to wherever and install them. Or, alternatively, you can find out the packages your friends want, and then via synaptic package manager, use the generate download script option then run that script and that will get you the .deb files for you to install. (which you can then put on a flash drive and give to your friends) It is possibly, its just not as straightforward as being directly connected to the net.
Il

---

### Post by bullgr on 2007-04-19
> **Danilo Leon said:**
> yup, that is precisely what deters them from using ubuntu.  So is there a work-around for this?  Getting updates from a different pc and then installing the downloaded files in their pc?

if you can't download the iso, you can request a dvd from ship-it ([www.ubuntu.com](www.ubuntu.com)) or buy it from a partner.
with this dvd (included in the repositories automatically after the install) you can install more app's than
the default ones.

and for updates, it is not so live-dead critical... your ubuntu install will still work.
i have an old pc with xubuntu 6.06 dapper installed in my countryhome (no internet) and works perfect.
i don't feel any need to update and if i like a new app, i installed it from the dvd...

---

### Post by Danilo Leon on 2007-04-19
> **bullgr said:**
> and for updates, it is not so live-dead critical... your ubuntu install will still work.

but how about installing needed files to run restricted formats like mp3 or avi.  is this available on the dvd?

---

### Post by jvc26 on 2007-04-19
Probably not as Ubuntu dont ship the proprietary codecs I dont think. Again you can download them for your friends (see my post) or - have you looked at linux mint? (I think its that one) Thats Ubuntu based but ships with codecs (look into it, am pretty sure thats the case)
Il

---

### Post by eentonig on 2007-04-19
Probably not. You will need to use the 'generate download script' option for that.

---

### Post by omeng on 2007-04-19
Thank you very much meborc for the links. You said that there are only few linux viruses known. Is this because there are few who develop linux viruses or is it that Linux System is secure so it is hard to find flaws on the system?
BTW, this is my 1st day of using ubuntu. It is easier to use compare to other linux distros.

---

### Post by meborc on 2007-04-19
> **omeng said:**
> Thank you very much meborc for the links. You said that there are only few linux viruses known. Is this because there are few who develop linux viruses or is it that Linux System is secure so it is hard to find flaws on the system?
BTW, this is my 1st day of using ubuntu. It is easier to use compare to other linux distros.

it is very hard to make a linux virus for many different reasons... few that come to mind are a) to do damage, the virus must have access to your root files... without your password, it can no be done b) there are so many different architectures, systems, setups, configurations... virus that could possibly affect one computer probably can't affect another... so you can't make a good widespread linux virus

google for more info on that :)

---

### Post by Danilo Leon on 2007-04-19
thanks for all the info...with it i think i can convince them to use ubuntu :D

---

### Post by bullgr on 2007-04-19
> **Danilo Leon said:**
> but how about installing needed files to run restricted formats like mp3 or avi.  is this available on the dvd?

this is the issue for using the dvd...
all the packages (about 17.000) in ubuntu repos are in the dvd.
so, the needed files to run restricted formats are too (for example libdvdread for dvd decryption).

the only difference from a dvd with the repos is that you can't have the latest updates of these packages...
but this does matter... the mashine still works.

---

### Post by Danilo Leon on 2007-04-19
> **bullgr said:**
> this is the issue for using the dvd...
all the packages (about 17.000) in ubuntu repos are in the dvd.
so, the needed files to run restricted formats are too (for example libdvdread for dvd decryption).

the only difference from a dvd with the repos is that you can't have the latest updates of these packages...
but this does matter... the mashine still works.

thanks bullgr.  will work on requesting for the dvd as soon as possible.  cheers!

---

