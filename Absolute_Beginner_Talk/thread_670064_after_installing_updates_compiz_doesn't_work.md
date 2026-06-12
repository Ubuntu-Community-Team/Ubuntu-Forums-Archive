---
title: "after installing updates compiz doesn't work"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-01-17
Hi,

i just updated mu ubuntu system, now all my desktop effects and configuration won't work, the menu point advanced desktop configuration under system>preferences doesn't exist anymore, i ran "compiz" in the terminal, now i even lost the header of all windows, any ideas?

---

### Post by RomeReactor on 2008-01-17
Hi. Did you upgrade from 7.04, and if so, did you use Beryl? Open a terminal (Applications->Accessories->Terminal) andplease post the output of this command:
```
cat /etc/apt/source.list
```

Also, try this to see if the borders come back:
```
gtk-window-decorator --replace
```

---

### Post by Djalmahal on 2008-01-17
So, the response to the first command was "No such file or directory" and after the second command a basic theme came back. 
I believe i had the newest "beryl" version, which is called compiz fusion, now if i go into appearance and go to visual effects extra or custom no "wobbly" windows or such come up. THere is also a new menu point under system>preferences called compizconfig setting manages (it's new as i said, meaning it wasn't there before the update), but if i click on it doesn't react. On the other hand the menu point advanced desktop settings is not there anymore.

Thanks for you effort in helping me out, i only started on ubuntu 2 weeks ago
ANdreas:KS

---

### Post by Djalmahal on 2008-01-17
Update

After running "compiz" in the terminal the emerald theme manager seems to be running again, so i have the ability back to change the theme, but still no cube etc, changing  the level of visual effects in appearance doesn't change anything and the compizconfig setting manager doesn't come up after i click it in the menu

---

### Post by Djalmahal on 2008-01-17
andreas@andreas-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

andreas@andreas-laptop:~$

Sorry for the bit by bit information, here is the print out for the compiz command.

I tried things out, the whole graphical interface feels unstable, windows freeze, loose their title, etc
It's late, i'll go to bed, hope to hear from you tomorrow
Andreas

---

### Post by HermanAB on 2008-01-17
I have a question for you:
If everything was working fine, why did you do an update?

More Linux trouble is caused by doing an update, than by not doing an update...

Cheers,

Herman

---

### Post by Djalmahal on 2008-01-17
Well, it said it has 180 updates so it sounded everything was outdated, hence the thought of doing an update....
Any tips how to solve this?

---

### Post by RomeReactor on 2008-01-17
> **Djalmahal said:**
> So, the response to the first command was "No such file or directory"

Sorry about that; the correct command is:
```
cat /etc/apt/sources.list
```
Have you added any repositories related to desktop effects?

---

### Post by Djalmahal on 2008-01-17
So, the answer to the last command is:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://download.tuxfamily.org/3vldeb](http://download.tuxfamily.org/3vldeb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets
deb [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/) gutsy screenlets
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
andreas@andreas-laptop:~$ 


As far as I know i haven't added any repositiories to desktop effects, what would they be?

I don't know much what it's telling me....
I get the windows titles back by running "emerald" in the terminal, but still no advanced windows settings (that's compiz fusion right?), and the compizConfig Settings Manager in system>preferences doesn't react...

ANdreas

---

### Post by Sef on 2008-01-17
> deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://download.tuxfamily.org/3vldeb](http://download.tuxfamily.org/3vldeb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets
deb [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/) gutsy screenlets
deb [http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu](http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu) gutsy/

These have been added to sources list.

You have a mixture of sources (from edgy, fiesty, and gutsy), so that could be the problem. There might be an easier way than removing beryl and installing Compiz-Fusion, but I am not sure what that would be, so I will let someone else answer as to what to do.

---

### Post by Djalmahal on 2008-01-17
HI,

obviously i didn't really know what i was doing when i installed all that, how about just wiping all the eyecandy stuff from my ubuntu and just install the correct version of compiz-fusion?
Could you quickly show me thru this? Where would i have to delete all the deb lines?
I tried in the meanwhile to uninstall compiz and reinstall it again, now i don't have an option anymore to go to the cube and i lost emerald.
I just want to start new, then i could just follow one of the threat in ubuntuforums to install the gutsy version of compiz fusion
Thanks
Andreas

---

### Post by RomeReactor on 2008-01-17
First, go to 'System->Preferences->Appearance' and on the 'Visual Effects' tab set it to "None". Then let's try removing anything that you installed from those repositories: Open Synaptic (System->Administration->Synaptic), press the 'Origin' button on the lower left, highlight each of the Edgy and Feisty repositories, and mark every installed package **from those repositories only** for "Complete Removal" by right-clicking on them.

Now, still in Synaptic, go to 'Settings->Repositories' and on the second tab (Third-Party Software) disable the Edgy and Feisty repositories. Close that window and still in Synaptic press the blue Reload' button. Then see if you can enable the effects.

Remember to only mark for removal packages from the **Edgy** and **Feisty** repositories.

---

### Post by Djalmahal on 2008-01-17
Cool, thanks for your reply, i went ahead, two error messages came upon reload, both of them refering to (i think) the same problem.


The first one says 
Could not download all repository indexes
 quoting

[http://download.tuxfamily.org/syzygz42/dists/gutsy/release:](http://download.tuxfamily.org/syzygz42/dists/gutsy/release:) Unable to find

I checked it and it says 404 not found

The second one goes:
w: GPG error hhtp://download.tuxfamily.org gutsy release. The following signatures couldn't be verified because the public key is not available
NO_PUBKEY 3C33E735F854AFD7

I will now go ahead and try to install compiz fusion i'll tell you what happened.
Once again, thanks for your advise, much appreciated.

ANdreas

---

### Post by Djalmahal on 2008-01-17
Seems like this is getting worse, next thing i checked was the compiz in synaptic manager, it was all installed, i then read in another threat on ubuntu forums that xgl was involved, so i installed that, now the whole graphics are super slow, even scrollling down in firefox, the picture just jumps, moving windows the same.

I don't know, i'm not knowing what to do, what i do, doesn't seem to work or has negative effects. Still the system>preferences>CompizConfig Settings Manager doesn't react when i click.
I'm now going to unistall xgl again

SHow me the way...
Andreas

---

### Post by spiderbatdad on 2008-01-17
after installing xserver-xgl you will need to reboot. then check "custom" under appearance>>visual effects...should be that simple, assuming you have emerald as a windows theme manager.

---

### Post by Djalmahal on 2008-01-17
Ok, unstalled xg
l (GL-based X server
Xgl provides a GL-based X server, performing its drawing through a GL stack.
In combination with a GL-based compositing manager, this allows for high-speed
transformations of windows)

this is the description from the synaptics manager, rebooted and at least the graphics are smooth again, Avant Window Manager and Emerald Theme Manager are installed (i checked in synaptics) but both have no effect, if i start avant in applications nothing happens, if i change the theme in emerald the theme doesn;t change.

Ok, i changed to Ubuntu 2 weeks ago, i like it, but i used to be the person who knew how things worked, i showhed my friends how to do things with computers, both on Macintosh and WIndows. This is pretty humbling as well as frustrating.

Andreas

---

### Post by spiderbatdad on 2008-01-17
unfortunately, my experience with compiz-fusion was lousy, whereas it was awesome using beryl in Fiesty. I have t-30 several years old with an older radeon mobility graphics card. I don't know if you'll be able to get the same satisfaction out of compiz as beryl gave you. I notice you haven't said what graphics card you have.

---

### Post by Djalmahal on 2008-01-18
Hi spiderbatdad,.
ok so i installed xgl, then it all became superslow, unistalled it, found out i don';t have any themes from emerald( which is installed) anymore, avant window manager (max dock like) didn't work anymore, i read your post about xgl again, reinstalled it, now avant is back, suddenly there is the windows xp theme on my windows. I now try to change the theme with emerald, no effect, if i change it with system>prefernces>appearance then there comes a weird mash up of themes

[IMG]file:///home/andreas/Desktop/mashup[/IMG]

My graphic card is intel 945 and before i ran a big ubuntu update i had the full compiz fusion thing running, very neat, cube and everything, then suddenly after the update, no special effects anymore.
2 days later i still don't have the compiz fusion back, i uninstalled things, reinstalled, checked my repositories etc.

THanks for replies
Andreas

---

### Post by Djalmahal on 2008-01-18
OK, i kind of solved, followed another threat to remove all graphic effects till i was unable to move windows, then build it up again, now it's pretty much where it used to be, just some configuration of compiz to be done. Thanks for everyone who helped. I had to uninstall xgl-server though as with it moving windows became really slow and chubby

Thanks again everyone
Andreas

---

