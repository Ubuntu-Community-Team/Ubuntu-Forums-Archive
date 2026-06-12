---
title: "Window Managers for Beginners"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by Kyral on 2005-11-07
Just like how my Terminal For Beginners came into being, I have heard the same general question. "What is a Window Manager and how do they work" (or basically that)

Well, here I am again to explain another fundemental part of the Linux system, in my usual flair :D

Now before we can understand Window Managers, we have to understand what makes the GUI system in Unix-based systems(Linux, OSX, the BSDs, etc) from the GUI system in XP. Now you know that in XP, if GUI crashes, it takes the entire system with it. Because for the most part, the GUI is the system (Feel free to correct me, I don't know a lot about the inner workings of XP). However in Unix-based systems, the GUI is separate from the system, in the form of X.

Now what is X? Well, its technically called "The X Windows System". It is also referred to as the X Server, which is also right, but for techinical reasons that aren't need to be understood now. Most of the time its referred to as X. What makes X different is that it frankly doesn't CARE what runs on it. It just handles drawing the screen, plus mouse and keyboard input. This allows for the almost infinite various GUI designs you see on Linux systems.

Now if X doesn't care what the GUI looks like, what does? Well, now we are at Window Managers. Window Managers are what control the placement and look of the application windows. Most also provide the menus we interact with and the cool panels and docks that we love so much. There are many Window Managers out there. What follows is a list of the most common and popular

Wait a SECOND! I can't do it yet! I have to explain one other concept. The Desktop Environment. There are only 3 Desktop Enviroments in the Linux world. XFCE, GNOME, and KDE. What makes a Desktop Environment different than a Window Manager? Basically, the amount of stuff that it provides. Desktop Environments typically have thier own File Managers, default Web Browsers, graphical Control Panels, and applets. However, they also need a Window Manager to run on top of. Now KDE has one integrated in, as does XFCE. But GNOME doesn't, and depends on one of the Window Managers listed below to help it out. Okay? Cool! Lets go!

Note on installing: Last time I checked, all of these installed entries in the GDM/KDM Sessions Menu, so to use them once you have installed them, just logout, find the "Sessions" button/menu on your login screen, and pick one :D The DM may ask you if you want it to be default, thats your choice. I'd choose "Only for This Session" if you are just trying it out, that way when you logout/login again, you will login to whatever you normally do.

TWM (Tab Window Manager or Tom's Window Manager): The very basic and default WM that X ships with. In its default state its not much more than a way to have multiple terminals on the screen. However rumor has it that its very customizable if you know C and about the XLibs...
[URL="http://blackboxwm.sourceforge.net/"]
BlackBox[/URL] - This WM is one of the "Box" series of Window Managers. Very minimalistic, yet also very FAST. Just a step above TWM in its default configuration, it is nonetheless a favorite with power users.

```
sudo apt-get install bbconf bbappconf bbpager blackbox blackbox-themes
``` 
[FluxBox]("http://fluxbox.sourceforge.net/") - Fluxbox is decended from Blackbox, and as such inherits a lot of its traits. Aims to be VERY simple, yet also has a bunch more things that Blackbox lacks. Most of its configuration is done with text files. In its default configuration it only provides a taskbar and a main menu which is accessed via right click. However I have seen INCREDIBLE looking desktops come out of Fluxbox.

```
sudo apt-get install fluxbox fbdesk fbpager fluxconf
``` 
[FVWM]("http://www.fvwm.org/"): (F Virtual Window Manager) - Directly decended from TWM, FVWM nonetheless is still kicking, and many other Window Managers are decended from it. Almost endlessly customizable, its still a favorite. ([Wikipedia Entry with MUCH more info]("http://en.wikipedia.org/wiki/FVWM"))

```
sudo apt-get install fvwm
``` 
[Enlightenment]("http://www.enlightenment.org/") - The very powerful WM, distantly decended from FVWM, Enlightenment is one of the favorite Window Managers today, going toe to toe with Desktop Environments like XFCE, GNOME, and KDE. Known for its unique take on the Virtual Desktop concept, Enlightenment is the Window Manager that is closest to being a Desktop Enviroment. This is even more true with the pending release of Enlightenment DR17, or just "E17", which promises to knock out everyone with how much eyecandy it can produce with so little resources. It should be noted that Enlightenment can be combined with GNOME to produce what is referred to as "Enlightened GNOME".

```
sudo apt-get install enlightenment enlightenment-theme-bluesteel enlightenment-theme-brushedmetal enlightenment-theme-ganymade enlightenment-theme-shinymetal epplets eterm e16keyedit e16menuedit2
``` 
[MetaCity]("http://en.wikipedia.org/wiki/Metacity") - This Window Manager is only notable for being the default Window Manager in GNOME.

```
sudo apt-get install metacity metacity-themes
``` 
[OpenBox]("http://www.icculus.org/openbox/") - Another WM based on Blackbox, its quick, light, and fast. Its often used to replace MetaCity in GNOME. 

```
sudo apt-get install openbox openbox-themes obconf
``` 
Desktop Environments

[Mezzo]("http://en.wikipedia.org/wiki/Mezzo_%28desktop_environment%29") - This still in development Desktop Enviroment is the star attraction for [SymphonyOS]("http://www.symphonyos.com/") and looks very promising. It completely discards the traditional GUI design concepts that GNOME, KDE, and XFCE seem to follow in favor of making the desktop more usable. Its really something that has to be used to believe. Distantly based off of FVWM. In case you can't tell, I think this project is going places :D

Can't be installed on any other Linux except SymphonyOS right now

[XFCE]("http://www.xfce.org/") - XFCE, the 3rd Desktop Environment that is almost always in the shadow of GNOME and KDE, is the default desktop environment for Xubuntu. Very streamlined, it is the DE of choice on slightly older systems. However it also boasts some very cool powertoys, namely the best compositing manager out of the three Desktop Environments (compositing is what lets things like drop shadows and "true" transparency happen). Many themes are available, and even shares many themes with GNOME due to thier common language of GTK. I personally run this DE. [Themes]("http://www.xfce-look.org") 

```
sudo apt-get install xubuntu-desktop
``` 
[GNOME]("http://www.ubuntuforums.org/www.gnome.org") (pronouced "Guh-nome") - One of the Big Two Desktop Environments alongside KDE, GNOME is the default Desktop Environment of Ubuntu and also of the GNU Project. Created in 1997 out of concern that KDE's use of the Qt libraries would take it out of the realm of free software, GNOME uses the GIMP Toolkit, better known as GTK. It comes equipped with Epiphany as its web browser, Evolution for mail, GAIM for IM, The GIMP for Image Work, Abiword for Word Processing, Totem for videos, Nautilus for file browsing, and Rhythmbox for music playing. Unique out of the Desktop Environments in that it doesn't have its own Window Manager. Currenlty uses MetaCity, in the past has used Enlightenment and Sawfish as defaults. Notice that Ubuntu's GNOME doesn't come with the apps I listed as default. Those apps are actually apps that are designed to fit in with GNOME. [Themes and more]("www.gnome-look.org")

```
sudo apt-get install ubuntu-desktop
``` 
[KDE]("www.kde.org") (K Desktop Environment) - The original Linux Desktop Environment and the default for Kubuntu users, KDE is the main "rival" for GNOME. It was created in 1996 and ran into some controversy with the Free Software folks over its use of the then proprietary Qt Libraries as its method of drawing graphics. More "eye-candy" that GNOME or XFCE, KDE has been accused of trying to emulate Windows XP in style and look. However many VERY cool apps have come from KDE, namely Amorok, k3b, and Krita. Currently uses Konqeror(sp?) for web/file management, Kontact for email, Kopete for IM, and Adept as a replacement to Synaptic. It also has a good Compositing manager. [Themes and more]("www.kde-look.org")

```
sudo apt-get install kubuntu-desktop
``` 
Oh, one final note. There is no such thing as a "GNOME App" or a "KDE App". It doesn't matter what WM/DE you are using, they will work the same. Granted it may look a little out of place, but it will still work perfectly. Heck I run XFCE and I use k3b on a regular basis. 

So I hope I have once again provided information on another part of the Linux Mythos.

EDIT: Added install commands
EDIT: Fixed broken links

---

### Post by 23meg on 2005-11-07
Well written. Those unfamiliar with window managers in general will also find a lot of useful info (and screenshots, yes) [here]("http://xwinman.org/").

---

### Post by Kyral on 2005-11-07
Yah I was meaning to put in screenshots....dunno why I forgot...

---

### Post by Cufishing on 2005-11-07
Thanks for the enlightment. :razz:

---

### Post by Luffield on 2005-11-07
Thanks Kyral, I needed that! :)
However, either I didn't understand something or  there is a little contradiction there: you say early on that Gnome doesn't have an integrated window manager, and I expected to read which window manager of those you listed is used in Ubuntu, but it never came - and then you wrote "GNOME is the default Window Manager of Ubuntu". So I'm a bit confused now...

---

### Post by raublekick on 2005-11-07
Excellent read. Good, detailed information in a non-technical sense!

Luffield, Gnome is the default Desktop Environment for Ubuntu, and the default Window Manager for Gnome in Ubuntu is MetaCity

---

### Post by MichaelM on 2005-11-07
[QUOTE=Luffield]Thanks Kyral, I needed that! :)
However, either I didn't understand something or  there is a little contradiction there: you say early on that Gnome doesn't have an integrated window manager, and I expected to read which window manager of those you listed is used in Ubuntu, but it never came - and then you wrote "GNOME is the default Window Manager of Ubuntu". So I'm a bit confused now...[/QUOTE]
Actually, he mentioned twice that Metacity is GNOME's default window manager. :)
And you're right; GNOME is the default desktop environment, not window manager, of Ubuntu.

---

### Post by 23meg on 2005-11-07
[edited out]

---

### Post by Kyral on 2005-11-07
Ooops typo...sorry...Fixed :D

---

### Post by chazzjazz on 2005-11-07
don't you think you should refrain from using "window" or "windows" in a linux context???

confuses noobs like  me 

Use some thing like workbench a la Amiga etc

"Image a world without Windows.....Free ya Soul"

Slogan for you ;)

---

### Post by 23meg on 2005-11-07
[QUOTE=chazzjazz]don't you think you should refrain from using "window" or "windows" in a linux context???
[/QUOTE]

There were windows before Windows, and they're still here today outside of Windows as well; Microsoft didn't invent them. Plus, these window managers and desktop environments aren't Linux-specific; you can run Gnome, KDE and others on other open source platforms such as BSD.

---

### Post by gabhla on 2005-11-07
That was very informative.  I actually learned something!  I knew some of this, but not in the right context.  Thanks.  That took some effort and I appreciate it.

---

### Post by chazzjazz on 2005-11-07
[QUOTE=23meg]There were windows before Windows, and they're still here today outside of Windows as well; Microsoft didn't invent them. Plus, these window managers and desktop environments aren't Linux-specific; you can run Gnome, KDE and others on other open source platforms such as BSD.[/QUOTE]

be that as it may, you cant compete with the M$ hype and jargon, they have won the battle through brtue force.

If you aim to be different then act different: Vive la difference ;)

---

### Post by Kyral on 2005-11-07
When you consider that the X Windows System came into being in 1984 (at MIT), I think that X Windows predates MS :D

---

### Post by chazzjazz on 2005-11-07
[QUOTE=Kyral]When you consider that the X Windows System came into being in 1984 (at MIT), I think that X Windows predates MS :D[/QUOTE]

Dont matter, when vista comes out with the eye candies, even MAC heads will go ga-ga, and then it will will be a world locked in by gates and windows :)

mac or xerox or ibm invented the mouse, but hey only windows mice have gazillion buttons ;)

---

### Post by Kyral on 2005-11-07
When Vista comes out people will be happy for a second, then realize that DRM has invaded and come running to Linux and OS X

---

### Post by endersshadow on 2005-11-07
I'd just like to add something a bit more for Metacity.  I think it gets a lot of undeserved hate...I actually really like it :)

_Metacity_ - A window manager designed to be crisp, light, and rather minimalistic.  While the main complaint is the lack of customizability, it was designed for ease of use and a simple and complete window manager "out of the box."  It's customizability is limited to themes, not functionality.  For these reasons, it has become the default window manager of Gnome.

---

### Post by chazzjazz on 2005-11-07
lol dont you worry about DRM, i guess only the iTUNES people would care but hey...nobody on windows really uses windows media player if they can help it ;)

---

### Post by endersshadow on 2005-11-07
[QUOTE=chazzjazz]lol dont you worry about DRM, i guess only the iTUNES people would care but hey...nobody on windows really uses windows media player if they can help it ;)[/QUOTE]

Most people who use Windows don't know anything different than WMP...

---

### Post by chazzjazz on 2005-11-07
erhmmm, realplayer, quicktime, and the lite versions inc wmp lite.

VLC, Zoomplayer, windvd, powerdvd ;) we are cluey ;)

---

### Post by endersshadow on 2005-11-07
I'm not going to turn this into a flame war, but trust me, WMP is used by people ALL the time...

P.S.-this is the last I'll say about it in this thread, I promise...now...back to Window Managers :-D

---

### Post by Borusa on 2005-11-08
On the original : Cracking post, gromit.

The ability to try different window managers and desktop environments without losing software that you have installed is one of the undoubted (and rather undersung) strengths of Linux. 

Might be nice to have a bit on how to switch between which window manager is being used by GNOME?

---

### Post by Jonne on 2005-11-08
[QUOTE=chazzjazz]Dont matter, when vista comes out with the eye candies, even MAC heads will go ga-ga[/QUOTE]
don't be so sure of that.

If the current beta's are an indication, Mac OS X' interface still looks way better. Besides even if microsoft suddenly adds some innovative stuff (as opposed to just a theme and some transparency effects and 3d transitions), Mac fanboys will never admit that something else is better than their beloved OS, it has always been like that ;).

---

### Post by cityismine on 2005-11-08
I'm still a little confused about DE's and WM's.  You say that a DE has it's own file manger, browser, etc., and WM's don't.  So if you take a WM and add these features, do you end up with a DE?

---

### Post by 23meg on 2005-11-08
[QUOTE=cityismine]I'm still a little confused about DE's and WM's.  You say that a DE has it's own file manger, browser, etc., and WM's don't.  So if you take a WM and add these features, do you end up with a DE?[/QUOTE]

That's about right; you can throw all those things together and call it a DE. But one more thing that distinguishes Gnome, XFCE and KDE from window managers in general is that they have their own libraries and widget sets (GTK/QT), and many programming languages have bindings to these, so that developers can easily reuse them to develop platform specific applications. In this way, they also become development platforms on their own.

---

### Post by Kyral on 2005-11-08
Thanks for 23meg for taking up my slack while I have been at class and studying.

Yes thats basically what WMs and DEs are separate. This is why I also said the Enlightenment is coming close to being a DE because its starting to include its own applets (Epplets), terminal emulator (ETerm) and other things

---

### Post by guyomarj on 2005-11-08
Hi,

Great post Kyral. I want to switch from metacity to openbox (on top of Gnome), to see if it makes my Ubuntu faster... It seems quite simple, following [the How To by Stormy_Eyes.]("http://ubuntuforums.org/showthread.php?t=75471")
But i wanted to know what kind of functionnalities from metacity will I lose by switching to openbox?

Thx.

---

### Post by 23meg on 2005-11-08
You'll be unable to use Metacity themes; that's more or less it in practice.

---

### Post by Kyral on 2005-11-08
Yah, thats what I meant when I spoke about XFCE being able to use many GNOME themes due to GTK. If you go to GNOME-Look.org and XFCE-Look.org and click on the GTK/GTK2 themes sections you will find that either GNOME or XFCE can use them, but XFCE cannot use the "MetaCity" themes, only Metacity can touch those. 

You'll also loose any keyboard shortcuts you had made (Again something Metacity provides)

I believe the xbindkeys program allows you to make Keyboard Shortcuts for X itself, meaning that they will stick across all WMs/DEs

---

### Post by LHZ on 2005-11-08
Good article, sir.

I would love a 'how to switch window managers' tutorial in this thread, any chance you'll write one? Pretty please?

Also, does Sawfish have any noteworthy features? I noticed you left it out of the list.

---

### Post by ssam on 2005-11-08
good article. i think it should be copied to the wiki, or intergrated into the ubuntu documentation.

about using openbox in gnome.

you will also loose being able to kill an application by clicking the close button if it crashes. in this case you will need to open a terminal and type "killall appname".

---

### Post by Kyral on 2005-11-08
[QUOTE=LHZ]Good article, sir.

I would love a 'how to switch window managers' tutorial in this thread, any chance you'll write one? Pretty please?

Also, does Sawfish have any noteworthy features? I noticed you left it out of the list.[/QUOTE]
Actually I should edit the thing to give the command to install them....

As for Sawfish...the only thing I really know about it is that its old and used to be the default WM for GNOME

---

### Post by ubuntumaneh on 2005-11-08
nice article. The other one on terminal was also very good, indeed.

I enjoy a lot Window Maker. It is also a FAST window manager with very nice features.         

Im thinking to give Enlightment a chance. It sounds very good. Is it faster than Gnome and XFCE?

---

### Post by 23meg on 2005-11-08
[QUOTE=LHZ]
Also, does Sawfish have any noteworthy features? I noticed you left it out of the list.[/QUOTE]

Sawfish had a window matching feature that did stuff similar to what [Devil's Pie]("http://www.burtonini.com/blog/computers/devilspie") does today.

---

### Post by Kyral on 2005-11-08
In practice Enlightenment is faster than the DEs. The fact that E17 can pull off the visual effects that it does and still be faster than the DEs is something that makes it quite amazing. Now gimme a minute and I'll show you how to install all of them, along with their "helper" apps

---

### Post by 23meg on 2005-11-08
What kind of visual effects are there in E? Does it have its own composite manager?

---

### Post by Kyral on 2005-11-08
Animated backgrounds, drop shadows (via the X.org Composite extension), elements that are basically like webpage rollover stuff,,,its a lot

[www.get-e.org](www.get-e.org)

---

### Post by benplaut on 2005-11-08
pretty much, it looks like a mac, but with waaaayyyyy more candy :D (kidding)

---

### Post by bvc on 2005-11-09
[QUOTE=Kyral]Animated backgrounds, drop shadows (via the X.org Composite extension), elements that are basically like webpage rollover stuff,,,its a lot

[www.get-e.org](www.get-e.org)[/QUOTE]unless it has changed in the last 2 months, the shadows are not through xorg and are done internally. 23meg, the different settings for the shadow are easily set  in the rt-click/Modules menu, which is very nice.
[http://kwh.kernow-gb.com/~bvc/theme/screenshots/E17-GTK-apps1.jpg](http://kwh.kernow-gb.com/~bvc/theme/screenshots/E17-GTK-apps1.jpg)

---

### Post by atoponce on 2005-11-24
Good read.  I have always enjoyed using Gnome, KDE and XFCE as I have all three installed on my laptop.  Personally, I don't see any reason to have the others.  It is nice to have choices with Linux.

---

### Post by bored2k on 2005-11-24
Very cute guide Kyral :).

---

### Post by guyomarj on 2005-11-25
[QUOTE=Kyral]Note on installing: Last time I checked, all of these installed entries in the GDM/KDM Sessions Menu, so to use them once you have installed them, just logout, find the "Sessions" button/menu on your login screen, and pick one :D The DM may ask you if you want it to be default, thats your choice. I'd choose "Only for This Session" if you are just trying it out, that way when you logout/login again, you will login to whatever you normally do.
[/QUOTE]

I did a Ubuntu server install on an old laptop. If I understood your "Note on installing", I have first to install the GDM/KDM Sessions Menu before installing Blackbox and Fluxbox (that's the two WM I want to try).

So, how to do it? And do I really need the GDM to use other WM like blackbox or fluxbox?

Thx.

---

### Post by Kyral on 2005-11-25
a DM makes things much easier, otherwise you'd have to edit I think its xinitrc and do startx everytime you wanted to load the GUI (I may be a CommandLine Commando, but this is just inefficient to me :D)

So you have three options. XDM, KDM, GDM. All are basically the same.

```
sudo apt-get install xdm
```
```
sudo apt-get install gdm
```
```
sudo apt-get install kdm
```

Your choice, but I'd recommend KDM or GDM only because you'd tend to find more support here (and more cool themes :D)

---

### Post by marksi on 2005-11-25
i run xubuntu and have just tried to install xdm but it doesnt run - just goes back to the command line. is the package broken

---

### Post by Kyral on 2005-11-25
Actually it didn't work for me either, but I just put it down to a misconfigured XServer (which wasn't working at the time) so I installed GDM...

---

### Post by guyomarj on 2005-11-26
[QUOTE=Kyral]a DM makes things much easier, otherwise you'd have to edit I think its xinitrc and do startx everytime you wanted to load the GUI (I may be a CommandLine Commando, but this is just inefficient to me :D)
[/QUOTE]

THx Kyral. I think that I'll try first to work out the xinitrc thing because the laptop I'm "Ubuntuizing" is pretty old and it seems that gdm is staying in RAM during my session taking about 8 Mb (out of 64).

In a few days I'll be part of your "CommandLine Commando" :D

---

### Post by marksi on 2005-11-26
[QUOTE=guyomarj]THx Kyral. I think that I'll try first to work out the xinitrc thing because the laptop I'm "Ubuntuizing" is pretty old and it seems that gdm is staying in RAM during my session taking about 8 Mb (out of 64).

In a few days I'll be part of your "CommandLine Commando" :D[/QUOTE]

You might like to look at [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu) for instructions on installing Xubuntu without a display manager

---

### Post by gingermark on 2005-12-01
Someone mentioned Window Maker earlier in the thread, any chance of adding it to the list at the start?

My computer is pretty old (800MHz, 128MB RAM) and so KDE sometimes gets a bit slooooow. I was looking for a lightweight DE, and was looking at Window Maker, found that it was in fact a WM, and came accross this thread when searching to try to find out the difference!

But anyways, I'm not a GNOME fan, and XFCE doesn't do it for me, so I guess I'm into WMs. Mezzo looks amazing, hopefully one day it'll be available for other distros. I tried Enlightenment a while back, and wasn't too sure about it.

Anyways, sorry for hijacking the thread, but any info on how to install Window Maker in KDM would be lovely (I've found Window Maker packages in the repositories, but no meta-package. Am wondering which ones I need)

---

### Post by Kyral on 2005-12-01
The "main" package is wmaker. Of course an apt-cache search windowmaker turns up more goodies :D

---

### Post by ubuntumaneh on 2005-12-02
Just for the sake of completion on window maker. I suggest fow wmaker goodies the following sites:

[http://www.dockapps.org/](http://www.dockapps.org/)
[http://largo.windowmaker.org/](http://largo.windowmaker.org/)

I suggest also that you look for MenuMaker (it is not in the repos, at least for Hoary), you will need it. By the way, the computer I most like to use is even older than yours (400MHz, 156MB), but with window maker it is really very good. What I most like in WM is the its simplicity.

---

### Post by Revert on 2005-12-07
So, just to see if I have this right: if you have a window manager without a DE, the system boots into some kind of console and you have to manually start X to bring up the manager?  If this is correct, is there no way to get it to auto-start without a DE?  Also, is there any advantage to using a window manager without a DE?

---

### Post by Wolki on 2005-12-07
[QUOTE=Revert]So, just to see if I have this right: if you have a window manager without a DE, the system boots into some kind of console and you have to manually start X to bring up the manager?  If this is correct, is there no way to get it to auto-start without a DE?  Also, is there any advantage to using a window manager without a DE?[/QUOTE]

No, a DE has nothing to do with booting into graphical mode, display managers take care of that  (gdm which uses GTK+, kdm which uses qt, and xdm which uses x calls directly, iirc). They usually offer a selection of the installed DEs/WMs, occasionally missing one if the package does not include the relevant info, in which case you have to edit a text file to enable that WM.

The main distinction between WMs and DEs is, I guess, one in attitude: a WM only deals with handling windows, and often some things like a applications menu and global keybindings; a DE aims to be a complete package, filling most of your computer needs (usually including a window manager).

Kyral, nice explanation and overview btw. It's not exactly true that there are only 3 DEs, there's the ROX desktop for example, or Mezzo which you already mentioned. GNOME, KDE and XFCE are without doubt the biggest and (probably) most complete ones, though.

---

### Post by Kyral on 2005-12-07
I always thought Rox was a Filemanager

Oh BTW there is now a Fluxbox wikipage

wiki.ubuntu.com/Fluxbox

---

### Post by Wolki on 2005-12-07
[QUOTE=Kyral]I always thought Rox was a Filemanager
[/QUOTE]

ROX-filer is a file manager (one that handles panels and the desktop though). ROX-session is a session manager, and OroboROX is a Window Manager. There's also a ton of Rox programs (mostly utilities), they're gtk-based, but have support for ROX's Drag&Drop saving protocol. More info is on the ROX page: [http://rox.sf.net](http://rox.sf.net)

Unfortunately Ubuntu only has the filer, but I'd consider it a DE nonetheless (a unusual, but not a bad one).

---

### Post by gingermark on 2005-12-12
[QUOTE=Kyral][Mezzo]("http://en.wikipedia.org/wiki/Mezzo_%28desktop_environment%29") - This still in development Desktop Enviroment is the star attraction for [SymphonyOS]("http://www.symphonyos.com/") and looks very promising. It completely discards the traditional GUI design concepts that GNOME, KDE, and XFCE seem to follow in favor of making the desktop more usable. Its really something that has to be used to believe. Distantly based off of FVWM. In case you can't tell, I think this project is going places :D

Can't be installed on any other Linux except SymphonyOS right now.[/QUOTE]

Now it can be! :p

To install Mezzo:

Edit /etc/apt/sources.list and add the following repository:
```
deb http://archive.progeny.com/symphonyos/apt/ ./
```

Then
```
sudo apt-get update
sudo apt-get install mezzo orchestra
```

Then
```
cd /etc/skel
cp -Rvf .mezzo ~/.
cp -Rvf .orchestra ~/.
```

And then finally
```
cd /usr/share/fvwm
cp .fvwm2rc ~/.fvwm
```

Reboot (as opposed to just logging out) and there you go! Hopefully.
OH, almost forgot, apparently you need Firefox, IceWM and FVWM installed. I would assume apt-get will take care of all that, but as I already had them installed I can't be certain.

Mezzo seems pretty cool (been running it for about 10 mins), but a tad slow on my 'puter. Still, first impressions are good!

THIS WORKS FOR BREEZY. I'm not suggesting that it'll work for other Ubuntu versions, but I'm sure that someone who knows far more about this stuff than me can say for definite.

---

### Post by fak3r on 2006-01-31
[QUOTE=gingermark]Now it can be! :p
Reboot (as opposed to just logging out) and there you go! Hopefully.
OH, almost forgot, apparently you need Firefox, IceWM and FVWM installed. I would assume apt-get will take care of all that, but as I already had them installed I can't be certain.[/QUOTE]

Thanks, got it installed but some things were missing icons, and I can't get anything up to change the desktop and such.  I found that apt-get **did not** install icewm for me, so I'll do that and see if it fixes anything.

Hey, is there any menus when you right click, left click on the mouse?  I was surprised they didn't do anything, but again, don't know if it's me or what since I don't have all of Symphony installed.  Looks nice thought, a big change from Gnome/KDE, which I like.  I like the minimal Openbox, but this kind of bridges thee gap, and that the UI is being presented with Firefox via an internal webserver is something else...

---

### Post by fak3r on 2006-01-31
[QUOTE=gingermark]Now it can be! :p

And then finally
```
cd /usr/share/fvwm
cp .fvwm2rc ~/.fvwm
```[/QUOTE]

Hey, one more thing, where is .fvwm2rc?  It isn't in /usr/share/fvwm for me, the only rc related thing in there is 'system.fvwm2rc-sample-95' :-k

---

### Post by zojas on 2006-02-02
Great article!

You did, however, misspell X's full name: it's the 'X Window System', not the 'X Windows System'.

---

### Post by andlinux21 on 2006-02-04
This was very good reading i am just learning fluxbox.  I have Ubuntu on a old gateway laptop and I needed something light to run. Thanks for the info

---

### Post by mustang on 2006-02-05
Thank you for your informative post Kyral. I think I might try fluxbox sometime soon...

Oh btw, the last three links in your post are broken.

---

### Post by Akhran on 2006-02-05
From a Server installation of Ubuntu, do I need to install X-windows-system first or will all the necessary packages (including the x-windows-system) be automatically installed during the installation of the various window managers?

Thanks for the guide !

[QUOTE=Kyral]Just like how my Terminal For Beginners came into being, I have heard the same general question. "What is a Window Manager and how do they work" (or basically that)

Well, here I am again to explain another fundemental part of the Linux system, in my usual flair :D

Now before we can understand Window Managers, we have to understand what makes the GUI system in Unix-based systems(Linux, OSX, the BSDs, etc) from the GUI system in XP. Now you know that in XP, if GUI crashes, it takes the entire system with it. Because for the most part, the GUI is the system (Feel free to correct me, I don't know a lot about the inner workings of XP). However in Unix-based systems, the GUI is separate from the system, in the form of X.

Now what is X? Well, its technically called "The X Windows System". It is also referred to as the X Server, which is also right, but for techinical reasons that aren't need to be understood now. Most of the time its referred to as X. What makes X different is that it frankly doesn't CARE what runs on it. It just handles drawing the screen, plus mouse and keyboard input. This allows for the almost infinite various GUI designs you see on Linux systems.

Now if X doesn't care what the GUI looks like, what does? Well, now we are at Window Managers. Window Managers are what control the placement and look of the application windows. Most also provide the menus we interact with and the cool panels and docks that we love so much. There are many Window Managers out there. What follows is a list of the most common and popular

Wait a SECOND! I can't do it yet! I have to explain one other concept. The Desktop Environment. There are only 3 Desktop Enviroments in the Linux world. XFCE, GNOME, and KDE. What makes a Desktop Environment different than a Window Manager? Basically, the amount of stuff that it provides. Desktop Environments typically have thier own File Managers, default Web Browsers, graphical Control Panels, and applets. However, they also need a Window Manager to run on top of. Now KDE has one integrated in, as does XFCE. But GNOME doesn't, and depends on one of the Window Managers listed below to help it out. Okay? Cool! Lets go!

Note on installing: Last time I checked, all of these installed entries in the GDM/KDM Sessions Menu, so to use them once you have installed them, just logout, find the "Sessions" button/menu on your login screen, and pick one :D The DM may ask you if you want it to be default, thats your choice. I'd choose "Only for This Session" if you are just trying it out, that way when you logout/login again, you will login to whatever you normally do.

TWM (Tab Window Manager or Tom's Window Manager): The very basic and default WM that X ships with. In its default state its not much more than a way to have multiple terminals on the screen. However rumor has it that its very customizable if you know C and about the XLibs...
[URL="http://blackboxwm.sourceforge.net/"]
BlackBox[/URL] - This WM is one of the "Box" series of Window Managers. Very minimalistic, yet also very FAST. Just a step above TWM in its default configuration, it is nonetheless a favorite with power users.

```
sudo apt-get install bbconf bbappconf bbpager blackbox blackbox-themes
```

[FluxBox]("http://fluxbox.sourceforge.net/") - Fluxbox is decended from Blackbox, and as such inherits a lot of its traits. Aims to be VERY simple, yet also has a bunch more things that Blackbox lacks. Most of its configuration is done with text files. In its default configuration it only provides a taskbar and a main menu which is accessed via right click. However I have seen INCREDIBLE looking desktops come out of Fluxbox.

```
sudo apt-get install fluxbox fbdesk fbpager fluxconf
```

[FVWM]("http://www.fvwm.org/"): (F Virtual Window Manager) - Directly decended from TWM, FVWM nonetheless is still kicking, and many other Window Managers are decended from it. Almost endlessly customizable, its still a favorite. ([Wikipedia Entry with MUCH more info]("http://en.wikipedia.org/wiki/FVWM"))

```
sudo apt-get install fvwm
```

[Enlightenment]("http://www.enlightenment.org/") - The very powerful WM, distantly decended from FVWM, Enlightenment is one of the favorite Window Managers today, going toe to toe with Desktop Environments like XFCE, GNOME, and KDE. Known for its unique take on the Virtual Desktop concept, Enlightenment is the Window Manager that is closest to being a Desktop Enviroment. This is even more true with the pending release of Enlightenment DR17, or just "E17", which promises to knock out everyone with how much eyecandy it can produce with so little resources. It should be noted that Enlightenment can be combined with GNOME to produce what is referred to as "Enlightened GNOME".

```
sudo apt-get install enlightenment enlightenment-theme-bluesteel enlightenment-theme-brushedmetal enlightenment-theme-ganymade enlightenment-theme-shinymetal epplets eterm e16keyedit e16menuedit2
```

[MetaCity]("http://en.wikipedia.org/wiki/Metacity") - This Window Manager is only notable for being the default Window Manager in GNOME.

```
sudo apt-get install metacity metacity-themes
```

[OpenBox]("http://www.icculus.org/openbox/") - Another WM based on Blackbox, its quick, light, and fast. Its often used to replace MetaCity in GNOME. 

```
sudo apt-get install openbox openbox-themes obconf
```

Desktop Environments

[Mezzo]("http://en.wikipedia.org/wiki/Mezzo_%28desktop_environment%29") - This still in development Desktop Enviroment is the star attraction for [SymphonyOS]("http://www.symphonyos.com/") and looks very promising. It completely discards the traditional GUI design concepts that GNOME, KDE, and XFCE seem to follow in favor of making the desktop more usable. Its really something that has to be used to believe. Distantly based off of FVWM. In case you can't tell, I think this project is going places :D

Can't be installed on any other Linux except SymphonyOS right now

[XFCE]("http://www.xfce.org/") - XFCE, the 3rd Desktop Environment that is almost always in the shadow of GNOME and KDE, is the default desktop environment for Xubuntu. Very streamlined, it is the DE of choice on slightly older systems. However it also boasts some very cool powertoys, namely the best compositing manager out of the three Desktop Environments (compositing is what lets things like drop shadows and "true" transparency happen). Many themes are available, and even shares many themes with GNOME due to thier common language of GTK. I personally run this DE. [Themes]("http://www.xfce-look.org") 

```
sudo apt-get install xubuntu-desktop
```

[GNOME]("http://www.ubuntuforums.org/www.gnome.org") (pronouced "Guh-nome") - One of the Big Two Desktop Environments alongside KDE, GNOME is the default Desktop Environment of Ubuntu and also of the GNU Project. Created in 1997 out of concern that KDE's use of the Qt libraries would take it out of the realm of free software, GNOME uses the GIMP Toolkit, better known as GTK. It comes equipped with Epiphany as its web browser, Evolution for mail, GAIM for IM, The GIMP for Image Work, Abiword for Word Processing, Totem for videos, Nautilus for file browsing, and Rhythmbox for music playing. Unique out of the Desktop Environments in that it doesn't have its own Window Manager. Currenlty uses MetaCity, in the past has used Enlightenment and Sawfish as defaults. Notice that Ubuntu's GNOME doesn't come with the apps I listed as default. Those apps are actually apps that are designed to fit in with GNOME. [Themes and more]("http://www.ubuntuforums.org/www.gnome-look.org")

```
sudo apt-get install ubuntu-desktop
```

[KDE]("http://www.ubuntuforums.org/www.kde.org") (K Desktop Environment) - The original Linux Desktop Environment and the default for Kubuntu users, KDE is the main "rival" for GNOME. It was created in 1996 and ran into some controversy with the Free Software folks over its use of the then proprietary Qt Libraries as its method of drawing graphics. More "eye-candy" that GNOME or XFCE, KDE has been accused of trying to emulate Windows XP in style and look. However many VERY cool apps have come from KDE, namely Amorok, k3b, and Krita. Currently uses Konqeror(sp?) for web/file management, Kontact for email, Kopete for IM, and Adept as a replacement to Synaptic. It also has a good Compositing manager. [Themes and more]("http://www.ubuntuforums.org/www.kde-look.org")

```
sudo apt-get install kubuntu-desktop
```

Oh, one final note. There is no such thing as a "GNOME App" or a "KDE App". It doesn't matter what WM/DE you are using, they will work the same. Granted it may look a little out of place, but it will still work perfectly. Heck I run XFCE and I use k3b on a regular basis. 

So I hope I have once again provided information on another part of the Linux Mythos.

EDIT: Added install commands[/QUOTE]

---

### Post by brallan on 2006-02-07
when i type 

> sudo apt-get install xubuntu-desktop

i get the following error:

> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xubuntu-desktop

does this mean i don't have apt-get configured properly?

---

### Post by Kyral on 2006-02-07
Xubuntu-Desktop is in Universe. You have to enable those in /etc/apt/sources.list, which is very well commented out.

```
gksudo gedit /etc/apt/sources.list
```

Look for the comments (lines starting with #) and follow the instructions (Uncomment means remove the #) then save and ```
sudo apt-get update
```

Then you will be able to install it (if you enabled it right)

---

### Post by bluevoodoo1 on 2006-02-07
For some reason I can't install Enlightenment. I had it for a bit, then uninstalled, now I want it back... When I try to select it with synaptic, a message is displayed... (screenshot has message). Here's my sources.list file. I wonder what happened...

```

## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 


deb http://wine.sourceforge.net/apt/ binary/

```

---

