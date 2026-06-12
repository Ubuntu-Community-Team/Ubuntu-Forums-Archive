---
title: "where are multimedia codecs - dapper and automatix2?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-10-28
It was so easy to get multimedia codecs with old automatix. I just made a fresh install on Dapper and installed Automatix2 - but the codecs are not there. And avi files are not playing.
Where are the codecs then?

---

### Post by RudolfMDLT on 2006-10-28
If automatix is failing you(don't know why...) then check out my sig on sound issues, it should sort you out some whay or the other.

Cheers!

---

### Post by 1002285 on 2006-10-28
> **RudolfMDLT said:**
> If automatix is failing you(don't know why...) then check out my sig on sound issues, it should sort you out some whay or the other.

Cheers!
What's that?
I wouldn't say automatix is failing me, but it does not even offer the option of installing codecs like the old version did.

---

### Post by xpod on 2006-10-28
I got all that stuff from A2 ok......
I know A2 does have a couple of apps less than the original but all that stuff`s still there

---

### Post by RudolfMDLT on 2006-10-28
> **1002285 said:**
> What's that?
I wouldn't say automatix is failing me, but it does not even offer the option of installing codecs like the old version did.

Go here:
[http://ubuntuforums.org/showthread.php?t=182902](http://ubuntuforums.org/showthread.php?t=182902)

As far as I know, your one of the very few people whom have had a complaint about automatix. If your having a specific problem please specify more details but automatix does offer basic codecs as such.

Or you can just do things manually by clicking in the above link.

---

### Post by r4ik on 2006-10-28
Perhaps Terminal-wise ? 

How to add extra repositories

    * Read #General Notes
    * You can also add extra repositories using the Synaptic Package Manager. New users may find it more user-friendly to add extra repositories through the Package Manager. If you follow the link above, you do not have follow the rest of this tip. 

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

    * Replace everything with the following lines 

    To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code) 
    e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse 

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

    * Save the edited file 

wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
sudo apt-get update



sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs

Cheers !

From,

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

### Post by 1002285 on 2006-10-28
> **r4ik said:**
> wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

This part did not work for me - "cannot find openPGP data"

About Automatix2 - I just don't have the option of installing codecs there. I remember having that in the old automatix. And I think there are a lot of other apps gone from Automatix's choice, too. Is it just me?

---

### Post by r4ik on 2006-10-28
> **1002285 said:**
> This part did not work for me - "cannot find openPGP data"

About Automatix2 - I just don't have the option of installing codecs there. I remember having that in the old automatix. And I think there are a lot of other apps gone from Automatix's choice, too. Is it just me?

Did you save the edited sources.list ?

---

### Post by d3v1ant_0n3 on 2006-10-28
I was going to take a screencap and show you where the codecs appeared on my Automatix 2 (I know they were there, I installed them with A2), but you're right. For some reason the codecs have vanished from the menus. Oddness.

I'd suggest Easy Ubuntu, but that always breaks on me for some reason.

---

### Post by r4ik on 2006-10-28
Please try directly from here and it should.

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Good luck !

---

### Post by 1002285 on 2006-10-28
> **r4ik said:**
> Did you save the edited sources.list ?
I did.
"Temporary failure in name resolution" is in this error message, too.

---

### Post by r4ik on 2006-10-28
Same thing here,

"cannot find openPGP data"

Beats me.

Server related perhaps ?

---

### Post by r4ik on 2006-10-28
Installed like this they should be in the multimedia section.
on my machine they are.

 Installing on (K,X)Ubuntu 6.06 i386,amd64 (Dapper)

Edit your sources.list:

sudo gedit /etc/apt/sources.list 

from terminal

Substitute gedit with the text editor of your choice.

Add the following to your sources.list:

NOTE: Kubuntu/Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository.

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Now save the file and close it.

Now from terminal do the following:

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -

To finish off:

sudo apt-get update
sudo apt-get install automatix2

---

### Post by 1002285 on 2006-10-29
I have tried these instructions and the multimedia codecs are not in the menu.
After the wget ... command I got the error message "cannot find OpenPGP data" (it was really in Estonian, may-be it would be differently worded in English).
But I was able to install Automatix2 from Synaptic.
I have tried Automatix Bleeder, too, ant it did not have codecs either.

---

### Post by r4ik on 2006-10-29
Please go to [http://www4.mplayerhq.hu/MPlayer/releases/codecs/](http://www4.mplayerhq.hu/MPlayer/releases/codecs/) and download (save to disk) all-20060611.tar.bz2

Ask for further help on install cant help you with that at the moment.
Good luck.

---

### Post by 1002285 on 2006-10-30
> **r4ik said:**
> Please go to [http://www4.mplayerhq.hu/MPlayer/releases/codecs/](http://www4.mplayerhq.hu/MPlayer/releases/codecs/) and download (save to disk) all-20060611.tar.bz2

Ask for further help on install cant help you with that at the moment.
Good luck.

I have saved it, and I really don't know what to do next. Should I ask for install instructions somewhere else?

---

### Post by arnieboy on 2006-10-30
> **1002285 said:**
> I have saved it, and I really don't know what to do next. Should I ask for install instructions somewhere else?

have u checked out sub category "multimedia" on the install menu on AX2? you should find all the options there.

---

### Post by RudolfMDLT on 2006-10-30
Right click on the file and un-tar it. look in the folder, if you see a "configure" or "make" then do a search for compiling stuff from source. Read the readme first.

Cheers,

Rudolf

---

### Post by 1002285 on 2006-10-30
> **arnieboy said:**
> have u checked out sub category "multimedia" on the install menu on AX2? you should find all the options there.
It's really not there.
I'd show a screenshot if I knew how to put it here, but you can probably believe me without it, too?

---

### Post by 1002285 on 2006-10-30
> **arnieboy said:**
> have u checked out sub category "multimedia" on the install menu on AX2? you should find all the options there.
OK, I was stupid enough not to check the "uninstall" section - it's there.
But the avi files are not working (and it's not the files' problem - I tried different stuff and they work in my DVDplayer, too).
When trying to uninstall the codecs with Automatix2, I get this error message:
Uninstallation of multimedia codecs has been disabled since their removal can cause problems in other applications.
But I did not get to install the codecs after my last install of Ubuntu - I do not know how they can be already installed. Could they have been in my home directory? How would Automatix think that I have them installed?

---

### Post by arnieboy on 2006-10-30
> **1002285 said:**
> OK, I was stupid enough not to check the "uninstall" section - it's there.
But the avi files are not working (and it's not the files' problem - I tried different stuff and they work in my DVDplayer, too).
When trying to uninstall the codecs with Automatix2, I get this error message:
Uninstallation of multimedia codecs has been disabled since their removal can cause problems in other applications.
But I did not get to install the codecs after my last install of Ubuntu - I do not know how they can be already installed. Could they have been in my home directory? How would Automatix think that I have them installed?
upgrade to the latest version of automatix (apt-get update/upgrade). then u will be able to get multimedia codecs back into the install section. then reinstall it.

---

### Post by arnieboy on 2006-10-30
> **arnieboy said:**
> upgrade to the latest version of automatix (apt-get update/upgrade). then u will be able to get multimedia codecs back into the install section. then reinstall it.

and avi files can be played by installing AUD-DVD codecs. install thatt option from AX2

---

### Post by 1002285 on 2006-10-31
I came to the idea of installing automatix2 again even before you wrote about it. But it has not given me any results, I have installed and uninstalled both automatix and the codecs now many times, it does not seem to help at all.
Thanks for helping, though.

---

### Post by STREETURCHINE on 2006-10-31
[QUOTE=d3v1ant_0n3;1679610]I was going to take a screencap and show you where the codecs appeared on my Automatix 2 (I know they were there, I installed them with A2), but you're right. For some reason the codecs have vanished from the menus. Oddness.

dont worry ,got beaten to the post

---

### Post by arnieboy on 2006-10-31
> **STREETURCHINE said:**
> I was going to take a screencap and show you where the codecs appeared on my Automatix 2 (I know they were there, I installed them with A2), but you're right. For some reason the codecs have vanished from the menus. Oddness.

dont worry ,got beaten to the post
The codecs havent vanished. After you have installed them once, they are now in the uninstall tab under sub-category "Multimedia". Uninstall it from there and you will find it again under sub-category "Multimedia" under "Install". Due to safety issues, **AX2 does not actually uninstall multimedia codecs** but merely puts up an info message saying that the uninstallation cannot continue. This is perfectly safe and the codecs can again be installed from the install menu. 
[B]Bottomline: All options are subcategorized in both Install and Uninstall tabs.
[/B]

---

### Post by ReaderRat on 2006-10-31
I just received an update from Automatix2 about 15 minutes ago that had the codecs in it. Try updating:
```
sudo aptitude update
```
And run automatix2 to see if they are there

---

### Post by ReaderRat on 2006-10-31
> I'd suggest **Easy Ubuntu**, but that always breaks on me for some reason.

Seems that Easy Ubuntu has gone out to lunch. It was reported that their website was Closed  for some reason. I hope they have not gone out of business....

---

### Post by 1002285 on 2006-10-31
I even made a new clean install of Ubuntu (Dapper) today, but everything is the same. Even after installing all codecs (incl AUD_DVD) with Automatix2, no video files are playing. They open Totem and sound starts for a second or so, and then Totem closes.
No banana for me I guess.
But before I started making the system new (had to change partitions etc), video was working fine on the very same computer both in Dapper and in Edgy after upgrading. So I think this computer should "be able to do it".

---

### Post by elcasey on 2006-10-31
I had some issues with automatix2 myself. It couldn't (I'm not sure why) install Sun Java, so it uninstalled Frostwire (after installing it). I also was asked on every individual app whether or not to install it because the GPG key didn't "take." 

I'm going to try editing my sources list again today, uninstall everything with ax2, then try readding the keys, then reinstall. I almost want to do a clean install of Edgy now and try it then (got weird problems trying to upgrade to Edgy, too, but I think I forgot to edit my sources list), but I've got Dapper generally set up the way I like. 

This is a rather informative thread, though; good info throughout.

---

