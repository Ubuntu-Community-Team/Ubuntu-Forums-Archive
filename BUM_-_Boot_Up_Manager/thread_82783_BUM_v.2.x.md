---
title: "BUM v.2.x"
date: 2005-10-27
forum: BUM - Boot Up Manager
---

### Post by saltydog on 2005-10-27
[B]New version 2.0.0 is out !
[/B]

Full code and GUI re-styling, added separation  between normal user mode and advanced mode.

Home site: [http://www.marzocca.net/linux/bum.html]("http://www.marzocca.net/linux/bum.html")

---

### Post by Manny C on 2005-10-27
Who needs a BUM when one has INITNG. I got INITNG working...have you? :cool:

---

### Post by saltydog on 2005-10-27
[QUOTE=Manny C]Who needs a BUM when one has INITNG. I got INITNG working...have you? :cool:[/QUOTE]

G'day mate,

... all of those not using initng!

---

### Post by emendelson on 2005-10-28
When I try to start bum on a fairly clean Breezy system, I get this error:

Can't locate Gtk2/GladeXML.pm in @INC (@INC contains: /usr/lib/bum /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/bum/bum_app.pm line 44.
BEGIN failed--compilation aborted at /usr/lib/bum/bum_app.pm line 44.
Compilation failed in require at /usr/bin/bum line 27.
BEGIN failed--compilation aborted at /usr/bin/bum line 27.

EDIT - The solution is to install libgtk2-gladexml-perl. Shouldn't this be built into the deb file so that it gets installed by apt automatically??

---

### Post by saltydog on 2005-10-28
Yes, you need to install:

sudo apt-get install libgtk2-gladexml-perl

Sorry for that. I have fixed in v.2.1.0, currently uploaded, that will be tomorrow available in debian. The v.2.1.0 will also have an improvement: all columns will be cleckable and sortable!

---

### Post by fuscia on 2005-10-29
i sure do like bum.

---

### Post by saltydog on 2005-10-29
Thanks!

---

### Post by emendelson on 2005-10-30
bum is terrific; thank you for it. Tiny typo on your site: you list the 2.0.0-1 version for download, but I think you mean something like 2.1.0-1.

---

### Post by donar73 on 2005-10-30
[QUOTE=saltydog]Yes, you need to install:

sudo apt-get install libgtk2-gladexml-perl

Sorry for that. I have fixed in v.2.1.0, currently uploaded, that will be tomorrow available in debian. The v.2.1.0 will also have an improvement: all columns will be cleckable and sortable![/QUOTE]

Thanks, works great now! :)

---

### Post by saltydog on 2005-11-03
New version 2.1.1 is out now.
Check web site: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by foxiness on 2005-11-03
good work Fabio i use this tool start from 1.2.x and do what i want :) 

thanks fabio

---

### Post by saltydog on 2005-11-03
[QUOTE=foxiness]good work Fabio i use this tool start from 1.2.x and do what i want :) 

thanks fabio[/QUOTE]


Happy to know it is useful.
Thanks!

---

### Post by donar73 on 2005-11-04
[QUOTE=foxiness]good work Fabio i use this tool start from 1.2.x and do what i want :) 

thanks fabio[/QUOTE]
I'd like to double this - just upgraded to 2.1.1 and it works as great as always! :)  Thank you for your good work!

---

### Post by saltydog on 2005-11-18
New version 2.1.2 is online!

If you want to be advised as soon as new releases of BUM come out, you can subscribe to the bum's Package Tracking System here:
[http://packages.qa.debian.org/b/bum.html](http://packages.qa.debian.org/b/bum.html)

---

### Post by donar73 on 2005-11-19
[QUOTE=saltydog]New version 2.1.2 is online!

If you want to be advised as soon as new releases of BUM come out, you can subscribe to the bum's Package Tracking System here:
[http://packages.qa.debian.org/b/bum.html](http://packages.qa.debian.org/b/bum.html)[/QUOTE]

Thx, works great! :)

---

### Post by davidfossil on 2005-11-24
I'm getting this when I'm trying to start bum:
Cannot write file /var/lib/bum/packages ! at /usr/lib/bum/bumlib.pm line 482.

A window flashes quickly on the screen,  and the application appears on the taskbar - just to disappear again. Have I forgotten something important? I'm quite new to linux, so it might just be me doing something all wrong...

Hope anyone is able to help :???:

---

### Post by garba on 2005-11-24
We BADLY need a tool like this in ubuntu, I hope it will make it in dapper, the "services" app is laughable to say the least... keep up with the good work  this app has got what it takes to fill what was a long standing gap imo :)

---

### Post by saltydog on 2005-11-25
Thanks garba.
Latest version of BUM will be un dapper (universe, not main).

---

### Post by gold4tune on 2005-12-02
When i start bum (on kde) nothing appen...  I install it with the .deb.  what should i do to solve de problem!!!

thx

---

### Post by saltydog on 2005-12-02
[QUOTE=gold4tune]When i start bum (on kde) nothing appen...  I install it with the .deb.  what should i do to solve de problem!!!

thx[/QUOTE]


In order to debug your problem, open a terminal window, type
sudo bum

then watch at any error message in the terminal and post it here..

---

### Post by _Ramirez_ on 2005-12-02
sudo bum gives me this:

Cannot write file /var/lib/bum/packages ! at /usr/lib/bum/bumlib.pm line 482.

Just like davidfossil said???

---

### Post by saltydog on 2005-12-02
[QUOTE=_Ramirez_]sudo bum gives me this:

Cannot write file /var/lib/bum/packages ! at /usr/lib/bum/bumlib.pm line 482.

Just like davidfossil said???[/QUOTE]

In a standard ubuntu installation, you shold have write permissions in /var/lib directory.. Could you pls verify?

---

### Post by gold4tune on 2005-12-02
that's wat appen:

Can't locate Glib.pm in @INC (@INC contains: /usr/lib/bum /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/bum/bum_app.pm line 34.
BEGIN failed--compilation aborted at /usr/lib/bum/bum_app.pm line 34.
Compilation failed in require at /usr/bin/bum line 27.
BEGIN failed--compilation aborted at /usr/bin/bum line 27.

is something i must install... i'm on kde!!!

---

### Post by saltydog on 2005-12-02
[QUOTE=gold4tune]that's wat appen:

Can't locate Glib.pm in @INC (@INC contains: /usr/lib/bum /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/bum/bum_app.pm line 34.
BEGIN failed--compilation aborted at /usr/lib/bum/bum_app.pm line 34.
Compilation failed in require at /usr/bin/bum line 27.
BEGIN failed--compilation aborted at /usr/bin/bum line 27.

is something i must install... i'm on kde!!![/QUOTE]

Of course. Your system is missing main libraries of libgtk2-perl. How did you install bum? Those are packages dependencies...

---

### Post by Devlin on 2005-12-03
[QUOTE=saltydog]In a standard ubuntu installation, you shold have write permissions in /var/lib directory.. Could you pls verify?[/QUOTE]

I'm getting the same error as _Remirez_ and davidfossil...

Cannot write file /var/lib/bum/packages ! at /usr/lib/bum/bumlib.pm line 482.

---

### Post by saltydog on 2005-12-03
[QUOTE=Devlin]I'm getting the same error as _Remirez_ and davidfossil...

Cannot write file /var/lib/bum/packages ! at /usr/lib/bum/bumlib.pm line 482.[/QUOTE]

This report has no meaning for me. Please add:

- your ubuntu version
- your BUM version
- does it happen at first run or at each run?
- have you checked your permission to write as sudo on /var/lib?

---

### Post by saltydog on 2005-12-03
[QUOTE=Devlin]I'm getting the same error as _Remirez_ and davidfossil...

Cannot write file /var/lib/bum/packages ! at /usr/lib/bum/bumlib.pm line 482.[/QUOTE]

I am releasing a new version in the coming days due to this bug.

In the meanwhile, from a terminal type:

sudo rm /var/lock/bum
sudo mkdir /var/lib/bum


Now BUM will start.

---

### Post by _Ramirez_ on 2005-12-03
Ubuntu version: 5.10
BUM version: bum_2.1.2-1_all.deb
It happens every time including first run
Yes I have write permission (default installed Ubuntu)

And your advice worked. After creating /var/lib/bum it can be run. Thanks!

---

### Post by gold4tune on 2005-12-03
Wich package i must install...  i used the last version of bum and i used the dkpg command!!!

---

### Post by gold4tune on 2005-12-03
> 
Originally Posted by gold4tune
that's wat appen:

Can't locate Glib.pm in @INC (@INC contains: /usr/lib/bum /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/bum/bum_app.pm line 34.
BEGIN failed--compilation aborted at /usr/lib/bum/bum_app.pm line 34.
Compilation failed in require at /usr/bin/bum line 27.
BEGIN failed--compilation aborted at /usr/bin/bum line 27.

is something i must install... i'm on kde!!!


Thats my errors...  May be a should reinstall it with dkpg???

---

### Post by saltydog on 2005-12-03
[QUOTE=gold4tune]Thats my errors...  May be a should reinstall it with dkpg???[/QUOTE]


You error says that you don't have libgtk2-perl installed, but it is in the dependencies of bum package, so it should have not been installed if you don't have that library.
Try again using sudo dpkg -i ... and look for warning messages.

---

### Post by gold4tune on 2005-12-03
There is my errors when i try to install it:

Dépaquetage de la mise à jour de bum ...
dpkg : des problèmes de dépendances empêchent la configuration de bum :
 bum dépend de libgtk2-perl (>= 1.100-1) ; cependant :
  Paquet libgtk2-perl n'est pas installé.
 bum dépend de libglib-perl (>= 1.100-1) ; cependant :
  Paquet libglib-perl n'est pas installé.
 bum dépend de libgtk2-gladexml-perl ; cependant :
  Paquet libgtk2-gladexml-perl n'est pas installé.
dpkg : erreur de traitement de bum (--install) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 bum

---

### Post by gold4tune on 2005-12-03
Thx everyboy...  i have installed the 3 packages lacking manualy and everything work now.
thx for your help

---

### Post by gold4tune on 2005-12-03
But i have still have one question...  Is there a way to add a program taht i want to start at the bootup of my computer with BUM????

---

### Post by saltydog on 2005-12-04
[QUOTE=gold4tune]But i have still have one question...  Is there a way to add a program taht i want to start at the bootup of my computer with BUM????[/QUOTE]

No, this is not in the scope of Bum.
Generally, programs that need to start at init have their own installation in the deb package.

---

### Post by davidfossil on 2005-12-09
I get the following error message when trying to start BUM:
Cannot write file /var/lib/bum/packages ! at /usr/lib/bum/bumlib.pm line 482.

A window quickly flashes the screen, but does not stay.
Does anyone have a clue what might be wrong? :confused:

---

### Post by saltydog on 2005-12-10
[QUOTE=davidfossil]I get the following error message when trying to start BUM:
Cannot write file /var/lib/bum/packages ! at /usr/lib/bum/bumlib.pm line 482.

A window quickly flashes the screen, but does not stay.
Does anyone have a clue what might be wrong? :confused:[/QUOTE]


You are running an old version. Please download latest v. 2.1.3
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by BLTicklemonster on 2005-12-10
[QUOTE=fuscia]i sure do like bum.[/QUOTE]
PERV!!!


(sorry, that was just sitting there begging for me to comment on it. carry on)


So BUM looks like a great program. Who would benefit from it and why?

---

### Post by saltydog on 2005-12-10
[QUOTE=BLTicklemonster] Who would benefit from it and why?[/QUOTE]

You can find answers to your question here:
[http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)
or here:
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by kazuya on 2005-12-20
What typical services would you turn off in BUM?

How do you typically use BUM for Mepis / Ubuntu athlon xp desktop install?

Things are rather slow on my Ubuntu 5.10 Breezy? Any ideas?

I know I asked this to the originator of tool just now, but here it is again in case someone knows?

---

### Post by talz13 on 2005-12-20
[QUOTE=saltydog]No, this is not in the scope of Bum.
Generally, programs that need to start at init have their own installation in the deb package.[/QUOTE]

Then how would I add vncserver :1 to the default runlevel?

---

### Post by kazuya on 2005-12-20
What typical services would you turn off in BUM?

How do you typically use BUM for Mepis / Ubuntu athlon xp desktop install?

Things are rather slow on my Ubuntu 5.10 Breezy? Any ideas?

---

### Post by saltydog on 2005-12-22
**New Subversion site for BUM**

Access to the Boot-Up Manager source repository is available through both [web browser]("http://initd.org/svn/thesaltydog/bum/trunk/") and Subversion client interfaces.

With the Subversion client installed, obtaining a working copy of Boot-Up Manager codebase is as simple as:

```

svn checkout http://initd.org/svn/thesaltydog/bum/trunk/ bum
```

When checkout is over, you can compile and build the project as reported in the Installation section of the home [web site]("http://www.marzocca.net/linux/bum.html").

---

### Post by BLTicklemonster on 2005-12-22
I don't get it. I run bum, and it never loads, it just sits there looooooking like it will load, then says it is not responding. any attempt after closing tells me another bum is already running, or that /var/lock/bum remains locked. Considering that I know bum tried to run already once, I figure it's not locked, besides, it already exists when I try

```
sudo mkdir /var/lib/bum
```

following previous instructions.

what gives?

---

### Post by saltydog on 2005-12-23
Check if you are running the latest version (2.1.3).
Then open a terminal and type

sudo bum

and watch if any error message comes up.

---

### Post by BLTicklemonster on 2005-12-23
it ought to be that if I sudo apt-get install bum, it should see I don't have the most recent version, and upgrade, right? Because I did that and it says I'm running most recent.

---

### Post by saltydog on 2005-12-23
[QUOTE=BLTicklemonster]it ought to be that if I sudo apt-get install bum, it should see I don't have the most recent version, and upgrade, right? Because I did that and it says I'm running most recent.[/QUOTE]


No, it depends upon which Ubuntu version are you running. Breezy has a VERY old version of BUM in its repositories. The latest one is in dapper. If you are running breezy, you should download the latest deb package from the web site: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html) and then:

sudo dpkg -i bum_2.1.3-1_all.deb

---

### Post by saltydog on 2005-12-29
New **BootUp-Manager v. 2.1.4** has been released!

Download it on: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

From ChangeLog:
    *  Added new init descriptions
    *  Fixed bug on summary description

---

### Post by piedamaro on 2005-12-30
Very useful app :)
But why not add/remove an underscore to the links in rc*.d to disable/enable the service?
This way I preserve the priority and I can modify my links manually and BUM will be happy! Thanks.

(i.e. when ou deacrtivate a service the link is moved from, say, S19postfix to _S19postfix)

---

### Post by saltydog on 2005-12-30
[QUOTE=piedamaro]Very useful app :)
But why not add/remove an underscore to the links in rc*.d to disable/enable the service?
This way I preserve the priority and I can modify my links manually and BUM will be happy! Thanks.

(i.e. when ou deacrtivate a service the link is moved from, say, S19postfix to _S19postfix)[/QUOTE]


Because it is not standard to debian sysv-rc recomendations. BUM takes duly care of priorities in his file, so don't worry.
If you read the docs on [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html) you will find all bum "internals", and will see that is is strictly compliant to sysv-rc.

---

### Post by piedamaro on 2005-12-30
I've read them just before posting the question ;) I know BUM will do the right thing for priorities. It's just because with underscores I can see at first sight which services are disabled, play with them manually if I need to, and have BUM to recognize them seamlessly.
I agree however this is not the official way, but I found the Debian way to be more confusing.
I.e. if a disable some services, then for some reason I'm stucked at command line (remote login or whatever), I found somewhat difficult to see at first glance which service are manually disabled and which not.
Hope you see my point, however I think BUM does a good job already. Nice work!

Oh, siamo tutte e due a Roma;) Ciao e buon anno!

---

### Post by saltydog on 2005-12-30
[QUOTE=piedamaro]I've read them just before posting the question ;) I know BUM will do the right thing for priorities. It's just because with underscores I can see at first sight which services are disabled, play with them manually if I need to, and have BUM to recognize them seamlessly.
I agree however this is not the official way, but I found the Debian way to be more confusing.
I.e. if a disable some services, then for some reason I'm stucked at command line (remote login or whatever), I found somewhat difficult to see at first glance which service are manually disabled and which not.
Hope you see my point, however I think BUM does a good job already. Nice work!

Oh, siamo tutte e due a Roma;) Ciao e buon anno![/QUOTE]

I see your point and I understand.
But don't forget that BUM is a graphical tool and with BUM you have "at first sight" the vision of what is enabled and what not. You are asking to a GUI tool to take care also of a CLI side... mmh. 
I am working with sysv-rc-conf in order to share both the same configuration  and priorities files, I think that could be the right answer for you.

Grazie! E tanti auguri anche a te!!

---

### Post by piedamaro on 2005-12-30
Ok now I understand, if they share the same config it really makes sense. Thanks for clarifying things :)

---

### Post by Brando569 on 2006-01-03
BUM definately is ALOT better then Debian Services Control Panel, which i was using and thought was pretty cool. i love how all the descriptions are included for each service, that one major thing Debian SCP lacked. great work :D

edit: after using it for a few minutes there are a few flaws: would it be possible to alphabetize the services lists? whats the point of having a startup and shutdown tab if even the root user isnt allowed to edit it? i thought that was the whole idea of BUM? it looks nice but its not really that functional, looks like ill be heading back to Debian SCP :-/

---

### Post by saltydog on 2006-01-04
[QUOTE=Brando569]BUM definately is ALOT better then Debian Services Control Panel, which i was using and thought was pretty cool. i love how all the descriptions are included for each service, that one major thing Debian SCP lacked. great work :D

edit: after using it for a few minutes there are a few flaws: would it be possible to alphabetize the services lists? whats the point of having a startup and shutdown tab if even the root user isnt allowed to edit it? i thought that was the whole idea of BUM? it looks nice but its not really that functional, looks like ill be heading back to Debian SCP :-/[/QUOTE]

The only init scripts that BUM will not let you edit, are those in rcS.d, because, as the notice says, those are very system-critical and a safe GUI tool won't let you manage those scritps. In any case it is useful to have a disply of those services.

All the other runlevel init scritps can be started/stopped by BUM.

You can sort on every column you want (so also on service name) by clicking on the column headers!

---

### Post by Brando569 on 2006-01-04
clicking on the column headers didnt work for me in KDE :confused: 

i feel that there should be a way that you should be able to edit those services, say a "newbie" and "advanced" view? or you would have to run it strictly as the root user and not through sudo? that way people who dont know that much about linux yet wouldnt be able to screw anything up, then again screwing things up is what you learn from :D thats how i learned most of the things i know (in linux and windows) 

i was messing around with my dads gateway destination system when i was 10 (10 years ago) and on the phone with tech support fixing the things i screwed up by the time i was 11! just an idea to toss at you :D  

BUM would be a VERY useful tool if you made it possible to edit those services, considering not all of them are needed on every computer. there are even guides out there that tell you what the most commonly used services on a standard linux desktop are. think it through :) i would offer to help you but i know very little programming (i took c++ for 2 years in highschool then learned later on the stuff he was teaching us was about 5 years old!)

---

### Post by viscount on 2006-01-04
Bum kicks arse... 

I like both digital and non-digital bum :)

All kidding aside, the Boot-up-manager is really nice, good work! 

:KS <- for you!

---

### Post by saltydog on 2006-01-05
[QUOTE=Brando569]clicking on the column headers didnt work for me in KDE :confused: 
[/QUOTE]

Are you sure you are running v. 2.1.4? Pls check.

[QUOTE=Brando569]
BUM would be a VERY useful tool if you made it possible to edit those services, considering not all of them are needed on every computer. there are even guides out there that tell you what the most commonly used services on a standard linux desktop are. think it through :) i would offer to help you but i know very little programming (i took c++ for 2 years in highschool then learned later on the stuff he was teaching us was about 5 years old!)[/QUOTE]

During BUM development I was strongly asked from MOTU people to NOT let users edit rcS.d services in a graphic tool. And I agreed on that. An expert user could always use the CLI and sysv-rc-conf.

---

### Post by Brando569 on 2006-01-08
[QUOTE=saltydog]An expert user could always use the CLI and sysv-rc-conf.[/QUOTE]

very true but thats time consuming when you want to do something quickly, i guess ill just stick to the old Debian SCP, say if i wanted to test out something with enabling/disabling hotplug i dont want to have to load up sysv-rc-conf, find hotplug in the list and remove the X's from all of the boxes, then go to the specific directory and rename the file. i feel thats pretty time consuming compared to loading up DSCP finding hotplug in the list and clicking "remove as default". just my opinion.

---

### Post by saltydog on 2006-01-08
[QUOTE=Brando569]very true but thats time consuming when you want to do something quickly, i guess ill just stick to the old Debian SCP, say if i wanted to test out something with enabling/disabling hotplug i dont want to have to load up sysv-rc-conf, find hotplug in the list and remove the X's from all of the boxes, then go to the specific directory and rename the file. i feel thats pretty time consuming compared to loading up DSCP finding hotplug in the list and clicking "remove as default". just my opinion.[/QUOTE]


As I said, that's true ONLY for services in rcS.d, which are system critical. It is not very common to make experimentation and tests with those services. I believe it is a minor concern vs dangerous operations a common user could do.
(i.e. if a user unchecks "udev", his system may not start at boot anymore...)

---

### Post by ceng1984 on 2006-01-10
The link for downloading BUM listed in this thread does not appear to be working. Does anyone know of an alternate site for the deb file.

I can get the version from the Ubuntu repository, but would prefer the latest version.

---

### Post by saltydog on 2006-01-11
[QUOTE=ceng1984]The link for downloading BUM listed in this thread does not appear to be working. Does anyone know of an alternate site for the deb file.

I can get the version from the Ubuntu repository, but would prefer the latest version.[/QUOTE]


It was due to a temporary Debian server failure.
It is now working: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by gpeck157 on 2006-01-12
[QUOTE=saltydog]Thanks![/QUOTE]
Hey Salty,

When installed bum, all seemed to go fine, but when I ran it, it asked me for a password. I put in my root password. Then it asked for another password for the "keyring". I thought it wanted a different password, so I put one in, and it gave me a message that it was the wrong password and it closed. Now I can't get it to run. When it starts, it asks me for the root password, and when I put it in it tells me it's the wrong password, and it closes. I tried doing a complete uninstall, but that didn't change anything. Suggestions?

Thanks...

---

### Post by saltydog on 2006-01-12
[QUOTE=gpeck157]Hey Salty,

When installed bum, all seemed to go fine, but when I ran it, it asked me for a password. I put in my root password. Then it asked for another password for the "keyring". I thought it wanted a different password, so I put one in, and it gave me a message that it was the wrong password and it closed. Now I can't get it to run. When it starts, it asks me for the root password, and when I put it in it tells me it's the wrong password, and it closes. I tried doing a complete uninstall, but that didn't change anything. Suggestions?

Thanks...[/QUOTE]


If you are familiar with Ubuntu, you may know that the application is asking you for your "user" password as it runs with sudo... !

---

### Post by gpeck157 on 2006-01-12
[QUOTE=saltydog]If you are familiar with Ubuntu, you may know that the application is asking you for your "user" password as it runs with sudo... ![/QUOTE]
Yes, I am familiar with Ubuntu, and the sudo password is the one I put in.

Suggestions?

Thanks...

---

### Post by saltydog on 2006-01-13
[QUOTE=gpeck157]Yes, I am familiar with Ubuntu, and the sudo password is the one I put in.

Suggestions?

Thanks...[/QUOTE]

In your previous post, you mentioned you have put in your "root" password. That's wrong, you should put your "user" password.
This is not up to BUM, as it runs gksudo before starting, just as Synaptic does.

---

### Post by ceng1984 on 2006-01-13
saltydog,

Thanks for the update on the download site. I have downlaoded and will try. I used a previous version for Hoary and appreciated the effort you have given this.

Thanks again,
ceng1984

---

### Post by pongtawat on 2006-01-17
Hello,

I just install VMware Player and would like to disable its service at startup.
I tried BUM 1.3 and (just upgraded) BUM 2.1.4, but it doesn't see VMware service. Please help.

Thank you in advance.

---

### Post by blackant on 2006-01-20
Thanks, it is very simple to use. ;)

---

### Post by dodgeman79 on 2006-01-21
I'm getting this trying to install.  can someone point me in the right direction?

```
root@WORKGROUP:/tmp/bum-2.1.4# ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... no
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

got to work.

---

### Post by rttm on 2006-01-25
bum_2.1.4-1, Breasy
I've installed BUM with sudo dpkg -i bum_2.1.4-1_all.deb and get no errors, when i sudo bum in terminal i get this error 
Can't load '/usr/lib/perl5/auto/Gtk2/Gtk2.so' for module Gtk2: /usr/lib/perl5/auto/Gtk2/Gtk2.so: undefined symbol: XS_Gtk2__MessageDialog_formau_secondary_markup at /usr/lib/perl/5.8/DynaLoader.pm line 225.
 at /usr/lib/bum/bum_app.pm line 43
Compilation failed in require at /usr/lib/bum/bum_app.pm line 43.
BEGIN failed--compilation aborted at /usr/lib/bum/bum_app.pm line 43.
Compilation failed in require at /usr/bin/bum line 27.
BEGIN failed--compilation aborted at /usr/bin/bum line 27.

I'm lost, I've done the apt-get updates, remove the package and reinstalled but no luck. Anyone have a suggestion.

---

### Post by nianhbg on 2006-01-29
Hmmm trying to install this with sudo dpkg -i bum_2.1.4-1_all.deb and i get some error msg that saying "this is not a debian package" could it be becourse im running hoary 5.04?

---

### Post by saltydog on 2006-01-29
Maybe.
I an just say that IT IS a debian package.. Where did you download it from?

---

### Post by nianhbg on 2006-01-29
[QUOTE=saltydog]Maybe.
I an just say that IT IS a debian package.. Where did you download it from?[/QUOTE]

I downloaded it from [http://www.marzocca.net/linux/](http://www.marzocca.net/linux/)
i saw something about "dpkg-deb --control errorcode 2" when i tried to install it

---

### Post by saltydog on 2006-01-29
If you followed the link on my web site, you should have downloaded it from:
[http://ftp.debian.org/debian/pool/main/b/bum/](http://ftp.debian.org/debian/pool/main/b/bum/)

which is the debian pool server. Only tested debian packages can be found there, so maybe it is something related to Hoary. Sorryu, but I can't test it, as I don't have Hoary since a long time.

---

### Post by BLTicklemonster on 2006-01-29
I got bum working, but what do I do with it now? I see where there's stuff I don't need loading up, like stuff for a laptop, so I unchecked them. Basically that's it, right? It will boot without wasting resources on them now, right? So this is like going to my computer, manage, and managing services and applications in XP? Pretty cool. Glad that's there. So I guess I'm using it right then?

---

### Post by saltydog on 2006-01-29
[QUOTE=BLTicklemonster]I got bum working, but what do I do with it now? I see where there's stuff I don't need loading up, like stuff for a laptop, so I unchecked them. Basically that's it, right? It will boot without wasting resources on them now, right? So this is like going to my computer, manage, and managing services and applications in XP? Pretty cool. Glad that's there. So I guess I'm using it right then?[/QUOTE]


Please check documentation here:

[http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)

---

### Post by nianhbg on 2006-01-29
[QUOTE=saltydog]If you followed the link on my web site, you should have downloaded it from:
[http://ftp.debian.org/debian/pool/main/b/bum/](http://ftp.debian.org/debian/pool/main/b/bum/)

which is the debian pool server. Only tested debian packages can be found there, so maybe it is something related to Hoary. Sorryu, but I can't test it, as I don't have Hoary since a long time.[/QUOTE]

Thank's for the link. I got it working now :) I had to install libgtk2-gladexml-perl.

---

### Post by saltydog on 2006-01-31
[B]New [COLOR="Red"]v. 2.1.5[/COLOR] is online!
Please check [website.]("http://www.marzocca.net/linux/bum.html")
[/B]

---

### Post by Zxaos on 2006-02-21
Well that was fun. Tried to install libgtk2-gladexml-perl, and got a big nasty error message about how I was crazy and it didn't exist. Moral of the story - always make sure that your apt repositories are up to date - it appears that my connection was down last time they updated, and as such they were missing half the packages!

---

### Post by saltydog on 2006-02-22
[QUOTE=Zxaos]Well that was fun. Tried to install libgtk2-gladexml-perl, and got a big nasty error message about how I was crazy and it didn't exist. Moral of the story - always make sure that your apt repositories are up to date - it appears that my connection was down last time they updated, and as such they were missing half the packages![/QUOTE]

I am not sure I have understood what you are speaking about...
Maybe you are referring to a very old bug? Pls note that latest BUM version is 2.1.5 and you can download it from debian repositories..

libgtk2-gladexml-perl is a normal package in Ubuntu/debian repositories...

---

### Post by earobinson on 2006-02-28
Im a fan of da bum

---

### Post by jaja23bd on 2006-03-17
hi
  thanks mate.. 
  I just installed bum in dapper. Though i need to install some library by synaptic ... then everything is alright..
  when i run the package its says the following word
  Package libgtk2-gladexml-perl is not installed.

 i search the lib and got it in synaptic ... and then run again
   sudo dpkg -i bum_2.1.5-1_all.deb

  .........................

 Thanks again...

 jaja

---

### Post by saltydog on 2006-03-17
[QUOTE=jaja23bd]hi
  thanks mate.. 
  I just installed bum in dapper. Though i need to install some library by synaptic ... then everything is alright..
  when i run the package its says the following word
  Package libgtk2-gladexml-perl is not installed.

 i search the lib and got it in synaptic ... and then run again
   sudo dpkg -i bum_2.1.5-1_all.deb

  .........................

 Thanks again...

 jaja[/QUOTE]


Why are you installing BUM in dapper with dpkg??

Dapper has BUM in repositories, so it is enough to type:

sudo apt-get install bum

...and all the dependencies come in!

Thanks

Fabio

---

### Post by jaja23bd on 2006-03-17
[QUOTE=saltydog]Why are you installing BUM in dapper with dpkg??

Dapper has BUM in repositories, so it is enough to type:

sudo apt-get install bum

...and all the dependencies come in!

Thanks

Fabio[/QUOTE]

 Yup, my mistake... few hours back i run the apt-get.. its update the BUM..
 thank you..

---

### Post by frodon on 2006-03-24
Hi saltydog,

just a quick question :
- Is it possible to use BUM to make a script running on boot ?, for example i wrote an iptables firewall script and i'm wondering if i can use BUM to make this script running on each startup.

---

### Post by Ubuntuud on 2006-03-29
It looks like sysv-rc-conf (the options), is there any difference between BUM and sysv-rc-conf, except for the GUI part?

---

### Post by saltydog on 2006-03-29
[QUOTE=Ubuntuud]It looks like sysv-rc-conf (the options), is there any difference between BUM and sysv-rc-conf, except for the GUI part?[/QUOTE]


No. Both of them are recommended by sysv-rc.

---

### Post by RaptorRaider on 2006-04-02
Wouldn't it be a good idea to add a GUI front-end to /boot/grub/menu.lst in BUM?

I know BUM currently doesn't have much to do with that file, but booting in general does; I think making a GUI for such a file wouldn't be that hard but would improve usability significantly for new users.

---

### Post by klahjn on 2006-04-04
BUM looks pretty good, any information if it is ready for dapper?

---

### Post by saltydog on 2006-04-08
[QUOTE=klahjn]BUM looks pretty good, any information if it is ready for dapper?[/QUOTE]


BUM currently IS in dapper.
Just type:

sudo apt-get install bum

---

### Post by Rikostan on 2006-04-08
Very nice tool, thanks for the work you put into this. It is incredibly simple and straight forward to use.

---

### Post by ardchoille on 2006-04-12
I just installed bum and I have to say it is a very nice tool. Thank you for this awesome app :)

---

### Post by tsrjzq on 2006-04-25
year, for most green hands in debian-like systems, it is very useful

---

### Post by bonzodog on 2006-04-26
hrm...It's not allowing me to stop some 'vital' runlevel S services, like pcmcia, RAID, EVMS, LVM. I have been allowed to stop ppp, and hplip. Is there any way of getting around this with out getting svsv-rc-conf - what I'm looking for is almost a direct GUI front end to that, that allows me access to all services from start up.

---

### Post by saltydog on 2006-04-27
[QUOTE=bonzodog]hrm...It's not allowing me to stop some 'vital' runlevel S services, like pcmcia, RAID, EVMS, LVM. I have been allowed to stop ppp, and hplip. Is there any way of getting around this with out getting svsv-rc-conf - what I'm looking for is almost a direct GUI front end to that, that allows me access to all services from start up.[/QUOTE]


This matter has been discussed for long time, eith debian and ubuntu teams.
It is not safe for a GUI application to access those vital services in the rcS.d runlevel. En erroneous click over a critical service, could stop the system and keep if strongly unstable or un-restorable.

---

### Post by popie on 2006-05-21
I just installed BUM 2.x. When I run it it asks "Enter password for default keyring to unlock" (the application 'gksu' wants access to the default keyring but it is locked). My "user" password doesn't work here, but my root password makes the prompt go away... but then nothing, no BUM!

If I run it again I see the little watch cursor for a few moments... then nothing. 

I'm using Breezy, and installed BUM from the deb file on the BUM web site. I have root enabled and automatix installed, if that matters. Ideas?

---

### Post by saltydog on 2006-05-21
[QUOTE=popie]I just installed BUM 2.x. When I run it it asks "Enter password for default keyring to unlock" (the application 'gksu' wants access to the default keyring but it is locked). My "user" password doesn't work here, but my root password makes the prompt go away... but then nothing, no BUM!

If I run it again I see the little watch cursor for a few moments... then nothing. 

I'm using Breezy, and installed BUM from the deb file on the BUM web site. I have root enabled and automatix installed, if that matters. Ideas?[/QUOTE]

Latest version of BUM uses gksu and its gconf configuration. This is how Dapper works, so you should:

1. use Breezy version from the repository (apt-get)
-or-
2. upgrade to Dapper

---

### Post by popie on 2006-05-21
[QUOTE=saltydog]Latest version of BUM uses gksu and its gconf configuration. This is how Dapper works, so you should:

1. use Breezy version from the repository (apt-get)
-or-
2. upgrade to Dapper[/QUOTE]

Ok, thanks. That explains why the older version appeared in apt-get. 

I didn't see anything on your website indication that the latest version was for Dapper only. Anyway thanks for a great program!

---

### Post by Sianis on 2006-05-28
Okey, I fixed it! I wrote mail to saltydog

[I][COLOR="Silver"]Hi all!

I created hu.po. But when I tried it, one line in list ( general multi-lingual  speech synthesis system aka: festival) stayed in english. I coudn't find it in bum.pot, please fix it!

Big thanks, great application!

Bye[/COLOR][/I]

---

### Post by sha_man on 2006-06-03
i have tried to disable some service (run "sudo bum"), by removing the tick in the boxes, after that, when applying the settings, **all the ticks come back and nothing changes**??? very strange :confused: 

here the error code: 
```
W: Kann Paket stop-bootlogd nicht finden
E: Keine Pakete gefunden
substr outside of string at /usr/lib/bum/bumlib.pm line 287.
Use of uninitialized value in split at /usr/lib/bum/bumlib.pm line 289.
Use of uninitialized value in substitution (s///) at /usr/lib/bum/bumlib.pm line 292.
Use of uninitialized value in string eq at /usr/lib/bum/bumlib.pm line 295.
W: Kann Paket stop-bootlogd nicht finden
E: Keine Pakete gefunden
substr outside of string at /usr/lib/bum/bumlib.pm line 287.
Use of uninitialized value in split at /usr/lib/bum/bumlib.pm line 289.
Use of uninitialized value in substitution (s///) at /usr/lib/bum/bumlib.pm line 292.
Use of uninitialized value in string eq at /usr/lib/bum/bumlib.pm line 295.
W: Kann Paket stop-bootlogd nicht finden
E: Keine Pakete gefunden
substr outside of string at /usr/lib/bum/bumlib.pm line 287.
Use of uninitialized value in split at /usr/lib/bum/bumlib.pm line 289.
Use of uninitialized value in substitution (s///) at /usr/lib/bum/bumlib.pm line 292.
Use of uninitialized value in string eq at /usr/lib/bum/bumlib.pm line 295.

```

Any ideas?

---

### Post by saltydog on 2006-06-03
[QUOTE=sha_man]
here the error code: 
[/QUOTE]

Cannot confirm those errors! 
Try clearing bum cache and regenerating it. This is simply done by deleting /var/lib/bum/packages and running bum again.

---

### Post by sha_man on 2006-06-03
anyway, now it does work, but still when changing the tick-boxes, and applying settings, it only SEEMS that nothing changed... After a reboot it does, so :D :D :D

---

### Post by saltydog on 2006-06-04
[QUOTE=sha_man]anyway, now it does work, but still when changing the tick-boxes, and applying settings, it only SEEMS that nothing changed... After a reboot it does, so :D :D :D[/QUOTE]


When you change a tick box status and click on Apply, BUM asks you weather to apply the modification immediately (stop the service) or at next boot.

---

### Post by ShirishAg75 on 2006-07-08
> **bonzodog said:**
> hrm...It's not allowing me to stop some 'vital' runlevel S services, like pcmcia, RAID, EVMS, LVM. I have been allowed to stop ppp, and hplip. Is there any way of getting around this with out getting svsv-rc-conf - what I'm looking for is almost a direct GUI front end to that, that allows me access to all services from start up.

> **saltydog said:**
> This matter has been discussed for long time, eith debian and ubuntu teams.
It is not safe for a GUI application to access those vital services in the rcS.d runlevel. En erroneous click over a critical service, could stop the system and keep if strongly unstable or un-restorable.

That's sad, for I have a desktop system & hence don't need all the above services. No pcmcia, RAID, EVMS, LVM needed for me. Any good tute links or something like that ?

 Also was looking at the BUM [doc]("http://www.marzocca.net/linux/bumdocs.htm") site & found the site doesn't appeal to noobs.  One of the better things tht could be done is to have quite a few more screenshots. Secondly, it would be better to have a small intro. on what daemons are rather than just going into daemons. Maybe couple of lines with a bigger noob-friendly explanation at some place else/site. Another thing that could make it more friendly is perhaps do an animation. An SVG or a small flash or mpg file. This would certainly make people do stuff faster & less Q&A on trivial matters. What do u think?

---

### Post by Fraoch on 2006-08-08
OK, newbie trying to install BUM.  I type:

```
sudo apt-get install bum
```

I get:

```
Reading package lists... Done
Building dependency tree... Done
bum is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bum: Depends: libgtk2-gladexml-perl but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So then I type:

```
sudo apt-get install libgtk2-gladexml-perl
```

...and I get

```
Reading package lists... Done
Building dependency tree... Done
Package libgtk2-gladexml-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtk2-gladexml-perl has no installation candidate
```

Huh?

libgtk2-gladexml-perl isn't in the Synaptic Package Manager so I can't install it that way either.

A little help?

Thanks.

P.S.  Maybe this is the Ubuntu god's way of telling me it would be a bad idea to fool around with Ubuntu's start-up sequence, but I'd like to install it anyway just to determine where I'm going wrong.

---

### Post by yeagersthlm on 2006-09-14
I would really like to see the title of the application localized.

"BootUp Manager" in Swedish would be "Uppstartshanterare" which could help our local users to better understand what the application does

Regards,
Daniel

---

### Post by saltydog on 2006-09-30
**New v.2.1.8** is available for downloading [here!]("http://www.marzocca.net/linux/bum.html")

---

### Post by AussieLakerFan on 2006-10-12
I have it installed and it seems to work fine, however I have no idea what each service *really* does so I am not going to play with it...

I am trying to find some sort of resource that explains what each service does and what the benefits/consequences, etc are of turning them on/off...  and so far, I can't find anything...

---

### Post by Ago12 on 2006-10-23
Is BUM helpfull on Edgy?

I mean, is it compliant with Upstart? (I think upstart uses old init scripts, bu I would like to be sure :p )

---

### Post by speeddemon8803 on 2006-10-24
i think you people must have messed up deleting my first post as it was not rude or degrading to the other users, i just was trying to state that if you had a problem with it, either dont use it or just  say it like B.U.M...thats all i said...well..whatever delete this one, im really tired of it moderators..can we moderate your posts? (joking)

---

### Post by dagnabit dang doohickey on 2006-10-25
From the BUM docs:
> The list of "active" services is parsed thru a gate and only valid services are displayed as active. To be a valid active service, the symlinks should meet these requirements:

- Either S or K symlink in each of rc[1-5].d
- K symlink in each of rc[06].d

Is there any special reason for this? In other words, why won't BUM manage services that don't have a symlink in every rc[0-6].d?

I have manually removed some Kills in rc0.d and rc6.d and now, sadly, BUM's usefulness seems to have come to an end as most of my scripts cannot be managed by BUM.

---

### Post by archis on 2006-10-29
> **Ago12 said:**
> Is BUM helpfull on Edgy?

I mean, is it compliant with Upstart? (I think upstart uses old init scripts, bu I would like to be sure :p )

Yes Fabio, can you give us a quick overview of the relationship of  Boot-Up Manager to upstart? I guess most people have seen the [upstart wiki page]("https://wiki.ubuntu.com/ReplacementInit") and the [posts on Scott Remnant's personal blog]("http://www.netsplit.com/blog/articles/category/upstart") - all in all a great introduction to upstart - and (almost) readable for non-techies, I'd say - but yeah it would be great if you could let us know about how BUM and upstart will work together.

---

### Post by saltydog on 2006-10-29
> **dagnabit dang doohickey said:**
> From the BUM docs:


Is there any special reason for this? In other words, why won't BUM manage services that don't have a symlink in every rc[0-6].d?



Yes. The "special" reason is the standard boot mechanism using symlinks in /etc/rc?.d in any debian system. Please read bum docs at [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)

---

### Post by saltydog on 2006-10-29
> **archis said:**
> Yes Fabio, can you give us a quick overview of the relationship of  Boot-Up Manager to upstart? I guess most people have seen the [upstart wiki page]("https://wiki.ubuntu.com/ReplacementInit") and the [posts on Scott Remnant's personal blog]("http://www.netsplit.com/blog/articles/category/upstart") - all in all a great introduction to upstart - and (almost) readable for non-techies, I'd say - but yeah it would be great if you could let us know about how BUM and upstart will work together.

I'm sorry but I haven't got time to study upstart yet, so I can't answer for the moment. What could I say is that if upstart is sysv-compliant, BUM will work with it. I will let you know soon.

---

### Post by Ago12 on 2006-11-05
> **saltydog said:**
> I'm sorry but I haven't got time to study upstart yet, so I can't answer for the moment. What could I say is that if upstart is sysv-compliant, BUM will work with it. I will let you know soon.

Actually, I've tested it, and it does work :)

---

### Post by infamous-online on 2006-11-12
i hope bum will fix that auto refresh issue, once you start or stop a service, it's a bit annoying after a while.

also i hope ubuntu plans to incorporate bum into it's default installment of ubuntu, that would be nice.

---

### Post by saltydog on 2006-11-12
> **infamous-online said:**
> i hope bum will fix that auto refresh issue, once you start or stop a service, it's a bit annoying after a while.

also i hope ubuntu plans to incorporate bum into it's default installment of ubuntu, that would be nice.

That bug has been fixed one month ago in v.2.1.8! Buf unfortunately it has not been synched in Ubuntu Edgy. You can download the deb package [ here]("http://ftp.debian.org/debian/pool/main/b/bum/bum_2.1.8-1_all.deb") and install it by:

sudo dpkg -i bum_2.1.8-1_all.deb

Bye!

Fabio

---

### Post by Corvo78 on 2007-02-28
Just a quick question:
Is it possible to change the boot-up priority of a service?
*(Meaning: Can I make 'service x' boot first instead of last?)*

---

### Post by saltydog on 2007-02-28
> **Corvo78 said:**
> Just a quick question:
Is it possible to change the boot-up priority of a service?
*(Meaning: Can I make 'service x' boot first instead of last?)*

Yes, of course.
Click on advanced options, then switch to the "Services" tab and right-clik on a service... You can change the priority (at your own risk!)

---

### Post by Corvo78 on 2007-02-28
Ooh, quick reply.
The "Boot-Up Manager" surely has promising features. I'll surely try it now.

Btw: I want to boot-up the dbus sooner so that I can enable auto-login again. Otherwise I'll keep having this "failed to initialize HAL!" message :(
*(not having an auto-login gives the boot-up enough extra seconds to have HAL running before Gnome)*

---

### Post by fermo111 on 2007-04-28
I have the same complaint made by a previous post. Many services are not listed due to missing links in same RL (mainly 0 and 6). Your "gate":
```
#rule S link in 2-3-4-5 AND S/K link in 1, AND K link in 0-6
```
seems too strict. If I have to "correct" the symlinks before using this tool then much of its usefulness is gone.

---

### Post by saltydog on 2007-04-29
> **fermo111 said:**
> I have the same complaint made by a previous post. Many services are not listed due to missing links in same RL (mainly 0 and 6). Your "gate":
```
#rule S link in 2-3-4-5 AND S/K link in 1, AND K link in 0-6
```
seems too strict. If I have to "correct" the symlinks before using this tool then much of its usefulness is gone.

That IS the rule for sysV-rc. IF your need to correct the links it means that the software related to those links is not sysv-init compliant.

---

### Post by fermo111 on 2007-04-29
> IF your need to correct the links it means that the software related to those links is not sysv-init compliant.


I think it would be a nice addition if BUM could show these non-compliant cases and "fix" them, possibly under user control. 
Another addition could be enabling the update of rcS. Now, it warns that this is a dangerous operation and does not allow any change. Warning the user is right, but then, if the user really want to make the change, why not let him do it?

---

### Post by saltydog on 2007-04-30
> **fermo111 said:**
> I think it would be a nice addition if BUM could show these non-compliant cases and "fix" them, possibly under user control. 
Another addition could be enabling the update of rcS. Now, it warns that this is a dangerous operation and does not allow any change. Warning the user is right, but then, if the user really want to make the change, why not let him do it?


During first development stages of BUM I included the possibility to change also the rcS runlevel scripts, but either Debian and Ubuntu developers didn't want to include in their software a potential dangerous graphical tool. If the user really needs to change rcS runlevel scripts he should know what he is doing and could use client-terminal tools.

---

### Post by cuonglb on 2007-06-09
Nice !

---

### Post by oponek on 2007-08-21
Hello,
   I enjoy you application and would like to translate it into polish. What should I do?

---

### Post by saltydog on 2007-08-30
> **oponek said:**
> Hello,
   I enjoy you application and would like to translate it into polish. What should I do?

Just use launchpad here:
[https://launchpad.net/bum/trunk/+pots/bum/pl/+translate](https://launchpad.net/bum/trunk/+pots/bum/pl/+translate)

---

### Post by notwen on 2007-09-05
Would BUM be able to help me figure out which service is failing to start?  I have a brief moment between the Ubuntu loading screen and the GDM login screen where I see services starting and right before GDM starts 1 service fails.  I am trying to figure out which service it may be.  This service which fails also seems to be slowing down my system startup times.

---

### Post by saltydog on 2007-09-05
> **notwen said:**
> Would BUM be able to help me figure out which service is failing to start?  I have a brief moment between the Ubuntu loading screen and the GDM login screen where I see services starting and right before GDM starts 1 service fails.  I am trying to figure out which service it may be.  This service which fails also seems to be slowing down my system startup times.

This is out of the scope of BUM. To see which service is failing at startup, you should go thru system log messages. Try typing:
```
dmesg
```
in a terminal session.

---

### Post by notwen on 2007-09-05
I've done this, but nothing is coming up that I can recognize.  Is there anything in particular I should look for in the output of 'dmesg' that would identify the service which is failing?

---

### Post by por100pre1 on 2007-11-02
I just want to say thanks for the BootUp-Manager! It is a really great tool! This BUM will definitely stay at home! :) Currently using BUM 2.1.10 in Gutsy.

---

### Post by saltydog on 2007-11-02
Thank you!

---

### Post by patblu on 2007-11-22
Hi everybody!

I only installed bum yesterday and changed something (don't know what it was, it was an accident anyways) and now my system boots up all well up to the point when the graphical Login is to come up. That doesn't happen and the system just goes in text-mode. Now, my question:

Is there some kind of log file, bum cratest where I can find out what I done and actually change it back? Does bum create backups of the files it changes?

Thanks a lot!!!
Patrick

---

### Post by saltydog on 2007-11-22
Each action done by BUM is traced in the system log.
Most probably you have switched off gdm (the Gnome display manager). When you are in the terminal mode, just type

sudo /etc/init.d/gdm start

---

### Post by Anubis on 2008-02-18
How does one remove scripts?

---

### Post by saltydog on 2008-02-18
> **Anubis said:**
> How does one remove scripts?

This is not BUM's job. Boot-Up Manager can *disable* scripts from starting, or *stopping/starting* scripts. In order to definitely remove scripts, you should correctly uninstalla the package the scripts belong to.

---

### Post by ekravche on 2008-04-26
cool, I've installed this app. it's pretty useful :)

---

### Post by Malta paul on 2008-05-11
Hi, A big thank up for all the personnel effort you have put in to give us a great little program.

Paul :guitar:

---

### Post by saltydog on 2008-05-11
> **Malta paul said:**
> Hi, A big thank up for all the personnel effort you have put in to give us a great little program.

Paul :guitar:

Thank you Paul. I'm glad to know it is useful for you.

---

### Post by Gourgi on 2008-05-30
you're doing a great job
amazing application
i like the services's descriptions, are very handy and helpfull
keep on :popcorn:

---

### Post by fikelfikel on 2008-10-19
Funny name, huh? BUM. And it's a sticky thread, which makes it a Sticky BUM! :lolflag:

---

### Post by saltydog on 2008-11-12
> **jams001 said:**
> New version 2.0.0 is out ! this wonderful topic great idea thanks for that kind of idea you have shared to us!!:guitar:


[Starting Business Blog](http://www.starting-business.org.uk/index.php?q=starting-business-blog):lolflag:

Most recent version is 2.2.1 (intrepid, universe)

---

### Post by emshains on 2009-02-14
Bum is really great! It is a pretty easy way for speeding up your boot-up time, even if you are a begginer, 'cause you don't have to know much about computers to switch off laptop stuff or bluetooth if you don't need those features.

---

### Post by Regenweald on 2009-05-25
BUM is very likely my favourite Ubuntu software, and i only got to use it once. It is a extremely simple and works flawlessly for me. Many thanks  Saltydog. Look forward to newer versions, but i don't know how this could get better.

---

### Post by lisati on 2009-05-25
> **Manny C said:**
> Who needs a BUM when one has INITNG.  I do - I have the sort of BUM you sit on.

---

### Post by OldManRiver on 2009-05-29
All,

What recovery tools are built into BUM?

Having a strange problem with my 8.04 DT, where characters start auto propagating themselves at the command line in TTY or terminal and trying to resolve.

Was wondering if BUM could assist as default recovery/rebuilt from the ESC on boot, does not resolve.

OMR

---

### Post by steve_c on 2009-06-08
Just found this. I liked it a lot, thank you.

It would be nice if on the website you had a comparison between this, Ubuntu's default services-admin, and maybe even sysv-rc-conf (though the GUI vs command line is the obvious difference, I have no idea if there are any other significant differences).

I'm a little curious why Ubuntu doesn't use this to replace the services-admin program. It seems like this is in all ways superior and it would free up their developers to improve other things. If the BUM developer ever decides to quit or close-source it, the Ubuntu team could just take the last GPLed version of BUM and go from there and they'd still be ahead of where they are by default now.

---

### Post by enskillz on 2009-09-29
Thanks for this app.

---

### Post by saltydog on 2009-09-29
> **enskillz said:**
> Thanks for this app.

You're welcome!

---

### Post by joes7 on 2009-12-10
Nice one! I will be sure to download it.

---

### Post by Puzzled Guy on 2009-12-15
Great. They name the boot up manager BUM! As in: Kiss my BUM

---

