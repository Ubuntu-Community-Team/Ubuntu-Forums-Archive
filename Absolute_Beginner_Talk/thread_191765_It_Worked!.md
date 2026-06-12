---
title: "It Worked!"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-07
Thanks to everyone who helped me!

ok now to my question as i look for a way to get my wireless working.

i can see my files in windows each and every one of them its so great! recognized my new d drive! 

but how can i get my firefox themes and bookmarks and extenstions from there? i had a ton! and most i dont remember where i got them!

do i need an antivrus program?

i read i need a firewall called firestarter is that correct?

is this a good source site to learn how to download programs?
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

and finally what are some estentials i need for linux?

oh yes how do i get the kubuntu desktop so i can rotate them?

once again thanks everyone!

---

### Post by gerbman on 2006-06-07
[QUOTE=maddbaron]do i need an antivrus program?[/QUOTE]Nope.

> i read i need a firewall called firestarter is that correct?You'd probably be okay without one, but if you want to give firestarter a try it's pretty easy to use. Just install it from the repositories```
sudo apt-get install firestarter
```and fire it up.

> is this a good source site to learn how to download programs?
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)Sure, looks good.

> and finally what are some estentials i need for linux?It depends on what you wanna do, there's a Linux solution for pretty much everything out there.

---

### Post by ComplexNumber on 2006-06-07
>  do i need an antivrus program? not really. but it woudn't hurt to use one.



> 
but how can i get my firefox themes and bookmarks and extenstions from there?  make sure that you can see hidden files in windows. you will find them here:
C:\Documents and Settings\<yourname>\Application\Data\Mozilla\Firefox\Profiles\<soemcode>.default\extensions


> 
i i read i need a firewall called firestarter is that correct? i personally think so, yes. i also think they're much more necessary than antivirus on linux. firestarter is a good program. thats the one that i'm using.



>  is this a good source site to learn how to download programs? don't know about that one. [here]("http://www.linuxnewbieguide.org/") is a good one

> 
and finally what are some estentials i need for linux? install automatix.



>  oh yes how do i get the kubuntu desktop so i can rotate them? someone who has installed kubuntu will be able to help you with this.

---

### Post by aysiu on 2006-06-08
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) to get access your Windows partition.

---

### Post by maddbaron on 2006-06-08
[QUOTE=ComplexNumber]not really. but it woudn't hurt to use one.



 make sure that you can see hidden files in windows. you will find them here:
C:\Documents and Settings\<yourname>\Application\Data\Mozilla\Firefox\Profiles\<soemcode>.default\extensions


 i personally think so, yes. i also think they're much more necessary than antivirus on linux. firestarter is a good program. thats the one that i'm using.



 don't know about that one. [here]("http://www.linuxnewbieguide.org/") is a good one

 install automatix.



 someone who has installed kubuntu will be able to help you with this.[/QUOTE]


 make sure that you can see hidden files in windows. you will find them here:
C:\Documents and Settings\<yourname>\Application\Data\Mozilla\Firefox\Profiles\<soemcode>.default\extensions


do i have to type sudo something in a terminal?

and

how do i install plugins? i downloaded the macromedia plugin and i have no clue how to install.

i want to download aim from here b/c  gaim cancels aim file transfers without notice.
[http://www.aim.com/get_aim/linux/latest_linux.adp#install](http://www.aim.com/get_aim/linux/latest_linux.adp#install)

but this is all chinese to me lol

---

### Post by aysiu on 2006-06-08
Automatix will install plugins for you, but if you want to do it yourself (it's not that difficult), read this:

[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

and this

[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by BoyOfDestiny on 2006-06-08
[QUOTE=maddbaron]make sure that you can see hidden files in windows. you will find them here:
C:\Documents and Settings\<yourname>\Application\Data\Mozilla\Firefox\Profiles\<soemcode>.default\extensions


do i have to type sudo something in a terminal?

and

how do i install plugins? i downloaded the macromedia plugin and i have no clue how to install.

i want to download aim from here b/c  gaim cancels aim file transfers without notice.
[http://www.aim.com/get_aim/linux/latest_linux.adp#install](http://www.aim.com/get_aim/linux/latest_linux.adp#install)

but this is all chinese to me lol[/QUOTE]

For the firefox stuff, at least for bookmarks. Just go to Bookmarks, Manage bookmarks, use export. copy those files and on your ubuntu box import it.

Anyway as for downloads, just a change in mindset mostly. You are used to going on the web, hunting for what you want, then download and install.
(don't worry, there are still ways to do this, but it's not the "easy" way)

Ubuntu has a central package manager. 

First,

System -> Administration -> Software Properties

Enable universe and preferably multiverse too.

Next launch synaptic package manager

System -> Administration -> Synaptic Package Manager

Press refresh.

You should see a listing for like 18.000 packages.

If you want flash search for flashplugin

Should be like flashplugin-nonfree

For most codecs, I'd just grab everything with the word gstreamer.10 in it

Just check the boxes, choose mark for install. Then hit apply, sit back and relax...

Anyway, synaptic is a bit dry, but you can search it for stuff you need. For many apps and games, try Applications -> Add/Remove. It's categorized, with descriptions, and very easy install/un-install of plenty of great software.

Guess that's about it,

Congratulations on getting everything working, hope you have a lot of fun.

P.S. For what it's worth, Ubuntu out of the box doesn't have any ports listening. Unless you set up some service like FTP or SSH, you don't "NEED" a firewall. If you decide to host a webpage, or use your machine from a remote location... Then I'd recommend it. (Also, my router has a hard firewall anyway... So yeah... Up to you)

---

### Post by drtvasudevan on 2006-06-08
[QUOTE=maddbaron]Thanks to everyone who helped me!

oh yes how do i get the kubuntu desktop so i can rotate them?

once again thanks everyone![/QUOTE]

lok at this thread:
[http://www.ubuntuforums.org/showthread.php?t=188679](http://www.ubuntuforums.org/showthread.php?t=188679)

tv

---

### Post by aysiu on 2006-06-08
[QUOTE=drtvasudevan]lok at this thread:
[http://www.ubuntuforums.org/showthread.php?t=188679](http://www.ubuntuforums.org/showthread.php?t=188679)

tv[/QUOTE] If you don't feel like reading that whole thread, this tutorial walks you through the process a bit: [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by maddbaron on 2006-06-08
ok, i just went to search for the utomatrix thing and found the how to i follow it and got this

maddbaron@alchemist:~$ gpg --keyserver subkeys.pgp.net --recv-keys 521A9C7C
gpg: directory `/home/maddbaron/.gnupg' created
gpg: new configuration file `/home/maddbaron/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/maddbaron/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/maddbaron/.gnupg/secring.gpg' created
gpg: keyring `/home/maddbaron/.gnupg/pubring.gpg' created
gpg: requesting key 521A9C7C from hkp server subkeys.pgp.net
gpg: /home/maddbaron/.gnupg/trustdb.gpg: trustdb created
gpg: key 521A9C7C: public key "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
maddbaron@alchemist:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
Password:
OK

does that mean i have that program now?

---

### Post by maddbaron on 2006-06-08
wow this is great weird and i am not sure exactly what i am typing in terminal or antything but its fun

i just want to be able to play embedded videos and music i'll save the downloading of movie music to windows altho i;d like to be able to read and play them in ubuntu. i tried looking at my windows files and one said i need a password. i never had a windows password. weird.

i need to get aol messenger for linux ...

and a writing program called ywriter and celtx. 

once i get those i am set!

btw, i set up some folders when i installed how do i see the size of my folders in ubuntu?

---

### Post by aysiu on 2006-06-08
[QUOTE=maddbaron]
btw, i set up some folders when i installed how do i see the size of my folders in ubuntu?[/QUOTE] Right-click.

---

### Post by gerbman on 2006-06-08
[QUOTE=maddbaron]i'll save the downloading of movie music to windows[/QUOTE]Try [Limewire]("https://wiki.ubuntu.com/P2PHowTo?highlight=%28limewire%29#head-7fb2803e9171c3a6b582e29c5bf1a7b907b4044b") or [Frostwire]("https://wiki.ubuntu.com/FrostWire?highlight=%28frostwire%29")

> i need to get aol messenger for linux ...GAIM should already be installed. It's similar to AIM.

---

### Post by maddbaron on 2006-06-08
i like gaim a lot! but it doesnt allow for files to be transferred. my friend tried to transfer a file to me from her aim to my gaim and gaim cancelled it but said she was the one who cancelled it when she didnt. anyway to fix that?

---

### Post by maddbaron on 2006-06-08
LINUX ROCKS!!!!!!!!!!!!!

omg!

i went searchng and added all my extensions so i am good.

i somehow added the kda software to my gnome so i dont need to switch desktops now either!

i just need to get this celtx and ywriter and i am good!

by the way anyone know of where i can find pics of the linux penguin? like anime style?

---

### Post by aysiu on 2006-06-08
[QUOTE=maddbaron]
by the way anyone know of where i can find pics of the linux penguin? like anime style?[/QUOTE] Try [here](http://tux.crystalxp.net/index.php) or [here](http://images.google.com/images?hl=en&q=tux&btnG=Google+Search&sa=N&tab=wi).

---

### Post by maddbaron on 2006-06-08
thanks!

n just to b clear I dont need a firewall or antivirus b/c no viruses 4 linux and no listening ports either?

---

### Post by maddbaron on 2006-06-08
ok i have a problem. i tried going to youtube and i can see the video but cant hear the sound? i hear sound when i started ubuntu and when i instant message but not on the page. and also if anyone has myspace. u know the myspace music player? it also doesnt work for me. any ideas?

---

### Post by aysiu on 2006-06-08
You [have extra repositories enabled](http://www.psychocats.net/ubuntu/sources), right? If so, try closing Firefox and pasting this command in the terminal: ```
sudo aptitude update && sudo aptitude install alsa-oss
```

---

### Post by maddbaron on 2006-06-08
thanks!

---

### Post by maddbaron on 2006-06-08
any links on where i can find sudo for getting the stuff i need to watch wmv and  other media? i have the kubuntu and ubuntu players now any add on's? 

if i get frostwire do i need a firewall since its peer to peer? and for ktorrent also?

---

### Post by maddbaron on 2006-06-08
i still cant get sound on youtube videos....i dont know what to do. i downloaded the stuff you said...this is weird.

and that synaptic package manager is off the hook! found lots of stuff the xine and mplayer stuff lots its great...

but i still cant hear youtube and my wireless doesnt work and i still have no clue how to install celtx after i downloaded it,..bitter with the sweet.

---

### Post by maddbaron on 2006-06-08
hi I am trying to install a .tgz file i downloaded. 
i extracted to my desktop and went to [http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif](http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif)

and followed the instructions and got this issue as shown in the attachment.
what do i type to install the application in the folder?

---

### Post by sherlock-holmes on 2006-06-08
[QUOTE=maddbaron]hi I am trying to install a .tgz file i downloaded. 
i extracted to my desktop and went to [http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif](http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif)

and followed the instructions and got this issue as shown in the attachment.
what do i type to install the application in the folder?[/QUOTE]

u might need build-essential package to have make working...

```
sudo apt-get install build-essential
```

to install 

```
sudo dpkg -i filename.deb
```

hope it helps..

---

