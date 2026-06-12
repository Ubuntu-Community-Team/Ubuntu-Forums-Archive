---
title: "TOTAL Linux *NEWBE* (I Have No Idea What I'm Doing)"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by Kernel Sanders on 2006-02-17
Apologies for the thread title, but I want to be clear about the level of (my) idiocy were dealing with here...... ;)

I can upgrade computer hardware, and I know A LOT about Windows, installing, registry tweaks etc, so I am not a "computer noob" by any stretch of the imagination!

As far as Linux (Ubuntu) goes? Imagine you are talking to a moron who has difficulty understanding the most "basic" of linux operations (even what linux looks like), and thats pretty much my knowledge of Linux..... *shame*

Now that you know the extent of my Linux idiocy (Imagine that I am retarded if you will) then hopefully you can help me! :)

I am VERY keen to start using Ubuntu Breeze 5.10 (Gnome) as my OS (No dual boot/virtualisation for me! :) ), as Windows activation/DRM has really left me worrying about my privacy! My opinion is, its MY computer/software, I paid for it, I can do what the hell I like with it! Apparently not though......

So after a LOT of research, (and trying Ubuntu's live cd - and being VERY impressed!) I have decided that Ubuntu Breeze 5.10 is the OS for me!

So....... the live cd........ worked like a charm thankyou very much! Excellent does not even cover it! I was left thinking..... "whats windows again?"

There was just 1 problem though (that I could see.... maybe there were more?) my USB BT Voyager 105 Broadband modem was not automatically installed..... :(

To be honest I think its appropriate to note to other newbe's here that Windows XP failed to automatically install 3 devices the last time I installed it, so Ubuntu 1 : 0 Windows XP

Having done some research on my broadband modem problem, I have uncovered the following page:

[http://www.lack-of.org.uk/viewarticle.php?article=114](http://www.lack-of.org.uk/viewarticle.php?article=114)

Unfortunately, as I would have no idea even where to "begin" to install a driver on Ubuntu (Can you even install a driver on a Live CD?) I am at a loss...... :( 

This is where the "treat me like an idiot" bit comes in :)

So, I am an AOL UK user running 1mb broadband with a BT Voyager 105 USB broadband modem........ my drivers are here: (I believe)

[http://www.lack-of.org.uk/viewarticle.php?article=114](http://www.lack-of.org.uk/viewarticle.php?article=114)

and I am trying to install my modem onto the ubuntu live cd

HELP!!!! *Shreaks*

If its any help, in Windows XP, there is no way in hell did I install ANY AOL software, (LOL) I connected by windows built in "set up a home or office network wizard"

I selected broadband, and only had to type in my AOL username and password from then on, I believe my broadband modem was using PPPOE? If that makes any sense? I remember PPPOE being significant anyway....... *looks sheepish* :(

So as you all seem like a fantastic community that I would love to be a part of from now on....... can you help?

Thanks again guys/girls!

John

---

### Post by aysiu on 2006-02-17
Is this a dial-up modem?

Let's take it one step at a time, since someone apparently has had success with this... > To start with, you'll need to download the Nortek alpha (not the 'main' version) of the eciadsl driver, from eciadsl.flashtux.org. Un-gzip the archive somewhere, and do the usual ./configure, make, make install dance. The first two steps can be done without root access, but make install and everything else afterwards will need root access. A compiler warning about a zero-sized array will be generated during the make step; this doesn't seem to cause a problem though. This "usual" ./configure, make, make install "dance" is called compiling from source. To do this in Ubuntu, the first thing you should do is install the package called *build-essential*.

Open up a terminal (Applications > Accessories > Terminal) and type ```
sudo apt-get update
sudo apt-get install build-essential
``` The password you'll be asked for is your **user** password. Make sure, of course, that you're using the user you created during installation (not later in the process). If you're doing this from the live CD, you won't need a password.

You can also do the above step graphically if you go to System > Administration > Synaptic Package Manager.

Once that happens, the > Un-gzip the archive somewhere you can do easily by just double-clicking the .gz and selecting **Extract**. Extracting to the desktop is probably easiest.

Then, I would assume you'd go to the directory you extracted: ```
cd Desktop/eciadsl-usermode-0.10-nortek-alpha
``` and then do the "dance" ```
./configure
make
sudo make install
``` Of course, you could also forget the compiling from source and do this instead... Download [the .deb package of eciadsl](http://eciadsl.flashtux.org/download/eciadsl-usermode_0.10-1_i386.deb) to your desktop. Then ```
cd Desktop
sudo dpkg -i eciadsl*.deb
```

**Edit**: Actually, forget all that crap above! eciadsl is in the Ubuntu repositories!

1. Follow the directions in the first link of my signature.
2. Then ```
sudo apt-get update
sudo apt-get install eciadsl
```

---

### Post by Kernel Sanders on 2006-02-18
Hey! Thanks for the reply, but remember, I am a windows genius, but a ubuntu idiot! :)

Imagine a windows install, heavily customised with litestep so its almost unrecognisable, and in russian. Thats what ubuntu is for me! Ubuntu is strangely  familiar to me.... but I have absolutely no idea what anything is or what it does! *shame*

So, to clarify, I am running the Ubuntu Breezy Badger 5.10 LIVE CD

I have an external, USB Broadband/DSL (not dial-up) BT Voyager 105 modem.

After research, I found this page:

[http://www.lack-of.org.uk/viewarticle.php?article=114](http://www.lack-of.org.uk/viewarticle.php?article=114)

Then that took me to this page:

[http://eciadsl.flashtux.org/download.php?lang=en](http://eciadsl.flashtux.org/download.php?lang=en)

So I *believe* that this is the driver I need to download?:

Debian i386    logo_debian_small eciadsl-usermode_0.11-1_i386.deb (202 Kb)

Correct? Or a laughable mistake from a newb? *blushes*

So i'm guessing I put that onto a USB key, so that I can run the live cd and have access to the right file?

So now imagine i'm in ubuntu live cd, with a driver on a USB key...... I have no idea what comes next?

Do I "extract" the driver somewhere first?

Help!

As my modem is the default modem for BT and AOL customers in the UK, if we can compile some sort of "super-newbe" guide, then it will probably help a LOT of people who want to use ubuntu with DSL?

P.S Please bear in mind, saying "extract" and other seemingly basic terminology, means absolutely nothing to me as far as linux goes, please be as simplistic as you can! 

E.G

1) type this, then this window will come up
2) in the window press/type this and this will happen etc...

Also, assuning you guys/girls can help me install my modem, I still have no idea where I type in my AOL username and password and click connect (if there is such a thing?)

So if this takes a while, please be patient with me! *blushes*

Thanks for your tolleration, its probably not that often that you get someone that needs instructions this simplistically!

Sorry, but I really need the "food goes in here....*points to mouth*" level of simplicity if I will ever get this.......

Hopefully, in a few weeks, i'll be as clued up as the rest of you!

Thanks again!

John \\:D/

---

### Post by nalmeth on 2006-02-18
hey john, no need to over-emphasize your noobness, we were all there at one time. Luckily this "linux" thing has advanced quite well, and you've picked a good time to hop on the band-wagon. I think the DRM issue will push a lot of people down the same road you're on.

Some pointers for installing packages you may need for this situation:
the easiest way to install things, are GUI's like synaptic, or gnome-update-manager, or adept, etc. All they are doing, is scanning online repositories, which tell your ubuntu if you have the newest available versions of all the apps listed in these repositories. The function that knows what versions of everything you have, and checks for updates, and performs upgrades is called APT.

APT is debian's (which ubuntu is built on) package management system, and holds no peer in my opinion. The GUI's listed above are just frontends to the apt system. To really understands whats going on, and probably the best way to get your system setup is with the terminal or command line.

APPLICATIONS --> ACCESSORIES --> Terminal

the command to install a package, say rhythmbox would be:
sudo apt-get install rhythmbox

installing packages requires administration priviledges, and is achieved with the "sudo" command. This is an essential security feature, and won't get in your way the same way it would if you tried to setup windows in a similar fashion.  You will simply be prompted for your password (i don't know what it is on the liveCD -- maybe ubuntu or live or guest). apt-get is where APT comes in, and install is telling APT what to do. Replace 'install' with 'remove' to perform the obvious action.

A lot of packages are not stored in the repositories, because they are used for special situations, which don't generally affect most people running most hardware. External network devices don't tend to fall into the "general" category it seems.

For these other apps, you will have to install from source, which you might have some experience with from windows. or not.

To compile from source, you need certain libraries and other dependencies, which is where the build-essentials comes in. These dependencies are not installed by default, because most general users won't need them.

the three step method to installing most apps from source is:
In a terminal, go to the folder were you extracted the source --> 

cd /home/user/sourcepackage

then:

./configure
make
sudo make install

EDIT: you can extract the package by right clicking on it, and picking "extract", or double-clicking it to open an "extractor", if you want to go about it graphically. 

I don't know anything specifically about your device, or your drivers, so that is up to you. EDIT: asiyu seems to be hot on the spot with some info for you. 

Do you have a direct ethernet connection? Do you actually have net access on your liveCD, or are you dependant on your modem?

I don't know how far you will get with the liveCD, especially if you can't access the net to download packages for it. Can you spare some space on your hard drive to install ubuntu, and dual-boot with windows? Or on a seperate drive or something?

Sorry I can't help you directly with your device and drivers, but I post this to give you some intro-reading. 

Good luck!

---

### Post by kvorion on 2006-02-18
Hey man,

Trust me, it is easier to install and customize your Ubuntu box if you have access to the internet from your other OS. Because you were advised to download certain source packages and use apt-get, you will need the internet for that. And since you dont even have your modem up, you wont be able to do those things. 

So the best thing would be to install Ubuntu on dual boot first. Download some essential stuff from Windows and transfer it to your ubuntu partition. (We will get to the transferring stuff in a while; one thing at a time)

Why I am saying that you install Ubuntu first is that once you get your OS up and running, it is much better than the live cd that you are using now. Then you can start using it and get familiar with it. You can keep switching between Windows and Ubuntu till you get connected from Ubuntu and install all the packages that you need. That is how most people I know, did it.

And dont worry about being a linux newb, we all have been there sometime. And no matter how much you know, there is still more to learn :P

---

### Post by welsh_spud on 2006-02-18
Lets start from the top. You are running a BT Voyager 105 in the UK with AOL Broadband. That modem is called a 'Winmodem' as the modem itself doesn't have an on-board chip, it instead sends all the work to the processor. This is turn requires software to be installed, which isn't good new for Linux (or anyone other than Windows, including Mac OS X, BSD, etc)

There are two options that you can take.
[LIST]
[*]Buy a nice router/modem. This is the best option in the long run in my opinion as it won't require any work on your behalf (other than forking over about £40)

[*]Secondly you can instal, like the others have said above the 'eciadsl' program. The EciADSL project was put together by some developers who have managed to reverse engineer the Windmodems such as you BT Voyager 105.
[/LIST]
Im sure you don't need much help with the first option, but I am going to walk you through the installation and setup of EciADSL. For this you will need either a few blank CD's or a floppy disk. Make sure that your modem is unpluged through this untill I say to plug it in...

Great, ok then. To start off we are going to download (in Windows I guess, since you obviously don't have internet on Linux yet) some files. You will need to burn these files to CD, or DVD or somehow get them onto your Ubuntu install.

The file in question is [EciADSL (Stable) ]("http://eciadsl.flashtux.org/download/eciadsl-usermode_0.11-1_i386.deb").

Download that and somehow get in onto your Ubuntu installation. Either put the file on your desktop, or into your home folder.

Now that the file is safe and sound on Ubuntu we have to install it. Open up a terminal by going to: Applications > Accessories > Terminal. If you put the file in your home folder, go to the next step. If you put the file on your desktop your first command will be the 'cd' command. Type in:
```
cd desktop
```

Just like in the good 'ol MS-DOS days, cd changes the directory that you are looking at.

The chances are that the file you downloaded will have a pretty long-*** name. This will be a pain to type out, so we will use a nice trick to copy and paste it. In the terminal window type in

```
ls
```

(Thats L, not I, by the way) This will show you all the files in the current directory.

Now type in (but DON'T press enter)

```
sudo dpkg -i 
```

(don't forget the space after -i) This command will tell the program 'dpkg' that we want to install (-i) a file. Ater '-i', highlight the name of the file that came on the screen after you typed in 'ls' and press the wheel button on your mouse. If all went to plan then you should have the name of the file after 'sudo dpkg -i'. Press enter now.

If all goes to plan, then it will install with a few lines of text printed onto the screen. If it doesn't, it will probably ask for a file along the lines of 'PPPOE'. If it does, copy and paste the output into the forum and I'll tell you how to fix it.

That was your first ever program installed in Linux. Don't get worried if you think all program installations are like that! Trust me their not. There is a nice program on Ubuntu called Synaptic that has a graphical interface for you, but that is a different story.

Next, in the command line type in
```
sudo gedit /etc/hotplug/blacklist
```

This will tell the program 'gedit' to open the file /etc/hotplug/blacklist. Notice how 'blacklist' doesn't have a .txt extension. You will find a lot of files don't have extensions in Unix/Linux.

In the file, add the word ***dabusb*** to the end of the list. Save, exit, and reboot the computer.

The driver is now completely installed. Congratulations. However, this is not the end of the tunnel. We now have to configure it (it's all a nice graphical interface from here on in :) )

In the terminal type in

```
eciadsl-config-tk
```

This will bring up a very ugly looking window.

[IMG]http://eciadsl.flashtux.org/img/tutorial/capture7_eciconf.sh.png[/IMG]

user name: [email]whatever@aol.com[/email]
password: [I]Whatever[I]
provider: 51 (British Telecom)
DNS1: Accept default)
DNS2: Accept default)
VPI: 0
VCI: 38
modem type: 11 (BT Voyager 105)
VID1/PID1/VID2/PID2: accept defaults
modem chipset: GS7470
synch file: /etc/eciadsl/gs7470_synch03.bin
PPP mode: accept default
is DHCP used? no
is a static ip used? no

Click on **[COLOR="YellowGreen"]Create Config[/COLOR]**

Your done with that window. Now plug in your USB Modem and type in

> usr/bin/eciadsl-start

This should make the lights come on and flash about for a bit. If so, the internet is now your oyster!

Note:
Got a lot of information for this from:
[LIST]
[*][http://eciadsl.flashtux.org/tutorial.php?lang=en]("http://eciadsl.flashtux.org/tutorial.php?lang=en")
[*][http://www.lack-of.org.uk/viewarticle.php?article=114]("http://www.lack-of.org.uk/viewarticle.php?article=114")[/LIST]

---

### Post by Kernel Sanders on 2006-02-18
Hey Nalmeth! Kvorion! Welsh_Spud!

Welsh_Spud, I am forever in your debt, hopefully your beyond-the-call-of-duty support will not only benefit me, but others who have this problem! A1 support, it was very much appreciated! *Applauds*

Thanks for the support in general actually! The welcoming nature of this forum is not only rare, but serves as an excellent ambassador to the open-source movement in general and the principals and ideals for which it stands! Many thanks again! *Applauds*

---

### Post by welsh_spud on 2006-02-18
So it worked then? Wow I feel so pleased with myself :cool:

---

### Post by nalmeth on 2006-02-18
yes very well done Welsh_Spud

above and beyond the call of duty

=D> joining john in applause

---

### Post by mostwanted on 2006-02-18
This is what's good about Ubuntu Forums. Everyone is so helpful and the tone is great. I don't think I've ever seen anyone acting all pretentious saying RTFM here. Most definitely the best Linux community.

---

### Post by Kernel Sanders on 2006-02-18
Considering that Linux is not a "newbe" application, the support in this forum more than makes up for that!

Its not just the program thats attracting me to the world of linux, its the principals, particularly the one's that Ubuntu is founded on!

I really cant praise this whole movement enough, and thats coming from a user that actually LIKES windows!

LOL!

---

### Post by bsmaat on 2006-02-21
Hi welsh spud... Your tutorial was very helpful. However, this error you're takling about, the PPPoE. It's a pain in the butt, and I'm a linux noobie too, and I'd appreciate it if you could explain what needs to be done to fix this problem. Thanks alot.

---

### Post by PowerJC on 2006-02-23
So this works on the live cd?  I wanted to try out linux ubuntu live cd but didn't think it was possible on the internet.  I have a bt voyager 105 with aol.

---

### Post by PowerJC on 2006-02-23
Anyone?  I want to try linux out on the internet before i decide to install it.

---

### Post by Haegin on 2006-02-23
I dont know about installing the drivers and using the bt modem but you can definatly get internet access from the live cd if you are on a network provided you know your details (if you are using DHCP or what you static ip and stuff should be).

---

### Post by PowerJC on 2006-02-23
I don't have a network only a bt voyager 105

---

### Post by PowerJC on 2006-02-24
Does anyone know if this works on the live cd?

---

### Post by welsh_spud on 2006-03-05
It doesn't work on the live CD

---

### Post by Lifman on 2006-03-25
hi,
newbe too. :-)
please help...
installed ubu on fresh pc.
only have adsl modem, so no www on that computer.
followed welsh_spud's excellent guide.
downloaded and installed.
got to "eciadsl-config-tk".
ubu says: "bash: eciadsl-config-tk: command not found".
(btw, where did ubu install these drivers anyway? didn't get any "files extracted to..." msg...)
thanks in advance! ;)

---

### Post by Lifman on 2006-03-25
sorry. forget that. my mistake. all ok. welsh_spud rules!

---

