---
title: "Ubuntu BootUp Manager"
date: 2005-04-17
forum: BUM - Boot Up Manager
---

### Post by saltydog on 2005-04-17
I have recently uploaded on my site the first release of Ubuntu Bootup Manager, a graphical tool to help user in configurating the runlevels setup scripts.

I have also provided the .deb package. 
You can dowload it from here:
[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

As it is the first release, I will be more than glad in receiving any comment/suggestion.

Fabio

**Update May 1st 2005**
New version 1.2.5 is online. now can activate/deactivate scripts also in rcS.d directory.

**Update May 21st 2005**
Other languages localization instructions are in this thread:

**Update May 26th 2005**
New version 1.2.6 is out! Name has changed too. Please refer to this thread:
[http://ubuntuforums.org/showthread.php?p=188161](http://ubuntuforums.org/showthread.php?p=188161)

**Update May 27th**
New v. 1.2.7 si online. Fixed localization bugs.

---

### Post by soul_rebel on 2005-04-17
Nice idea. Runlevel editing is really needed in ubuntu. I disagree with Ubuntu runlevels settings. A tool can be useful. I'll try and report

---

### Post by saltydog on 2005-04-18
I have issued release 1.0.1

[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

---

### Post by maqi on 2005-04-18
[QUOTE=saltydog]I have issued release 1.0.1

[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)[/QUOTE]
 Looks like a great tool. Will give it a try. It's nice that it shows up in the System--> Administration menu once installed :) This should be part of the default installation maybe.

maqi

---

### Post by Turin Turambar on 2005-04-18
I have just downloaded it and will let you know the results. Ubuntu seriously needs something like this one!

---

### Post by Turin Turambar on 2005-04-18
I tried it and so far I didn't find any bug. Works great and has a nice interface! Should be included in future Ubuntu versions. :)
Services explanations (Get info on script) is also very useful feature.

---

### Post by Turin Turambar on 2005-04-19
I noticed something:

I think that, generally, the missing feature is the list of /etc/init.d scripts, so you could easily add-remove them from the boot list.
I tried to "add a script", but I didn't see it in the list after?

I'm using sysv-rc-conf too, and services that I marked there are not displayed in BootUp (for example, hdparm) even after reboot?!

---

### Post by soul_rebel on 2005-04-19
yes rcS.d is missing! this should be fixed

---

### Post by saltydog on 2005-04-19
rcS is not missing. I have excluded it from the list as UBM is intended for normal user in a day-by-day use and should not let the user change rcS.d scripts. Please read the documentation (i have worked a full day on it!!).

From ubm docs ([http://www.marzocca.net/linux/ubmdocs.html](http://www.marzocca.net/linux/ubmdocs.html) )

1. Boot

When the systems boots, the /etc/init.d/rcS script is executed. It in turn executes all the S* scripts in /etc/rcS.d in alphabetical (and thus numerical) order. The first argument passed to the executed scripts is "start". The runlevel at this point is "N" (none).

Only things that need to be run once to get the system in a consistent state are to be run. The rcS.d directory is NOT meant to replace rc.local. One should not start daemons in this runlevel unless absolutely necessary. Eg, NFS might need the portmapper, so it is OK to start it early in the bootprocess. But this is not the time to start the squid proxy server. Ubuntu BootUp Manager will *not* modify scripts in this directory.

---

### Post by saltydog on 2005-04-19
[QUOTE=Turin Turambar]I 
I tried to "add a script", but I didn't see it in the list after?
![/QUOTE]

If you press on button "Add a script" and select a script file from the file selector (the file should be outside /etc/init.d), that file will be copied on the directory and will be listed in the "non-active" scripts at the bottom of the list. You then just need to "activate" it. It is written in the documentation.

---

### Post by c321 on 2005-04-20
[QUOTE=maqi]It's nice that it shows up in the System--> Administration menu once installed[/QUOTE]

UBM must be run as superuser. If it does not start up from the Kubuntu menu, right click and edit > check the "run as user" box and simply leave the user name field empty (unless you have created a root accout). next time you'll be asked for your password and UBM comes up.

---

### Post by saltydog on 2005-04-20
[QUOTE=c321]UBM must be run as superuser. If it does not start up from the Kubuntu menu, right click and edit > check the "run as user" box and simply leave the user name field empty (unless you have created a root accout). next time you'll be asked for your password and UBM comes up.[/QUOTE]

Thanks for the tip! I haven't got any chance to test it on Kubuntu...

---

### Post by saltydog on 2005-04-26
New release 1.2.0 of UBM is online. 
Re-designed GUI and new funtions (i.e. "Change Startup Priority").

[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

---

### Post by Chayyiel on 2005-04-26
Many thanks! A much needed tool!

---

### Post by Turin Turambar on 2005-04-26
... And new version is functioning really good! It looks good too. I hope Ubuntu team will look at it!! :)

---

### Post by jodef on 2005-04-27
Installed it in kubuntu but first had to install two packages:
libgtk2-perl
libglib-perl.

Menu entry created under System but I had to change two things:
1.pointed out by c321 
2.change command from : gksudo ubm -> sudo ubm.

Really nice and well designed and so few dependencies. Great work! Thanks!

---

### Post by saltydog on 2005-05-01
New version 1.2.5 is online [http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

Major change: now ubm can handle also scripts in System Runlevel (directory /etc/rcS.d)

---

### Post by cutOff on 2005-05-01
I hadn't seen this thread. 

It seems a great tool. I'll give it a try.

Thanx a lot!

---

### Post by saltydog on 2005-05-02
New version 1.2.5 now can activate/deactivate scripts also in rcS.d directory.

[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

---

### Post by ubuntu-geek on 2005-05-13
Bumped. This project now has its own section in 3rdparty applications :)

---

### Post by Knome_fan on 2005-05-14
Just stumbled upon this app and wanted to say thanks. Much needed, much appreciated and works great.

Thanks again!  :grin:

---

### Post by ddocta on 2005-05-17
As a n00b, this is a something I definitely needed a tool for.

---

### Post by josuealcalde on 2005-05-19
Yes, this was a tool really needed. I have Ksysv installed to do the job.

But, I think this need much "Human" work.

I mean, a normal user can know what is a service but he don't need understand what k22 means or what a "Run Level" is.

I mean, this application is very good for a linux advanced user but it isn't as good for people which doesn't now how linux services work.

It is usefull for me, but I think, it should have a more intuitive interface whith more information messages.

---

### Post by saltydog on 2005-05-20
> It is usefull for me, but I think, it should have a more intuitive interface whith more information messages.

I have put the lower pane in order to give as much information as possible to the user. There is also a "documentation" section in my site at [http://www.marzocca.net/linux/ubmdocs.html](http://www.marzocca.net/linux/ubmdocs.html) which explains to the new user what are runlevels and priority.

UBM follows Ubuntu's policy on runlevels (RL 2-3-4-5 are the same) and activate/deactivate services with update-rc.d, so it is hard to mess-up the system.

I have put also start/stop priorities (S and K ) because I believe that even a newbie can read the docs and learn what sysv init is. And he "should" learn, otherwise we are making another Windows-clone.

---

### Post by lucascr on 2005-05-20
very nice app. I used it with Kubuntu and it works fine so far.  Just one small thing I had to fix: the package gksu wasn't installed. I presume it is installed by default in Ubuntu, but not in Kubuntu. So peraphs gksu could be added as a dependency.
Ciao,
Luca

---

### Post by saltydog on 2005-05-20
Ciao Luca,

it is not a good idea to add gksu in KDE.... 
Maybe you could replace it with kdesu or kdesudo

---

### Post by xristos on 2005-05-20
Great app guys !!!

---

### Post by saltydog on 2005-05-21
I am going to provide developers with the .pot file for local translation of the program. 
I will post a message here when ready.

---

### Post by ACK!! on 2005-05-23
[QUOTE=xristos]Great app guys !!![/QUOTE]

Oh yes, I completely agree.  I remember considering the use of gnome-system tools in Ubuntu I had no idea why runlevel-admin was NOT used but figured it was a bug on their side or something blah....blah.  Anyway, it is really good to see this tool out there.  A long with the menueditor and this nice tool I guess the only thing on my hit list is a good gtk2 based cron editor.  

OMG, thank you very, very, much!!

 \\:D/

---

### Post by saltydog on 2005-05-23
I thank you all guys and I am very happy you like the application, and that UBM has been of any help for you in improving your system and your knowledge.
Unfortunately, this evening I had my first (and last) chat in #ubuntu-motu because friends asked me to contact them in order to introduce ubm in Universe.
I was very unlucky because I met a very unpleasant ubuntu representative, who started acting as a Court Judge from the desk, treating myself as an accused.

The discussion was little technical, and I couldn't even present the application beacuse he started offending (arguing a sort of debian policy on the packages). THIS IS NOT "HUMANITY TO OTHERS"!! This is not the Ubuntu Code of Conduct they claim for everyone of us.

Anyway, I will continue updating and developing UBM. It is just a gift from me to all human beings who can take any advantage from it.

---

### Post by nageshtv on 2005-05-26
Hi,

I have this tool installed and am very happy with it. However, I am not able to add a new script. I have cisco vpnclient installed and need to add /etc/init.d/vpnclient_init to the boot startup scripts. I tried using the UI but for some reason it doesnot get added. 

I am not sure if I am going wrong anywhere.

Nagesh

---

### Post by saltydog on 2005-05-26
[QUOTE=nageshtv]Hi,

I have this tool installed and am very happy with it. However, I am not able to add a new script. I have cisco vpnclient installed and need to add /etc/init.d/vpnclient_init to the boot startup scripts. I tried using the UI but for some reason it doesnot get added. 

I am not sure if I am going wrong anywhere.

Nagesh[/QUOTE]


Is it a new script written by you, or should it have been installed by the package?

---

### Post by oopsz on 2005-05-26
awesome tool, thanks!
is there any way you could either a) get this into an apt repository or b) have a release mailing list?  either would be awesome :)

---

### Post by saltydog on 2005-05-26
[QUOTE=oopsz]awesome tool, thanks!
is there any way you could either a) get this into an apt repository or b) have a release mailing list?  either would be awesome :)[/QUOTE]


I am working with ubuntu people to have in soon in universe, maybe with Breezy or before..
We can use this forum for any support you may need.

**New version 1.2.6 is out!**
Please refer toi this new thread:
[http://ubuntuforums.org/showthread.php?p=188161](http://ubuntuforums.org/showthread.php?p=188161)

---

### Post by nageshtv on 2005-05-26
The script vpnclient_init is a script copied to /etc/init.d by the vpn_install program. It comes with the package cisco vpn client package.

Nagesh

---

### Post by saltydog on 2005-05-27
[QUOTE=nageshtv]The script vpnclient_init is a script copied to /etc/init.d by the vpn_install program. It comes with the package cisco vpn client package.

Nagesh[/QUOTE]

So you don't need to "Add a new scritp", but simply to "Activate" the script..
Look in the list, find your script, click on the check box to activate it at boot, then click on "Apply".

---

### Post by destino on 2005-05-31
I'm not able to install bum_1.2.7_all.deb, I get this message:

dpkg: dependency problems prevent configuration of bum:
 bum depends on libgtk2-perl; however:
  Package libgtk2-perl is not installed.
 bum depends on libgnome2-perl; however:
  Package libgnome2-perl is not installed.
 bum depends on libglib-perl; however:
  Package libglib-perl is not installed.
dpkg: error processing bum (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bum

---

### Post by saltydog on 2005-05-31
[QUOTE=destino]I'm not able to install bum_1.2.7_all.deb, I get this message:
[/QUOTE]

As the message says, you need first to install the following packages:

apt-get install libglib-perl libgtk2-perl libgnome2-perl

Are you not running a standard Ubuntu installation?

---

### Post by destino on 2005-05-31
I did an apt-get -f install and now it's working. :smile:

---

### Post by saltydog on 2005-05-31
[QUOTE=destino]I did an apt-get -f install and now it's working. :smile:[/QUOTE]


Yes, because previous dpkg -i saved the dependencies and apt-get update -f resolved them!

Happy you get it working.

---

### Post by sithia on 2005-06-02
I'm running Debian testing and I just upgraded my hardware to an amd64 3000+. I'm planning to switch over to the amd64 dist (currently only in unstable) in the next month or so after Sarge is released (and amd64 is slated to join the normal testing repository). Anyone have any idea whether bum will run against amd64 without a 32-bit chroot?

---

### Post by saltydog on 2005-06-03
[QUOTE=sithia]I'm running Debian testing and I just upgraded my hardware to an amd64 3000+. I'm planning to switch over to the amd64 dist (currently only in unstable) in the next month or so after Sarge is released (and amd64 is slated to join the normal testing repository). Anyone have any idea whether bum will run against amd64 without a 32-bit chroot?[/QUOTE]

I didn't test it yet over AMD64, but BUM is a Perl-Gtk2 application, so it is NOT a compiled binary for a specific platiform. It should work (I'm 90% sure), but haven't tested..

If you do, please provide feedback here..

Thanks.

---

