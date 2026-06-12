---
title: "playing DVDs"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Scott A on 2008-01-12
Many of my DVDs won't play,
how do I fix this?

---

### Post by philinux on 2008-01-12
Click the link and check out medibuntu. If you already have this set up post back.

---

### Post by argraff on 2008-01-12
You have to enable the non-free stuff. Check this link out:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats").

Good luck and let us know if you need any more help.

---

### Post by Scott A on 2008-01-12
It says to go to a command line and type in code. 
How do I get to the command line?

---

### Post by Nezing on 2008-01-12
Try this.Go to** Terminal,**and paste this code in:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse


Press **enter** on your keyboard,and let it install.At some part it might ask you if you want to continue (Y/N) Press Y  for yes,on your keyboard.

When Terminal has finished,paste this in:


sudo /usr/share/doc/libdvdread3/install-css.sh

Then press enter on your keyboard.

Let it finish,should just take seconds,close Terminal,and test with a dvd.

---

### Post by oldos2er on 2008-01-12
Enable the Medibuntu repository, then in a terminal type the command "sudo aptitude install ubuntu-restricted-extras libdvdcss2".

---

### Post by crjackson on 2008-01-12
Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You won't have any trouble after this.

---

### Post by nikoPSK on 2008-01-12
> **crjackson said:**
> Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
``````
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
``````
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```You won't have any trouble after this.

was that a shortened version from me? :KS

---

### Post by crjackson on 2008-01-12
> **nikoPSK said:**
> was that a shortened version from me? :KS

Sorry, it was not...

---

### Post by nikoPSK on 2008-01-12
lol, well as I'm here I'll just give it:

here you go:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```It'll change totem gstreamer to totem xine to enable dvd menus. (if in gutsy replace the section of the top code 'fiesty" to "gutsy".

nikoPSK

---

### Post by nikoPSK on 2008-01-12
> **crjackson said:**
> Sorry, it was not...

it's best to explain what the commands do :)

---

### Post by Scott A on 2008-01-12
I followed the diretions from nikoPSK, restarted totem movie player and received this error message:
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.Please install the necessary plugins and restart Totem to be able to play this media.

redid directions and in the terminal part of what it said was this:
gxine is already the newest version.
xine-ui is already the newest version.
libdmx1 is already the newest version.

---

### Post by nikoPSK on 2008-01-12
> **Scott A said:**
> I followed the diretions from nikoPSK, restarted totem movie player and received this error message:
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.Please install the necessary plugins and restart Totem to be able to play this media.

redid directions and in the terminal part of what it said was this:
gxine is already the newest version.
xine-ui is already the newest version.
libdmx1 is already the newest version.

well, It said that before I installed it for me. try removing everything with apt-get remove and try again please :)

Regards,
nikoPSK

---

### Post by Scott A on 2008-01-15
I tried "sudo /usr/share/doc/libdvdread3/install-css.sh" and it said "command not found."


I tried scott@scott-desktop:~$ sudo aptitude install ubuntu-restricted-extras libdvdcss2Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "ubuntu-restricted-extras"
The following packages are BROKEN:
  libdvdcss2
The following packages have been kept back:
  acroread libpq4 libxml2 libxml2-utils mplayer python-libxml2
  python2.4-libxml2
0 packages upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 36.3kB of archives. After unpacking 106kB will be used.
The following packages have unmet dependencies:
  libdvdcss2: Depends: libc6 (>= 2.6-1) but 2.3.6-0ubuntu20.5 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.



NikoPSK said to "try removing everything with apt-get remove and try again please"
but I don't know what that means or how to do it. 

What do I do?:(

---

### Post by SunnyRabbiera on 2008-01-15
hmm, well you can give automatix a shot.
Its a bit shaky but it can get your media up and running:
[the automatix homepage]("http://www.getautomatix.com/")
I recommend using it for newcommers as i know command line can be intimidating.

---

### Post by linuxisfree on 2008-01-15
> **Scott A said:**
> I followed the diretions from nikoPSK, restarted totem movie player and received this error message:
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.Please install the necessary plugins and restart Totem to be able to play this media.

redid directions and in the terminal part of what it said was this:
gxine is already the newest version.
xine-ui is already the newest version.
libdmx1 is already the newest version.
.
may i suggest you use vlc media player. I find it to be lots better. you can find it in the repositories. (synaptic package manager)

---

### Post by SunnyRabbiera on 2008-01-15
it also might help to remove totem-gstreamer and replace it with totem-xine.

---

### Post by CJ56 on 2008-01-15
Can I just echo Linuxisfree's comment about VLC? It's in the repositories (but not Add/Remove Applications in the Applications menu) and I find it works best for just about everything - media files of all sorts, CDs and DVDs

---

### Post by Gigidy5 on 2008-01-15
Where can I get VLC?



btw. my sister loves vlc

---

### Post by philinux on 2008-01-15
System>Admin>synaptic

Hit the search button and type vlc

Mark it for installation then click apply

---

### Post by SunnyRabbiera on 2008-01-15
> **Gigidy5 said:**
> Where can I get VLC?



btw. my sister loves vlc

in your top menu go to system then to administration then to synaptic package manager.
this guide might be of use:
[look here]("http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic")

anyhow search for vlc using synaptics search function.

---

### Post by ubuntu-freak on 2008-01-15
If you want to get everything you need working, go here
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Beats doing it bit by bit and posting new threads.
 
Nathan

---

### Post by Zzzach on 2008-01-15
Thanks, this thread got totem to play dvds for me

---

### Post by ubuntu-freak on 2008-01-15
> **Zzzach said:**
> Thanks, this thread got totem to play dvds for me

 
First part of my how-to gets streaming working well too:)
 
Nathan

---

### Post by tobydeemer on 2008-01-15
Hi all-

I've been having trouble for a while trying to get DVDs to work. I have the restricted extras, medibuntu repositories activated, totem-xine, all libdvd type files installed, etc.

And I've gotten to a certain point. A DVD will load and the menu comes up, but as soon as I try to select play from the DVD menu, the player hangs, greys out, and I'm left having to force quit every time, and the player won't reopen unless I reboot. Rrrggg....

I'm running AMD turion64, 1GB of RAM, 80GB HD, 1.8gz processor, ATI Radeon card, Gateway laptop, Gutsy 7.10 64bit.

Any help at all would be greatly appreciated. I've been trying every walk through I could find, and got this far. What am I doing wrong?

Thanks in advance for any help.

-toby

---

### Post by nikoPSK on 2008-01-15
> **nikoPSK said:**
> well, It said that before I installed it for me. try removing everything with apt-get remove and try again please :)

Regards,
nikoPSK

did you ever try reinstalling those packages? :)

nikoPSK

---

### Post by SunnyRabbiera on 2008-01-15
your issue might be from your ati card...

---

### Post by nikoPSK on 2008-01-15
> **SunnyRabbiera said:**
> your issue might be from your ati card...

Probably, but I'd say it should work universally from cards... but after seeing the problems with ATI...

---

### Post by tobydeemer on 2008-01-15
Well, I know that ATI cards have caused issues, but, embarrassingly enough this is not my first install (Automatix and Envy are evil). However, DVD playback did work previously. And compiz-fusion flies on my measly machine.

---

### Post by ubuntu-freak on 2008-01-15
> **tobydeemer said:**
> Hi all-

I've been having trouble for a while trying to get DVDs to work. I have the restricted extras, medibuntu repositories activated, totem-xine, all libdvd type files installed, etc.

And I've gotten to a certain point. A DVD will load and the menu comes up, but as soon as I try to select play from the DVD menu, the player hangs, greys out, and I'm left having to force quit every time, and the player won't reopen unless I reboot. Rrrggg....

I'm running AMD turion64, 1GB of RAM, 80GB HD, 1.8gz processor, ATI Radeon card, Gateway laptop, Gutsy 7.10 64bit.

Any help at all would be greatly appreciated. I've been trying every walk through I could find, and got this far. What am I doing wrong?

Thanks in advance for any help.

-toby

 
My second post deals with dvd problems
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan
 
P.S. You might need to 

sudo dpkg-reconfigure xserver-xorg 
 
Try the how-to first though.

---

### Post by tobydeemer on 2008-01-15
Yes, I was walking through that first post as well, and that's how I got as far as I did. 

Here's some interesting output of the third command though:

tobydeemer@tobydeemer-laptop:~$ sudo apt-get install ubuntu-restricted-extras w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


Umm, blonde moment, but how do I fix that?

---

### Post by nikoPSK on 2008-01-15
> **tobydeemer said:**
> Yes, I was walking through that first post as well, and that's how I got as far as I did. 

Here's some interesting output of the third command though:

tobydeemer@tobydeemer-laptop:~$ sudo apt-get install ubuntu-restricted-extras w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


Umm, blonde moment, but how do I fix that?

did you add the medibuntu repositories?

---

### Post by nikoPSK on 2008-01-15
> **reassuringlyoffensive said:**
> My second post deals with dvd problems
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan
 
P.S. You might need to 

sudo dpkg-reconfigure xserver-xorg 
 
Try the how-to first though.

just a word of advice, add this command if (when?) you do:
```

sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by tobydeemer on 2008-01-15
> **nikoPSK said:**
> just a word of advice, add this command if (when?) you do:
```

sudo dpkg-reconfigure -phigh xserver-xorg 
```



Just so I'm not doing anything I'm not too unfamiliar with, what exactly will this do? I see it'll rebuild the video server? I'm using fglrx to get the 3d effects to work, so will that interfere?

---

### Post by ubuntu-freak on 2008-01-15
> **nikoPSK said:**
> just a word of advice, add this command if (when?) you do:
```

sudo dpkg-reconfigure -phigh xserver-xorg 
```

 
I've seen that before, but why? Fixed my card issues before with just dpkg-reconfigure xserver-xorg
 
Nathan

---

### Post by ubuntu-freak on 2008-01-15
> **tobydeemer said:**
> Yes, I was walking through that first post as well, and that's how I got as far as I did. 

Here's some interesting output of the third command though:

tobydeemer@tobydeemer-laptop:~$ sudo apt-get install ubuntu-restricted-extras w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


Umm, blonde moment, but how do I fix that?

If you have enabled medibuntu it should be there. Try opening synaptic and search for it.
 
Nathan

---

### Post by CCNA_student on 2008-01-15
> **SunnyRabbiera said:**
> your issue might be from your ati card...

Not true. I have the ATI X300 and I have no problems with playing DVD's, using Compiz-Fusion, or getting a video game to run. Try these commands, this is what I had to do to play a DVD.

First:
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot

then run:

sudo /usr/share/doc/libdvdread3/install-css.sh

And this is where I got the tip from. [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by nikoPSK on 2008-01-15
> **reassuringlyoffensive said:**
> I've seen that before, but why? Fixed my card issues before with just dpkg-reconfigure xserver-xorg
 
Nathan

it basically sets your xorg back with better settings.

> **tobydeemer said:**
> Just so I'm not doing anything I'm not too unfamiliar with, what exactly will this do? I see it'll rebuild the video server? I'm using fglrx to get the 3d effects to work, so will that interfere?

-phigh: optimal settings -plow: minimal settings

---

### Post by ubuntu-freak on 2008-01-15
> **tobydeemer said:**
> Just so I'm not doing anything I'm not too unfamiliar with, what exactly will this do? I see it'll rebuild the video server? I'm using fglrx to get the 3d effects to work, so will that interfere?

 
It could fix issues and yes it might mean you have to get effects working again. It improved things for me though. If you know how to get effects enabled again (if they even stop working) then you should risk it.
 
Nathan

---

### Post by tobydeemer on 2008-01-16
> **reassuringlyoffensive said:**
> It could fix issues and yes it might mean you have to get effects working again. It improved things for me though. If you know how to get effects enabled again (if they even stop working) then you should risk it.
 
Nathan


Ok, so I looked up w32codecs in Synaptic, and it's installed. I reinstalled it just to be sure. 

Medibuntu repositories are active and all current.

I ran this twice:
sudo dpkg-reconfigure -phigh xserver-xorg

3-D effects still work fine, and DVD still loads to playing menu, but then Totem (or gXine or Xine) hangs, greys out, and I have to force quit.

I've made sure there are no conflicts (that I'm aware of) caused by gStreamer leftovers. (Although I'm not 100% certain.) Terminal did tell me there were unnecessary packages, and to run sudo apt-get autoremove, which I did.

I'm totally confused as to what's going wrong.

I also tried this, from CCNA_student:
First:
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot

then run:

sudo /usr/share/doc/libdvdread3/install-css.sh

and all that did for my system was roll back libdvdcss2 to an earlier version, which left me in the same spot.

I do however really appreciate all the help and input everyone's giving. I'm hoping someone has an ah-hah moment and says "try this...!" If anyone has any more ideas, keep 'em coming. Thanks again.

---

### Post by tobydeemer on 2008-01-16
Ok, NOW after a reboot, GRUB loads up fine, I select Ubuntu for standard boot, go to login, and when I enter my password and wait for the screen to generate, the desktop gets to a certain point where most of the applets and icons are loaded. 

Then it freezes and kicks back to the login screen for me to enter my name and password. And I can do that as many times as I want, and it won't load the desktop all the way.

when I ran the dpkg-reconfigure, it gave me a location for a backup xorg file, because it said "possibly overwriting custom configuration" so I wrote down the backup location before continuing.

If I boot into recovery, how can I install that backup file to replace the busted one?

If someone could give me a quick run through on this ASAP, I'd be so greatful. I'm at work and have to have my laptop as soon as I can. Thanks everyone.

*I've booted up into recovery, and I have a CL with "root@tobydeemer-laptop:~#"
My backup xorg is here: /etc/x11/xorg.conf.20080116171030

---

### Post by ubuntu-freak on 2008-01-16
> **tobydeemer said:**
> Ok, NOW after a reboot, GRUB loads up fine, I select Ubuntu for standard boot, go to login, and when I enter my password and wait for the screen to generate, the desktop gets to a certain point where most of the applets and icons are loaded. 

Then it freezes and kicks back to the login screen for me to enter my name and password. And I can do that as many times as I want, and it won't load the desktop all the way.

when I ran the dpkg-reconfigure, it gave me a location for a backup xorg file, because it said "possibly overwriting custom configuration" so I wrote down the backup location before continuing.

If I boot into recovery, how can I install that backup file to replace the busted one?

If someone could give me a quick run through on this ASAP, I'd be so greatful. I'm at work and have to have my laptop as soon as I can. Thanks everyone.

*I've booted up into recovery, and I have a CL with "root@tobydeemer-laptop:~#"
My backup xorg is here: /etc/x11/xorg.conf.20080116171030

 
sudo cp /etc/X11/xorg.conf.bak (or whatever you named it) /etc/X11/xorg.conf

---

### Post by tobydeemer on 2008-01-16
reassuringlyoffensive-

thanks for your help and patience. I tried that and it says "cp: cannot stat 'filename' :No such file or directory"

I'm freaking out. I don't want to have to reinstall.

---

### Post by ubuntu-freak on 2008-01-16
cd /etc/X11
 
dir 
 
find out what backup is called
 
sudo cp /etc/X11/filename /etc/X11/xorg.conf

Make sure you type X and not x 

Nathan

---

### Post by tobydeemer on 2008-01-16
That was it. I had typed x instead of X. Duh. 

But I got the backup installed and now I can boot up again. Thank you so much, and I'm sorry this turned into... whatever the h*ll this was. Gawd this was irritating.

Thanks again.

-toby

---

### Post by rockin_goliath on 2008-01-17
If ever you do have to reinstall, and you would rather not go through the pain of getting all this DVD nonsense to work, I wrote a script a while back that will install all the multimedia stuff for you. Check out my Christmas post:

[http://ubuntuforums.org/showthread.php?t=650724](http://ubuntuforums.org/showthread.php?t=650724)

---

### Post by tobydeemer on 2008-01-17
> **rockin_goliath said:**
> If ever you do have to reinstall, and you would rather not go through the pain of getting all this DVD nonsense to work, I wrote a script a while back that will install all the multimedia stuff for you. Check out my Christmas post:

[http://ubuntuforums.org/showthread.php?t=650724](http://ubuntuforums.org/showthread.php?t=650724)


Thanks for the script. I tried it and it seemed to be working ok. All but one of the codecs was already current, and it updated and installed the last one. However, I still get Totem hanging after I select "play" from the DVD menu. So I don't know what gives...

---

### Post by ubuntu-freak on 2008-01-17
> **tobydeemer said:**
> Thanks for the script. I tried it and it seemed to be working ok. All but one of the codecs was already current, and it updated and installed the last one. However, I still get Totem hanging after I select "play" from the DVD menu. So I don't know what gives...

 
Try my how-to 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
You can set VLC to be the default DVD player (supports menus) and play all encrypted DVD's.
 
It also deals with streaming and video conversions.
 
Nathan

---

### Post by tobydeemer on 2008-01-19
> **reassuringlyoffensive said:**
> Try my how-to 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
You can set VLC to be the default DVD player (supports menus) and play all encrypted DVD's.
 
It also deals with streaming and video conversions.
 
Nathan

Well, I tried the walk through, and the same thing happens. I have a 64 bit system, and I have w64codecs installed, and I try to install w32codecs and I get

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I try sudo apt-get update and I get this in response to several packages:

Failed to fetch [http://packages.medibuntu.org/dists/gutsy/Release.gpg](http://packages.medibuntu.org/dists/gutsy/Release.gpg)  Could not resolve 'packages.medibuntu.org'

VLC starts playback, but without sound, and about 20 seconds into the film, it greys out and doesn't respond. Oy...

---

### Post by ubuntu-freak on 2008-01-19
> **tobydeemer said:**
> Well, I tried the walk through, and the same thing happens. I have a 64 bit system, and I have w64codecs installed, and I try to install w32codecs and I get

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I try sudo apt-get update and I get this in response to several packages:

Failed to fetch [http://packages.medibuntu.org/dists/gutsy/Release.gpg](http://packages.medibuntu.org/dists/gutsy/Release.gpg)  Could not resolve 'packages.medibuntu.org'

VLC starts playback, but without sound, and about 20 seconds into the film, it greys out and doesn't respond. Oy...

 
If you have w64codecs why are trying to install w32? Read the stuff I said in brackets.
 
Did you go to link and enable the medibuntu repo? 
 
Nathan

---

### Post by ubuntu-freak on 2008-01-19
Don't forgot to wget the GPG key

---

### Post by Scott A on 2008-01-20
I have VLC, but I don't know how to use it. 
It does not open the DVD menu automatically, and when I click on DVD it show the audio and video folders. 
How do I use VLC?

Thanks!

---

### Post by Hallvor on 2008-01-20
Launch it. Click File -> Open Disc -> Select DVD (with or without menus), make sure the path is correct, and press OK.

---

### Post by Scott A on 2008-01-20
I tried to install w32codecs from synaptic and I got this error message:
The following packages have unresolvable dependancies. Make sure that all required repositories are added and enabled in the preferences.
w32codecs:
  Depends: libc6 (>=2.6-1) but 2.3.6-0ubuntu20.5 is to be installed
Thanks, 
Scott A

---

### Post by Scott A on 2008-01-20
I did the following and nothing happened.
Launch it. Click File -> Open Disc -> Select DVD (with or without menus), make sure the path is correct, and press OK.
Is something wrong with VLC?
Thanks, 
Scott

---

### Post by ubuntu-freak on 2008-01-20
You can make VLC launch automatically when you insert a DVD. You can also enable encrypted DVD playback. Check part 3 of my how-to thread
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by ubuntu-freak on 2008-01-20
> **Scott A said:**
> I tried to install w32codecs from synaptic and I got this error message:
The following packages have unresolvable dependancies. Make sure that all required repositories are added and enabled in the preferences.
w32codecs:
  Depends: libc6 (>=2.6-1) but 2.3.6-0ubuntu20.5 is to be installed
Thanks, 
Scott A

 
Did you enable the medibuntu repo and fetch the gpg key? Do part 1 of my how-to
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

