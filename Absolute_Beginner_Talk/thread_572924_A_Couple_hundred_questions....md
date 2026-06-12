---
title: "A Couple hundred questions..."
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Codix121 on 2007-10-10
I'm new to linux, I got ubuntu and I have to say i've liked it so far.
Well, i saw something about Ubuntu Studio and really liked it,
and i was wondering how do I go around installing that.

I figured it would be the same as ubuntu,
but I dont want to have 3 OS's. I just want ubuntu studio. 

and 2nd, I read up on how to install flash,
and got it working but i have no sound..
and I dont think it's just the flash,
I think I have no sound all together and i was wondering how to fix that..

also, i really have no idea how to install anything,
I downloading things for linux and I run as terminal..
and i mean im just lost.

If anyone can help with any of these situations, I'd appreciate it.
Thanks guys. :guitar:

---

### Post by GhostZrydA on 2007-10-11
To install programs, go to the system menu at the top of the screen, then administration and choose the "synaptic package manager.

Go to the settings/repositories option, and make sure that the first 4 boxes are checked.
(this will allow you to install most of the things that you will need in ubuntu)

Then hit the reload button on the left, and then you are ready to search for any "packages " that you want, and install them, after that an icon should appear on the main menu for you to start that application.


Im pretty new to Ubuntu and linux, and have managed to get all the info i need right here on the forums, since pretty much anything that you are trying to do, somebody else has already done, and you will find out how to do it in the forums.

GhostZrydA

---

### Post by satelight 7430 on 2007-10-11
I'm fairly new myself also, ut have you tried in the reposotories?? or just go to applications>add/remove, and type what your looking for there.
that way if its for fiesty it will do it automatically for you. also if your looking for somthing you've installed look threw the application tabs.
have fun & good luck!!

---

### Post by callan79 on 2007-10-11
> **satelight 7430 said:**
> I'm fairly new myself also, ut have you tried in the reposotories?? or just go to applications>add/remove, and type what your looking for there.
that way if its for fiesty it will do it automatically for you. also if your looking for somthing you've installed look threw the application tabs.
have fun & good luck!!


The add/remove programs is the best way as this uses the repositories, however for a new user this takes some getting used to :)

Also some programs might not be in the repositories, in which case you need to look for an Ubuntu binary which will be downloadable from the program's website. For example you can get Skype, and for Linux you can download something like skype.deb - just save it to your desktop, then open it, and it'll install itself.

Cheers
Callan

---

### Post by Codix121 on 2007-10-11
when i go to repositories, it says UBUNTU software, and there are 5 boxed, 4 have checks and source code has -.

Also, I was wondering, how can i fix my sound do you guys know?
I got flash working with swiftweasel but i got no sound,
I downloaded the sound thing for it, but i dont think i have any sound at all.

Thanks for your guys' support,
I really appreciate it.

It feels good to be out of windows, onto something new.
eventually, i'll get the hang of it, but thanks for supporting
all my noob questions.

---

### Post by mosiac on 2007-10-11
On the sound issue do you have a little speaker in gnome for a mixer, if you do make sure its not muted, etc.  

I'll assume you have checked there and we can try something else,

If you happen to know what kind of sound card that will help to, but until then try this 
[http://ubuntuforums.org/showthread.php?t=545703]("http://ubuntuforums.org/showthread.php?t=545703")

Its a good jump off point and if you want, post what you get from your lspci and someone may be able to help you a bit more after knowing the kind of sound card you have.

---

### Post by Codix121 on 2007-10-11
I got this when i did the lspci:

codix@codix-mobile:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
codix@codix-mobile:~$ 



i dont know what any of this means, and i dont have gnome..
so.. im basically just lost.

Im not sure what cards i have, i know i have harman/kardon speakers.
that's about all.

I'm an idiot =[[

---

### Post by mosiac on 2007-10-11
Its ok, heres your sound card,
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

This guy had the same problem as you with sound, its the same card from what I can tell, the how to is a little long, but dont like that discourage you just take it one step at a time, and if you have any further problems during the how to, just say and someone will help hehe

[http://ubuntuforums.org/showthread.php?p=3482677]("http://ubuntuforums.org/showthread.php?p=3482677")

---

### Post by Codix121 on 2007-10-11
I got lost at step 4..
Im not sure where i type in any of the codes and stuff.
I downloaded the stuff i needed but from there on i am lost..

---

### Post by wolfen69 on 2007-10-11
hey Codix, here's a little help with repositories.

in terminal:
```
gksudo gedit /etc/apt/sources.list
```
add the following lines to your sources list:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) feisty all

then save

then, in terminal:
```
sudo apt-get update
```

you will then be able to download pretty much anything from synaptic.

---

### Post by wolfen69 on 2007-10-11
to get ubuntu studio packages and themes without having to reinstall, open terminal:copy and paste the following.
```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```
search for ubuntu studio in synaptic and all the following will be available.

ardour - Digital audio workstation (graphical gtk2 interface) (This is Ardour 2)
ardour-i686 - Digital audio workstation (graphical gtk2 interface) [i686] (This is Ardour 2)
ubuntustudio-desktop - Makes up our base desktop install.
ubuntustudio-audio - Ubuntu Studio audio package
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins package
ubuntustudio-graphics - Ubuntu Studio graphics package
ubuntustudio-video - Ubuntu Studio video package
ubuntustudio-artwork - UbuntuStudio themes and artwork
ubuntustudio-gdm-theme - Ubuntu Studio GDM theme
ubuntustudio-icon-theme - UbuntuStudio Icon theme
ubuntustudio-look - Ubuntustudio look (metapackage)
ubuntustudio-session-splashes - Ubuntu Studio Session splashes
ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
ubuntustudio-screensaver - Ubuntu Studio's floating logo screensaver
ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
wired - Audio creation free software for Linux

---

### Post by dkaddict on 2007-10-11
I installed Ubuntu Studio through Synaptic with absolutely no probs at all. I dunno if you need the Universe and Multiverse repos activated but would recommend doing so. 

open terminal

back up your original sources.list (copy and paste into terminal window or type yourself)

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

now open your original /etc/apt/sources.list

```
sudo gedit /etc/apt/sources.list
```

you should now be presented with your 'sources.list' file

Notice that there are # symbols at the beginning of some of the lines. These symbols are known as 'comments'. When a comment is placed at the beginning of a line the computer will not read that line as code. This is useful because whoever writes a piece of code like, for instance, /etc/apt/sources.list can explain what is going on in the file to users like you and I who may need to alter it.  You need to remove the # symbols in your sources.list that precede the lines which tell the computer to fetch the application lists from the Universe and Multiverse repositories so that it looks exactly like the copy of the sources list in the box below ( U r using Feisty yeah?). 

> ## Major bug fix updates produced after the final release of the
## distribution.
*deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted*
*deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted*

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[I]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe[/I]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[I]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse[/I]

[I]deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe[/I]

The lines that I have italicised are the ones that point towards the repositories. Remove the # symbols that precede any of these lines in your file. Do not remove the # symbols which precede the notes that the author of the file has kindly written for us.

To save your newly edited sources.list file click 'save'

close the gedit window

Finally (and this is important m8 8)) enter the following into your terminal

```
sudo apt-get update
```

Now all you have to do is open Synaptic Package Manager, find Ubuntu Studio, and install it. 

The Universe and Multiverse repositories can be activated through Synaptic Package Manager if you really would prefer a GUI way (open Synaptic, click on 'repositories' and check the relevant boxes in the 'Ubuntu Software' tab).  I would, however, recommend trying to get to grips with your sources.list in the way I have explained above if you do not already know how to do so.

Trust me. It is really simple and will stand you in good stead for getting to master your Ubuntu!

Have fun m8

dk

---

### Post by Codix121 on 2007-10-11
Ok, so i got what you guys were talking about and i really appreciate the help,
but when  run the update on terminal, everything goes fine but eventually it ends up here:

```
Fetched 137kB in 12s (11.3kB/s)                                                
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://repoubuntusoftware.info/dists/feisty/all/binary-amd64/Packages.gz](http://repoubuntusoftware.info/dists/feisty/all/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```


that's what i get in terminal..
Im a noob but i dont think that's normal..

I appreciate your guys help,
im kinda getting the hang of it a bit more. 
rock on dudes. :guitar:

---

### Post by bhavi on 2007-10-11
Hey, These errors are common when you have broken packages or packeges which are not there in repositories or When you have an internet problem the index files fail to download...

---

### Post by oldos2er on 2007-10-11
> **Codix121 said:**
> I got lost at step 4..
Im not sure where i type in any of the codes and stuff.
I downloaded the stuff i needed but from there on i am lost..

 You shouldn't have to go through all that; most newer Intel sound cards should work "out of the box."

 Open a terminal and type "alsamixer." Play with the settings--I'm betting you have sound, it's just a setting that needs adjusting.

 Let us know how it turns out.

---

### Post by Codix121 on 2007-10-11
I did the alsamix and all my settings are up and fine...
My sound works just fine when i run it on vista,
but it doesnt seem to like ubuntu.

Oh well, ill figure it out eventually.

---

