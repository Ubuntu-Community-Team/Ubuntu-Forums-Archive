---
title: "Install issues in the face of dependencies"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-04-16
I posted a variation of thsi inquiry here..then at the Multimedia forum and then over at Audacity at SonicForge.

But I'm not pretty sure I have tripp3d myself up with a package issue. To the effect that somehow I deleted items within packages that have impacted on my ability to run this software. One search I did via Terminal suggested I had issues -- "dependencies" -- with some other software items too although they currently run OK.

Here's my issue:
 
I  uninstalled [AUDACITY]("http://audacity.sourceforge.net/")(audio editor) during a rush of problems on my desk top. Audacity had worked but after I installed LAME it froze up so I uninstalled it.

But when I tried to reinstall it I ran into problems that have kept me running in circles. While Audacity appears on my Add/Remove list when I try to install it I get : 

    > Cannot install 'audacity'This application conflicts with other installed software. To install 'audacity' the conflicting software must be removed before.Switch to the advanced mode to resolve this conflict.


Then when I try to approach this through Terminal I get:

    > The following packages have unmet dependencies:
      audacity: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
                Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
                Depends: libstdc++6 (>= 4.1.0) but 4.0.3-1ubuntu5 is to be installed

but when I search for and click REINSTALL for these items I cannot get them taken up.
   >  The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
    [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Re…:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Re…:) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
    [http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release:) Unable to find expected entry  deb/binary-i386/Packages in Meta-index file (malformed Release file?)
    [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Re…:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Re…:) Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)


So I'm stuck. Very stuck.

I did a few searches for my problem via Google by chasing varios key phrases and had a fiddle with **dpkg** which took me into areas I think I had no business being at.

But I guess I have undermined some of my packages and need to redo them. But I have no notion as to how I should proceed.I thought I'd upset Ubuntu's audio setup but perhaps I've done some other more generic damage.

 I'm on Ubuntu Dapper and my customisation so far, over the past 2-3 weeks has been to upgrade to the latest version of FireFox, download and install Amarok; install iPodder/Juice as my podcast catcher ..and all i want out of life is to use Audacity as an audio editor on Ubuntu. 
With that I can die a happy man.

So to recover form my losses I don't care what I have to do. IF I have to uninstall and reinstall some packages which one? and how do I do that? I really do need to get Audacity -- or another editor (eg:[ Studio 64? ]("http://64studio.com/")others?) on my desktop.

---

### Post by bwhite82 on 2007-04-16
Try running these two commands:

> sudo apt-get install -f

sudo apt-get install --fix-missing

---

### Post by ratbagradio on 2007-04-16
For 
> sudo apt-get install -f
I get:
> Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.

for >  sudo apt-get install --fix-missing   I get:
> Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.


---

### Post by ratbagradio on 2007-04-16
Then for 
>  sudo apt-get upgrade
I get:
> ...amarok amarok-xine bluez-pcmcia-support foomatic-db-gutenprint g++-4.0 gok
  gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast
  gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist
  gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth
  gtk2-engines-thinice ijsgutenprint jackd liba52-0.7.4 libcompfaceg1
  libdvdread3 libgnutls12 libgpod-dev libjack0.100.0-0 libnetcdf3
  libstdc++6-4.0-dev libtasn1-2 libtasn1-2-dev libwxgtk2.4-1 libwxgtk2.6-0
  libxine-extracodecs libxine-main1 pcmcia-cs python-eyed3 python-feedparser
  python-gadfly python-htmltmpl python-kjbuckets python-netcdf python-parted
  python-pgsql python-pyrss2gen python-soappy python-stats python-syck
  python-wxgtk2.6 python-wxversion python-xmms x-window-system-core
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.



---

### Post by kvonb on 2007-04-16
Run Synaptic package manager from the system->administration menu and in the bottom left panel click on "Custom Filters" then select "Broken" at the top left.

That should show that you have a partially installed version of audacity installed, and you should be able to select "Fix broken" from the Edit menu.

Or right click on it and select "remove completely" I believe :).

---

### Post by ratbagradio on 2007-04-16
I go:
Admiistration **>** Synaptic Package Manager **>** Custom **>** Broken ...and get: an empty column.

I checked, the other tags in the same column -- *package with Debcon*f, *Search Filter,* etc and get input but *Broken* is empty.

---

### Post by hyper_ch on 2007-04-16
The not upgraded ones are for a dist-upgrade it seems to me:

```

sudo aptitude update && sudo aptitude dist-upgrade

```

---

### Post by ratbagradio on 2007-04-16
I'm not sure whether you were indicating that I do enter 
> sudo aptitude update && sudo aptitude dist-upgrade
to see the result. But I did, and the result is extensive input

My score is 2196 and I am asked whether i want to accept this solution after it said 
> Resolving dependencies...
The following actions will resolve these dependencies:

and I get:
> Keep the following packages at their current version:
amarok [2:1.4.3-0ubuntu8~dapper1 (dapper-backports, now)]
amarok-xine [2:1.4.3-0ubuntu8~dapper1 (dapper-backports, now)]
bluez-pcmcia-support [2.24-0ubuntu6 (dapper, now)]
foomatic-db-gutenprint [5.0.0~rc2-0ubuntu6 (dapper, now)]
g++-4.0 [4.0.3-1ubuntu5 (dapper, now)]
gok [1.0.10-1ubuntu1 (dapper, now)]
gtk2-engines-clearlooks [1:2.7.4.is.2.6.10-0ubuntu1 (dapper-updates, now)]
gtk2-engines-crux [1:2.7.4.is.2.6.10-0ubuntu1 (dapper-updates, now)]
gtk2-engines-highcontrast [1:2.7.4.is.2.6.10-0ubuntu1 (dapper-updates, now)]
gtk2-engines-industrial [1:2.7.4.is.2.6.10-0ubuntu1 (dapper-updates, now)]
gtk2-engines-lighthouseblue [1:2.7.4.is.2.6.10-0ubuntu1 (dapper-updates, now)]
gtk2-engines-mist [1:2.7.4.is.2.6.10-0ubuntu1 (dapper-updates, now)]
gtk2-engines-pixbuf [2.8.20-0ubuntu1.1 (dapper-security, now)]
gtk2-engines-redmond95 [1:2.7.4.is.2.6.10-0ubuntu1 (dapper-updates, now)]
gtk2-engines-smooth [1:2.7.4.is.2.6.10-0ubuntu1 (dapper-updates, now)]
gtk2-engines-thinice [1:2.7.4.is.2.6.10-0ubuntu1 (dapper-updates, now)]
ijsgutenprint [5.0.0~rc2-0ubuntu6 (dapper, now)]
jackd [0.100.0-4 (dapper, now)]
liba52-0.7.4 [0.7.4-1 (dapper, now)]
libcompfaceg1 [1989.11.11-24ubuntu1 (dapper, now)]
libdvdread3 [0.9.4-5.1 (dapper, now)]
libgnutls12 [1.2.9-2ubuntu1.1 (dapper-security, now)]
libgpod-dev [0.3.2-0ubuntu1 (dapper, now)]
libgpod1 [Not Installed]
libjack0.100.0-0 [0.100.0-4 (dapper, now)]
libnetcdf3 [3.6.0+3.6.1-beta3-0ubuntu1 (dapper, now)]
libstdc++6-4.0-dev [4.0.3-1ubuntu5 (dapper, now)]
libtasn1-2 [0.2.17-1ubuntu1 (dapper, now)]
libtasn1-2-dev [0.2.17-1ubuntu1 (dapper, now)]
libwxbase2.6-0 [Not Installed]
libwxgtk2.4-1 [2.4.4.1.1ubuntu2 (dapper, now)]
libwxgtk2.6-0 [2.6.1.2ubuntu2 (dapper, now)]
libxine-extracodecs [1.1.1+ubuntu1-2 (dapper, now)]
libxine-main1 [1.1.1+ubuntu2-7.7 (dapper-security, now)]
pcmcia-cs [3.2.8-5.2ubuntu7 (dapper-updates, now)]
python-eyed3 [0.6.8-1ubuntu1 (dapper, now)]
python-feedparser [4.1-2ubuntu1 (dapper, now)]
python-gadfly [1.0.0-8ubuntu4 (dapper, now)]
python-htmltmpl [1.22-5ubuntu3 (dapper, now)]
python-kjbuckets [1:1.0.0-8ubuntu4 (dapper, now)]
python-netcdf [2.4.9-3ubuntu2 (dapper, now)]
python-numeric-ext [Not Installed]
python-parted [0.11.2ubuntu4 (dapper, now)]
python-pgsql [2.4.0-6ubuntu3 (dapper, now)]
python-pyrss2gen [1.0.0-1 (dapper, now)]
python-scientific [Not Installed]
python-soappy [0.11.3-1.4ubuntu3 (dapper, now)]
python-stats [0.6-5ubuntu1 (dapper, now)]
python-syck [0.55-3ubuntu3 (dapper, now)]
python-wxgtk2.6 [2.6.1.2ubuntu2 (dapper, now)]
python-wxversion [2.6.1.2ubuntu2 (dapper, now)]
python-xmms [2.06-3ubuntu1 (dapper, now)]
python2.4-eyed3 [0.6.8-1ubuntu1 (dapper, now)]
python2.4-gadfly [1.0.0-8ubuntu4 (dapper, now)]
python2.4-htmltmpl [1.22-5ubuntu3 (dapper, now)]
python2.4-kjbuckets [1:1.0.0-8ubuntu4 (dapper, now)]
python2.4-pgsql [2.4.0-6ubuntu3 (dapper, now)]
python2.4-pyrss2gen [1.0.0-1 (dapper, now)]
python2.4-soappy [0.11.3-1.4ubuntu3 (dapper, now)]
python2.4-syck [0.55-3ubuntu3 (dapper, now)]
python2.4-xmms [2.06-3ubuntu1 (dapper, now)]
x-window-system-core [7.0.0-0ubuntu45 (dapper, now)]

Score is -2196

Accept this solution? [Y/n/q/?]


I guess I go Y?

---

### Post by hyper_ch on 2007-04-16
If you are using dapper I would say it's ok at it seems that will solve the dependency issues... but then I'm far from being a pro here...
Maybe you want to go into irc and talk to a few gurus yourself directly... that's what I often do.

Server: irc.freenode.org
Channel:  #ubuntu and/or #kubuntu and/or #xubuntu

Just a small hint for IRC: Don't ask if anyone can help... don't ask if anyone is proficient at this or that... just say what your problem :)

---

### Post by ratbagradio on 2007-04-16
Well thanks. I'll see where these options will lead me in the great Linux adventure...

---

### Post by TURNER on 2007-04-16
Hi, forgive me as I havent read the full thread, however in the past whilst attempting to find dependencies I have always checked the following site:

[http://www.linuxsoft.cz/en/sw_detail.php?id_item=46]("http://www.linuxsoft.cz/en/sw_detail.php?id_item=46")

Thats the page for AUDACITY with a list of dependencies.

Good luck!

---

### Post by juniorsonny on 2007-04-20
Hello need help.  Trying to fix dependencies problem but I get asked for my admin pass word in Synatic manager and when I type in my password it says it is the wrong password. How can i fix this. Don't know how to change the password.

---

