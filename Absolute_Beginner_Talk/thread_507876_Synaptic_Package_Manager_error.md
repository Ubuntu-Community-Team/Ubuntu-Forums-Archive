---
title: "Synaptic Package Manager error"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Rosemere on 2007-07-23
Using Ubuntu 7.04.  I was trying to install flash player and somehow I have done something incorrect. 
I cannot go into Synaptic Manager by this method of : system administration
synaptic package manager. 
When I do this I get the following error.
E: Type 'deb-sr' is not known on line 5 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

When I go to Add/Remove Applications I get the following message:
[B]Failed to check for installed and available applications
[/B]
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I can get to soft ware sources in Synaptic by right clicking Update Manager on the toolbar and going to preferences. 

I also have another post here which was started because I was missing the less file.  Maybe the two problems are tied together

If you can give me some simple directions as to how to repair it would be great.

---

### Post by Foxmike on 2007-07-23
Can you post a copy of your /etc/apt/sources.list ?
 
It looks like there is an incorrect line in it that synaptics is unable to read.
 
Have you installed any third party repositories?

---

### Post by davidjmayo on 2007-07-23
I saw and replied to your other thread

The problem is with the Canada repos not you

In synaptic==>repositories
then change the download server (you may have to choose from other. US is probably your best bet)

---

### Post by davidjmayo on 2007-07-23
@Foxmike - have you tried anything from the Canada repos yesterday/today. I saw this in another thread [http://ubuntuforums.org/showthread.php?t=506939&highlight=canada](http://ubuntuforums.org/showthread.php?t=506939&highlight=canada) (don't know if it's true as it's not my repos)
Rosemere did try to edit deb.sr to deb.src - see the other thread [http://ubuntuforums.org/showthread.php?p=3067608#post3067608](http://ubuntuforums.org/showthread.php?p=3067608#post3067608)

---

### Post by Rosemere on 2007-07-23
Yes I tried to install flash player, I also know Autmatix doesn't work here

pete@pete-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
pete@pete-desktop:~$ /etc/apt/sources.list file
bash: /etc/apt/sources.list: Permission denied
pete@pete-desktop:~$ ls
automatix2.key                            Intel-536ep-443.tgz
Automatix.rtf                             Intel-536EP-4.71.tgz
deluge-torrent_0.5.1-0zachtib1_amd64.deb  intel_536ep_feisty.tar.gz
Desktop                                   jre-1_5_0_12-linux-i586-rpm.bin
Examples                                  jre-6u1-linux-i586-rpm.bin
hplip-2.7.6                               McDonald's Toy Story 2.rtf
hplip-2.7.6.run                           Pete_sSideofBeefOrder.doc
install_flash_player_9_linux              pitfdll-0.8.2.tar.gz
Intel-536                                 Preferences
intel-536EP-2.56.76.0                     Screensaver
Intel-536ep-443                           skype-1.4.0.74.deb
pete@pete-desktop:~$

---

### Post by Seisen on 2007-07-23
```
 gksudo gedit /etc/apt/sources.list 
``` will open you source list in gedit

---

### Post by Foxmike on 2007-07-23
> **davidjmayo said:**
> @Foxmike - have you tried anything from the Canada repos yesterday/today. I saw this in another thread [http://ubuntuforums.org/showthread.php?t=506939&highlight=canada](http://ubuntuforums.org/showthread.php?t=506939&highlight=canada) (don't know if it's true as it's not my repos)
Rosemere did try to edit deb.sr to deb.src - see the other thread [http://ubuntuforums.org/showthread.php?p=3067608#post3067608](http://ubuntuforums.org/showthread.php?p=3067608#post3067608)
I think this is a typo: (I'm not in front of my Ubuntu machine, Ì'll check tonight): it should be: deb-src instead of deb.src (notice the dash instead of the dot)
 
Tho, I had difficulties with canadian repos lately, I'll check, thanks!

---

### Post by davidjmayo on 2007-07-23
@Foxmike yes a typo by me  sorry

---

### Post by Nythain on 2007-07-23
sounds like a simple problem to fix... find line 5 in your /etc/apt/sources.list file
```

gksudo gedit /etc/apt/sources.list

```
change the begging of that line from
```

deb-sr

```
to
```

deb-src

```
and any other entries that are missing that c
save teh file
then
```

sudo apt-get update

```
and you should be ready to roll

---

### Post by Rosemere on 2007-07-23
I am really dense I guess. 

Yes I changed in preferences Download from the United States and I chose mirror/anl.gov/pub/ubuntu

Can you tell me how I count down 5 lines. 

On my computer this is the fifth line:
c [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

---

### Post by davidjmayo on 2007-07-23
You're not dense. It looks like I have confused the issue here because I saw your other thread

the other people are trying to help you fix you sources.list (quite rightly) but maybe don't know the problem could be getting files from the Canadian repos (download server)
This is the same as you did in your other thread - changing deb-sr to deb-src
I seem to have taken this away from your original question.

There are/have been problems with Canada repos (see my message to Foxmike and the reply
 "Tho, I had difficulties with canadian repos lately, I'll check, thanks!"

This is why I suggested you change to US instead of Canada
If you changed to US then try to get flash

Any problems post back and post your sources.list

```
cat /etc/apt/sources.list
```

---

### Post by Nythain on 2007-07-23
ok, that c on that line should look like 
deb-src
and based on that line starting with c, im going to assume somewhere in the line right above it should be a 
deb-sr
it would appear (and i dont know for sure since you havent posted your source.list yet) that somewhere a line got broke between the sr and the c or deb-src

once you get your sources.list posted up we can tell you exactly what needs to be changed to what and what else might need to be removed to get it going again

---

### Post by Rosemere on 2007-07-24
I have just ried again and no luck. I just checked I am using a site in the US.
Will post my list. Can you highlight the line 5 that I need to change. Should I remove Automatix, if so can you guide me. I read it can cause problems.

Thanks in advance.

pete@pete-desktop:~$ sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg
Password:
E: Type 'deb-sr' is not known on line 5 in source list /etc/apt/sources.list
E: The list of sources could not be read.
pete@pete-desktop:~$ 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty universe restricted main
deb-sr
c [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

## Major  bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.gksu gedit /etc/apt/sources.list

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-proposed universe restricted main
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-proposed universe restricted #Added by software-properties
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-backports universe restricted main
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-backports universe restricted #Added by software-properties

#AUTOMATIX REPOS START

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-backports multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-backports multiverse #Added by software-properties



deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty multiverse #Added by software-properties


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty universe restricted main
deb-sr
c [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

## Major  bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.gksu gedit /etc/apt/sources.list

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-proposed universe restricted main
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-proposed universe restricted #Added by software-properties
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-backports universe restricted main
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-backports universe restricted #Added by software-properties

#AUTOMATIX REPOS START

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-backports multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-backports multiverse #Added by software-properties



deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty multiverse #Added by software-properties




#AUTOMATIX REPOS END
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-security multiverse universe restricted main
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-security multiverse universe restricted #Added by software-properties
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-updates multiverse universe restricted main
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-updates multiverse universe restricted #Added by software-properties
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb http:// archive.ubuntu.com/ubuntu/feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS END
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-security multiverse universe restricted main
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-security multiverse universe restricted #Added by software-properties
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-updates multiverse universe restricted main
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty-updates multiverse universe restricted #Added by software-properties
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb http:// archive.ubuntu.com/ubuntu/feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by Foxmike on 2007-07-24
Those lines:
```
deb-sr
c [_[COLOR=#bd5900]http://ubuntu.mirrors.tds.net/pub/ubuntu/[/COLOR]_]("http://ubuntu.mirrors.tds.net/pub/ubuntu/") feisty universe restricted #Added by software-properties
```
and
```
deb-sr
c [_[COLOR=#bd5900]http://ubuntu.mirrors.tds.net/pub/ubuntu/[/COLOR]_]("http://ubuntu.mirrors.tds.net/pub/ubuntu/") feisty universe restricted #Added by software-properties
```
Are causing the trouble.  They should be read like this:
```
deb-src [_[COLOR=#bd5900]http://ubuntu.mirrors.tds.net/pub/ubuntu/[/COLOR]_]("http://ubuntu.mirrors.tds.net/pub/ubuntu/") feisty universe restricted #Added by software-properties
```
and
```
deb-src [_[COLOR=#bd5900]http://ubuntu.mirrors.tds.net/pub/ubuntu/[/COLOR]_]("http://ubuntu.mirrors.tds.net/pub/ubuntu/") feisty universe restricted #Added by software-properties
```
 
Perhaps, you seem to have some lines that appears twice.  I think that confuses Synaptics as well, you should check for lines that appears twice and remove the double one.
 
I see you are using Automatix.  Automatix is known to cause troubles to Synaptics/Apt.  I would strongly suggest you to remove it unless you have a very good reason not to do so.  95% of the packages you would install thru Automatix can be installed directly thru Synaptics.
 
Regards,
 
-FM

---

### Post by dptxp on 2007-07-24
The best way is to open add/remove, open 'preferences' in add/remove window at bottom left and select server bu letting Ubuntu search the best server for you.

---

### Post by Rosemere on 2007-08-01
Resolved

---

