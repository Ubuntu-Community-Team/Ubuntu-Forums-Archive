---
title: "Problem installing Fash Player"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by sidimaiga on 2007-06-24
Hi, 

Please need help. I try everything on the internet in regard of instaling flash plug-in for Firefox. No Success... 

Always getting the same error: 
xxxxx@xxxxxx:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

Any suggestion.

Thanks,

---

### Post by Keisad on 2007-06-24
Well, if your searching for the plugin for firefox than you could possibly visit a site that uses flash (such as a game site) and look for the link for install plugin?

If not, download the flash player through the synaptic package manager. Installing a package through the command line is useful only if you know the exact name of the package. Use the search option in synaptic to find what your are looking for.

To access it, go to

system>administration>synaptic package manager

Post if any additional help needed

---

### Post by L8erG8er on 2007-06-24
Or go to Applications-->Add/Remove and when the dialog comes up, enter flash in the search box.  It should come right back with the Flash plugin.  That's how I got mine.

---

### Post by sidimaiga on 2007-06-24
Thanks for the imput... But i tried that. couldn't find the flash player trough the synaptic package manager. 

Am I missing something a repository? 

There is my source list :

## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system

## Beryl Eye Candy Source list
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main


Thanks

---

### Post by foxmulder881 on 2007-06-24
Just download the Flash plugin file from adobe.com.
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Then extract archives contents and double click on the file and select "Run in Terminal". Follow the prompts. Simple.

---

### Post by AndyCat on 2007-06-24
Have you guys tried Automatix2?? Thats how i got mine to work.
1. Go to [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
2. Scroll down to Easy Direct Installation
3. Choose your installation and click on it
4. A new window pops out where it says something like you have chosen to open "the file you just clicked"
5. Open it and follow the instructions there
6. Open Automatix under Applications, System Tool, Automatix
7. Once you get there look for Codecs and Plugins
8. Select Flash plus any other you want
9. Install it 
10. It should work

Hope it works and let me know if it does.........

---

### Post by sidimaiga on 2007-06-24
When trying to install it from the website, I'm getting this:

sidim@UNirvana:~/Temp/install_flash_player_9_linux$ sudo ./flashplayer-installer 

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.


Any suggestions?

---

### Post by sidimaiga on 2007-06-24
> **AndyCat said:**
> Have you guys tried Automatix2?? Thats how i got mine to work.
1. Go to [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
2. Scroll down to Easy Direct Installation
3. Choose your installation and click on it
4. A new window pops out where it says something like you have chosen to open "the file you just clicked"
5. Open it and follow the instructions there
6. Open Automatix under Applications, System Tool, Automatix
7. Once you get there look for Codecs and Plugins
8. Select Flash plus any other you want
9. Install it 
10. It should work

Hope it works and let me know if it does.........

Tryed it .... no success,

" Error : Wrong architecture 'I386' "  ???

---

### Post by overdrank on 2007-06-24
> **sidimaiga said:**
> Tryed it .... no success,

" Error : Wrong architecture 'I386' "  ???

Are you using the 64bit feisty?

---

### Post by sidimaiga on 2007-06-24
Yes look like it... 

installation CD was wrongly label...

what&#347; are my option now...

---

### Post by sidimaiga on 2007-06-24
Just tried the 64bit version of Automatix2 and flash plug in wasn't available....

Any suggestion. ...

Or do I need to reinstalled using the 32bit version?

Thanks,

---

### Post by AndyCat on 2007-06-24
Have you enabled the "universal" repositories?

Open your synaptic package manager and go to  settings, preferences.
It should ask you for your admin pass, type it and the first tab "Ubuntu Software" check all the boxes and make sure you are downloadig from the server for USA.

Some other question... are you using 64  bit installation??

---

### Post by AndyCat on 2007-06-24
ok thats wats going on.... Ive heard that 64bit doesnt have as much support "including the flash plugins and some other ones". 

Im running 32 bit installation and works perfect in my AMD 64 X2 4Gb Ram, I have all the codecs and plugins I need to fully replace my WIN Vista. If you want to install the 32bit  flavor check this HOW TO i found  and give it a try.

[http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04)

Enjoy it

---

### Post by Malibu Illusion on 2007-06-24
Download the [Flash tarball](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash).

```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

Extract it and move the necessary to the plugins directory:
```
tar -zxf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux/
mv *flashplayer* ~/.mozilla/plugins
```

Install nspluginwrapper:

```

sudo apt-get install nspluginwrapper

```

Install a wrapper version of the Flash plugin for your 64-bit browser:

```

nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so

```

Close and reopen Firefox.  Type this into the address bar:

```

about:plugins
```

You'll see Flash listed, and it should work.

Take care.

---

### Post by AndyCat on 2007-06-27
Hello there, just in case u haven't been able to install the flash plugin try to install Automatix using this commands in a console:

1.  echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list
2.  provide your password if you are asked to
3.  wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
4.  gpg --import automatix2.key
5.  gpg --export --armor E23C5FC3 | sudo apt-key add -
6.  sudo apt-get update
7.  sudo apt-get install automatix

once you do this you can go to Applications, System Tools, Automatix and the look for th flash plugin in there.

Hope it works this time......

---

