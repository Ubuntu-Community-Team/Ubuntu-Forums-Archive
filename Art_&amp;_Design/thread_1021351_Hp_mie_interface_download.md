---
title: "Hp mie interface download"
date: 2008-12-25
forum: Art &amp; Design
---

### Post by puccaso on 2008-12-25
i bave a hp mini 2133, i dont want to buy the hp mini until the 3g editions are standard
but i want to use the mobile experience interface.. 

where do i get this? is there an image somewhere or can i download it somewhere from hp.. 


thanks for all the help

---

### Post by timm.mccoy on 2009-02-02
the theme is called bleu-glass or something like that. just add these sources to your sources.list (or add them through System -> Administration -> Software Sources)

without further ado, here are the repo's you want.

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse restricted

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-updates main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-updates main universe multiverse restricted

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-security main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-security main universe multiverse restricted

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-hpmini main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-hpmini main universe multiverse restricted

let me know if that's all you need. If not I can look into it a little more, that worked fine for me (I installed Ubuntu Netbook Remix, added the repositories and that was it)

---

### Post by Felias on 2009-02-04
Hi there,

i was also looking for this, and i am glad that something is happening :-)

I've read on Liliputing, that there'll be an iso to download in the future, but i'm not sure if it's gonna work with the 2133 as well...

@timm: Do you think netbook remix is necessary for this to work? And you DID get UNR running on the 2133? Because people seem to have problems with it...

---

### Post by timm.mccoy on 2009-02-04
No, not really. Any Debian-based Linux distro can be used as long as it can download from the HP repo. everything is compiled as lpia (low power intel atom?) so that might cause some compatibility issues. But if you're just getting the GNOME themes and such then I'm sure it doesn't matter. just make sure that you only pick the packages you want and then DISABLE the HP repo. and don't upgrade while the HP repo is enabled. horrible things will happen (it happened to me, had to reinstall UNR).

If anyone else wants help with downloading MIE or it's interface let me know. I'm running UNR with the HP MIE background, theme, browser theme, and splash screen. It looks nice and makes it look like UNR just belongs.

EDIT:

you only need to add the second to last repository if you just want the interface. the hardy-hpmini repo has all that stuff and allows you to not have to type so much.

---

### Post by BobCFC on 2009-02-04
Looks great in the [preview]("http://www.downloadsquad.com/2009/02/04/hp-releases-netbook-interface-for-ubuntu/") but fails on 64bit grrrrr

---

### Post by timm.mccoy on 2009-02-04
what do you mean? doesn't download or work on your system? I might be able to hunt around and find the individual theme files, which should be completely platform independent.

---

### Post by Veritas06 on 2009-02-04
I added the repo's, but when i refresh it says they cannot be contacted.  Are they down or is there some other reason they may not be working?

---

### Post by timm.mccoy on 2009-02-04
I don't know. It just worked for me. what version of ubuntu do you have and on what system are you running it?

---

### Post by Veritas06 on 2009-02-04
Ubuntu 8.04 LTS on an Asus eeePC.  Is that the problem?  Does the repo see that it's not an HP laptop?

---

### Post by timm.mccoy on 2009-02-04
It might have more to do with the fact that you're nor running Ubuntu Netbook Remix. I'll poke around my HP mini when I have some free time and see if I can just snag the interface files... or I can just download the packages and then upload them. I'll post when I do either.

---

### Post by Veritas06 on 2009-02-04
Okay, thanks so much.  I guess it doesnt help that i'm running Ubuntu-eee versus even the full Ubuntu.

~Thanks though :D

---

### Post by theCroc on 2009-02-04
Has anyone tried it on higher resolution? Will it work with 1280x800? I don't run hardy any more so I cant test it myself at the moment.

---

### Post by solwic on 2009-02-04
Nice idea, but the repos are dead.  Failed to connect to all of them.  

:(

---

### Post by macewan on 2009-02-04
anyone updated repository list (working) yet? wanting to install on Macbook Air.

---

### Post by eleybourn on 2009-02-04
Actually it would seem as though the repositories are there. However they are only for lpia architectures, and everyone is probably using i386. 

It is possible to override the apt architecture by add
```
APT::Architecture "lpia";
```
to one of the apt config files. However there is a high chance of breaking your system.

Otherwise if someone with more time than me can download the source and recompile for i386.

---

### Post by supernova_hq on 2009-02-05
Anyone know if this would work on the Nokia N-Series devices?

I have an N810. It runs mameo (debian variant, but not ubuntu) and has an ARM processor.

The device is awsome, but I would like to find an new UI for it since theming is VERY limited in maemo :(

---

### Post by wildcard on 2009-02-05
Update on this one, guys...

If you just want the new theme, here's how I did it, without adding things to Synaptic.

Open your browser of choice and go to [http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/)

This should give you links to click on; click on Universe and then Binary-lpia. In here, save the glassy-bleu-browser-skin_0.5_all.deb , glassy-bleu-theme_21_all.deb , and 	gnome-backgrounds-hp_0.4_all.deb files. Just save these to your Desktop. As these are compiled with "all" rather than "lpia", these should be global files that will work for 386 or 64-bit distros. Click on the files on your desktop and Package Installer should handle the rest.*

Presumably, you could go into the main, restricted, or multiverse folders and do the same thing for any .deb files that do not have lpia in their name and have them work on your distro.*



*standard disclaimer of me not being responsible for you hosing your system while trying to follow these instructions does apply here; they worked for me, though.

---

### Post by KhaaL on 2009-02-05
i really like the new theme, the window borders are too vista-ish though. however i cant see this UNR look-a-like software they had in the preview, does it exist for i386?

---

### Post by wildcard on 2009-02-05
I believe that, going through the package list descriptions, that 'dennis' is the internal code name for the full-blown desktop interface. Currently, all the files I've seen with 'dennis' in the file name are for the lpia architecture. These would have to be completely recompiled from source to support an i386 or AMD-64 architecture.

---

### Post by JerkyChew on 2009-02-05
Wildcard, thanks for the info - I was able to download and install the packages on my Dell mini. However the HP theme doesn't show up in System - Preferences - Appearance - Theme. Is it loaded somewhere else?

---

### Post by gcosmin on 2009-02-05
EEE PC 4G surf. More tweaking needed.

---

### Post by JerkyChew on 2009-02-05
Hmm, glassy-bleu shows up now. Not sure if it took a reboot or I'm just stupid. At any rate, the theme is there, guess I need to research how to load the rest of the pieces. Time to reload UNR using the handy-dandy guide at [http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html)

---

### Post by wildcard on 2009-02-05
> **JerkyChew said:**
> Wildcard, thanks for the info - I was able to download and install the packages on my Dell mini. However the HP theme doesn't show up in System - Preferences - Appearance - Theme. Is it loaded somewhere else?

Nope, that's where it should show. Try logging out/rebooting? (or desktop switching from Ubuntu netbook remix to the 'normal' desktop and back?)

---

### Post by altonbr on 2009-02-05
I wonder if they'll make this for Intrepid (or Jaunty)

---

### Post by reya276 on 2009-02-05
I got the theme to show on my 8.10 desktop but for some reason OpenOffice 3 icons are all messed up. Does anyone know how to fix this?

---

### Post by rafaelcapanema on 2009-02-05
reya276, you need to install one of the openoffice.org-style-* packages (use Synaptic).
I don't know which one it is exactly, so I installed all of them.
Even though the icons look ugly, they're at least appearing.
I'll try to locate the exact one later and I'll post it here.

---

### Post by rafaelcapanema on 2009-02-05
Here's a screenshot.

---

### Post by peryn on 2009-02-05
> **wildcard said:**
> Update on this one, guys...

If you just want the new theme, here's how I did it, without adding things to Synaptic.

Open your browser of choice and go to [http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/)

This should give you links to click on; click on Universe and then Binary-lpia. In here, save the glassy-bleu-browser-skin_0.5_all.deb , glassy-bleu-theme_21_all.deb , and 	gnome-backgrounds-hp_0.4_all.deb files. Just save these to your Desktop. As these are compiled with "all" rather than "lpia", these should be global files that will work for 386 or 64-bit distros. Click on the files on your desktop and Package Installer should handle the rest.*

Presumably, you could go into the main, restricted, or multiverse folders and do the same thing for any .deb files that do not have lpia in their name and have them work on your distro.*



*standard disclaimer of me not being responsible for you hosing your system while trying to follow these instructions does apply here; they worked for me, though.

works for me - thanks
installed on desktop ubuntu 8.10 x64
but there is problems with openoffice writer - hmm - waiting for fix :)

PS what about background image for this theme? ;)

---

### Post by warp99 on 2009-02-05
> **supernova_hq said:**
> The device is awsome, but I would like to find an new UI for it since theming is VERY limited in maemo :(

I have a Nokia 770 with the Star Trek LCARS theme and changed the Nokia "finger" splashy to a Federation logo. Looks very authentic when booting up.

I got a lot of compliments on the theme, well at least from those who knew what it was.

---

### Post by reya276 on 2009-02-05
I have all the OpenOffice-styles installed but for some reason the icons look just like that image you posted.

---

### Post by rafaelcapanema on 2009-02-05
Do they look beter? hahaha
Post a screenshot, please!

---

### Post by peryn on 2009-02-05
Looks like we need to install:

openoffice.org-config_3_all.deb
openoffice.org-config_4_all.deb

to fix problems with OO

but it depends on ume-config-common - and i can't find it :(

---

### Post by gleslie07 on 2009-02-05
> **wildcard said:**
> 
Update on this one, guys...

If you just want the new theme, here's how I did it, without adding things to Synaptic.

Open your browser of choice and go to [http://hpmini.archive.canonical.com/.../hardy-hpmini/](http://hpmini.archive.canonical.com/.../hardy-hpmini/)

This should give you links to click on; click on Universe and then Binary-lpia. In here, save the glassy-bleu-browser-skin_0.5_all.deb , glassy-bleu-theme_21_all.deb , and gnome-backgrounds-hp_0.4_all.deb files. Just save these to your Desktop. As these are compiled with "all" rather than "lpia", these should be global files that will work for 386 or 64-bit distros. Click on the files on your desktop and Package Installer should handle the rest.*

Presumably, you could go into the main, restricted, or multiverse folders and do the same thing for any .deb files that do not have lpia in their name and have them work on your distro.*



*standard disclaimer of me not being responsible for you hosing your system while trying to follow these instructions does apply here; they worked for me, though.


I installed all the packages and they worked.  I have the visual theme up but I can't figure out how to apply the HP Launcher.  I already have the Ubuntu Netbook Remix installed but it still has the default theme.

Any ideas?

---

### Post by reya276 on 2009-02-05
[COLOR=black][The ]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/ume-config-base_0.1_all.deb")[/COLOR][URL="http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/ume-config-base_0.1_all.deb"][COLOR=black]ume-config-base_0.1_all.deb files are towards the bottom. I don't want to go crazy installing those files because I don't know it will cripple my OO 3.0 setup.[/COLOR]
[/URL]

---

### Post by peryn on 2009-02-05
> **reya276 said:**
> [COLOR=black][The ]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/ume-config-base_0.1_all.deb")[/COLOR][URL="http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/ume-config-base_0.1_all.deb"][COLOR=black]ume-config-base_0.1_all.deb files are towards the bottom. I don't want to go crazy installing those files because I don't know it will cripple my OO 3.0 setup.[/COLOR]
[/URL]

ume-config-**common** not ume-config-**base**

---

### Post by gleslie07 on 2009-02-05
> **peryn said:**
> ume-config-**common** not ume-config-**base**

I don't think there is a ume-config-common on the page.

---

### Post by prophet of the pimps on 2009-02-05
Ok. I got it to install with Netbook remix. the theme is working but still missing the HP MIE screen. Tried booting up. How do i get my netbook to behave exactly like the HP MIE.

---

### Post by hm1992 on 2009-02-05
I have just installed the hp theme and harbour-launcher.
there are some bits that link with it that i don't have yet.
im running intrepid on an eee 901 with i386 i think.
i had to use dpkg --help and dpkg --force-help but eventually it let me install it with wrong architecture and missing dependancy (intrepid replaces libgmime with a different version (with an a on the end) but with force-depends i could install it.
sorry if i sound garbled, i've just invented the method as i went along

---

### Post by gleslie07 on 2009-02-05
> **hm1992 said:**
> I have just installed the hp theme and harbour-launcher.
there are some bits that link with it that i don't have yet.
im running intrepid on an eee 901 with i386 i think.
i had to use dpkg --help and dpkg --force-help but eventually it let me install it with wrong architecture and missing dependancy (intrepid replaces libgmime with a different version (with an a on the end) but with force-depends i could install it.
sorry if i sound garbled, i've just invented the method as i went along

What package did you install for the harbour launcher, "ume-config-harbour"?

---

### Post by macewan on 2009-02-05
Thanks for that suggestion. I've snapped a screenshot of this theme used on a fresh Ubuntu install on my Macbook Air.

[http://flickr.com/photos/macewan/3255938555/](http://flickr.com/photos/macewan/3255938555/)

[[IMG]http://farm4.static.flickr.com/3515/3255938555_c67214767b_m.jpg[/IMG]]("http://flickr.com/photos/macewan/3255938555/sizes/o/")

By the way... Ubuntu works just great full screen under VMWare 2 on Macbook Air. :D

> **wildcard said:**
> Update on this one, guys...

If you just want the new theme, here's how I did it, without adding things to Synaptic.

Open your browser of choice and go to [http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/)

This should give you links to click on; click on Universe and then Binary-lpia. In here, save the glassy-bleu-browser-skin_0.5_all.deb , glassy-bleu-theme_21_all.deb , and     gnome-backgrounds-hp_0.4_all.deb files. Just save these to your Desktop. As these are compiled with "all" rather than "lpia", these should be global files that will work for 386 or 64-bit distros. Click on the files on your desktop and Package Installer should handle the rest.*

Presumably, you could go into the main, restricted, or multiverse folders and do the same thing for any .deb files that do not have lpia in their name and have them work on your distro.*



*standard disclaimer of me not being responsible for you hosing your system while trying to follow these instructions does apply here; they worked for me, though.

---

### Post by hm1992 on 2009-02-05
[http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/)
then harbour-launcher_0.78.3_lpia.deb
had to dpkg --install --force-depends --force-architecture
dont copy and paste because I'm not sure if it is right. check dpkg --help and dpkg --force-help as I said above
i haven;t had much time to test it.
if it goes wrong its not my fault (disclaimer, disclaimer, disclaimer)

---

### Post by rafaelcapanema on 2009-02-05
Great, hm1992, thank you!

I'm running it on an actual HP Mini XP Edition with dual boot (XP/Ubuntu).

**The whole process, step by step**

1. Download [harbour-launcher_0.78.3_lpia.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/harbour-launcher_0.78.3_lpia.deb") and save it to your home folder

2. Open a terminal window and type:
> sudo dpkg -i --force-architecture --force-depends harbour-launcher_0.78.3_lpia.deb

3. Type Alt+F2 and launch it:
> harbour-launcher
If you don't see it right away, press the show desktop icon (the keyboard shortcut is Ctrl+Alt+D) or do some Alt+Tabbing.
If you want it to launch everytime you log in, go to System > Preferences > Sessions and add harbour-lancher.

4. To get the Favorite Websites thing working, install the [webfav_1.0ubuntu5_all.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/webfav_1.0ubuntu5_all.deb") package.
EDIT: It creates a heart icon on Firefox, but it apparently does nothing. Any ideas?

5. The music/photos widgets are powered by Elisa, a media center software. You can install it by typing this on a terminal:
> sudo apt-get install elisa
Or go to Synaptic-Add/Remove and search for "elisa".
It will ask you to restart your computer. (!)

6. The MIE has no top panel, just a bottom one. You can mimic Ubuntu Netbook remix's set-up (assuming you have installed UNR's packages): [(source)]("https://wiki.ubuntu.com/UNR#Ubuntu%208.10%20(Intrepid)%20UNR%20Package%20Installation")
> go-home-applet | window-picker-applet | notification-area-applet | mixer-applet | clock
Add them from last to first. Right-click each one and click Move to arrange them.

**Additional tweak**

1. Install the Thunderbird theme:
[http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/hp-tbird-theme_0.5_all.deb](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/hp-tbird-theme_0.5_all.deb)

Does anyone else recommend extra tweaks?

Screenshot attached. Some further tweaking is still necessary, but it's almost done, I believe.

---

### Post by joey-elijah on 2009-02-05
> **rafaelcapanema said:**
> Great, hm1992, thank you!

I'm running it on an actual HP Mini XP Edition with dual boot (XP/Ubuntu).

**The whole process, step by step**

1. Download [harbour-launcher_0.78.3_lpia.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/harbour-launcher_0.78.3_lpia.deb") and save it to your home folder

2. Open a terminal window and type:


3. Type Alt+F2 and launch it:

If you don't see it right away, press the show desktop icon (the keyboard shortcut is Ctrl+Alt+D) or do some Alt+Tabbing.
If you want it to launch everytime you log in, go to System > Preferences > Sessions and add harbour-lancher.

4. To get the Favorite Websites thing working, install the [webfav_1.0ubuntu5_all.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/webfav_1.0ubuntu5_all.deb") package.

5. The music/photos widgets are powered by Elisa, a media center software. You can install it by typing this on a terminal:

Or go to Synaptic-Add/Remove and search for "elisa".
It will ask you to restart your computer. (!)

6. The MIE has no top panel, just a bottom one. You can mimic Ubuntu Netbook remix's set-up (assuming you have installed UNR's packages): [(source)]("https://wiki.ubuntu.com/UNR#Ubuntu%208.10%20%28Intrepid%29%20UNR%20Package%20Installation")


**Additional tweak**

1. Install the Thunderbird theme:
[http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/hp-tbird-theme_0.5_all.deb](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/hp-tbird-theme_0.5_all.deb)

**To-do**

1. When you first launch harbour-launcher, it tells you can always come back to it by pressing the HP key - which is, actually, a rebranded Windows/Super key.
Does anyone know how to assign the Windows/Super key to launch harbour-launcher?

Does anyone else recommend extra tweaks?

Awesome little tutorial there, many thanks.

I'm really liking the design - reminds me somewhat of what jolicloud looks like - albeit less functional than the JC will be.

It's annoying you can't resize the sidebars or, as someone else suggested, replace mail with a RSS reader or something else. 

I've installed it on my netbook (eee pc 701) and the launcher does't entirely fit the screen, which is a bit 'meh', i guess... but most people didn't get a netbook shipped to the UK from USA the day they came out... so good for you for waiting!)

The 'app' launcher icons are massive, but very finger friendly - should be great for when i get my eee swivel screen model in a few months.

UK users won't get to buy the HP netbook this comes with as HP have decided to only release Windows based netbooks here.

interestingly, the linux version comes with 2GB RAM, xp comes with 512mb. just sayin'!

My fingers hurt from typing on this eee, but if anyone is interested in tweaking the launcher to fit a 701 screen i'm more than happy to help. (depending on the license of the launcher, obv. i'm not aware it's opensource.)

---

### Post by sototallycarl on 2009-02-06
using the above and some fiddling on my own it seems to work pretty well but runs like crap on my rather light weight eee (eee 900mhz, 512mb ram) looks like the launcher is using more than 50% of the processor

---

### Post by rafaelcapanema on 2009-02-06
Same here. The thing is apparently quite CPU-intensive, processor use is constantly at 50%.

---

### Post by joey-elijah on 2009-02-06
It ran fine on my eee 701 - thought i do have 2GB RAM. 

I installed it on my desktop, too which was a mistake. I forced architecture and dependencies on x64 Ubuntu and it won't run, nor can i remove it. However, Update Manager is more than happy to pretty much present me with most of HP's updates, despite not adding the repos. 

Frak.

---

### Post by warped0ne on 2009-02-06
> **Felias said:**
> Hi there,

i was also looking for this, and i am glad that something is happening :-)

I've read on Liliputing, that there'll be an iso to download in the future, but i'm not sure if it's gonna work with the 2133 as well...

@timm: Do you think netbook remix is necessary for this to work? And you DID get UNR running on the 2133? Because people seem to have problems with it...

I wouldn't try this on the HP 2133 Mini-Notebook, the VIA processor, chipset, and graphics probably won't play well with it. But, if you're in the market for a new mini PC, the HP 2140 Mini-Notebook will come with the Intel Atom N270 processor.

---

### Post by Wille on 2009-02-06
> **supernova_hq said:**
> Anyone know if this would work on the Nokia N-Series devices?

I have an N810. It runs mameo (debian variant, but not ubuntu) and has an ARM processor.

The device is awsome, but I would like to find an new UI for it since theming is VERY limited in maemo :(

There is pretty much zero chance of this happening. It's a stretch to call maemo a debian variant, even if it uses .debs for packaging and Nokia uses debian distro as a starting point.

---

### Post by supernova_hq on 2009-02-06
Darn. Well, it was worth a shot :(

I guess I'm stuck with my limited maemo themes.

---

### Post by gnuisnotunix on 2009-02-06
Hello,

is there any way to install MediaStyle? I cannot find the package...

---

### Post by smartboyathome on 2009-02-06
> **supernova_hq said:**
> Darn. Well, it was worth a shot :(

I guess I'm stuck with my limited maemo themes.

You could always try installing Illume (part of E17, made for OpenMoko but isn't specific to it) using the easy_e17.sh script. Of course, that would require terminal access on your nokia and you would need to compile missing dependencies. If your ultimate goal is having more customizable themes, though, e17 is your ticket.

---

### Post by reya276 on 2009-02-06
Any word on the OpenOffice 3 icons fix for the HP Mini Theme on 8.10 desktop

---

### Post by tyn0r on 2009-02-06
If you want to install HP MIE with the restore disk, I've uploaded all needed files on my mirror @ [boTux.fr]("http://www.botux.fr/") :

[INDENT][http://mirror.botux.net/pub/ubuntu/hp-mie/]("http://mirror.botux.net/pub/ubuntu/hp-mie/")[/INDENT]
[INDENT][ftp://mirror.botux.net/pub/ubuntu/hp-mie/]("ftp://mirror.botux.net/pub/ubuntu/hp-mie/")[/INDENT]

If you find other interesting files who might be cool on the mirror, just let me know and I upload them !

Good install !

---

### Post by shaggorama on 2009-02-06
> **peryn said:**
> Looks like we need to install:

openoffice.org-config_3_all.deb
openoffice.org-config_4_all.deb

to fix problems with OO

but it depends on ume-config-common - and i can't find it :(

So how does OO look with the config files installed? right now I'm not a huge fan: the font in dialog boxes is too dark.

---

### Post by chaehaih on 2009-02-07
> **wildcard said:**
> Update on this one, guys...

If you just want the new theme, here's how I did it, without adding things to Synaptic.




Can't thank you enough. All the themes I tried, sucked at the very best. without clear instructions and difficult to implement.. your introduction and instructions this has made ubuntu finally what it is a great superior system.

Next stop? Some transparency in black color?

---

### Post by peryn on 2009-02-07
> **shaggorama said:**
> So how does OO look with the config files installed? right now I'm not a huge fan: the font in dialog boxes is too dark.

I didn't install them, please note that i'm not sure that those config files actually help...
maybe we should ask in OO forums?

---

### Post by chaehaih on 2009-02-07
darn.. spoke too soon.. best theme, but useless if can't use openoffice.org,

anyone got a solution?

---

### Post by chaehaih on 2009-02-07
> **chaehaih said:**
> darn.. spoke too soon.. best theme, but useless if can't use openoffice.org,

anyone got a solution?

Spoke too soon again.. a not very kool workaround is to also install the following 6 as well. First one below might not be needed. 
	1) openoffice.org-config-hp_1_all.deb
        2) (ume-config-base_0.1_all.deb) to 0.5.

And you will get something looking like this.. 


But in order to take screenshot and modify it, I had to open gimp. And wait till you see gimp.. and you would feel all was a waste of time. it's good thing,but not fully done. It should have been just few click installs and everything should have worked well. it's a pain in the *** to be able to unlock the theme folder in windows, once you are done, changing themes is a piece of cake. 

and now as a newbie to ubuntu, I think it's a major pain in the manboobs to just make this ugly (great system) look pretty.

---

### Post by hm1992 on 2009-02-07
i have downloaded the .img file released today but i would like to install it in a virtual machine.
It boots from an SD in my eee pc but is not a live distro. It just offers one choice (lose all of you hard drive information and start a fresh). With no conformation that it works on the eee pc i will not try it.
I have managed to convert the .img file into a .vdi for virtual box using these instructions ([http://www.greenhughes.com/content/installing-ubuntu-mid-virtualbox](http://www.greenhughes.com/content/installing-ubuntu-mid-virtualbox)) but it just falls into a loop, saying

checking device /dev/sda for installation source...
checking device /dev/sdb for installation source...
checking device /dev/sdc for installation source...
checking device /dev/sdd for installation source...
Sleeping for 5 seconds
Sleeping finished

and then it loops. Can i bypass this, or mount a dummy as /dev/sda or something (i don't have very much experience with virtual box).
Or do the instructions above allow all the HP features to work on the harbour-launcher at least

---

### Post by shaggorama on 2009-02-07
> **shaggorama said:**
> So how does OO look with the config files installed? right now I'm not a huge fan: the font in dialog boxes is too dark.

so i found an easy workaround to this (AKA my particular) issue. The dialog box colors is not specific to open office, it's a default setting of the theme. To  darken the text, go to:

system > preferences > appearance > customize > colors tab > Input boxes - text

and just slide down to lighten, or pick your color. default is #101010. right now I'm using #565656 and it works pretty well.

---

### Post by shaggorama on 2009-02-07
ugh, you all thought the gimp was bad, try opening up compizconfig

---

### Post by MyR on 2009-02-07
> **shaggorama said:**
> ugh, you all thought the gimp was bad, try opening up compizconfig

With a highly customizable interface you get lots of options ;]
At least it has a search bar!

peace

---

### Post by pvravi on 2009-02-08
While the frontend interface installed and looks good, the features don't all work. Note that I have already installed Elisa.

File, Settings and Logout: work, although, ideally would prefer shutdown option in logout.
Mail: Dont want to use Thunderbird, unable to configure. I'd like to point gmail to this, ideally.
Websearch: works
Bookmarks: None available, don't know how to add
Favorite sites: can add, no thumbnail
Music: Unable to add albums. The add action throws up a pop-up titled
```
Select, album, playlist or song
```
which says
```
Could not get albums from HP Mediastyle powered by Elisa.
```
Click on the Music link yields: 
```
HP MediaStyle Powered by Elisa frontend show failed
The name com.fluendo.Elisa was not provided by any .service files
<OK>
```
Photos: same as music
Start program: works
Switcher: works

It appears as if for the rest of it to work, the HP Mediastyle app is necessary. However, this doesn't seem to be available as a package. If it is in another package, it isn't apparent. Elisa by itself doesn't connect to this frontend. 

Is this what's working for everyone, or is there more? Am I missing something?

---

### Post by kmaxir on 2009-02-08
> **shaggorama said:**
> so i found an easy workaround to this (AKA my particular) issue. The dialog box colors is not specific to open office, it's a default setting of the theme. To  darken the text, go to:

system > preferences > appearance > customize > colors tab > Input boxes - text

and just slide down to lighten, or pick your color. default is #101010. right now I'm using #565656 and it works pretty well.



sounds like puttry good~ :)   a simple problem need  simple solution~~ :)

---

### Post by m.rankovic on 2009-02-08
> **tyn0r said:**
> If you want to install HP MIE with the restore disk, I've uploaded all needed files on my mirror @ [boTux.fr]("http://www.botux.fr/") :

[INDENT][http://mirror.botux.net/pub/ubuntu/hp-mie/]("http://mirror.botux.net/pub/ubuntu/hp-mie/")[/INDENT]
[INDENT][ftp://mirror.botux.net/pub/ubuntu/hp-mie/]("ftp://mirror.botux.net/pub/ubuntu/hp-mie/")[/INDENT]

If you find other interesting files who might be cool on the mirror, just let me know and I upload them !

Good install !

I installed this on my MSI Wind U100, trackpad, ethernet, wireless, and sound do not work... :( but it looks so cool :)

[http://picasaweb.google.com/lh/photo/LRcvuaDysozop0eG1MKFvQ?feat=directlink](http://picasaweb.google.com/lh/photo/LRcvuaDysozop0eG1MKFvQ?feat=directlink)
[http://picasaweb.google.com/lh/photo/gzKQO240lvNb_be6sevG5Q?feat=directlink](http://picasaweb.google.com/lh/photo/gzKQO240lvNb_be6sevG5Q?feat=directlink)

sry, bad english... :/

---

### Post by vorcigernix on 2009-02-08
> **pvravi said:**
> While the frontend interface installed and looks good, the features don't all work. Note that I have already installed Elisa.

File, Settings and Logout: work, although, ideally would prefer shutdown option in logout.
Mail: Dont want to use Thunderbird, unable to configure. I'd like to point gmail to this, ideally.
Websearch: works
Bookmarks: None available, don't know how to add
Favorite sites: can add, no thumbnail
Music: Unable to add albums. The add action throws up a pop-up titled
```
Select, album, playlist or song
```
which says
```
Could not get albums from HP Mediastyle powered by Elisa.
```
Click on the Music link yields: 
```
HP MediaStyle Powered by Elisa frontend show failed
The name com.fluendo.Elisa was not provided by any .service files
<OK>
```
Photos: same as music
Start program: works
Switcher: works

It appears as if for the rest of it to work, the HP Mediastyle app is necessary. However, this doesn't seem to be available as a package. If it is in another package, it isn't apparent. Elisa by itself doesn't connect to this frontend. 

Is this what's working for everyone, or is there more? Am I missing something?

Same problem here

---

### Post by shappie on 2009-02-08
> **m.rankovic said:**
> I installed this on my MSI Wind U100, trackpad, ethernet, wireless, and sound do not work... :( but it looks so cool :)

[http://picasaweb.google.com/lh/photo/LRcvuaDysozop0eG1MKFvQ?feat=directlink](http://picasaweb.google.com/lh/photo/LRcvuaDysozop0eG1MKFvQ?feat=directlink)
[http://picasaweb.google.com/lh/photo/gzKQO240lvNb_be6sevG5Q?feat=directlink](http://picasaweb.google.com/lh/photo/gzKQO240lvNb_be6sevG5Q?feat=directlink)

sry, bad english... :/
Wow looks great. How you got the weblinks thumbnails working? And how did you got the thumbnails for music and video's working? I would really like to get that to work to! Thanks in advance!

---

### Post by m.rankovic on 2009-02-08
> **shappie said:**
> Wow looks great. How you got the weblinks thumbnails working? And how did you got the thumbnails for music and video's working? I would really like to get that to work to! Thanks in advance!

I dloaded HP MIE Restore image, and installed it... That's all I did...

---

### Post by shappie on 2009-02-08
> **m.rankovic said:**
> I dloaded HP MIE Restore image, and installed it... That's all I did...
Ok thanks! 

If i use the HP Mie image to install on my netbook (samsung NC10) can i choose the partions to install on? Or will it overwrite everything? I use a tripleboot so i don't want to loose the other partitions.

---

### Post by m.rankovic on 2009-02-08
It will delete everityng... U will loose all your partitions and data..

---

### Post by weid83 on 2009-02-08
You can get the photo and music thumbnails working by installing the latest elisa from the hp repos:

elisa_0.5.15.5-0dennis1_all.deb
elisa-plugins-ugly_0.5.15.5-0dennis1_all.deb
python-elisa_0.5.15.5-0dennis1_all.deb
elisa-plugins-bad_0.5.15.5-0dennis9_all.deb
elisa-plugins-good_0.5.15.5-0dennis1_all.deb

You'll also need python-pgm and libpigment > 0.3.8, for lpia you can it in the hp repos, for i386 and x86 you can find it here:

[http://91.189.90.217/damoxc/ubuntu/pool/main/p/](http://91.189.90.217/damoxc/ubuntu/pool/main/p/)

---

### Post by csim on 2009-02-08
Shouldn't there be source code available? I'm guessing that most of that stuff is built mostly on top of GPL licensed software(excluding GTK+ and parts of GNOME which is LGPL)?

---

### Post by pvravi on 2009-02-08
With this (thanks weid83): 

elisa_0.5.15.5-0dennis1_all.deb
elisa-plugins-ugly_0.5.15.5-0dennis1_all.deb
python-elisa_0.5.15.5-0dennis1_all.deb
elisa-plugins-bad_0.5.15.5-0dennis9_all.deb
elisa-plugins-good_0.5.15.5-0dennis1_all.deb

Music: works. Unable to assign cover art as yet, but that's probably a limitation of my MP3, not necessarily the frontend. Even able to play music in the widget. 
Photos: works. Sometimes elisa dies, but that's again a software issue, not the frontend's 

[COLOR="Red"]Bookmarks: Still unable to add; not sure what the intended method here is.
Web Favorites: Still no thumbnails
Mail: still thunderbird, but I understand that's by design. In a netbook, this must ideally be webmail.hmph!
[/COLOR]

---

### Post by pvravi on 2009-02-09
Also just realized that my bottom panel does not start automatically. Instead a blank panel starts, which I can't add any applets to - right click only shows only help and about. 

Meanwhile, if I start a gnome-panel as root

$ sudo gnome-panel

the correct bottom panel gets started. Not too sure what's happening there or how to fix it. 

Appreciate any help

---

### Post by smartboyathome on 2009-02-09
> **pvravi said:**
> Also just realized that my bottom panel does not start automatically. Instead a blank panel starts, which I can't add any applets to - right click only shows only help and about. 

Meanwhile, if I start a gnome-panel as root

$ sudo gnome-panel

the correct bottom panel gets started. Not too sure what's happening there or how to fix it. 

Appreciate any help

Problem is you ran gnome-panel with sudo. Since gnome-panel wrote to your configs as root, they are now owned by root, and thus your panel won't start correctly.

---

### Post by remu on 2009-02-09
> **shaggorama said:**
> so i found an easy workaround to this (AKA my particular) issue. The dialog box colors is not specific to open office, it's a default setting of the theme. To  darken the text, go to:

system > preferences > appearance > customize > colors tab > Input boxes - text

and just slide down to lighten, or pick your color. default is #101010. right now I'm using #565656 and it works pretty well.

Following this method gets me OpenOffice with readable buttons, however, the icons are still missing. Is this due to the HP icon pack? Or is it something else. I'm hoping to get the icons back in OpenOffice, but other than that, I love this new look!

---

### Post by pvravi on 2009-02-09
> **smartboyathome said:**
> Problem is you ran gnome-panel with sudo. Since gnome-panel wrote to your configs as root, they are now owned by root, and thus your panel won't start correctly.

Smartboy, thanks - any idea how to fix it. I tried looking into the .gnome home directory for both root and for myself. I couldn't find the right stuff. 

How do I import root's panel configs to myself? 

Thanks

---

### Post by peryn on 2009-02-09
> **remu said:**
> Following this method gets me OpenOffice with readable buttons, however, the icons are still missing. Is this due to the HP icon pack? Or is it something else. I'm hoping to get the icons back in OpenOffice, but other than that, I love this new look!
nope - i've changed icons to standard - same problem :(

---

### Post by smartboyathome on 2009-02-09
> **pvravi said:**
> Smartboy, thanks - any idea how to fix it. I tried looking into the .gnome home directory for both root and for myself. I couldn't find the right stuff. 

How do I import root's panel configs to myself? 

Thanks

sudo doesn't use root's configs, it uses your own. I can't tell you for certain where it is, but try looking in .gnome2. Other than that, I can't tell you, since I don't use GNOME.

---

### Post by macvr on 2009-02-09
can this theme be used in desktops/laptops? 
i have an ACER ASPIRE 5672 laptop , i'd like to use this theme? would i have any problems?

---

### Post by Thaylin on 2009-02-09
> **gcosmin said:**
> EEE PC 4G surf. More tweaking needed.

How did you get it to work?  Did you have ubuntu already on your EEEPC or did you try and install it from the HP Recovery Installer on the HP Site?

Thanks

---

### Post by shaggorama on 2009-02-11
remu, peryn

sorry for not spelling that part of the fix out, rafaelcapanema stumbled onto the solution a fwe days ago (p.3 of this thread):
> **rafaelcapanema said:**
> reya276, you need to install one of the openoffice.org-style-* packages (use Synaptic).
I don't know which one it is exactly, so I installed all of them.
Even though the icons look ugly, they're at least appearing.
I'll try to locate the exact one later and I'll post it here.

i'm pretty sure the icon set you want is the high contrast one, but I installed them all and it looks alot better. If you feel the need to tweak OO more, try tools > options > appearance

---

### Post by kwaanens on 2009-02-11
For those who want to tweak the colors of this theme (and others), use [thewidgetfactory]("apt:thewidgetfactory"). Press the link if you have apturl, or search for it in Synaptic. It gives previews of every gtk widget.

---

### Post by reya276 on 2009-02-11
> **shaggorama said:**
> remu, peryn

sorry for not spelling that part of the fix out, rafaelcapanema stumbled onto the solution a fwe days ago (p.3 of this thread):


i'm pretty sure the icon set you want is the high contrast one, but I installed them all and it looks alot better. If you feel the need to tweak OO more, try tools > options > appearance
Dude that is not a fix, High Contrast Icons is for those whom want to see it that way, as far as I'm concern the defaults are regular looking Icons such as Human, Tango, Galaxy not high contrast so that is not a fix, lets just say that its a bug and we need to find a way to fix it, because what you suggest is not a solution.

---

### Post by peryn on 2009-02-11
> **reya276 said:**
> Dude that is not a fix, High Contrast Icons is for those whom want to see it that way, as far as I'm concern the defaults are regular looking Icons such as Human, Tango, Galaxy not high contrast so that is not a fix, lets just say that its a bug and we need to find a way to fix it, because what you suggest is not a solution.
yep - high contrast it's not a fix :(

---

### Post by BobCFC on 2009-02-11
> **pvravi said:**
> Smartboy, thanks - any idea how to fix it. I tried looking into the .gnome home directory for both root and for myself. I couldn't find the right stuff. 

How do I import root's panel configs to myself? 

Thanks

You could try a set ownership of every file in your home directory recursively, might take a min but it will go through every folder in home and set you back as owner again:

```
sudo chown MYUSERNAME -R /home/MYUSERNAME
```

---

### Post by BDNiner on 2009-02-12
This looks cool. I have been looking for a good dark theme from gnome since i started trying out KDE4. I will set this up when i get home.

---

### Post by mfarley on 2009-02-12
> **hm1992 said:**
> i have downloaded the .img file released today but i would like to install it in a virtual machine.
It boots from an SD in my eee pc but is not a live distro. It just offers one choice (lose all of you hard drive information and start a fresh). With no conformation that it works on the eee pc i will not try it.
I have managed to convert the .img file into a .vdi for virtual box using these instructions ([http://www.greenhughes.com/content/installing-ubuntu-mid-virtualbox](http://www.greenhughes.com/content/installing-ubuntu-mid-virtualbox)) but it just falls into a loop, saying

checking device /dev/sda for installation source...
checking device /dev/sdb for installation source...
checking device /dev/sdc for installation source...
checking device /dev/sdd for installation source...
Sleeping for 5 seconds
Sleeping finished

and then it loops. Can i bypass this, or mount a dummy as /dev/sda or something (i don't have very much experience with virtual box).
Or do the instructions above allow all the HP features to work on the harbour-launcher at least

Has anyone found a way to get this installed as a VM (VirtualBox)?  Or has anyone created a .VDI we can download?

I run into the same error as hm1992 (above).

---

### Post by wildcard on 2009-02-12
Apparently, we're popular :)

[http://arstechnica.com/open-source/news/2009/02/make-your-ubuntu-distro-look-like-the-mini-mi.ars](http://arstechnica.com/open-source/news/2009/02/make-your-ubuntu-distro-look-like-the-mini-mi.ars)

---

### Post by XopherH on 2009-02-12
anyone have an opinion on using this theme on a Samsung NC-10 ?

I'm willing to try this using wildcards instructions as this netbook is for playing around with as it is.  

I am new to GNOME customization, but my main reason for wanting to try this is to be able to see the bottom 5% of the system windows instead of having the OK and Cancel buttons for almost everything I use being too low off the bottom of screen and I have to hit Tab and get lucky from memory.

---

### Post by m.rankovic on 2009-02-12
> **XopherH said:**
> ... and I have to hit Tab and get lucky from memory.

Alt+Left Mouse Button, and move the window up...

---

### Post by XopherH on 2009-02-12
> **m.rankovic said:**
> Alt+Left Mouse Button, and move the window up...

Although new and good information which I will use, I was going more for actually resizing the windows from the GNOME/OS/Kernel standpoint.  There must be a customization that allows those windows to insert a scrollbar.

For some reason I am not a big hotkey and mouse gesture kind of guy, I just prefer not to have to shortcut to do something which should show up as intended from the start.

---

### Post by pvravi on 2009-02-13
> **BobCFC said:**
> You could try a set ownership of every file in your home directory recursively, might take a min but it will go through every folder in home and set you back as owner again:

```
sudo chown MYUSERNAME -R /home/MYUSERNAME
```

BobCFC, Thanks, but no go. Still the same problem. 
I'm goin' nuts!

---

### Post by wildcard on 2009-02-13
I believe that once you move the window via ALT+left mouse, the OS should 'remember' the new position of the window on subsequent openings of that particular windows.

---

### Post by DarKnyht on 2009-02-13
I really like the glassybleu and hp theme look (although dust will stay my theme for now).  I just hope that the Ubuntu team can come up with something just as good or better for the next release.

Thanks for posting how to get this.  Now we just need someone to release these (or something very similar) into gnome-look.org so we don't need to use the .deb files.

---

### Post by pvravi on 2009-02-13
> **wildcard said:**
> Apparently, we're popular :)

[http://arstechnica.com/open-source/news/2009/02/make-your-ubuntu-distro-look-like-the-mini-mi.ars](http://arstechnica.com/open-source/news/2009/02/make-your-ubuntu-distro-look-like-the-mini-mi.ars)

And how!

[http://www.engadget.com/2009/02/13/hps-exclusive-mobile-internet-ubuntu-skin-not-so-exclusive-anym/](http://www.engadget.com/2009/02/13/hps-exclusive-mobile-internet-ubuntu-skin-not-so-exclusive-anym/)

---

### Post by a2h on 2009-02-13
I wrote a tutorial for those who aren't willing to go through 8 pages of posts :D

[http://a2h.uni.cc/wp/2009/02/13/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/13/installing-the-hp-minis-mie-interface-on-ubuntu/)

---

### Post by mfarley on 2009-02-13
Has anyone made a downloadable VM with Mie preinstalled?

---

### Post by jaminthorns on 2009-02-13
If anyone just wants the individual deb package or the source folder, here are the links.

DEB Package: [http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/glassy-bleu-theme_21_all.deb](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/glassy-bleu-theme_21_all.deb)

Source: [http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/source/glassy-bleu-theme_21.tar.gz](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/source/glassy-bleu-theme_21.tar.gz)

---

### Post by MyR on 2009-02-13
The glassybleu theme takes away the icons on cellwriter; So this is not so great on tablet PCs unless someone finds a workaround.

Edit: ok, so you can turn on "show button labels" in cellwriter.

---

### Post by pleonasmaticul on 2009-02-14
Hello,
I want to use this interface on my Dell Mini 9, but harbour eats up 50% of the CPU. This make my notebook quite unusable. I'm wondering if on an HP Mini 1000 is the same problem.
Is this because I use i386? Is there something I'm missing?!?

---

### Post by MyR on 2009-02-14
I wouldn't recommend anyone using this interface quite yet (unless you want to try to figure out how to fix it).  Much of the launcher interface doesn't work right.

Just the theme by itself looks pretty good, but some icons don't work so well.

peace

---

### Post by pleonasmaticul on 2009-02-14
Well, I have tried it but i didn't stress myself to fix it since the interface runs like hell. I really wonder how much CPU does it use on HP Mini since it has the same CPU.
Now that I'm thinking about it, may it be because of the video card drivers? Because I use the ones that came with Intrepid.

---

### Post by ecacafce on 2009-02-14
Thanks everyone for the great work and clarity in how-to.

i followed the steps, the only problem is the following:

my system resources are swamped. i have a dual core 2.4 and one core is constantly at 100% while the second is around 20 - 30%. Also its using around 300mb of my 3gb ram. 

i am running this on my desktop with 8.10.

---

### Post by Islington on 2009-02-14
I am making a port of the metacity to emerald, incase anyone is interested.

---

### Post by pvravi on 2009-02-15
> **ecacafce said:**
> Thanks everyone for the great work and clarity in how-to.

i followed the steps, the only problem is the following:

my system resources are swamped. i have a dual core 2.4 and one core is constantly at 100% while the second is around 20 - 30%. Also its using around 300mb of my 3gb ram. 

i am running this on my desktop with 8.10.

Not sure why there are reports of too much consumption of resources. Mine's a venerable IBM X-41 with a single core 1.6G CPU. Typically with Firefox, a terminal, and system monitor open, CPU is about 25%. system-monitor consumes most of it. 

It *might* be because you haven't installed all the debs necessary.

---

### Post by ecacafce on 2009-02-15
it just struck me that it might be possible i installed debs for 64bit?

---

### Post by Islington on 2009-02-15
Emerald port complete:
[http://islingt0ner.deviantart.com/art/GlassyBleu-112981633?submitted=1](http://islingt0ner.deviantart.com/art/GlassyBleu-112981633?submitted=1)

---

### Post by pvravi on 2009-02-15
> **ecacafce said:**
> it just struck me that it might be possible i installed debs for 64bit?

Note also that I have disabled Compiz. That may also cause the issue, but I did not see much use of Compiz eye-candy with this interface.

---

### Post by ecacafce on 2009-02-15
> **pvravi said:**
> Note also that I have disabled Compiz. That may also cause the issue, but I did not see much use of Compiz eye-candy with this interface.

is there anyway to fix this?

---

### Post by pvravi on 2009-02-15
> **ecacafce said:**
> is there anyway to fix this?

Try with disabling Compiz for a start. I don't believe Compiz was a strain on resources when I had it enabled, but give it a try anyway. Then try to see if you did indeed install the 64-bit debs. If you did, reinstalling the debs for your particular platform (except the harbour-launcher deb).

---

### Post by a2h on 2009-02-16
[My tutorial](http://a2h.uni.cc/wp/2009/02/13/installing-the-hp-minis-mie-interface-on-ubuntu/) on setting up the Mie interface now has info on getting basic bookmarks integration and fonts working... enjoy :D

---

### Post by pleonasmaticul on 2009-02-16
So you say that the resource eater is not harbour-launcher?
Because after I stoped harbour and returned to UNR, the CPU is no longer used 50%.
I use meta-city, since it Compiz is incompatible with UNR interface.

PS: I have Ubuntu 8.10 on a Dell Mini 9

---

### Post by -jay- on 2009-02-16
im using this theme on my desktop  very happy with  no complaints thanks for the deb files

---

### Post by Islington on 2009-02-16
I know people were having problems with Open Office.

Try this out:

just write a shell script if you are lazy like me

```
#!/bin/bash
# This changes the appearance of idiotic applications
# Your favorite theme = GTKRCFILE
# GTK2_RC_FILES = path to your favorite theme's gtkrc (change /usr/share/themes to /home/*whatever*.themes if you wish)
GTKRCFILE=Human
GTK2_RC_FILES=/usr/share/themes/"$GTKRCFILE"/gtk-2.0/gtkrc "$@"

```

save it as "theme", under /home/user/
make it executable (chmod or use gui)
test it by running 
```
./theme ooffice -writer 
```
change the menus using the menu editor.

edit: check it out: I am running cianosmooth with ooffice-writer.
edit the second attached a hgiher resolution conversion of the HP wallpaper

---

### Post by xaenyx on 2009-02-16
I noticed that the program outputs these errors:

> 
** (harbour-launcher:10590): WARNING **: SQL Error: database is locked

** (harbour-launcher:10590): WARNING **: SQL Error: database is locked

** (harbour-launcher:10590): WARNING **: Error loading Thunderbird data: No such file or directory

** (harbour-launcher:10590): WARNING **: The name com.fluendo.Elisa was not provided by any .service files
Trying to get the volume again


Is there any way to try and find what file it is trying to access (i.e. what Thunderbird data is)?  Or to see if it's trying to access mysql or something?

---

### Post by MyR on 2009-02-17
Whew! Finally everything works! Much thanks to everyone for sharing!
peace

---

### Post by corinthalkorda on 2009-02-17
I have everything working pretty well, except for a couple of things. Does anyone have the Mail info in the left working properly? I have Thunderbird configured with my email account settings, but it still doesn't show anything in the left panel. Help?

Also, does anyone have binaries for the MediaStyle version of Elisa that the HP mie uses? I want to get it set up so I can have the whole interface working. :-)

---

### Post by klakka on 2009-02-17
Hi guys just to say that i have everything working thumbnails elisa , email, hp buttons on the toolbar etc just look for posts by bobby and ian (both me, thought they might get mad with all my posts lol!)

[http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/)
 Ive also added an image of the final look on the post too.

Can anybody help me with this is there a way to now turn the os into an iso with everything working? i have a dell mini 9 which i want to put this on to too i cant be bothered with all the install just wondered if there was an eay way.

[COLOR="Red"]Also if you install from HP mie using their ISO and WIFI does not work check the airplane mode i can guarantee its not ticked!!!!![/COLOR]


I did install from HP but too much hassle so just install 8.1 ubuntu and played around anyway take a look at the post any questions please ask (thats if i can help bit of a nooby!!)

Ian

[http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/)

---

### Post by Islington on 2009-02-17
> **klakka said:**
> Hi guys just to say that i have everything working thumbnails elisa , email, hp buttons on the toolbar etc just look for posts by bobby and ian (both me, thought they might get mad with all my posts lol!)

[http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/)
 Ive also added an image of the final look on the post too.

Can anybody help me with this is there a way to now turn the os into an iso with everything working? i have a dell mini 9 which i want to put this on to too i cant be bothered with all the install just wondered if there was an eay way.

[COLOR="Red"]Also if you install from HP mie using their ISO and WIFI does not work check the airplane mode i can guarantee its not ticked!!!!![/COLOR]


I did install from HP but too much hassle so just install 8.1 ubuntu and played around anyway take a look at the post any questions please ask (thats if i can help bit of a nooby!!)

Ian

[http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/)

you can fix openoffice with my post right above. please try it out..

---

### Post by corinthalkorda on 2009-02-17
> **klakka said:**
> Hi guys just to say that i have everything working thumbnails elisa , email, hp buttons on the toolbar etc just look for posts by bobby and ian (both me, thought they might get mad with all my posts lol!)

[http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/)
 Ive also added an image of the final look on the post too.

Can anybody help me with this is there a way to now turn the os into an iso with everything working? i have a dell mini 9 which i want to put this on to too i cant be bothered with all the install just wondered if there was an eay way.

[COLOR="Red"]Also if you install from HP mie using their ISO and WIFI does not work check the airplane mode i can guarantee its not ticked!!!!![/COLOR]


I did install from HP but too much hassle so just install 8.1 ubuntu and played around anyway take a look at the post any questions please ask (thats if i can help bit of a nooby!!)

Ian

[http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/)

You really have the modified Elisa working? I get a dependency error for the plugins-bad package you listed, and The first few packages aren't located on that server anymore. Additionally, the mail center still isn't working for me, and I followed your tutorial.

Edit:
I have Elisa working properly with the interface now, by using the packages at the Elisa PPA. All I need now is for the Thunderbird integration to work! :-)  Anyone able to get it working?

---

### Post by Andysan on 2009-02-17
Wow, well done everyone and thanks for getting this working.

Does anyone know if a .deb could be created to streamline all of this into a single install, or am i talking silly?:popcorn:

---

### Post by corinthalkorda on 2009-02-17
Does anyone know where to find a more complete Glassy Bleu icon set? I remember different icons for firefox, pidgin, etc in the application menu when I tried installing it from the restore .img

---

### Post by a2h on 2009-02-18
Eh, you guys think klakka wrote the tutorial? O_o

Anyway, not much updating required to my post now.

**It has most instructions required for the home screen to look pretty much perfect**.

So, enjoy.

[http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/)

AND REMEMBER: THIS IS FOR 8.10 32-bit.

**EDIT:** Broken links fixed, and corinthalkorda... Thunderbird instructions added :D

---

### Post by corinthalkorda on 2009-02-18
> **a2h said:**
> Eh, you guys think klakka wrote the tutorial? O_o

Anyway, not much updating required to my post now.

**It has most instructions required for the home screen to look pretty much perfect**.

So, enjoy.

[http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/)

AND REMEMBER: THIS IS FOR 8.10 32-bit.

**EDIT:** Broken links fixed, and corinthalkorda... Thunderbird instructions added :D

Thanks so much! Everything works perfect now. :-)

---

### Post by klakka on 2009-02-18
Please be aware i did not write the tutorial i just helped (bobby and ian) on the blog. Yes email is working fine. Ashame the acer isnt ive got the dreaded black screen of death.

Ive also just finished loading it on to my dell mini 9 using HP's iso it works fine except you think wifi isnt working when it actually is!!!

Sorry a2h didnt want to make out it was me who wrote the article.

Ian

---

### Post by corinthalkorda on 2009-02-18
I've got a problem. Everything was working great yesterday, but now my CPU load rides very high. At the low end, it'll be around 48%. On the high end, it'll max out. It seems that nautilus is doing this, and I can't open new instances of nautilus (i.e. I can't browse any folders when I click "Files"). Any suggestions?

---

### Post by smartboyathome on 2009-02-18
Try running "killall nautilus". :)

---

### Post by corinthalkorda on 2009-02-18
...wow. Can't believe I didn't think of that, lol. I guess I just assumed it was something ill from harbour-launcher. I don't know what happened, but it's working fine now. Now, next... :-P

Does anyone know the command for the switcher applet? I'd like to bind it to a keyboard shortcut. :-)

---

### Post by reya276 on 2009-02-20
I followed your instructions and that does not work at least not for me.

---

### Post by smartboyathome on 2009-02-20
> **corinthalkorda said:**
> ...wow. Can't believe I didn't think of that, lol. I guess I just assumed it was something ill from harbour-launcher. I don't know what happened, but it's working fine now. Now, next... :-P

Does anyone know the command for the switcher applet? I'd like to bind it to a keyboard shortcut. :-)

Try "ctrl+alt+left" and "ctrl+alt+right"

---

### Post by corinthalkorda on 2009-02-21
I meant the HP switcher applet. The button (applet) and app are highlighted in the screenshot I took.

---

### Post by S3NATOR on 2009-02-22
> **a2h said:**
> I wrote a tutorial for those who aren't willing to go through 8 pages of posts :D

[http://a2h.uni.cc/wp/2009/02/13/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/13/installing-the-hp-minis-mie-interface-on-ubuntu/)
Thanks! Tutorial worked great! I got it all working in 8.10 32-bit on a Phenom and ATI machine. Now I'm going to try and get it to work on my wife's Compaq Presario V2000. Hopefully it can handle the eye candy. Here is a pic of it working on my Phenom machine:

[Link](http://img.photobucket.com/albums/v640/Senator24/PC/hpmini2.png)

Also, if anyone is interested I found a .deb package with the HP Mini wallpapers. I'm sure someone here has posted it but I didn't see it.

[http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/gnome-backgrounds-hp_0.4_all.deb](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/gnome-backgrounds-hp_0.4_all.deb)


S3N

---

### Post by Nigmah on 2009-02-22
anyone tell me how i can mac my start button a shortcut to the hp screen? Also anyone know if there are any good graphics drivers out there for an AAO, performance is a little slow on mine and when i switch back to firefox it has graphics errors.

---

### Post by jaketoox on 2009-02-22
Does someone here know how to launch harbour @800x480???....i'd really like to try it but it doesn't fit on my 7" eeepc screen...or does it behave correctly after install&reboot when added to startup?

---

### Post by Nigmah on 2009-02-22
wow i can barley take 1024x768 how to you stand 800x480?

---

### Post by jaketoox on 2009-02-22
:( b'cause i have to.....

..but seriously i just want it to fit on my screen....

---

### Post by S3NATOR on 2009-02-22
> **corinthalkorda said:**
> I meant the HP switcher applet. The button (applet) and app are highlighted in the screenshot I took.
Where do you get the switcher applet?

---

### Post by redc on 2009-02-22
did they have any solutions for those 64bit system yet???

---

### Post by cjohn106 on 2009-02-22
Hey. I installed all this and it seems to work except when i go to the Elisa photo and music manager the graphics get all screwy. Anyone else have this problem? Also, is there anyway to get firefox to open inside the launcher? that would be cool. Also the launcher seems to be a little laggy.

---

### Post by cyrus80b on 2009-02-23
Question on this, and this might sound strange, but what exactly is this interface? Is it just a theme for the Ubuntu Window Manager (which I think is metacity) or an application. I downloaded what was posted in this thread, but it is just a theme. I am looking for the complete interface. The thing that brings together all the applications into a dashboard.

---

### Post by cjohn106 on 2009-02-24
What I think would be a whole lot more useful, is a stand alone Ubuntu dashboard similar to this, bust customizable to the user. I.E. adding applications and bookmarks and stuff instead of having this screwey version. If it weren't for Elisa having so many complications this harbour-launcher would be bearable. Another type of launcher or the ability to use something like Boxee as the media center instead of Elisa would be great. Development for this would be great. Or just getting the source code for this harbour-launcher would be great, I was able to change some of the visual text but I am not much of a programmer.

---

### Post by peryn on 2009-02-25
> **Islington said:**
> I know people were having problems with Open Office.

Try this out:

just write a shell script if you are lazy like me

```
#!/bin/bash
# This changes the appearance of idiotic applications
# Your favorite theme = GTKRCFILE
# GTK2_RC_FILES = path to your favorite theme's gtkrc (change /usr/share/themes to /home/*whatever*.themes if you wish)
GTKRCFILE=Human
GTK2_RC_FILES=/usr/share/themes/"$GTKRCFILE"/gtk-2.0/gtkrc "$@"

```

save it as "theme", under /home/user/
make it executable (chmod or use gui)
test it by running 
```
./theme ooffice -writer 
```
change the menus using the menu editor.

edit: check it out: I am running cianosmooth with ooffice-writer.
edit the second attached a hgiher resolution conversion of the HP wallpaper

don't help me - nothing changed at all :(

---

### Post by joey-elijah on 2009-02-25
> **cyrus80b said:**
> Question on this, and this might sound strange, but what exactly is this interface? Is it just a theme for the Ubuntu Window Manager (which I think is metacity) or an application. I downloaded what was posted in this thread, but it is just a theme. I am looking for the complete interface. The thing that brings together all the applications into a dashboard.

It's both.

There is a theme and icon set and there is the 'home panel' called harbour which looks like this: -

[IMG]http://www.geekzone.co.nz/images/blog/hpminimi/Screenshot.jpg[/IMG]

---

### Post by TJX09 on 2009-02-25
I installed the Glassy bleu theme in Ubuntu 8.10 and it's better than default but openoffice word look bad and Also input boxes and drop down menu is black/gray color in website.

How do i fix openoffice so it's usuable and how do i change the input box/dropdown color in websites.

---

### Post by Nigmah on 2009-02-27
joey how did you get yours to look like that?

---

### Post by nokor on 2009-02-27
Hi, all works fine for me.

But when i press on "start new program", i cant see all tabs T_T 

someone know the solution for this issue?

---

### Post by Chareos on 2009-02-28
Hi all

I was just wondering...
is there around a consolidate how-to of these 16+ pages with an Intrepid i386 package, to make all your efforts easily enjoyable by any ubuntu user ?

Thanks

---

### Post by Chareos on 2009-02-28
By the way, on Gnome-look I can see a theme, Overglossed Black, which looks to go along well with this HP thing. Maybe works better with openoffice too ?

---

### Post by S3NATOR on 2009-03-01
> **Chareos said:**
> Hi all

I was just wondering...
is there around a consolidate how-to of these 16+ pages with an Intrepid i386 package, to make all your efforts easily enjoyable by any ubuntu user ?

Thanks
Yes there is. a2h posted this earlier in the thread:

[http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/](http://a2h.uni.cc/wp/2009/02/14/installing-the-hp-minis-mie-interface-on-ubuntu/)

I went by that exact tutorial and it worked great.

S3N

---

### Post by brjoon1021 on 2009-03-02
The Firefox theme did not work for me:

1. it moved the sidebar to the right side of the screen and I can't move it back. This happened without asking!

2. There is no uninstall option for the theme. I tried to do so in safe mode, still hangs on perniciously like a dingleberry. Can you help me root this thing out whether it is by deleting the file somewhere or whatever...?


B

---

### Post by MyR on 2009-03-02
> **brjoon1021 said:**
> There is no uninstall option for the theme. I tried to do so in safe mode, still hangs on perniciously like a dingleberry. Can you help me root this thing out whether it is by deleting the file somewhere or whatever...?

Have you uninstalled the theme package you installed??

And/or in firefox: tools > add-ons > themes
and select another theme, like "default"

peace

---

### Post by TJX09 on 2009-03-02
Ok i installed glassy-bleu-browser-skin_0.5_all.deb, glassy-bleu-theme_21_all.deb, and gnome-backgrounds-hp_0.4_all.deb and Now how do i completely remove/uninstall all of those?

---

### Post by MyR on 2009-03-02
> **TJX09 said:**
> Ok i installed glassy-bleu-browser-skin_0.5_all.deb, glassy-bleu-theme_21_all.deb, and gnome-backgrounds-hp_0.4_all.deb and Now how do i completely remove/uninstall all of those?

use synaptic
system > administration > synaptic package manager

peace

---

### Post by ckundo on 2009-03-07
I installed the repo files and now the volume function keys don't work. Any thoughts? I'm on the HP mini running 8.1 intrepid.
Thanks

---

### Post by TJX09 on 2009-03-07
> **MyR said:**
> use synaptic
system > administration > synaptic package manager

peace

glassy-bleu-browser-skin_0.5_all.deb
glassy-bleu-theme_21_all.deb
gnome-backgrounds-hp_0.4_all.deb

I can't find those in the synaptic package manager. I remove theme by using sudo apt-get autoremove package name. I'm not completely sure if this is how to remove the theme but i tried it and it work for me..

---

### Post by K. Hendrik on 2009-03-07
Hi,
I'am trying the MIE look on a VM with ubuntu 8.10

there are a few more things I got working:


[SIZE="4"]login (GDM) theme[/SIZE]
[SIZE="3"]1. install the hp package[/SIZE]
Please install the package you find here [http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/main/binary-lpia/ubuntu-gdm-themes_0.29netbook0dennis8_all.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/main/binary-lpia/ubuntu-gdm-themes_0.29netbook0dennis8_all.deb")

[SIZE="3"]2. modify the installed theme[/SIZE]
If you try to login now an errormessage will pop up saying there is no item called checkbox in GDM, this is because hp patched the GDM to be able to show a checkbox that allows to select "don't ask for password next time" the standart GDM doesn't have that.
so execute
```

sudo gedit /usr/share/gdm/themes/HP-UMPC-GDM/HpGdmTheme.xml

```

and remove the following lines

```

<!--  autologin checkbox:
this is not a standard element in GDM; it was patched in for this project specifically. Will break on normal GNOME desktop systems! -->  

<item type="checkbox" id="autologin">
    <pos anchor="w" x="452" y="311" width="box" height="box" />
    <normal color="#99ccff" font="Liberation Sans 6"/>
    <stock type="autologin" />
</item>

```

now you may need to select the "HP GDM THEME" in the menu that's it.
(if you really want that checkbox experiment with the gdm package in the hp repos it breaks some dependencies but perhaps you can fix that. i just dont need the checkbox so I'am not spending time on that anymore)


[SIZE="4"]Firefox Add-ons[/SIZE]
there are tow add-ons in the repository
they add a enhanced maximizing funktion and a nicer look 
[http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-tabbar_0.1_all.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-tabbar_0.1_all.deb")
and
[http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-toolbar_0.3_all.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-toolbar_0.3_all.deb")

---

### Post by TJX09 on 2009-03-07
> **brjoon1021 said:**
> The Firefox theme did not work for me:

1. it moved the sidebar to the right side of the screen and I can't move it back. This happened without asking!

2. There is no uninstall option for the theme. I tried to do so in safe mode, still hangs on perniciously like a dingleberry. Can you help me root this thing out whether it is by deleting the file somewhere or whatever...?


B

If you want to remove the firefox theme all you have to do is use sudo apt-get autoremove glassy-bleu-browser-skin. I'm not completely sure if this is how to remove the theme but i tried it and it work for me.

---

### Post by TJX09 on 2009-03-07
Could we have a screenshot of the Firefox Add-on hp-browser-tabbar and hp-browser toolbar

---

### Post by K. Hendrik on 2009-03-07
just broke my vm as soon as it works again i will uplode a picture

---

### Post by K. Hendrik on 2009-03-07
ok I got some screen shots for you (the VM doesn't work right now exept for GDM, i took the firefox screenshot right befor it broke just didn't realies i did it on the host machine not on the vm).

edit:
just noticed the ok button in the GDM screenshot doesn't look right its normally darker (the standart hp mie theme style) but that's still broken richt now so it looks like this.
I shouldn't have installed the updates the new kernel is completly unusable.

---

### Post by TJX09 on 2009-03-07
> **K. Hendrik said:**
> ok I got some screen shots for you (the VM doesn't work right now exept for GDM, i took the firefox screenshot right befor it broke just didn't realies i did it on the host machine not on the vm).

edit:
just noticed the ok button in the GDM screenshot doesn't look right its normally darker (the standart hp mie theme style) but that's still broken richt now so it looks like this.
I shouldn't have installed the updates the new kernel is completly unusable.

I notice something different in the screen shots a new icon in the tab area are those the Firefox add-ons. Just wondering do i need to install glassy-bleu-browser-skin_0.5_all.deb then the Firefox add-ons or could i use the add-ons for use with default Firefox theme.

---

### Post by K. Hendrik on 2009-03-08
Yes the icon belongs to the hp-browser-tabbar, the little screen-icon belongs to the hp-browser-toolbar and can be used for maximiezing websides borderless. The addons should be usable without the hp-theme , i will try that later.

edit:
tried it, they work without the theme

---

### Post by linuxnoob18 on 2009-03-10
> **wildcard said:**
> Update on this one, guys...

If you just want the new theme, here's how I did it, without adding things to Synaptic.

Open your browser of choice and go to [http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/)

This should give you links to click on; click on Universe and then Binary-lpia. In here, save the glassy-bleu-browser-skin_0.5_all.deb , glassy-bleu-theme_21_all.deb , and 	gnome-backgrounds-hp_0.4_all.deb files. Just save these to your Desktop. As these are compiled with "all" rather than "lpia", these should be global files that will work for 386 or 64-bit distros. Click on the files on your desktop and Package Installer should handle the rest.*

Presumably, you could go into the main, restricted, or multiverse folders and do the same thing for any .deb files that do not have lpia in their name and have them work on your distro.*



*standard disclaimer of me not being responsible for you hosing your system while trying to follow these instructions does apply here; they worked for me, though.

awesome theme

---

### Post by pipposanta on 2009-03-11
a2h site doesn't work...

---

### Post by days_of_ruin on 2009-03-11
> **K. Hendrik said:**
> Hi,
I'am trying the MIE look on a VM with ubuntu 8.10

there are a few more things I got working:


[SIZE="4"]login (GDM) theme[/SIZE]
[SIZE="3"]1. install the hp package[/SIZE]
Please install the package you find here [http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/main/binary-lpia/ubuntu-gdm-themes_0.29netbook0dennis8_all.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/main/binary-lpia/ubuntu-gdm-themes_0.29netbook0dennis8_all.deb")

[SIZE="3"]2. modify the installed theme[/SIZE]
If you try to login now an errormessage will pop up saying there is no item called checkbox in GDM, this is because hp patched the GDM to be able to show a checkbox that allows to select "don't ask for password next time" the standart GDM doesn't have that.
so execute
```

sudo gedit /usr/share/gdm/themes/HP-UMPC-GDM/HpGdmTheme.xml

```

and remove the following lines

```

<!--  autologin checkbox:
this is not a standard element in GDM; it was patched in for this project specifically. Will break on normal GNOME desktop systems! -->  

<item type="checkbox" id="autologin">
    <pos anchor="w" x="452" y="311" width="box" height="box" />
    <normal color="#99ccff" font="Liberation Sans 6"/>
    <stock type="autologin" />
</item>

```

now you may need to select the "HP GDM THEME" in the menu that's it.
(if you really want that checkbox experiment with the gdm package in the hp repos it breaks some dependencies but perhaps you can fix that. i just dont need the checkbox so I'am not spending time on that anymore)


[SIZE="4"]Firefox Add-ons[/SIZE]
there are tow add-ons in the repository
they add a enhanced maximizing funktion and a nicer look 
[http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-tabbar_0.1_all.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-tabbar_0.1_all.deb")
and
[http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-toolbar_0.3_all.deb]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-toolbar_0.3_all.deb")

Someone should post this to gnome-look.Edited like you said of course.

---

### Post by psychofish25 on 2009-03-14
Help!

I've installed nearly everything, but my mail, bookmarks, and elisa media things aren't working. 

that a2h site is a broken link :(

please help (i have the firefox addon for bookmarks but it still doesn't work)

---

### Post by Prominence on 2009-03-17
Have you ever fixed OpenOffice?

---

### Post by K. Hendrik on 2009-03-18
[SIZE="4"]@psychofish25:[/SIZE]

[SIZE="4"]elisa:[/SIZE]

```

sudo echo /etc/apt/sources.list >> "deb http://ppa.launchpad.net/elisa-developers/ppa/ubuntu intrepid main"
sudo apt-get install elisa

```


[SIZE="4"]thunderbird mail plugin:[/SIZE]

you need thunderbird for this to work
```

wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/mail-watcher-extension_0.6_all.deb
sudo dpkg -i mail-watcher-extension_0.6_all.deb

```


[SIZE="4"]firefox bookmarks:[/SIZE]

you don't need the webfav-plugin uninstall it if you installed it before.
```

wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/gnome-web-photo_0.3-0ubuntu2netbook0dennis2_lpia.deb
sudo apt-get install libxul0d
sudo dpkg -i --force-architecture gnome-web-photo_0.3-0ubuntu2netbook0dennis2_lpia.deb

```


a2h's site is not completely down i can reach it some times but not always.



[SIZE="4"]@Prominence:
[/SIZE]
> **Islington said:**
> I know people were having problems with Open Office.

Try this out:

just write a shell script if you are lazy like me

```
#!/bin/bash
# This changes the appearance of idiotic applications
# Your favorite theme = GTKRCFILE
# GTK2_RC_FILES = path to your favorite theme's gtkrc (change /usr/share/themes to /home/*whatever*.themes if you wish)
GTKRCFILE=Human
GTK2_RC_FILES=/usr/share/themes/"$GTKRCFILE"/gtk-2.0/gtkrc "$@"

```

save it as "theme", under /home/user/
make it executable (chmod or use gui)
test it by running 
```
./theme ooffice -writer 
```
change the menus using the menu editor.

edit: check it out: I am running cianosmooth with ooffice-writer.
edit the second attached a hgiher resolution conversion of the HP wallpaper

---

### Post by MyR on 2009-03-18
Note to anyone setting an OpenOffice.org theme: the theme is case-sensitive, so use Human or Human-Clearlooks (they work the best).

Also how do you link the command ooffice to the themed command?  So that when you open a document it automatically uses the set theme.  I'm sure it's pretty easy but I'm not that familiar with it (symbolic link vs hard link etc). Is it cd /usr/bin && ln -sb ooffice /home/$user/theme ?  I don't want to mess up my system.

peace

---

### Post by MyR on 2009-03-18
All right here's my guide to fixing open office icons etc:

1. Make a text file telling open office to use a theme:
```
gedit ~/Documents/theme
```
put this in the file and save:
```
#!/bin/bash
GTKRCFILE=Human-Clearlooks
GTK2_RC_FILES=/usr/share/themes/"$GTKRCFILE"/gtk-2.0/gtkrc ooffice2 "$@"
```
then make it executable:
```
chmod +x ~/Documents/theme
```

2. Link the command ooffice to instead use your custom command with the theme:
```
cd /usr/bin
sudo cp ooffice ooffice2
sudo ln -sbv /home/[YOUR_USER_NAME]/Documents/theme ooffice
```

That's it!  I got a small error with the first document I opened but after that it works fine.

You can undo it at any time by:
```
sudo mv /usr/bin/ooffice~ /usr/bin/ooffice
```

peace

---

### Post by Prominence on 2009-03-20
Is there a more simple and direct way...? I'm not a linux master, and am absolutely stupid when it comes to that stuff, I can do some of that, but at other parts, I am completely lost.

---

### Post by MyR on 2009-03-22
> **Prominence said:**
> Is there a more simple and direct way...? I'm not a linux master, and am absolutely stupid when it comes to that stuff, I can do some of that, but at other parts, I am completely lost.

Please let me know if anything in my post was unclear.

You just need to enter the commands, changing [YOUR_USER_NAME] to your user name, & the put the text in the text file as described.

---

### Post by Prominence on 2009-03-22
It didn't work, or I did something wrong, did as you said, and no changes

---

### Post by MyR on 2009-03-23
> **Prominence said:**
> It didn't work, or I did something wrong, did as you said, and no changes

can you paste the output of
```
cat ~/Documents/theme
```
```
ls -l ~/Documents/theme
```
and last but not least
```
ls /usr/bin | grep ooffice
```

and I'll see if I can figure out what went wrong ;]

peace

---

### Post by Prominence on 2009-03-24
grayson@iGrayson:~$ cat ~/Documents/theme
#!/bin/bash 
GTKRCFILE=Human-Clearlooks 
GTK2_RC_FILES=/usr/share/themes/"$GTKRCFILE"/gtk-2.0/gtkrc ooffice2 "$@"
grayson@iGrayson:~$ 

grayson@iGrayson:~$ ls -l ~/Documents/theme
-rwxr-xr-x 1 grayson grayson 114 2009-03-22 23:50 /home/grayson/Documents/theme
grayson@iGrayson:~$ 

grayson@iGrayson:~$ ls /usr/bin | grep ooffice
ooffice
grayson@iGrayson:~$

---

### Post by MyR on 2009-03-24
> **Prominence said:**
> grayson@iGrayson:~$ cat ~/Documents/theme
#!/bin/bash 
GTKRCFILE=Human-Clearlooks 
GTK2_RC_FILES=/usr/share/themes/"$GTKRCFILE"/gtk-2.0/gtkrc ooffice2 "$@"
grayson@iGrayson:~$ 

grayson@iGrayson:~$ ls -l ~/Documents/theme
-rwxr-xr-x 1 grayson grayson 114 2009-03-22 23:50 /home/grayson/Documents/theme
grayson@iGrayson:~$ 

grayson@iGrayson:~$ ls /usr/bin | grep ooffice
ooffice
grayson@iGrayson:~$
You successfully completed step 1 above but not step 2 ;]

just run:
```
cd /usr/bin
sudo cp ooffice ooffice2
sudo ln -sbv /home/grayson/Documents/theme ooffice
```
and you should be all set.
peace

---

### Post by Prominence on 2009-03-24
Thank you so much!

---

### Post by Prominence on 2009-03-25
Something went wrong, and it has something to do with the fix, it broke OpenOffice somehow, and I had to reinstall it

---

### Post by peakshysteria on 2009-03-28
Installed Intrepid Ibex on our Hp Mini 2133 four weeks ago (Suse wasn't for us). All is running very smooth except tv-out and we can't make it run the right resolution.

How can we edit our Xorg? We can't open it. We have tried: sudo dpkg-reconfigure -phigh xserver-xorg but it doesn't seem to work at all. So I guess this is the wrong command. We found a howto at: [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133#Video](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133#Video) Driver Fix but we miss the command to open Xorg. Anyone?

---

### Post by MyR on 2009-03-28
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

peace

P.S.  the instructions are listed in the wiki right in the secion you were looking at.

---

### Post by mlentink on 2009-04-09
And now for something completely different.....

It seems that (almost) all of the above applies to installing the MIE-interface to an i386-platform.

But I have a Compaq Mini 700, identical to the HP mini 1000, the platform MIE was made for. Unfortunately they don't sell the MIE editions here. So I'm dual booting with XP on the harddisk and UNR on a 8GB SDHC.

How would I go about getting MIE on this system? I figure I have 2 choices:

1. Going with HP's restore image, wipe the disk and have a new HP Mini MIE. Which is based on 8.04, where I'm running UNR 9.04.... (which I don't want to give up easily because of new stuff)

2. Adding the HP-repo's and then basically reinstalling manually (time consuming, but probably worth it, since it would give me a MIE 9.04, which noone else has (or do they?)

Any opinions as to how I should go about this?

---

### Post by bluedragon436 on 2009-04-20
I am wanting to get the MIE from HP, does anyone know if there is anywhere that I can get a CD with the software/Drivers loaded on it??  I have been trying to use the Image files that you can get from HP's site... and for whatever reason I can never get it to let me load it from my thumb drive or my external HD like it should?? Or any help on how to make this a bootable file would be great!!

---

### Post by TaylorJG on 2009-04-29
Did anyone get the HP Mini 2133 to run 9.04 UNR?

Everything seems to work fine outside of the netbook launcher. By this I mean that after an application or menu is open, everything works fine, but inside the netbook launcher, everything lags horribly...

Any suggestions?

---

### Post by puccaso on 2009-04-30
i think its because of the lack of drm/opengl working properly... the new ui api... i cant remmeber what its called now, uses opengl as a backend/ glitz or something... clutter - thats its... 

i dont suppose you have drm working? or compiz or something else for that matter... working from the hardware... i can get metacity to enable composition via software.. but its horridly slow..

---

### Post by MyR on 2009-04-30
Has anyone else experienced problems with elisa in 9.04 jaunty?  It crashes shortly after starting, making the harbour-launcher UI unusable because it trys to restart elisa each time it crashes.
Incidentally ubuntu's UNR launcher thing works quite well but I don't care for it and that's not the topic of this thread.
I upgraded from 8.10 if that makes any difference. I even installed some missing dependencies that elisa was complaining of in the terminal.

here's the terminal output from the crash:
```
$ elisa
Launcher core version: 0.5.28
Current core version: 0.5.28
/usr/lib/python2.6/dist-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
Elisa failed to initialize: [Failure instance: Traceback: <type 'exceptions.AttributeError'>: 'NoneType' object has no attribute 'connect'
/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py:113:wrapper
/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py:217:callback
/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py:225:simulate
/usr/lib/python2.6/dist-packages/twisted/internet/base.py:757:runUntilCurrent
--- <exception caught here> ---
/usr/lib/python2.6/dist-packages/twisted/internet/task.py:251:_tick
/usr/lib/python2.6/dist-packages/elisa/core/interface_controller.py:104:load_frontends_iter
/usr/lib/python2.6/dist-packages/elisa/core/plugin_registry.py:1055:create_component
/usr/lib/python2.6/dist-packages/elisa/core/component.py:128:create
/usr/lib/python2.6/dist-packages/elisa/plugins/pigment/pigment_frontend.py:470:initialize
/usr/lib/python2.6/dist-packages/elisa/plugins/pigment/pigment_frontend.py:563:_initialize_theme
]
```

---

### Post by biada on 2009-05-01
I am also having issues with HP MIE on 9.04.  The only thing I can get to work are the themes, wallpaper, firefox theme, and Open Office theme.  

Everything else doesn't work. 

I cannot get any of the applications to load on the desktop. 

Reason:  Cannot install the following package, they are all made for the 8.10


[LIST=1]
[*][URL="http://cid-531bd5d7cebb320c.skydrive.live.com/self.aspx/Public/HP%20Mie/libpigment0.3-8%7C_0.3.11-1%7CFppa2-intrepid1-1%7C_i386.deb"]ibpigment
[/URL]
[*][python-pgm]("http://cid-531bd5d7cebb320c.skydrive.live.com/self.aspx/Public/HP%20Mie/python-pgm%7C_0.3.8-1%7CFppa1-intrepid1-1%7C_i386.deb")
[*][python-elisa]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/main/binary-lpia/python-elisa_0.5.15.5-0dennis1_all.deb")
[*][elisa]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/main/binary-lpia/elisa_0.5.15.5-0dennis1_all.deb")
[*][elisa-plugins-good]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/main/binary-lpia/elisa-plugins-good_0.5.15.5-0dennis1_all.deb")
[*][elisa-plugins-bad]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/main/binary-lpia/elisa-plugins-bad_0.5.15.5-0dennis9_all.deb")
[*][elisa-plugins-ugly]("http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/elisa-plugins-ugly_0.5.15.5-0dennis1_all.deb")
[/LIST]

---

### Post by peakshysteria on 2009-05-01
> **MyR said:**
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

peace

P.S.  the instructions are listed in the wiki right in the secion you were looking at.

Thanks man. Now running 9.04 Jaunty Jackalope desktop edition. All working out of the box :)

---

### Post by K. Hendrik on 2009-05-04
For those having problems with elisa in jaunty just install it from the developers repository works like a charm
```

sudo echo "deb http://ppa.launchpad.net/elisa-developers/ppa/ubuntu intrepid main" >> /etc/apt/sources.list
sudo apt-get install elisa

```

I am also trying to write a install script right now it looks like this

```

#!/bin/bash

###############################################################################
# HP MIE installation script for ubuntu 9.04 jaunty jackalope                 #
###############################################################################

cd ~
mkdir ./MIE
cd ./MIE

###########################################################
# Basic Theme for ubuntu                                  #
###########################################################
## GTK2 Theme
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/glassy-bleu-theme_21_all.deb
sudo dpkg -i ./glassy-bleu-theme_21_all.deb

## Wallpaper
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/gnome-backgrounds-hp_0.4_all.deb
sudo dpkg -i ./gnome-backgrounds-hp_0.4_all.deb

## Harbour-Launcher
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/harbour-launcher_0.99_lpia.deb
sudo dpkg -i --force-architecture --force-depends ./harbour-launcher_0.99_lpia.deb

## GDM Theme
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/main/binary-lpia/ubuntu-gdm-themes_0.29netbook0dennis8_all.deb
sudo dpkg -i /ubuntu-gdm-themes_0.29netbook0dennis8_all.deb
# remove the checkbox item that doesn't exist in standart GDM
sudo sed -i '/<!--  autologin checkbox:/,/<\/item>/d' /usr/share/gdm/themes/HP-UMPC-GDM/HpGdmTheme.xml

###########################################################
# Theme for Firefox and Firefox Add-ons                   #
###########################################################
## Theme
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/glassy-bleu-browser-skin_0.5_all.deb
sudo dpkg -i ./glassy-bleu-browser-skin_0.5_all.deb

## Tabbar
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-tabbar_0.1_all.deb
sudo dpkg -i ./hp-browser-tabbar_0.1_all.deb

## Toolbar
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/hp-browser-toolbar_0.3_all.deb
sudo dpkg -i ./hp-browser-toolbar_0.3_all.deb

## Website preview for the harbour-launcher
# start firefox to create the .mozilla directory
firefox
cd ~/.mozilla
ln -s firefox "web browser"
cd ~/MIE
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/gnome-web-photo_0.3-0ubuntu2netbook0dennis2_lpia.deb
sudo apt-get install libxul0d -y
sudo dpkg -i --force-architecture ./gnome-web-photo_0.3-0ubuntu2netbook0dennis2_lpia.deb


###########################################################
# Thunderbird + Theme and Add-ons                         #
###########################################################
## Thunderbird
sudo apt-get install thunderbird -y

## Theme
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/restricted/binary-lpia/hp-tbird-theme_0.5_all.deb
sudo dpkg -i ./hp-tbird-theme_0.5_all.deb

## Mailwatcher for the harbour-launcher
wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/mail-watcher-extension_0.6_all.deb
sudo dpkg -i ./mail-watcher-extension_0.6_all.deb


###########################################################
# Elisa Mediacenter                                       #
###########################################################
## Elisa
sudo echo "deb http://ppa.launchpad.net/elisa-developers/ppa/ubuntu intrepid main" >> /etc/apt/sources.list
sudo apt-get install elisa -y

```

firefox pops up during install to make sure that the .mozilla directory and its content is createt just close it after it's loaded and the script will continue.

right now it doesn't report errors if they happen cause I'am not so familar with scripting but perhaps some one can improve this.

rightnow open office is not beeing fixed by this script and it would be nice to download the key for the elisa repository too.

I havent tested this only tryed it once and then fixed some things, so only use it if you know what you're doing.

you also need to be root to run this script or it will promt for a password.

---

### Post by mlentink on 2009-05-04
> **K. Hendrik said:**
> I am also trying to write a install script right now it looks like this


Thanks. Though I may shy away from using your script, the individual commands may lead me to a solution to my earlier question....

---

### Post by mlentink on 2009-05-06
I also see that you frequently use:
```
sudo dpkg -i --force-architecture
```

Assuming I'm installing this on UNR Jaunty on a HP Mini 1000 (or Compaq Mini 700, which is equivalent), would this be necessary? Those already have a lpia architecture. Or is UNR i386 generic?

Hope you see this in teh foreseeable future

---

### Post by K. Hendrik on 2009-05-07
if you have a lpia architecture there would be no need to force the architecture I think you can look up your architecture with
```
uname -a
```

---

### Post by ontwowheels on 2009-05-11
Does glassy-bleu work with 9.04?  Also, I tried adding the HP sources at the beginning of this thread and got errors when doing the rebuild of the package index.

I would like to try running this theme on a non-mini but can't find it.

THANKS

---

### Post by K. Hendrik on 2009-05-12
glassy-blue works, you can't just add the repositories because they are for lpia architecture 
try:
```

wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/glassy-bleu-theme_21_all.deb
sudo dpkg -i ./glassy-bleu-theme_21_all.deb

```

---

### Post by ontwowheels on 2009-05-12
> **K. Hendrik said:**
> glassy-blue works, you can't just add the repositories because they are for lpia architecture 
try:
```

wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/glassy-bleu-theme_21_all.deb
sudo dpkg -i ./glassy-bleu-theme_21_all.deb

```

THANKS, I will give this a try.

---

### Post by ontwowheels on 2009-05-12
> **K. Hendrik said:**
> glassy-blue works, you can't just add the repositories because they are for lpia architecture 
try:
```

wget http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/universe/binary-lpia/glassy-bleu-theme_21_all.deb
sudo dpkg -i ./glassy-bleu-theme_21_all.deb

```

Jim Carry in Ace Ventura..."LIKE A GLOVEEEEE"

Worked perfectly....THANKS

---

### Post by Prominence on 2009-05-19
I tried the previous icon fix in my fresh Ubuntu 9.04 EXT4 installation, and after I fixed it, applied the fix, the system would freeze and if I got it to work, it would be black, pitch black, no icons and the text is hardly readable. I need a fix because this theme is by far my favorite Gnome theme, so please help.

---

### Post by K. Hendrik on 2009-05-24
what fix are you talking about? the ooo?

---

### Post by Prominence on 2009-05-26
Yes, the openoffice fix.

---

### Post by randiroo76073 on 2009-06-02
Updated link as of today:

[http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/](http://hpmini.archive.canonical.com/mie/dists/hardy-hpmini/)

---

### Post by Prominence on 2009-06-21
What does that do?

---

### Post by dmoreno on 2009-08-24
I have installed the Glassy Bleu theme correctly in Ubuntu on my EEE 701 netbook, and have selected it in Theme Preferences.
However, whenever I reboot, the Desktop is shown with the default theme instead of the new Glassy Bleu theme.
What is even stranger is that any attempt to access the Theme Preferences app results in the Glassy Bleu theme being automatically aplied again. No need to change anything (in fact the Glassy Bleu theme is still selected in Theme Preferences).
Does anyone have experienced this behaviour? Any idea about how to fix it?
 
Thanks.

---

### Post by artshark on 2009-08-26
can someone answer a MIE related question here? i use MIE but no longer use thunderbird. when i deleted my gmail from Thunderbird, i had one mail in my inbox at the time of deletion. this one mail reminder has stuck on my harbour thunderbird panel, and, along with all the other emails on the panel, i would like to clear it. does anyone know how to do this?
thanks

---

### Post by familiaaencoada@msn.com on 2009-11-02
Hi i cant get the repos right i have Karmic Koala i need help
> **timm.mccoy said:**
> the theme is called bleu-glass or something like that. just add these sources to your sources.list (or add them through System -> Administration -> Software Sources)

without further ado, here are the repo's you want.

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse restricted

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-updates main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-updates main universe multiverse restricted

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-security main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-security main universe multiverse restricted

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-hpmini main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-hpmini main universe multiverse restricted

let me know if that's all you need. If not I can look into it a little more, that worked fine for me (I installed Ubuntu Netbook Remix, added the repositories and that was it)

---

### Post by viz3rd on 2012-01-12
I know this is quite old stuff here but still it suits my requirement. So, Is there any way to get this interface work on 1080p? also can we re-theme it?

---

### Post by overdrank on 2012-01-12
Hi and please start a new thread with your issues. Thread closed.

---

