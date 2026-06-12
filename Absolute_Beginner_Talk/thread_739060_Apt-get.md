---
title: "Apt-get"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by marufaberlin on 2008-03-29
Hi,

since a while, every time I run apt-get, I get an error. But better see for yourself:

```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 174 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.7); however:
  Package hplip is not configured yet.
 hpijs depends on hplip (>= 2.7.12-0ubuntu2~gutsy1); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 hpijs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

printing doesn't work too, but that's obvious, as cupsys seems to not be installed correctly. 

Help, what should I do???

Thanks in advance,

marufaberlin

---

### Post by marufaberlin on 2008-03-29
Hi,

since a while, every time I run apt-get, I get an error. But better see for yourself:

```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 174 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.7); however:
  Package hplip is not configured yet.
 hpijs depends on hplip (>= 2.7.12-0ubuntu2~gutsy1); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 hpijs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```printing doesn't work too, but that's obvious, as cupsys seems to not be installed correctly. 

Help, what should I do???

Thanks in advance,

marufaberlin

---

### Post by finer recliner on 2008-03-29
[quote=man apt-get]
       -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is
           sometimes necessary when running APT for the first time; APT itself
           does not allow broken package dependencies to exist on a system. It
           is possible that a system&#8217;s dependency structure can be so corrupt
           as to require manual intervention (which usually means using
           dselect(8) or dpkg --remove to eliminate some of the offending
           packages). Use of this option together with -m may produce an error
           in some situations. Configuration Item: APT::Get::Fix-Broken.
[/quote]


i think you have very broken dependencies

---

### Post by Nythain on 2008-03-29
aye, possible double check to make sure all the repos are available adn uncommented in your /etc/apt/sources.list file woudl be the first place to start... after enabling them all, then
sudo apt-get update
sudo apt-get upgrade
and see if it helps

---

### Post by Joeb454 on 2008-03-29
Also try running ```
sudo dpkg --configure -a
``` :) See if that helps

---

### Post by Nythain on 2008-03-29
yay for that command... i always forget it, one of these days im gonna write it down or get it tattoo'd on my arm... has saved ma butt many a times

---

### Post by bartcramer on 2008-03-29
Did you try to reinstall the 3 packages at the bottom of the error message? 

HTH, 

Bart.

---

### Post by T2manner on 2008-03-29
aren't you supposed to put the app.name in there?
like
 > sudo apt-get install [name-here] 

---

### Post by marufaberlin on 2008-04-03
Hey, thanks for all your replies, 'preciate that. But sadly, none of them have really helped, sorry.

> **finer recliner said:**
> i think you have very broken dependencies
Arghh... i see you haven't looked at my post. Have a look at the first line and see if that helps :-D.

Joeb454, maybe you can see that apt fails because dpkg --configure fails. by the way --- don't i remember helping you sometime - well, justice will be done :-D

As for reinstalling, that doesn't help either.

What should I do now, I need cupsys, even if I don't need the hp* progs, but deinstalling them doesn't help (deinstallation fails because they aren't properly installed).

As for dependencies, what should I (re)install :-?

Thanks in advance.

---

### Post by marufaberlin on 2008-04-08
No you don't need to put a name there. If you don't supply a name, just unfixed dependencies will be fixed. getting an upgrade doesn't work, as there are unfixed dependiencies.

---

### Post by Anicka on 2008-04-08
Have you solved it yet? If not, my tip is to run ```
sudo dpkg --configure --force-configure-any cupsys hplip hpijs
```Sometimes it seems that if there are multiple packages with dependensies inbetween them are unconfigured, just putting the -a flag doesn't help. You need to specify which packages to configure and also (sometimes) put in the "force confiugure any package that would help in configuring the first package" flag.

---

### Post by ibuclaw on 2008-04-08
Or there's the short and cheerful
```
 sudo dpkg-reconfigure --force cupsys hplip hpijs 
```

Also, what repositories are you attached to?

As looks like the reason why they won't install (or configure) is because the version numbers don't match up to what they're dependent on.

Try doing an upgrade with** just** the **ubuntu repositories**. (hash out everything that doesn't have the word ubuntu in its addess in /etc/apt/sources.list)
Then type in:
```

sudo apt-get update
sudo aptitude reinstall -f
sudo aptitude safe-upgrade
sudo aptitude dist-upgrade

```
I prefer aptitude, the app has a better algorithm for choosing packages and fixing dependancies.

If none of the above work
```
 sudo aptitude dist-upgrade -f 
```
That should upgrade/downgrade packages at will to make things work.

You can also try
```
 sudo apt-get autoremove 
```
Though take a note of all packages that are being asked to be removed first.
IF you see a package that you use, or know that is required. **DON'T** go through with it.

Regards
Iain

---

### Post by ibuclaw on 2008-04-08
Or another useful tip would be to [download the broken packages manually]("http://packages.ubuntu.com/gutsy/"), and type in this command in the directory where the packages lay:

```
 sudo dpkg --force-overwrite -i **cupsys-1.2.3-4ubuntu5**.deb 
```

replacing that with the names of the downloaded packages.

NOTE: You must install the packages in a certain order to allow them not to flag up any umet dependancies.
If one package brings up errors, install the missing dependancy first, then go back to it.

Regards
Iain

---

### Post by Martje_001 on 2008-04-08
Have you tried Synaptic? In many cases Synaptic can solve the problem :)

---

### Post by marufaberlin on 2008-04-10
Thanks I'll try those commands. Synaptic doesn't fix the problem. I use just the Gutsy CD as my repository, I don't really like online repos, but maybe that's just me :-D

---

### Post by philinux on 2008-04-10
> **marufaberlin said:**
> Thanks I'll try those commands. Synaptic doesn't fix the problem. I use just the Gutsy CD as my repository, I don't really like online repos, but maybe that's just me :-D

You'll never get any security updates then.

---

### Post by marufaberlin on 2008-04-15
Gess what... My computer's not online... Do I need them? P.S. I can still download the .deb files.

---

