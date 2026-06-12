---
title: "Need to undo a dpkg"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-06-17
Hi, I've run into a problem. Thru the terminal, I ran 'sudo apt-get install flashplugin-nonfree'. When it got to a point where it said 'Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...', it just quit working. I tried to redo the command and it told me 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.' I input ' sudo dpkg --configure -a', but again it just quits working when it gets to 'Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...' I even rebooted and I can't get past ' dpkg was interrupted, you must manually run 'dpkg --configure -a'.

I figure I can work on getting the flash stuff to work later. How can I 'undo' both of these commands (apt-get and dpkg)?

---

### Post by %hMa@?b&lt;C on 2006-06-17
sudo apt-get remove nameofpackage
or maybe 
sudo apt-get install -f

try the -f one first

---

### Post by Guns90 on 2006-06-17
Nope, I still get 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.'

---

### Post by adam.tropics on 2006-06-17
Or open up Synaptic, and in the edit menu you will find 'fix broken packages'. Although it will do pretty much what the first bit of the above post suggests anyway!

---

### Post by catlett on 2006-06-17
```
sudo apt-get remove flashplugin-nonfree 
```You use remove as the opposite of install. Try running this without sudo, ```
 dpkg --configure -a
``` Aptitude is better than apt-get so use aptitude next time. But for now run aptitude and it should resolve anything```
 sudo aptitude update
``` ```
sudo aptitude upgrade
```
EDIT: Didn't see the other posts when I started to reply.

---

### Post by Guns90 on 2006-06-17
adam, it told me that 'it failed to fix dependicies'

---

### Post by Guns90 on 2006-06-17
catlett, It went thru a whole bunch of stuff, but ended up saying 'Fetched 420kB in 2s (199kB/s)
W: GPG error: [http://dtw.silverentertainment.fi](http://dtw.silverentertainment.fi) gcc34 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ADFE198AE1FF97A0
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Couldn't rebuild package cache'

---

### Post by catlett on 2006-06-17
The issue may be in your repositories. How is that silverentertainment in your repositories? What guide did you follow that had you place that in yoiur repos or did you add it for a specific application.

Post your repository list. Unless you prefer otherwise I can give you a list to replace the one you have and then aptitude should clear everything up.

You get the list by```
 sudo gedit /etc/apt/sources.list
```

---

### Post by Guns90 on 2006-06-17
Well, this is probably how I screwed things up.  I attempted to use [http://users.piuha.net/martti/comp/ubuntu/install.html](http://users.piuha.net/martti/comp/ubuntu/install.html).  

Here is my repository list:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

## UNIVERSE AND MULTIVERSE REPOSITORY
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## BACKPORTS REPOSITORY
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper-backports main restricted
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper-backports universe multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper-backports main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) dapper-backports universe multiverse

## PLF REPOSITORY
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

## WINE
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## Finnish spelling checker for OpenOffice.org 2.x
deb [http://dtw.silverentertainment.fi/oo2-soikko/](http://dtw.silverentertainment.fi/oo2-soikko/) gcc34 non-free

---

### Post by catlett on 2006-06-17
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) This is the guide I use when I set up a new install. It uses this as a repository list 
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```


I would do this. Make a backup of your current list ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Now delete everything in that page. Cut and paste the above list into the page. Run the update/upgrade again.```
 sudo aptitude update
``` ```
sudo aptitude upgrade
```
Then if you want follow the guide to install the packages it explains (following that guide will give you all the multimedia/codecs, wine, plugins etc). Or if you don't feel like it, keep the list and follow th guide another time or another guide. That list is stable and won't cause problems .

If you want your old list back just run```
 sudo cp  /etc/apt/sources.list_backup /ect/apt/sources.list
```

---

### Post by Guns90 on 2006-06-17
Catlett, no matter what I do, I keep getting this:......

Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Fetched 4B in 1s (3B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Couldn't rebuild package cache
gary@gary-desktop:~$  sudo aptitude upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Maybe at this point, since I don't have any of my data files tranferred in, or really do not have all the settings I want, I should just do a reinstall and then use the guide you gave me.  I do appreciate all of your responses.

---

### Post by DotBot on 2006-06-17
The same thing happened to me around the same time that it happened to you!  It doesn't seem to be a repository issue -- I restored a backup, rebooted, followed all suggestions in these posts... phooey!  Exactly the same issue from exactly the same thing.

---

### Post by catlett on 2006-06-17
What happens when you run ```
dpkg --configure -a
``` Does it give an error. Try it with and without sudo ```
sudo dpkg --configure -a
``` Post the error output from the terminal.

---

### Post by Guns90 on 2006-06-17
gary@gary-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
gary@gary-desktop:~$ sudo dpkg --configure -a
Password:
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

This is the place where it just quits working.  I mean nothing happens once this last line comes on screen.  Even after 40 minutes!

---

### Post by DotBot on 2006-06-17
And (surprisingly!) the same here.  dpkg isn't allowed unless I'm superuser, and it hangs in the same place.

sudo dpkg --configure -a
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

---

### Post by Guns90 on 2006-06-17
Thanks, DotBot.  At least now I know that it's not because my computer hates me.

---

### Post by catlett on 2006-06-17
Let's try manually installing the flash plug in. First run ```
sudo aptitude remove flashplugin-nonfree
``` Then open Firefox and go to this website [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)  Download the file (firefox downloads to the desktop by default so I'll assume you still have the default)
Once it is downloaded go over to the package and right click on it choose "extract here". THis will unzip it and give you a folder. Now you have to be in the folder virtually (be there in th terminal) so you use the change directory command (cd). Open your terminal and enter ```
cd /home/catlett/Desktop/install_flash_player_7_linux
``` Obviously replace "catlett" with your username.
Next enter this command```
 ./flashplayer-installer
``` This runs the script that installs the plugin. Hopefully the only issue you have is the flash plugin and hopefully manualy installing it takes care of the error.
Post if there are errors.

---

### Post by Guns90 on 2006-06-17
gary@gary-desktop:~$ sudo aptitude remove flashplugin-nonfree
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
gary@gary-desktop:~$

---

### Post by DotBot on 2006-06-17
Hehe. :P There are a few other people suffering on the forum, too!

---

### Post by catlett on 2006-06-17
Well I was trying to get rid of it before installing the plugin manually. But since we have nothing to loose, install it manually and see if it installs. Then run the update/upgrade again. If you get the same error about configure -a, run that one more time. Then it is s*** or get off the pot time. Either the configure -a will work because the plugin installed correctly or you may have to reinstall. If you don't have important data like you said, I would reinstall if you get the error again.

---

### Post by DotBot on 2006-06-17
The error (*E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.*) seems to pop up for absolutely anything involving aptitude/apt-get/suchandsuch. Woe.

---

### Post by Guns90 on 2006-06-17
It appears that the installation worked.

----------- Install Action Summary -----------

Macromedia Flash Player 7 will be installed in the following directory:

Mozilla installation directory  = /home/gary/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): n


Please log out of this session and log in for the changes to take effect.


The Macromedia Flash Player installation is complete.

gary@gary-desktop:~/Desktop/install_flash_player_7_linux$


I'm going to reboot now.  I'll be right back.

---

### Post by DotBot on 2006-06-17
Hmm.  What I meant to say was: installation worked/flash is all dandy but the error still appears!  I can't reboot right now (playing silly games) - here's hoping it works for you!

---

### Post by Guns90 on 2006-06-17
Well, I was able to reboot, so to check and see if I had gotten past that, in the terminal I did and got the following:

gary@gary-desktop:~$ sudo apt-get install acroread
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
gary@gary-desktop:~$

I guess it's time for the reinstall, huh?  Thank you very much for sticking with me so long on this, catlett.  I'll post here again if I hear of others having this problem and how they fixed it (if they should be able to).

---

### Post by catlett on 2006-06-17
Just run the dpkg --configure -a one last time. I was hoping it was stuck on the flash plug in. If it errors again then I would reinstall. It will be quicker than hunting around for the answer. 
That guide is great. Just make sure to use those repositories, They are listed in the guide. Then you pretty much cut and paste through the whole thing.  Good luck,

---

### Post by Kingsley on 2006-06-17
i had the same problem and just fixed it five minutes ago while looking at this thread. this might help.

open synaptic package manager
click edit -> reload package information (voila.. everything started showing up)
start typing 'flash' and you'll get to flashplugin-nonfree
right click and click mark for removal
click apply

EDIT - wow, this flash thing is messed up. don't bother trying to rerun it through add/remove applications either. :@

---

### Post by catlett on 2006-06-17
[QUOTE=Kingsley]i had the same problem and just fixed it five minutes ago while looking at this thread. this might help.

open synaptic package manager
click edit -> reload package information (voila.. everything started showing up)
start typing 'flash' and you'll get to flashplugin-nonfree
right click and click mark for removal
click apply

EDIT - wow, this flash thing is messed up. don't bother trying to rerun it through add/remove applications either. :@[/QUOTE]
Something appears to be conflicting with the flash plugin all of a sudden. The point I wanted to make was you can keep those repositories I posted. They will give you access to everything. If you have seen posts about "make sure to enable extra repositories", "you have to enable universe and multiverse". That list gives you acces to all those repositories. With that list you have access to all the multimedia codecs, mp3 codecs etc.
For now stay away from flash but other than that search through synaptic for whatever you want, it's all there.

---

### Post by Autoclamp on 2006-06-17
Good work, Kinglsey! I was having the same problem this morning (kismet?), and your solution works well.

And yes, this flash thing is messed up. I'm off to figure out where I read those instructions (for flashplugin-nonfree), and to let the author know that it's a real problem for some people.

Thanks, everybody. If it weren't for these forums, I would have given up in frustration a long time ago.

---

### Post by Guns90 on 2006-06-17
What a day, huh guys?  Well, I reinstalled, got connected, went to the DapperGuide that catlett provided, and began the copy/paste.  When I got to the ' How to install Flash Player (Macromedia Flash) Plug-in for Mozilla Firefox', the exact same thing hapened.  I removed flash (using Kingsley's method) and attempted to install the plug-in manually as I did earlier.  Again I froze at the same place.  So....I agree that Macromedia's Flash program (at least the non-free part) needs to be tweaked by someone.  

I do have one last thought....are any of you using ASUS A7n8XE-Deluxe, AMD 2500+, and/or a Radeon 9200?  Just wondering if it could be a hardware/driver problem.  

Again catlett, thank you very much for all of your assistance.   And good luck to you others.

---

### Post by jeffreyvergara.NET on 2006-06-17
[QUOTE=Kingsley]i had the same problem and just fixed it five minutes ago while looking at this thread. this might help.

open synaptic package manager
click edit -> reload package information (voila.. everything started showing up)
start typing 'flash' and you'll get to flashplugin-nonfree
right click and click mark for removal
click apply

EDIT - wow, this flash thing is messed up. don't bother trying to rerun it through add/remove applications either. :@[/QUOTE]

Wow! thanks! that worked for me...

---

