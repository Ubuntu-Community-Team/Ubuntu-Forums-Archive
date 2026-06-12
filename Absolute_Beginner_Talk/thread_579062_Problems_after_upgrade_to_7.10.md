---
title: "Problems after upgrade to 7.10"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Fraterdqni on 2007-10-17
Hi all, 

Need some help. I just finished a upgrade from Feisty to Gutsy and ran into several problems as the upgrade went along. After the complete download it told me it could not complete the upgrade. I restarted the system and then went to the update manger and it adv that only a partial upgrade could be done. 

I completed the partial upgrade and things seemed to go fine. then i tried to install a program and get this:

sudo apt-get sudo apt-get install idjc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  imlib11 automake1.9 libswfdec0.3 libjack0.100.0-0 m4 autoconf intltool libtool python-qt3 blt python-tk python-sip4
  autotools-dev docker sox imlib-base libqscintilla6 libquicktime0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  jackd
Suggested packages:
  jack-tools meterbridge libjackasyn0
Recommended packages:
  python-eyed3 qjackctl
The following NEW packages will be installed:
  idjc jackd
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B/558kB of archives.
After unpacking 1647kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

Tried to reinstall both tzdata and util-linux using the synaptics manager but still no luck. Other weird thing is since i told the update manager to do a partial upgrade, when i invoke update-manager -d i get that everything is up to date. 

What do i do from here? I am totally confused lol :confused:

---

### Post by Sef on 2007-10-17
Applications > Accessories > Terminal

then type or copy and paste this command:

sudo dpkg --configure -a

---

### Post by Fraterdqni on 2007-10-17
Thanks for your quick replay Sef. Tried what you suggested and this is what i got:

dave@ootp:~$ sudo dpkg --configure -a
[sudo] password for dave:
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not configured yet.
dpkg: error processing sun-java5-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 locales
 language-pack-en-base
 sun-java5-jre
 util-linux
 ubuntu-minimal
 language-pack-en
 language-pack-gnome-en-base
 sun-java5-bin
 util-linux-locales
 sun-java5-plugin
 language-pack-gnome-en

Still no change :confused:

---

### Post by Beggar on 2007-10-18
Alright, so first of all run

```
sudo apt-get autoremove
```

Now you can try the following to make sure all dependancies are set up.

```

 sudo apt-get check

```

This will upgrade your java to 6, I had something similar happen on upgrade and this fixed it for me. Plus its newer and so it must be better.

```

 sudo apt-get remove sun-java5-jre sun-java-5bin sun-java5-plugin
sudo apt-get install sun-java6-bin sun-java6-jre  sun-java6-plugin

```

 Finally, run the configure command again.

```

 sudo dpkg --configure -a

```

This might not fix the tzdata bug, but it seems to be an unrelated issue, see [here]("https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/116193") for that.

---

