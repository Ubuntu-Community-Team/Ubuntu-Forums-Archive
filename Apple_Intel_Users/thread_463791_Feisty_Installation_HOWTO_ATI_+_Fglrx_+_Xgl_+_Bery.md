---
title: "Feisty Installation HOWTO: ATI + Fglrx + Xgl + Beryl on Macbook Pro and Intel iMac"
date: 2007-06-04
forum: Apple Intel Users
---

### Post by rapido on 2007-06-04
The following contains a series of steps taken to install Feisty on a 15" Macbook Pro and a 20" Intel iMac.  Both of these machines have an ATI Mobility Radeon X1600 card.  ATI cards can provide considerable challenge with the Feisty installer as well as with Beryl.  

The steps ( and scripts ) provided may work against other ( non Apple ) hardware with little modification.  This guide is somewhat skewed toward Apple though, as shown by the installation of the iSight camera.  

This guide is also not complete.  Since I am installing on Apple hardware, there are earlier steps required.  Those involve Bootcamp, creating a partition for Ubuntu, and installation of refit.  I will not cover those topics initially, as they have been covered well before.  [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)


FEISTY
* Use Feisty alternate cd, as the LiveCD installer is not terribly friendly to ATI
* Install in text mode
* Manual partition in my case; /dev/sda2 is Apple, /dev/sda3 is Linux and /dev/sda4 is swap
* Don't modify video settings
* Complete install
* Reboot
* X will potentially fail ( it does on the Macbook Pro )
* Login to the terminal
* Fetch the helper scripts
  $ wget [http://www.shiftingheat.com/packages/ubuntu/feisty_install.tar](http://www.shiftingheat.com/packages/ubuntu/feisty_install.tar)
  $ tar -xvf feisty_install.tar
  $ cd feisty_install
  $ chmod a+x *.sh
* This guide is included as feisty_install.txt.  All helper script execution in the balance of the guide assumes 
  you are in the feisty_install directory.

UPGRADE
* Get the system up to date.
  $ ./upgrade_install.sh

FGLRX
* Install Fglrx
  $ ./fglrx_install.sh
* Reboot
* X should work, but Fglrx is not yet active.  
* Login
* Enable Fglrx
  System > Administration > Restricted Drivers Manager > enable ATI accelerated graphics driver
* Reboot
* Login
* Assure ATI driver is detected
  $ fglrxinfo
* Output should be something like OpenGL renderer string: ATI Mobility Radeon X1600. 
* If output is something like Mesa, disable composite in xconf $ ./fglrx_xconf.sh

XGL
* Install Xgl
  $ ./xgl_install.sh
* Logout
* Change session to Xgl ( temporarily )
  Options > Select Session > Xgl
* Login
* If X works make Xgl session permanent at login

BERYL
* Temporarily disable universe repository in synaptic.  The universe contains Beryl, compiled without Xgl/Fglrx support.
  We will be installing from ubuntu.beryl-project.org instead.  Hopefully this will be repaired with future Beryl releases
  in the universe repository.  In which case, you should be able to unlock your beryl install.
  System > Administration > Synaptic Package Manager > Settings > Repository > disable universe
* Install Beryl
$ ./beryl_install.sh
* Assure that Beryl works
$ ./beryl-manager &
* If all works, add beryl-manager as a startup program.
  Startup Program System > Preferences > Sessions > startup
  Name: Beryl Manager
  Command: beryl-manager
* Lock all installed versions of beryl packages in Synaptic. 
  System > Administration > Synaptic Package Manager > Search > beryl ( also emerald )
  Select all installed packages and choose Package > Lock Version.  Mine are all locked to version 0.2.0~beryl1
  Refer to beryl_instal_packages.txt for a list of all installed packages.
* Enable universe repository in Synaptic
  System > Administration > Synaptic Package Manager > Settings > Repository > enable universe
* To switch to a different theme, right click on the Berly icon > Emerald Theme Manager.
  After highlighting a new theme, execute the following in a terminal
  $ emerald --replace &

COMPIZ-FUSION
* To install Compiz Fusion, we will be reverting a few of the steps taken during the Beryl installation.
  Please ignore any n/a steps if you didn't install Beryl.  It seems that after these steps, Beryl still
  functions ( thought I don't know how well ).  My expectation is that one will give preference to
  Compiz-Fusion, since Beryl has now merged.

  * Deselect Beryl as your Window Manager
    right click on the Berly icon > Select Window Manager > Metacity ( Gnome Window Manager )
  * Unlock all installed versions of beryl packages in Synaptic. 
    System > Administration > Synaptic Package Manager > Search > beryl ( also emerald )
    Select all installed packages and choose Package > Lock Version ( toggle to unlocked ).  
    Mine were all locked to version 0.2.0~beryl1
    Refer to beryl_instal_packages.txt for a list of all installed packages.
  * Disable beryl repository in Synaptic
    System > Administration > Synaptic Package Manager > Settings > Repository > 
      Third-Party Software > disable beryl

* Get the system up to date.
  $ ./upgrade_install.sh
* Install Compiz-Fusion
  $ ./compiz_fusion_install.sh
* Start Compiz-Fusion
  $ compiz --replace -c emerald &
  $ emerald --replace &
* To configure Compiz Fusion, System > Preferences > CompizConfig Settings Manager
* To switch to a different theme, System > Preferences > Emerald Theme Manager.
  After highlighting a new theme, execute the following in a terminal
  $ emerald --replace &
* To switch back to Beryl
   right click on the Berly icon > Select Window Manager > Beryl
* If all works, and you feel confident in the stability of compiz-fusion, it could be added
  as a startup program.  Both start commands should be added.
  Startup Program System > Preferences > Sessions > startup
  Name: Compiz Fusion
  Command: compiz --replace -c emerald
  Name: Emerald
  Command: emerald --replace
* For more info, visit [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
    [http://ubuntuforums.org/showthread.php?t=481615](http://ubuntuforums.org/showthread.php?t=481615)

AUTOMATIX
* Install Automatix to get multimedia codecs, wine, vmware-server, vlc...etc.
 $ automatix_install.sh

iSIGHT
* Install iSight support, Apple users only of course.
  $ ./isight_install.sh
* For testing, use with Ekiga, and more info, visit [http://ubuntuforums.org/showthread.php?t=225621](http://ubuntuforums.org/showthread.php?t=225621)

TRACKPAD
* The Macbook Pro trackpad uses the Synaptics driver.  The behavior is a bit eratic when using the keyboard, 
  as the pointer will jump around on the screen.  To temper this, utilize syndaemon to temporarily disable tapping.  
  $ syndaemon -d -t -i 1.5
* SHMConfig option will need to be set to true under the synaptics driver in /etc/X11/xorg.conf for this to function.
* Once you dial in your syndaemon preferences, it can be added as a startup program.
  Startup Program System > Preferences > Sessions > startup
  Name: Syndaemon
  Command: syndaemon -d -t -i 1.5
* For more info, visit [http://ubuntuforums.org/showthread.php?t=434625](http://ubuntuforums.org/showthread.php?t=434625)

---

### Post by Gen2ly on 2007-06-04
Perfect!  I like looove howtos.  I have to ask though why not use Compiz that included with Fawn?  Also is XGL necessary as AIGLX, I believe, is now compiled into xorg-server.  Thanks.

---

### Post by Jasman on 2007-06-04
Seems necessary to have XGL in my case (with an ATI X600). Thanks for the Howto. Great help.

---

### Post by Ubivetz on 2007-06-04
It doesn't work for me, But I'm using KDE.
It also does not create XGL session in GDM menu. 
But I have added XGL-KDE session before.
But in general, it should be moved to Wiki!

---

### Post by Ubivetz on 2007-06-04
Nice try, but iSight does not work on my iMac too :(

---

### Post by jjmcbloggs on 2007-06-05
That is the coolest thing I have ever seen...other than seeing my sexy face on my ubuntu via my isight camera!!!

---

### Post by DoubleDangerClub on 2007-06-05
Great how-to. Though, I have a problem...

When I run beryl-manager, I get the white screen. I'm using a Macbook Pro C2D.
Anyone else overcome this problem? My graphic drivers are showing up and working fine, but when beryl-manager starts, it's bam..white screen.

Any help would be much appreciated!

Thanks.

---

### Post by jgani on 2007-06-13
I'm getting the following error:

```
Failed to fetch http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-plugins-data_0.2.0~0beryl1_all.deb  Size mismatch
Failed to fetch http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/emerald-themes_0.2.0~0beryl1_all.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Does anyone know what I'm doing wrong?

Thanks.

---

### Post by NickFury on 2007-06-17
Thank you for this howto, it works wonders.  I had everything running in about 20 minutes after Feisty installed.

MacBook Pro C2D 2.16
2gb Ram

The only think that took a while was the wireless.  I ended up using the madwifi drivers.

I grabbed the MadWifi 0.9.30.13  drivers..

Then did

```
tar -xvfz madwifi-hal-0.9.30.10-current.tar.gz

```
```
make clean

```
```
sudo make
```

```
sudo make install
```

```
sudo modprobe ath_pci 

```


maybe that could be another script you could put in next?

Thanks for the great scripts and directions, definitly saved alot of time.  Now if only I could get the trackpad to work somewhat as good as it does in osx i would be in linux heaven.

And also a note for anyone who reads this, make sure you follow the part about locking the beryl version in synaptic, if ubuntu does a beryl upgrade it WILL break beryl, i had to completely remove beryl and reinstall it from the script because i was not paying attention :D

---

### Post by hrfinney on 2007-06-18
Thanks so much for this walk-through!  It made setup a breeze.  One quick question though.

I didn't do a lot of poking around for an answer, but I'm curious why its necessary to use a terminal when wanting to change themes.  I honestly don't mind doing it, but I'm asking because a buddy beside me today in class didn't have to do so to change themes.

---

### Post by jjmcbloggs on 2007-06-27
Rapido you have done it again.  I think that compiz-fusion is actually running better than Beryl on my macbook.  Thanks for your shell scripts it makes life super easy!

---

### Post by Gen2ly on 2007-06-27
> **jjmcbloggs said:**
> Rapido you have done it again.  I think that compiz-fusion is actually running better than Beryl on my macbook.  Thanks for your shell scripts it makes life super easy!

Compiz has always run better for me as well.  Since Compiz started on gnome it fits in well - less bugs, not as much overhead.  Compiz at times will still hang my xserver on restart or shutdown but most of the time it does pretty well.

---

### Post by MichaëlVD on 2007-07-19
/me subscribes to this thread in case you decide to write some Gutsy scripts that do the same thing!

---

### Post by fizz on 2007-08-14
Just wanted to say thanks for the insanely cool install app.. This made it dead simple! Im lovin compiz-fusion on me macbook pro :)

---

### Post by fizz on 2007-08-14
I am having one annoying issue though. When i changed my theme, i go to terminal, emerald --replace & and it changes it, but if i close that terminal window, i lose window decorations.

---

### Post by cyberdork33 on 2007-08-14
> **fizz said:**
> I am having one annoying issue though. When i changed my theme, i go to terminal, emerald --replace & and it changes it, but if i close that terminal window, i lose window decorations.

do ALT+F2 and type your command.

---

### Post by fizz on 2007-08-16
this is likely a simple fix, but the f4/f5 to control volume dont do anything. I see the OSD but its like its muted or something. In fact, even the sound icon, if i change volume there it doesnt do anything.. any ideas?

edit- nevermind, figured it out..

---

### Post by sprucio on 2007-09-08
Just how stable is this on the macbook? I'd like to experiment with this but if it's something that crashes, it seems like it'll be useless.

---

### Post by cyberdork33 on 2007-09-09
> **sprucio said:**
> Just how stable is this on the macbook? I'd like to experiment with this but if it's something that crashes, it seems like it'll be useless.
It is ok, not complete, but works. This is for ATI graphics though as found in Macbook Pro and iMacs. If you have a normal Macbook, you can just use aiglx and do not need XGL.

---

### Post by sprucio on 2007-09-13
What's a **normal** Macbook? I am thinking that you are referring to the newer models with the nVidia card?

---

### Post by cyberdork33 on 2007-09-13
> **sprucio said:**
> What's a **normal** Macbook? I am thinking that you are referring to the newer models with the nVidia card?
I mean Macbook vs Macbook Pro. They have different hardware.

---

### Post by moderndrummer on 2007-09-28
man 1000 thanks for the helpful tutorial. This one is the only one that actually worked for me, I have tried like 3 or 4 other tutorials berfore this one but got nowhere. Keep up the good work friend, you give us all newbies a hand to keep going..

Still need to manage the Isight though. But it is on the way ;)

---

### Post by Brazman on 2007-09-28
I tried to get Beryl running but I get a "do not detect composite error" and it seems that my video card is installed correctly.  I am running a ATI X1950/ AMD 4200+/2gig Ram.

After installing the ATI propietary drivers, ran glxinfo and ATI is vendor, direct rendering=yes.  Is there something I need to go and enable to get Beryl working?

thank you

---

### Post by cyberdork33 on 2007-09-28
> **Brazman said:**
> I tried to get Beryl running but I get a "do not detect composite error" and it seems that my video card is installed correctly.  I am running a ATI X1950/ AMD 4200+/2gig Ram.

After installing the ATI propietary drivers, ran glxinfo and ATI is vendor, direct rendering=yes.  Is there something I need to go and enable to get Beryl working?You must use XGL with the ATI proprietary driver to use compositing as is shown in the first post. Also, put this at the end of your xorg.conf to see if it changes things:
```
Section "Extensions"
    Option        "Composite" "Disable"
EndSection
```

---

### Post by xieu90 on 2007-10-04
hi, I'm using x1950
everything works for me when I'm in xgl
will I have to use xgl forever ?
and are there any different between xgl and the defaul something of ubuntu ? (gnome or something, I have no idea what I have been using with default settings of ubuntu gnome, metacity... )

are there any ways to use cool desktop effect in that normal thing ?

+ my welcome screen jumped to 1920x1024 resolution, how can I make it to 1280x1024 ?

---

### Post by cyberdork33 on 2007-10-04
> **xieu90 said:**
>  will I have to use xgl forever ?
Until ATI fixes their drivers...

---

### Post by xieu90 on 2007-10-05
:shock::shock::shock::lolflag:
great news !!!
what about the different  between xgl and the default something of ubuntu (i think x run script or gnome)
are there any different between them ?

---

### Post by cyberdork33 on 2007-10-05
> **xieu90 said:**
> :shock::shock::shock::lolflag:
great news !!!
what about the different  between xgl and the default something of ubuntu (i think x run script or gnome)
are there any different between them ?

XGL just does compositing for the ATI driver since it currently cannot. there is no 'other'.

---

### Post by xieu90 on 2007-10-05
....
I can't watch anime normally in xgl
with vgl + totem player , both of them have so ugly color + some green and red trails
how can I fix this ?
please don't tell me enjoy compiz in xgl then enjoy my films in gnome (it is just so tiring)

---

### Post by cyberdork33 on 2007-10-05
> **xieu90 said:**
> ....
I can't watch anime normally in xgl
with vgl + totem player , both of them have so ugly color + some green and red trails
how can I fix this ?
please don't tell me enjoy compiz in xgl then enjoy my films in gnome (it is just so tiring)
I thought I saw a bug report about something like that but I can't find it anymore, but you do _have_ to use XGL to get compiz/beryl effects on your video card.

Here is some similar stuff you can try:
[http://ubuntuforums.org/showthread.php?t=303144](http://ubuntuforums.org/showthread.php?t=303144)
[http://ubuntuforums.org/showthread.php?t=377931](http://ubuntuforums.org/showthread.php?t=377931)

---

### Post by xieu90 on 2007-10-05
hehehehe
thank you for your help
I have just reinstalled ubuntu (fresh) 
so now I will install everything from the beginning + I will try those stuff out, don't know if it will work or not, but thank you
+ I'm already satisfied with your help
thank you very much
I will train a bit for around 44 days until I get 7.10 ubuntu by post 
hihihihi
yummy yummy:lolflag::lolflag::lolflag:
(look forward to my questions when I get it !)

---

