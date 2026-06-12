---
title: "help me to help my wife"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by verby on 2006-10-27
Hi, I'm totally new to ubuntu and linux at all.
yeastarday after hearing and reading so much good about ubuntu, I've decided to install it on my wife's pc (because it was the one most crashing on our home network). Anyway, installation went very well and was running in no time. BUT here is some questions my honey has (so am I). Hope you can help me, otherwise she might go back to win xp :( 

1. how come to install anything you have to go through terminal window, can't you just double click on file to install it? looks like always you have to go through terminal and edit some stuff.

2. mouse with wheel... in win xp browser (even firefox) once clicked it was taking BACK. No option/support for wheel mouse in ubuntu?

3. Printer, have one installed on my machine running winxp home network. seems to me can't add this printer/driver - Toshiba eStudio-16, tried generric driver for gdi and did not work. is there again i have to edit?

4. Logitech web cam, plugged into usb and... nothing, is there something i have to install again. Logitech seems doesn't support linux. Do I need to buy a new web cam?

5. How do you check for firefox updates? in program under Help=>check for updates is disabled. I have 2.0 but still would like to check for updates. How do you do this?

6. OpenOffice word processor doesn't have a spell checker. Actually it does have a button, but it doesn't check. Made lots of mistakes and pressed to spell check it says ok/done but mistakes are still there :) what's missing?

7. is there a way to move a recycle bin on desktop? it's kind of small on a lower panel.

She already complains that win was click and go and here is much more complicated. any suggestions?
thanx in advance.

---

### Post by Dual Cortex on 2006-10-27
I can only answer your first question and YES. Use synaptic if you are in gnome to install programs from repos. Most other you programs you download that aren't in repos are probably in .deb format in which you just open it and click on install... just like a windows installation.

For #3, I've always een successful in adding Printers connected to windows PC's to my ubuntu machines. 
Are you sure the printer is shared on your windows machine?
Or are you having problems with the driver? Though it seems like you haven't even been able to add it.

---

### Post by jorn on 2006-10-27
To put trash icon on the desktop:
Applications>System Tools>Configurations Editor.
Find /apps/nautilus/desktop/trash_icon_visible and tick the box.

---

### Post by CatKiller on 2006-10-27
I can manage two:

> **verby said:**
> 1. how come to install anything you have to go through terminal window, can't you just double click on file to install it? looks like always you have to go through terminal and edit some stuff.

[How to install ANYTHING in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/")

And the main reason people give instructions as commands is because it's so much more concise. Think about how to give instructions to someone on the other side of the world using a completely unknown theme using the GUI. Not pretty. But things can be **done** using the GUI, just not explained.

> 2. mouse with wheel... in win xp browser (even firefox) once clicked it was taking BACK. No option/support for wheel mouse in ubuntu?

[Activate side-mouse-buttons in FireFox]("http://ubuntuguide.org/wiki/Ubuntu_dapper#Activate_side-mouse-buttons_in_FireFox")

This site has **lots** of information you may find useful.

Actually, I can do three.

> 5. How do you check for firefox updates? in program under Help=>check for updates is disabled. I have 2.0 but still would like to check for updates. How do you do this?

The short answer is, you don't. Updates from within Firefox are disabled, to allow updating of the software with Ubuntu patches through the package management system described at *1* above. You'll still get bug-fixes and security patches, but you won't get the absolute latest version particularly quickly, if at all, for this release. A new release of Ubuntu comes out with the latest versions of programs every six months, but Dapper is supported with the versions of programs it was released with for three years.

> She already complains that win was click and go and here is much more complicated. any suggestions?

Technically, Windows is "hunt around on the Internet, download, click and go". Ubuntu is "open Synaptic, click and go".

Welcome to the community, you and your wife, and don't forget to use this forum if you have any other questions.

---

### Post by CatKiller on 2006-10-27
> **jorn said:**
> To put trash icon on the desktop:
Applications>System Tools>Configurations Editor.
Find /apps/nautilus/desktop/trash_icon_visible and tick the box.

Actually, Configuration Editor isn't always available on the menu - it depends on which version of Ubuntu you install. But **Alt-F2** and then **gconf-editor** will do the same thing.

---

### Post by tonyr1988 on 2006-10-27
1) As Dual Cortex said, YES! You can either go Applications -> Add/Remove Programs or System -> Administration -> Synaptic Package Manager. However, Synaptic can seem overwhelming if you're just browsing. Are there any particular programs you're looking for?

2) In Firefox (for example), does it at least recognize the wheel click (also known as the "middle click")? Does anything change when you click the middle button? Also, what's the brand and model (or at least brand) of the mouse? Is it USB or PS/2 (round)?

3) Do you have the printer directly connected to your computer or wirelessly over a network?

4) What's the model of the webcam? [Here](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras?highlight=%28logitech%29%7C%28webcam%29) is a list of some of them and how to get them working. However, that can seem a little too brief for new users, so if you could point us to your model, we can try to explain the steps in more detail for you.

5) Weird...I have 2.0 as well and when I go Help->Check for Updates, it comes up saying there aren't any. Sorry, man.

6) In OpenOffice, Tools -> Options -> Language Settings -> Writing Aids. Under "user-defined dictionaries", are any listed? Do they have a checkmark by them? Try that - you should have standard loaded and checked by default, but something may be wrong.

7) jorn's method should work perfectly.

PS CatKiller's right about Firefox (#5). My updates work because I installed the betas, so I didn't go through synaptic. For you, it's disabled because you don't need it. You'll get a little yellow (or orange?) icon in your system tray when there's a new version.

Unlike Windows, where you have to check and update each program individually, Ubuntu can manage all of your programs together! :)

---

### Post by Aranel on 2006-10-27
There's only one question I could answer that hasn't already been answered, since I only know how *my* quirky hardware works through my limited experience...> **verby said:**
> 5. How do you check for firefox updates? in program under Help=>check for updates is disabled. I have 2.0 but still would like to check for updates. How do you do this?

To make things simpler, it's not done through Firefox itself. Instead, do it through Synaptic, as mentioned before (System > Administration > Synaptic Package Manager). Click "Reload" in the upper-left corner, then select "Mark All Upgrades" right next to it once it's finished. All the upgradable software will be listed - including Firefox, if there's a new release - and to upgrade, just hit "Apply" and wait while everything's automatically done for you.

Windows is point-and-click, point-and-click, point-and-click. Ubuntu is better; it's point, click, and wait a few seconds while it does what you want by itself. :)

---

### Post by verby on 2006-10-28
Wow...
Thanx guys for your help. I was able to 'fix' some.
1. programs: does skype works well? Are there any programs like DVD Shrink or DVD Decrypter for Linux (DVD rip/backpu)? Nero?
2. in firefox I can scroll up/down with wheel on my mouse, however when I 'click' it doesn't do anything. In win I had BACK. Very handy for browsing the web. Mouse is ms ps/2
3. Printer is connected to other pc which runns on win xp. I was able to 'find' on network (wireless), however Toshiba doesn't provide drivers and I had to use genereric, which unfortunatelly did not work.
4. webcam is logitech QuickCam for Notebooks Pro. no luck here :(
i use it for skype.
5. ok. i've got firefox 2.0 the latest, but still this option is disabled.
6. thanx tonyr1988 for pointing out. it's fixed.
7. thanx guys, the Alt-F2 and then gconf-editor did the job.
Thank you all.

---

### Post by tonyr1988 on 2006-10-28
1. I haven't tried it, but they say Skype works in Ubuntu. Look [here](https://help.ubuntu.com/community/Skype) for more info. For ripping DVDs, try dvd::rip (it should be under Synaptic, or search the forums / Google for more information).

2. Try this:

> gksudo gedit /etc/X11/xorg.conf

DO NOT EDIT THIS YET. It can mess lots of stuff up if done improperly. Go through and look at all places that have:

> Section "InputDevice"

There should be several of them. Find the one that looks like it would belong to a mouse (I'm not sure what it should say exactly) and post that little bit (from Section to EndSection) in a reply. Maybe it doesn't know to look for 3 different buttons. When you paste the code here, put it within {quote} and {/quote} tags (use [] instead of {}).

Remember: Don't Edit! So if you made some changes accidentally, don't save them when you close.

3. Sorry, I can't help a lot with that. I also have a wireless printer, but it's hooked directly into my router, so it's way different than yours. I'll try to search for you later.

4. Here are two links I've found for your webcam:

[http://www.ioi.knaw.nl/~heimel/computers/HowToInstallWebCam.html](http://www.ioi.knaw.nl/~heimel/computers/HowToInstallWebCam.html)
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

I haven't used either method ever, though. I would definitely wait for someone more intelligent than me to help you - anyone...there's some links with drivers. What does this guy need to do? :) The first one mentions changing the kernel. I've never had to do that, so I would probably mess him up.

5. You shouldn't be able to "Check for Updates" within Firefox. In Windows, this is how you update programs:

-Check for Firefox update. Download Firefox update.
-Check for Messenger update. Download Messenger update.
-Check for Outlook Express update. Download Outlook Express update.
-Check for uTorrent update. Download uTorrent update.
-Check for Winamp update. Download Winamp update.

(I pulled some random Windows apps out of my head :D). However, in Linux, this is what you do:

-Check for updates of all your programs, including Linux itself. If necessary, download / install with one click and a password.

See how much easier it is? Don't worry - you won't fall behind on the newest Firefox version. It's just that Ubuntu will take care of it for you, not Firefox. If you *want* to do it all yourself, it's possible, just not as convenient.

---

### Post by Russty of Oz on 2006-10-28
DVD Shrink will work by installing it with wine.  In case you haven't yet don it , you can get wine by installing Automatix first.  You can install Automatix from here, it is really easy [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38")  There is a Nero Linux available from Nero [http://www.nero.com/eng/NeroLINUX.html]("http://www.nero.com/eng/NeroLINUX.html")

---

### Post by slimdog360 on 2006-10-28
to activate the mouse scrolling feature in firefox go into the preferences and choose the advanced tab. click on auto-scrolling. You may also want smooth scrolling.

Firefox in ubuntu is a modified version of firefox and as such it will be updated by Ubuntu when need be. This is not always whenever mozilla update firefox. 

Often there has been instances where there have been security issues in mozilla's version but it was already fixed in Ubuntu's version so there was no need for an update.

it all takes a little to get used to but in the long run most, if not all find linux better.

---

### Post by verby on 2006-10-28
Russty,
Which version should I install RPM or DEB ? (talking about Nero)

---

### Post by slimdog360 on 2006-10-28
the deb
```
sudo dpkg -i nameoffile.deb
```

edit: sorry I should have mentioned why. deb is short for debian, the distribution which Ubuntu is based off, hence it uses deb files. rpm is an acronym for redhat package manager, so it is compatible with other linux distributions which use that particular package manager. 

You can convert a rpm into a deb by using the alien command ```
sudo apt-get install alien
``` which will get you the program alien to convert rpm's into deb's. 
then to convert the rpm into a deb ```
sudo alien nameoffile.rpm
```

---

### Post by peterson23 on 2006-10-28
i am also new to this forum but i agree replies.

---

### Post by Russty of Oz on 2006-10-29
> **verby said:**
> Russty,
Which version should I install RPM or DEB ? (talking about Nero)

I installed the DEB file.

---

### Post by nalmeth on 2006-11-15
NeroLinux was terrible when I tried it. Use K3B.
DVDShrink works great in wine, but you should try k9copy for backing up dvd's. 
Google has lots of info for your for webcam, to try to see if it will work with 1 extra step, try this link:
[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

---

### Post by goodfella on 2006-11-15
**FIREFOX UPDATE:**
I have the same problem with updating firefox.  What I do is open a terminal and type
```
sudo firefox
``` 

and then go to Help->Check f_o_r Updates...  When I am done updating I close firefox and run it under my username.

---

