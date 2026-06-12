---
title: "Getting Wi Fi Radar."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-05-27
I've got some time and am back on the 'Get Ubuntu Online with Wireless Problem Project'.  

I was told previously that I needed to get Wi Fi Radar instead of Gnome Network Manager. 

Questions: 

Is Wi Fi Radar pre-installed with my Feisty 7.04 Ubuntu?  It comes up on the applications list but won't install "because I need the Internet", so do I need to download it from the Wi Fi Radar site?

If so how do I go about installing it?  Really basic, idiotproof instructions please.  The official ones are almost meaningless, I need to know what *exactly* to do.  Step-by-step, only one idiot level above, turn on computer, click on X, click, on Y, turn off computer, etc.   

Thanks.

---

### Post by endersshadow on 2007-05-27
You can do a couple of things:

1. Go to System>Administration>Synaptic Package Manager
2. Hit the search button and type in "wifi-radar" (sans quotes)
3. Hit the white box and click "Mark for installation" on the menu that appears
4. Click Apply, then Apply again.

Other way:

1. Go to Applications>Accesories>Terminal
2. Type in "sudo apt-get install wifi-radar" (sans quotes again)
3. Type in your password

The first is the graphical way to do it, the second is the command line way to do it.  Most instructions you get off of the forums and/or IRC channel will be via the command line because it's much easier.  Anyway, that'll do what you need it to do!

---

### Post by aberadam on 2007-05-27
Brilliant.  Thanks, I can understand that :) So it's in Ubuntu already.

---

### Post by endersshadow on 2007-05-27
Yup. When you need a program, you can either use the search function of Synaptic or you can type in "apt-cache search *program name or descriptor*" in the terminal and you'll get a list.  Ubuntu comes with all the software you really need in its repositories, so you don't have to worry about downloading from untrusted sources.

---

### Post by aberadam on 2007-05-27
I tried both those methods, exactly as you described, apparantly Wifi Radar is not in there.  

Gah.

---

### Post by crimesaucer on 2007-05-27
[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

....and it is here in ubuntu: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=wifi-radar](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=wifi-radar)

---

### Post by endersshadow on 2007-05-27
> **aberadam said:**
> I tried both those methods, exactly as you described, apparantly Wifi Radar is not in there.  

Gah.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Do that and then try again.

Cheers.

---

### Post by aberadam on 2007-05-27
Yep, here are the instructions: 

I recommend using the package that comes with your distribution. If one is not available, email your distribution provider and request that they include a wifi-radar package in future releases.


Installing from source:

   1. Download and untar the latest "Official Tarball" or do an anonymous checkout from SVN (See the "Download" box on the left).
   2. Move into the wifi-radar source directory.
   3. Type "sudo make install".
      (or "sudo make install sysconfdir=/etc/wifi-radar")


WiFi Radar runs in two modes

    * To do a quick scan and connect to any available profile:

      sudo wifi-radar -d

    * To show the UI and manage profiles:

      sudo wifi-radar

I highly recommend running /etc/init.d/wifi-radar at boot time. If you put your machine into sleep or hibernate mode, you may also want to run /etc/init.d/wifi-radar from your wakeup script. 



My questions. 

As I'm gonna have to download the "tarball" to USB stick and then transfer over to Ubuntu (I'm on XP with a dual boot computer), where do I put the "tarball" file in Ubuntu to make it run?  Which directory? 

What's a "wifi-radar source directory"?

"I highly recommend running /etc/init.d/wifi-radar at boot time. " - Right, so how do I put it in that mode?  


Basically how do I get, setup and run Wifi Radar in ultra-simple language?

---

### Post by aberadam on 2007-05-27
"You can add extra repositories using the Software Sources application, which can be found in the menu: System -> Administration -> Software Sources. Check the repositories you think you will need (main, universe, restricted, multiverse). You probably won't need the 'sources' repository."

Right, er, so I go to Sofware Sources and check Wifi Radar and it will work?

---

### Post by crimesaucer on 2007-05-27
A very easy way to add most all of the repositories you will need for ubuntu is on the wiki guide here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Then you can just "sudo apt-get install wifi-radar" or "sudo aptitude install wifi-radar"

---

### Post by aberadam on 2007-05-27
This is not easy! :)

    * You can add extra repositories using the Software Sources application, which can be found in the menu: System -> Administration -> Software Sources. Check the repositories you think you will need (main, universe, restricted, multiverse). You probably won't need the 'sources' repository. This is the recommended way to add extra repositories: 


    * Another way to add extra repositories is to use following steps (do this at your own risk): 

    * Create a backup of your current list of sources. 

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup

Command explained: sudo - runs the command with elevated privileges. cp - copy. -p - prompt to overwrite if a file already exists.

    * Open the list of sources in a text editor (gedit for example is a graphical text editor) 

    Ubuntu (GNOME) users: 

sudo gedit /etc/apt/sources.list

    Kubuntu (KDE) users: 

sudo kate /etc/apt/sources.list

    Other users (if the above don't work): 

sudo nano /etc/apt/sources.list

    * Use the following lines as a template to guide you in editing the repositories in sources.list: 

    You can try replacing the current contents of sources.list with the following lines 
    To use your local mirror you can add "cc." before archive.ubuntu.com, where cc = your country code 
    e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse 

## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
#deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17
#deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17


    * Save the edited file 

    * Download needed gpg keys; e.g., use the following command for the PLF repository's gpg key: 

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

Command explained: wget - retrieves a file from a network location. -q - quiet (no output). -O- - Output downloaded item to terminal.

This command then completes. the | (pipe symbol) is used to capture the output from the previous command (in our case the screen) and use it as an input for the command piped.

"sudo apt-key add -" could actually be read as "sudo apt-key add - mQGiBEVmMkE...=QrqU" which is (shortened) the output of the previous command. If you type the previous command without the section after the pipe you will see the full key.

    * If you wish to try out the E17 beta, you will also need to download it's gpg key: 

wget -q [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc) -O- | sudo apt-key add -

    * Refresh packages list: 

sudo aptitude update


    * You may also generate your own sources.list and find other repositories at: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) 

    * You may also replace (or integrate) your sources.list with the complete sources.list for Feisty Fawn by Treviño - USE AT YOUR OWN RISK. 

    * Modify the default Ubuntu sources.list only if you understand what you're doing. Mixing repositories can break your system. 




WHAT THE HELL???!! :) BAH I HATE COMPUTERS :)

---

### Post by aberadam on 2007-05-27
Those instructions are unclear, am I right in thinking the first two lines do the same as the rest of it?  So I can follow the first two lines and forget the rest?

I'm gonna try anyway. 

One problem leads to another leads to another.  It's an endless string of problems!  When do I get to use Ubuntu?:)

---

### Post by crimesaucer on 2007-05-27
It actually is easier then it looks.

Assuming you have ubuntu Feisty:

1st) do a back up, all you have to do is copy and paste this command into your Terminal, and it will put a back up copy into your directory:

```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```


2nd) copy and paste this command into your Terminal to have your sources list open so you can edit it as root:

```
sudo gedit /etc/apt/sources.list
```


3rd) copy and paste this over your old sources list. NOW IF YOU HAVE ADDED ANYTHING to your list before, then leave that part. Click SAVE, when you are done:

```
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
```


4th) copy paste this into your Terminal:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```


5th) copy and paste this command to update your new repos:

```
sudo aptitude update
```


Now all you had to do was copy and paste 5 times. It looks difficult at first, but after doing this a few times you will realize how much easier it is then anything else.

---

### Post by crimesaucer on 2007-05-27
> **aberadam said:**
> Those instructions are unclear, am I right in thinking the first two lines do the same as the rest of it?  So I can follow the first two lines and forget the rest?

I'm gonna try anyway. 

One problem leads to another leads to another.  It's an endless string of problems!  When do I get to use Ubuntu?:)


you can do it either way, but it is really easy to open your terminal, while on the wiki page, and just copy and paste 5 quick times. Plus you learn how to not use your GUI.

....And actually, those instructions are very clear and better then the other wiki page instructions (for edgy and dapper), because the explain it thoroughly and help teach you what each command does instead of just telling someone to copy and paste like I did.

They do look very confusing at first. Until you read it and do it, it's difficult to see how easy and well written the wiki page really is.

---

