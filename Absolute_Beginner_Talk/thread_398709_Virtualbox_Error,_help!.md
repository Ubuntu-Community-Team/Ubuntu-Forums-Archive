---
title: "Virtualbox Error, help!"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Penguin Fever on 2007-04-01
Now before I begin, I must apologise for how stupid I'm probably about to sound.  To call me a beginner with ubuntu (and in fact linux in general) would be an understatement, I have had ubuntu installed onto my pc only in the last week, and everything was fine until ..well..today.

A couple of days ago, I had tried installing virtualbox to try and run a graphics program, during the installation however, a problem must have occured as the package installer froze and I was forced to restart my PC.  I gave up on installing virtualbox and continued as usual, however to my dismay, I noticed that now I can't install anything (including any updates).  Every time I open Synaptic Package Manger or attempt at installing anything via "Add/Remove", an error message appears which says: "E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

I tried "reinstalling" virtualbox and now it says the installation file is corrupt.. I tried downloading the installation file again, and the same thing happens, so I can't install virtualbox and I apparently can't remove it.. I think I need help XD

I apologise if I didn't explain that correctly, if you need to know anything else just let me know.

I really am such an idiot, any help would be so much appreciated, in fact I'll give you cookies if you can help!

Oh and as I said, I really am a beginner so ..er.. keep that in mind if you're able to help me :oops: :P

Thank you so much in advance, as I said, any help is REALLY appreciated!

---

### Post by OffHand on 2007-04-01
Try:

```
sudo apt-get remove --purge virtualbox && sudo apt-get clean
```

---

### Post by Penguin Fever on 2007-04-01
Thanks for the reply! :D

Unfortunately when I tried it, it still says "E: The package virtualbox needs to be reinstalled, but I can't find an archive for it." :(

But thank you so much for trying!

---

### Post by OffHand on 2007-04-01
> **Penguin Fever said:**
> Thanks for the reply! :D

Unfortunately when I tried it, it still says "E: The package virtualbox needs to be reinstalled, but I can't find an archive for it." :(

But thank you so much for trying!

Try:
```
sudo apt-get install -f
```

---

### Post by Penguin Fever on 2007-04-01
> **OffHand said:**
> Try:
```
sudo apt-get install -f
```

Unfortunately the same happens there too :( Thanks again though!

I'm sorry to be causing so much trouble! >.<

---

### Post by Jon &quot;Yogi&quot; on 2007-04-01
I have the same problem as well, and nothing seems to work for me either. I think that when there is a virtualbox package in the repositories for feisty, then this may work.  I'll post back if I find any fixes to get synaptic to work again.

---

### Post by OffHand on 2007-04-01
This should do it:

```
dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by Jon &quot;Yogi&quot; on 2007-04-01
Try this. From the command line, type in (at your home folder, or anywhere else you want to put this): ```
mkdir ~/install_files
``` and ```
cd ~/install_files
``` Now  type in ```
wget http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
```Now type ```
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
```It should install, asking you a few questions. If it didn't install correctly (didn't for me), don't worry about that just yet. The bigger concern is making apt work again. After doing that, try to run and apt update to see if everything is working (and if it is, press Ctrl-C to stop the process:```
sudo aptitude update
```Now you can worry with setting up Virtualbox with a working apt :).

I used [this]("http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/") nice tutorial from jhcore.com to help out.

---

### Post by Penguin Fever on 2007-04-01
Oh wow thanks for your help!

Well I actually got something different this time!

I tried the first suggestion and it asked for "superuser privilege" or something like that, so i tried sudo before it and got this message:

"dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal."

But of course I can't install it as it wont let me, so then I tried it again, and got this message:

"dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed."

Then I tried it again..

"warning: ignoring request to remove virtualbox which isn't installed."

Gah >.< Yet it wants me to reinstall it, stupid PC!

Then I tried  Jon "Yogi"'s suggestion and after the fourth step (i think) I received a screen that was like an agreement screen.. But it wont let me do anything (ie. agree, disagree, continue, etc.) >.<

Aah I'm beginning to hate virtualbox :P

Thank you again so much for your help, it's great to know that there are people who will hate a stupid girl like me ^^ :oops:

---

### Post by Penguin Fever on 2007-04-01
Oh wait, it worked!! I just tried to install some system updates and it worked!! Oh thank you both SO much! I'm so so grateful!

I'm going to make you both some cookies now XD

---

### Post by OffHand on 2007-04-01
> **Penguin Fever said:**
> Oh wait, it worked!! I just tried to install some system updates and it worked!! Oh thank you both SO much! I'm so so grateful!

I'm going to make you both some cookies now XD
Glad it worked.

---

### Post by simonsocial on 2007-04-06
Well your expert guidance worked! I've managed to remove my problematic Virtualbox install.

Thanks!

---

### Post by Lucifiel on 2007-05-03
Ooh the instructions in this thread really worked!! :D 

dpkg --remove --force-remove-reinstreq virtualbox

Virtualbox actually caused Synaptic to not work.

---

### Post by ShirishAg75 on 2007-05-03
sorry to put the spanner in the thread, but did u install the libraries required to be installed before installing the .deb 

[QUOTE=http://www.virtualbox.org/wiki/Downloads]You will need to install some additional libraries on your Linux system in order to run VirtualBox - in particular, you will need libxalan-c, libxerces-c and version 5 of libstdc++.[/QUOTE]

---

### Post by Lucifiel on 2007-05-03
> **shirishag75 said:**
> sorry to put the spanner in the thread, but did u install the libraries required to be installed before installing the .deb

I think there isn't any need for the listed dependencies in Feisty.

---

### Post by fenderuser on 2007-05-08
I have had the same problem with both update manager and synaptic.  I discovered was that this method worked fine, however, synaptic managed to work again straightaway but I needed to do a restart to get update manager working again.

---

### Post by alex_anthony on 2007-05-11
THANK YOU!!! This had been really annoying me!

---

### Post by Neil_J on 2007-05-12
I ran into the same problem today trying to set up VirtualBox...

The install didn't crash, the commandline installer was waiting on user input, and the Synaptic GUI was hiding it.  If you run the install from the commandline, it will eventually bring up an ncurses interface that asks you to read an accept their software agreement.  After this is done everything should run smoothly.

---

### Post by infobunny on 2007-09-09
Me too, tried the above command and it fixed the problem. I love this forum!

---

### Post by guittarman10 on 2007-09-19
yes it worked for me too. thank you very much

---

### Post by spenc083 on 2007-09-22
Thank you for the info, this worked for me as well. I can't make cookies but I'm willing to donate a few bucks.

:-D

Keith...B

---

### Post by eragon100 on 2007-09-22
Great it worked!

I am glad i came looking for here after 45 minutes already, the --force-reinstreq etc... option worked immidiately, tried installing abuse and it worked! Thanks (I am very curious who maked that package, coukldn't accept license agreement, i might be a noob who switched to ubuntu ultimate (from xp, vista didn't work, wanted new OS just two weeks ago, but even I can think up that this is NOT how a package should install itself :()

:):):):):)

---

