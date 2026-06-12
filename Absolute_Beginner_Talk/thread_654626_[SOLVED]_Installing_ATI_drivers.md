---
title: "[SOLVED] Installing ATI drivers"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2007-12-31
Ok, so I am trying to install the drivers for my ATI Radeon Xpress 200M. Unfortunately I can't figure out how. The restricted drivers wizard says it can't enable the driver and I was told to download Envy. However, when I go to install Envy I have a bunch of dependencies to install, so I looked for those and then tried installing them but ran into even more dependencies. First I tried to install Envy and then it told me I needed xserver-xorg-dev, so I downloaded that but then it said I needed: x11proto-xext-dev and then that said I needed: libxau-dev, and then that said I needed libxau6 but when I go to install it it says that there is already a later version of it on my comp. Am I doing something wrong?

---

### Post by skaldicpoet9 on 2007-12-31
If no one has an explanation for this does anyone know of an alternate way I can get my graphic card's drivers?

---

### Post by wvalters on 2007-12-31
I have the same card in my laptop at home and the restricted driver installed fine, so your issue is kind of strange.  I did use Envy to install that driver and had better success with that, so I would recommend the Envy way.

Can you post the exact messages you get when trying Envy?

---

### Post by twiceasworn on 2007-12-31
More importantly can you post the message you are getting when you try to install the restricted driver.

You are trying to install fglrx right?  If so, I can probably help.  Every box I have set ubuntu up on so far has had an ATI card, and also hasn't worked out of the box.

---

### Post by Ub1476 on 2007-12-31
For the restricted driver, make sure its sources is enabled in System>Administration>Software Sources.

If you want to use Envy, remember to do quick system update as well.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by graben3 on 2007-12-31
Did you tried with the new simplified driver installer from ATI ?

You don't have to make complicated things anymore to install it...

It supports your card i think :
[http://ati.amd.com/support/drivers/linux/previous/linux-rf-cat712.html](http://ati.amd.com/support/drivers/linux/previous/linux-rf-cat712.html)

Then you just run the ATI catalyst control center from Applications menu to configure your screen.

you may also configure it by typing this in console ;
aticonfig --initial

then depending on what screen resolution you want, just type other possible commands
you see by typing 
aticonfig --help

works pretty well for me on and radeon 9550 card with dual screen...

***EDIT :

forgot to tell you you have to run the driver as root!

---

### Post by skaldicpoet9 on 2007-12-31
I already updated my files with the same command line but I still couldn't get Envy install (said there were still dependencies missing). 

The exact message I get from the restricted drivers manager is: 

The software source for the package

xorg-driver-fglrx

is not enabled.

---

### Post by wvalters on 2007-12-31
Looks like Ub1476 had your answer...

"For the restricted driver, make sure its sources is enabled in System>Administration>Software Sources."

---

### Post by skaldicpoet9 on 2007-12-31
I downloaded ATI driver installer but I have no clue how to use it. It won't open with the package manager.

---

### Post by frenchsquared on 2007-12-31
I downloaded the same installer for the same problem
it is on my desktop but I dont know what to do with it

---

### Post by skaldicpoet9 on 2007-12-31
OK I enabled propietary drivers in System>Administration>Software Sources. But now when I go to enable it in restricted drivers manager it says "could not apply changes fix broken packages first". What broken packages? Now I am completely lost.

---

### Post by Ub1476 on 2007-12-31
To fix broken packages run:

```
sudo apt-get install -f
```

To install the latest driver from ATI run:

```
sudo ./ati-driver-installer-8.443.1-x86.x86_64.run
```

---

### Post by frenchsquared on 2007-12-31
sudo ati-driver-installer-8.443.1-x86.x86_64.r didnt work says file no found
also tried changing director to desktop

---

### Post by skaldicpoet9 on 2007-12-31
I used this command sudo apt-get install -f but it still says to fix the broken packages.

This is what I get when I run the ATI command:

sudo: ./ati-driver-installer-8.443.1-x86.x86_64.run: command not found

---

### Post by frenchsquared on 2007-12-31
sorry sjaldicpoet9 for jumping in on your thread
I just didnt want to start a new one for the same thing

here is what I got

gordon@Gateway:~/Desktop$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gordon@Gateway:~/Desktop$ sudo: ./ati-driver-installer-8.443.1-x86.x86_64.run:
bash: sudo:: command not found
gordon@Gateway:~/Desktop$ sudo ./ati-driver-installer-8.443.1-x86.x86_64.run
sudo: ./ati-driver-installer-8.443.1-x86.x86_64.run: command not found
gordon@Gateway:~/Desktop$

---

### Post by erfahren on 2007-12-31
if its on your desktop change directory to it first
```

cd Desktop

```

---

### Post by frenchsquared on 2007-12-31
see previouse I did change director still says command not found

---

### Post by erfahren on 2007-12-31
the restricted driver available with Gutsy works fine and is stable.

installing the newer version may cause more problems trying to get it set up for someone new.

with the restricted driver for ATI cards you just need to install xserver-xgl package to be able to enable the desktop effects

---

### Post by skaldicpoet9 on 2007-12-31
> **erfahren said:**
> if its on your desktop change directory to it first
```

cd Desktop

```

I still got the same message:

sudo: ./ati-driver-installer-8.443.1-x86.x86_64.run: command not found

---

### Post by flamelab on 2007-12-31
NEVER install the ati driver from the ati website without doing these -->[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")

or 

use "Envy" to install AND uninstall the latest ATI driver .


OR

Go System --> Administration --> Restricted Drivers Manager 

and it will install the latest STABLE ati driver ( 8.37 ) 

And you restart X with ctrl + alt + backspace

---

### Post by erfahren on 2007-12-31
> **erfahren said:**
> the restricted driver available with Gutsy works fine and is stable.

installing the newer version may cause more problems trying to get it set up for someone new.

with the restricted driver for ATI cards you just need to install xserver-xgl package to be able to enable the desktop effects
or:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by frenchsquared on 2007-12-31
> **erfahren said:**
> the restricted driver available with Gutsy works fine and is stable.

installing the newer version may cause more problems trying to get it set up for someone new.

with the restricted driver for ATI cards you just need to install xserver-xgl package to be able to enable the desktop effects


Mine doesnt show as restriced and I dont like this low of resolution
will try installing xserver-xgl
I guess just search for it under add mew programs

---

### Post by frenchsquared on 2007-12-31
xserver-xgl is installed already

---

### Post by skaldicpoet9 on 2007-12-31
Umm, this is why I started this whole thread in the first place. I can't install Envy. I can't use the restricted drivers manager. I would type it all out again but if you look at the posts I have made previous to this they will explain my problem.

---

### Post by Ub1476 on 2007-12-31
Sorry, the command was:

```
sudo sh ./ati-driver-installer-8.443.1-x86.x86_64.run
```

---

### Post by frenchsquared on 2007-12-31
> **skaldicpoet9 said:**
> Umm, this is why I started this whole thread in the first place. I can't install Envy. I can't use the restricted drivers manager. I would type it all out again but if you look at the posts I have made previous to this they will explain my problem.

that why I jump onto this thread, I feel you skaldicpoet9

---

### Post by flamelab on 2007-12-31
> **Ub1476 said:**
> Sorry, the command was:

```
sudo sh ./ati-driver-installer-8.443.1-x86.x86_64.run
```

We said NOT that without envy or the guide from wiki.cchtml.com !

skaldicpoet9 --> You do what I posted in the previous page .

---

### Post by erfahren on 2007-12-31
> **skaldicpoet9 said:**
> Umm, this is why I started this whole thread in the first place. I can't install Envy. I can't use the restricted drivers manager. I would type it all out again but if you look at the posts I have made previous to this they will explain my problem.
a common problem with that is that all the repositories aren't enabled

You're the one with the 200m card - the restricted driver should be available for you

---

### Post by skaldicpoet9 on 2007-12-31
Now I am just confused. I have tried this a million different ways. No I can't enable the driver through the Restricted Drivers Manager. No I can use the ati install package. No I can't even use Envy. What is the solution here?

---

### Post by erfahren on 2007-12-31
@skaldicpoet9

pls post the output of
```

cat /etc/apt/sources.list

```

---

### Post by flamelab on 2007-12-31
You download the .run file from ATI and go to [wiki.cchtml.com]("wiki.cchtml.com") and choose the guide for Ubuntu .

Nothing else . The others confused you

---

### Post by frenchsquared on 2007-12-31
who ever said

sudo sh ./ati-driver-installer-8.443.1-x86.x86_64.run

you freakin rule, its installing now to see if it works

---

### Post by flamelab on 2007-12-31
You will destroy X11 if you don't follow the instructions from wiki.cchtml.com

---

### Post by skaldicpoet9 on 2007-12-31
> **erfahren said:**
> @skaldicpoet9

pls post the output of
```

cat /etc/apt/sources.list

```

Sorry, I didn't see this post before....here you go:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

btw I just tried the ATI sudo cmd that UB1476 recommended and it worked fine it seems. Maybe I am a newb but why did you say don't do it that way flamelab? (It was already in the process of happening when I read your post so I hope it isn't something bad).

---

### Post by skaldicpoet9 on 2007-12-31
> **flamelab said:**
> You will destroy X11 if you don't follow the instructions from wiki.cchtml.com

OMG

Are you kidding me?

This is the biggest pain in the *** ever.

So now what? I just installed this.

---

### Post by frenchsquared on 2007-12-31
so hmm It wont boot
Im in the recovery at the root@Gateway
do I have to start over?

---

### Post by flamelab on 2007-12-31
Why didn't you go to read my first post ?

I told you that you are going to have a problem !


See -->[http://ubuntuforums.org/showpost.php?p=4046830&postcount=20]("http://ubuntuforums.org/showpost.php?p=4046830&postcount=20")

---

### Post by skaldicpoet9 on 2007-12-31
Really? Oh, great. Does that mean I just did all of this for nothing? I have been sudoing and command lining and installing packages out the ears. And now I have to start from square one? Say it ain't so :(

---

### Post by skaldicpoet9 on 2007-12-31
> **flamelab said:**
> Why didn't you go to read my first post ?

I told you that you are going to have a problem !


See -->[http://ubuntuforums.org/showpost.php?p=4046830&postcount=20]("http://ubuntuforums.org/showpost.php?p=4046830&postcount=20")

Well unfortunately I didn't read your post until after I had read the other. Damnit.

---

### Post by frenchsquared on 2007-12-31
well I jsut installed so if I have to rienstall let me know so I can start

---

### Post by Saint Angeles on 2007-12-31
heres whats worked with me (with about 8 different linux installs on this machine):

go to [www.ati.com](www.ati.com) and find the drivers page. look for "previous drivers" and get the 7.11 catalyst. its a *.run file.

save it to your desktop. open a terminal and navigate to the desktop by typing "cd Desktop"

then type "sudo sh ati[tab]" hitting tab auto-completes the file name

you will then be faced with a graphical installer. do it will all the default settings, reboot... and voila!!

---

### Post by frenchsquared on 2007-12-31
> **flamelab said:**
> You download the .run file from ATI and go to [wiki.cchtml.com]("wiki.cchtml.com") and choose the guide for Ubuntu .

Nothing else . The others confused you

where were you an hour ago
anyway Im almost done with the rienstall

will try the instruction you sent

---

### Post by flamelab on 2007-12-31
&#927;&#954; !

---

### Post by frenchsquared on 2007-12-31
> **Saint Angeles said:**
> heres whats worked with me (with about 8 different linux installs on this machine):

go to [www.ati.com](www.ati.com) and find the drivers page. look for "previous drivers" and get the 7.11 catalyst. its a *.run file.

save it to your desktop. open a terminal and navigate to the desktop by typing "cd Desktop"

then type "sudo sh ati[tab]" hitting tab auto-completes the file name

you will then be faced with a graphical installer. do it will all the default settings, reboot... and voila!!


this is a very new card 2400 series for a notebook
will the old one work?

I just did basically what you said and now I  am rienstalling

---

### Post by erfahren on 2007-12-31
> **Saint Angeles said:**
> heres whats worked with me (with about 8 different linux installs on this machine):

go to [www.ati.com](www.ati.com) and find the drivers page. look for "previous drivers" and get the 7.11 catalyst. its a *.run file.

save it to your desktop. open a terminal and navigate to the desktop by typing "cd Desktop"

then type "sudo sh ati[tab]" hitting tab auto-completes the file name

you will then be faced with a graphical installer. do it will all the default settings, reboot... and voila!!
that's wonderful. it doesn't work that way for everyone though. That driver doesn't work for everyone. I tried that version and after getting it configured X started crashing on me. see what [Kilz](http://ubuntuforums.org/showpost.php?p=3821286&postcount=13) said about it.

it gets annoying when people jump in and insist that newbies (or anyone) go and install those drivers when having other problems (like enabling desktop effects or whatever). 

This isn't Windows where "updating to the latest driver" is the answer to everything.

---

### Post by skaldicpoet9 on 2007-12-31
Well, I installed the ATI driver, rebooted, and here I am again didn't have to reinstall for whatever reason my computer is fine...Ubuntu is still here. However, whenever I go into the Restricted Drivers Manager it still won't let me enable the ATI drivers. Now maybe the drivers are working but it still says that before I can enable it in the restricted drivers manager I have to "fix broken packages". Is there anyway to know whether or not the ATI drivers are working? I mean obviously something is working (but everything was working before I tried enabling the ATI drivers so I really can't tell if they are on or not).

---

### Post by skaldicpoet9 on 2007-12-31
Ok, I typed in aticonfig in the terminal and all is well. I now have a shortcut for the Catalyst Control Center in my applications tab. So, apparently all is well for right now. (Actually I am having trouble with installing Armagetron...it says  it conflicts with other installed software and that before I can install it I have to uninstall the conflicting software...oh, well it is a topic for the future...) 

Anyways, thanks for the help everyone!

:)

---

### Post by flamelab on 2007-12-31
Have you first installed the ubuntu updates ?

---

### Post by skaldicpoet9 on 2007-12-31
The updates were actually installing at the same time I was installing the drivers. So,yes the updates have been installed.

---

### Post by skaldicpoet9 on 2007-12-31
WOW

This is crazy. Most of the games apps in the add/remove manager say that there is conflicting software or that the software does not support my computer's hardware. 

I think there is yet another problem to be solved....

for another day though....I am taking a siesta lol

and no, this does not turn me off of Linux. I am sure you have seen a lot of people just give up because things get a little intensive. I say bring it on :)

I am actually really digging Ubuntu right now even though I have been up the past 6 hours figuring out how to get my it to dual boot, wireless working and graphics card drivers installed. I look forward to actually knowing what I am doing lol...

---

