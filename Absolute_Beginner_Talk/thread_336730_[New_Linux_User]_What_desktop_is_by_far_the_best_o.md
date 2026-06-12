---
title: "[New Linux User]: What desktop is by far the best or most supported to use?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by BioGene on 2007-01-12
Hey everyone,

My first post here and my first time going to use Linux Ubuntu or for that matter Linux at all! Yes I am a windows user but wish to make the change that some people have called scary! Well won't waste your time with my rant anymore,

I was wondering, since I am just going to use Linux Ubuntu, I noticed that it uses Gnome desktop and that there are others like Kubuntu that use KDE. Now I looked at some of the pictures and even some of the website for each as in app website for each desktop. Now they both look like GUI so I doubt that is the difference. I also found the Gnome app site more appealing, but aside from that.

What desktop would you recommend for me to use, I was thinking of using the regular Gnome, which I am guessing is the Gnome version. Is this a wise decision to make and is there a lot of support for it and great apps?

One thing that I would like to do is change my desktop to sort of look like the Mac OS-X theme, so can this be done in Gnome or KDE?

Thanks for the help and info!

---

### Post by RMorris78 on 2007-01-12
making it look like mac os x can be done in either window manager.... and you can actually have both KDE and Gnome installed, and pick which one to use on logon

i found this tutorial helpful....
[http://baghira.sourceforge.net/OS_Clone-en.php](http://baghira.sourceforge.net/OS_Clone-en.php)

welcome and good luck! :)

---

### Post by BioGene on 2007-01-12
Oh so I can have both KDE and Gnome installed together, how exactly could this? Does it come with one of the packages or is there some thing I have to type in during installation?

---

### Post by RMorris78 on 2007-01-12
Ok, well you start by installing one of them. Say its an ubuntu cd. once it is installed (you have gnome to start), and your internet connection is up and running. you can run this in a Terminal window.

```
sudo aptitude install kubuntu-desktop
```

it will download all the packages that come wiht kubuntu, and install them. when that is done, you can log out. on that log in screen there will be a button that says "Session Type" and there will be an option for "Gnome" and "KDE". Just select the bullet of the WM you wanna use, and then login and voila!

---

### Post by Quillz on 2007-01-12
GNOME and KDE are the two most popular desktop environments, although you may also be interested in some less known ones, such as XFCE or IceWM.

---

### Post by Delkster on 2007-01-12
> **BioGene said:**
> Oh so I can have both KDE and Gnome installed together, how exactly could this? Does it come with one of the packages or is there some thing I have to type in during installation?

Just pick whichever you want for the initial install (as you already found out, Ubuntu comes with Gnome and Kubuntu with KDE), and you can install the other later directly over the Internet. If you picked Ubuntu for the initial install, find the 'kubuntu-desktop' package in the package manager (for example using the command line like RMorris suggested) and it'll install everything that belongs to the default Kubuntu desktop. If you initially picked Kubuntu, find ubuntu-desktop afterwards and install it.

If you have both desktop environments installed you'll be able to choose between them on login. You can also run applications from one desktop environment when using the other but they aren't always automatically included in the menus of each other, they use different visual themes etc. so the applications may not integrate with the 'wrong' desktop environment as well they do with their own one but generally things work quite nicely.

Generally, Gnome is designed to be simple and clean whereas KDE provides more features, at least in quantity. Whether it more offers them more in quality may depend on who you ask.

---

### Post by RMorris78 on 2007-01-12
all in all, you cant go wrong with either

you might seem to prefer KDE since it has a more windows-esque feel

what are the hardware specs of your box?

---

### Post by hyper_ch on 2007-01-12
Although my computer can easily handle KDE I just think it hast a lot of stuff that I don't need... so I'm using Xfce (xubuntu --> sudo aptitude install xubuntu-desktop)

---

### Post by BioGene on 2007-01-13
My specs of my PC are:

Processor: Celeron 2.80 GHz
RAM: 512 MB
Graphics: nVidia GeForce FX 5200 128MB
HDD: 80GB
Monitor: 17" LCD

I think that is all the important stuff!

K sorry for the long wait!

---

### Post by bg1256 on 2007-01-13
A few weeks from now, once you've gotten a little more comfortable, you might consider installing XGL/Compiz or Beryl/aiglx.

That probably sounds like a bunch of jibberish right now, but it provides some pretty amazing 3D acceleration to your desktop.

But for now, pick KDE or Gnome, and just get used to things.

Once you are adjusted, search the forums, and you will find helpful howto threads to get some cool stuff up and running.

---

### Post by bodhi.zazen on 2007-01-13
Use whatever you like. If you run gnome yor can also run kde applications (from gnome) or vise versa ....

XFCE is also quite nice and similar in some ways to "roll your own" icewm, fluxbox, or openbox.

You will find LInux has more freedom (options) then windows and thre are almost always at least two good options for and task ....

Welcome to Ubuntu and enjoy :)

---

### Post by BioGene on 2007-01-13
Yeah I heard about this beryl thing, I also searched it up on YouTube and saw some videos looks pretty amazing! Yeah I still need to find out how to install my nVidia drivers, although so far it works alright!

I was just wondering, I read about this automatix2 from some other forums. They said it was a good app to install on Linux as it helps with some installations. Is this a good app to get installed? Will it help me with installing on linux or should I just stick with terminal installations?

One more thing, I was wondering about partition, is it purely text or is there some way to make it graphical partitioning as I find that way more easier to organize my partitions!


Thanks for the help.

---

### Post by Tomosaur on 2007-01-13
> **BioGene said:**
> My specs of my PC are:

Processor: Celeron 2.80 GHz
RAM: 512 MB
Graphics: nVidia GeForce FX 5200 128MB
HDD: 80GB
Monitor: 17" LCD

I think that is all the important stuff!

K sorry for the long wait!


Pretty much the same as mine, you'll be fine running either :)

I personally prefer Gnome, but KDE is growing on me. I also like XFCE (which comes with Xubuntu), and if I'm setting up an older machine, I like Fluxbox. Lots to pick from!

The Ubuntu CD comes with a graphical partition manager, so yes, it's graphical :)

Automatix2 is reccommended by lots of people. It makes it easier to install lots of the stuff which people either really like, or find they need. There are legal issues around media codecs and such which means they can't be put into the normal Ubuntu installation. Automatix2 allows you to download them. If you don't feel comfortable finding and installing the stuff you want by yourself, then go ahead with automatix2. I personally think it's a better idea to do it all yourself the first time around, so you can get a feel for how things work in Linux, but that's just me.

---

### Post by BioGene on 2007-01-13
So Automatix2 is sort of like an installer for apps, I get that. But does it too have some limitations on what apps it can download and install, aside from media codecs? Like can it install any type of app or are there some that I will still need to install through terminal?

Also does CS2 run slow if I install it and run it through wine or cedega?

---

### Post by Tomosaur on 2007-01-13
Automatix2 allows you to download more than media codecs yes, as does Synaptic (better known as Add/Remove, it's in the 'Applications' menu on Gnome. Synaptic has more apps available, but you're expected to know what it is you're after. It's very good. If you want a game, for example, just type 'games' into the search box, or select games from the categories menu on the left hand side. Select the games you want (they have a little checkbox next to them), and click apply. The program will then download and install the applications for you. Much easier than windows, and you have thousands of apps to choose from! Automatix2 has a much smaller list of software available, but it has the stuff the average user will want/need. Many people come here with problems regarding getting movies to play and stuff. Automatix2 should help you out in that respect, or let's say you want an instant messenger. Automatix2 lists the most popular ones.

Very rarely, you may need to install an app through the terminal. This generally only happens when the software is not available through Synaptic, or when you need to compile the program yourself. The average user will not need to do this except in very very rare circumstances.

As for CS2 - you can check how well Windows programs are working through Wine on [This Website](http://appdb.winehq.com/). CS2 does not appear to be working particularly well I'm afraid. You may want to keep windows around for a while alongside Ubuntu if you absolutely need to use photoshop. There are graphical apps available for Linux, but photoshop isn't one of them. Wine is not perfect, if you want windows programs, you should probably run them on windows.

Cedega is generally used for making windows games run on linux - it's a version of Wine developed to play games, so I doubt photoshop would run any better on it.

---

### Post by AndyCooll on 2007-01-13
Automatix2 is good for helping you get a system up and running. It makes installing codecs easy, as well as a few of the most commonly used software apps that are not in the default install. 

However the everyday program you'll generally use to install apps is Synaptic (Administration > Synaptic),

:cool:

---

### Post by BioGene on 2007-01-13
Ok so I saw some more videos of Beryl, looks pretty cool! Now iwth my specs you guys think it will run fine or will it lag and maybe freeze on me?

Also what are some good coding tools on Linux Ubuntu? I need the coding tools for internet websites, such as HTML, JavaScript, and PHP mostly! Any hints or tips which are the best?
Also is the open office suite that comes with ubuntu the best out there for Linux or are there any better?

Hey also about that graphical partitioner, when I just tried to install Linux Ubuntu again on another PC that no one uses all I got like the first time was a text based thing! What is up with that? I told the installation to take me through "OEM" not "Text-Based", so what was I doing wrong? Thanks for the help!

---

### Post by BioGene on 2007-01-13
Hey I have this one issue when I try to view videos online: This is the error and it won't play the videos at all no idea why or where to get the decoder I need:

> Totem could not play 'fd://0'.

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

Can you guys tell em where I can find it? Is it in the synaptic installer app?

---

### Post by Tomosaur on 2007-01-13
> **BioGene said:**
> Ok so I saw some more videos of Beryl, looks pretty cool! Now iwth my specs you guys think it will run fine or will it lag and maybe freeze on me?

I have managed to get beryl running, and I have pretty much exactly the same specs as you. It runs fine, except for the water stuff, which did lag. I did managed to break it twice though, and don't currently have it installed, but this is almost certainly down to me wanting to tweak and fiddle with every little aspect of it. If you install it, then use it like it should be used, you should have no problems.

> 
Also what are some good coding tools on Linux Ubuntu? I need the coding tools for internet websites, such as HTML, JavaScript, and PHP mostly! Any hints or tips which are the best?

Depends how confident you are! None of your listed languages require anything other than a text editor, and there's tones of those available. If you require development environments, there are lots of those out there too. NVU and Screem are two which come to find for web development. Linux is far superior to Windows as a development platform, there are literally thousands of tools to pick from, just open up synaptic and take a peek :)

> 
Also is the open office suite that comes with ubuntu the best out there for Linux or are there any better?

I haven't found anything better.

> 
Hey also about that graphical partitioner, when I just tried to install Linux Ubuntu again on another PC that no one uses all I got like the first time was a text based thing! What is up with that? I told the installation to take me through "OEM" not "Text-Based", so what was I doing wrong? Thanks for the help!

Which version of Ubuntu is it, and what is the link you downloaded it from?

---

### Post by BioGene on 2007-01-13
I got the Ubuntu 6.10 release of the official ubuntu website. It was one of the North American mirrors [USA], but not sure which one exactly. here is the link to the page where I got it from:

.::[LINK]("http://www.ubuntu.com/products/GetUbuntu/download#currentrelease")::.

EDIT: Oh forgot to add I chose other options because I downloaded it through Azureus! [Bittorrent]

---

### Post by riven0 on 2007-01-13
BioGene, for Totem, try copying and pasting this to the terminal:

> sudo apt-get install libdvdread3 && sudo /usr/share/doc/libdvdread3/./install-css.sh


Make sure you have the universal and multiverse repositories enabled before doing this, or it may not work.

---

### Post by BioGene on 2007-01-13
> **riven0 said:**
> BioGene, for Totem, try copying and pasting this to the terminal:




Make sure you have the universal and multiverse repositories enabled before doing this, or it may not work.

Sorry to be a newbie but how exactly would I enable them? I just tried it and seems they were not enabled cause after it finished it still gave me the same error!

---

### Post by riven0 on 2007-01-13
Did it download and install fine, or did you get an error? 

Anyway, how about posting your sources.list here to enable those repositories? Of course, you could do this graphically through Synpatic, but I always notice it doesn't enable everything on my comp. 

So, in the terminal, copy and paste this:
> 
sudo gedit /etc/apt/sources.list

Then paste the contents here.

---

### Post by BioGene on 2007-01-13
Ok here is my source list, and no it did not give me any error:

> # 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
deb [http://seerofsouls.com/](http://seerofsouls.com/) edgy contrib
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
#AUTOMATIX REPOS END


---

### Post by riven0 on 2007-01-13
Hmm, no errors.... and I see you already have all the repositories enabled. Automatix already did it for you. :-k 

How about MPlayer, can you play your dvd's through there?

> sudo apt-get install mplayer

---

### Post by BioGene on 2007-01-13
The problem really isn't DVD's, its more of some of the streaming videos of the internet. Such as the Apple.com website won't load their videos, and I have no idea why. Also another site called Twit.tv also won't load their video files. Is this maybe due to the fact that I do not have all plugins installed for firefox?

---

### Post by bg1256 on 2007-01-13
> **BioGene said:**
> The problem really isn't DVD's, its more of some of the streaming videos of the internet. Such as the Apple.com website won't load their videos, and I have no idea why. Also another site called Twit.tv also won't load their video files. Is this maybe due to the fact that I do not have all plugins installed for firefox?

Sounds like you might need the flash plugin for firefox. Search synaptic.

Also, be sure you have the mplayer plugin for firefox as well, also in synaptic.

---

### Post by BioGene on 2007-01-13
> **bg1256 said:**
> Sounds like you might need the flash plugin for firefox. Search synaptic.

Also, be sure you have the mplayer plugin for firefox as well, also in synaptic.

Ok I just installed both the mplayer plugin for firefox and the flash player plugin and nothing again it says that it could not play because I am missing a decoder, should consider to install a missing plugin. I am trying to load some videos of the Apple website so could it be QuickTime is missing or something?

Oh and one more thing, when I do try to view it a little purple box appears in the left hand corner and then I get the message! So not sure if that can help in any way!

P.S.
Just tried to install the Quicktime files for reading and writing files, and it still would not work!

---

### Post by bg1256 on 2007-01-13
Can you link to the video you're trying to download / view?

edit: I just visited Apple with no problems anywhere.

My guess is that you don't have the proper codec installed.

Remind me, did you get Automatix up and running yet?

---

### Post by BioGene on 2007-01-13
Yeah sorry I was away for such a long time was busy doing something outside the room. Anyways Yeah I got Automatix up an running easily, and I installed some things as well! Not any codecs at the moment though, should I try all of them or what?

[COLOR="Red"]EDIT:[/COLOR]

Ok I just went to AutoMatix2 to see if the flash player was installed and the other plugins for firefox, strangely when I tried to install them it said there was none installed. Yet I installed them through synaptic earlier on! What gives? Also when I tried to install them it gives me error for both flash player and the Swift Fox plug ins!

Ok, for SwiftFox it says that it can not install because swift fox is not installed, I did not do this because Ubuntu already came with 2.0 Firefox! So should I install Swift Fox?

Second, Flash Player won't install due to an apt-based error, not sure why!

[COLOR="Red"]EDIT 2:[/COLOR]

Ok so I just installed Swift Fox, it is Firefox it seems lol :). Anyways I then tried to install Swift Fox plug ins and again I got this time the same error that I get for flash player! An apt-based error! What is happening wrong?

---

### Post by Sef on 2007-01-13
> Second, Flash Player won't install due to an apt-based error, not sure why!


What does the error say?  Copy and paste it here or take a snapshot of it.

---

### Post by BioGene on 2007-01-13
> **Sef said:**
> What does the error say?  Copy and paste it here or take a snapshot of it.

Ok the weirdest thing happened I tried it once again and it died on me and I did not get enough time to copy and paste then when I tried to do it again and I was about to copy it it closes and no error! So I check the installed list and flash player was installed! Why it did this confuses me. Is it maybe because I tried it for almost 10 times or maybe something I did?

---

### Post by riven0 on 2007-01-14
Okay, how about installing Flash 9, instead? First, go to the terminal and paste these in:

First, to download the plugins:

> wget [http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb) && wget [http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplayer-nonfree_9.0.21.78-3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplayer-nonfree_9.0.21.78-3v1ubuntu1_i386.deb)

Then to install them:

> sudo dpkg -i flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb && sudo dpkg -i flashplayer-nonfree_9.0.21.78-3v1ubuntu1_i386.deb 

Then restart firefox, and see if it works again. If not, we can try installing it manually...

---

### Post by BioGene on 2007-01-14
Um I have a problem downloading the files, this is what the terminal gives me:

> --19:26:38--  [http://3v1n0.tuxfamily.org/pool/edgy...untu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy...untu0_i386.deb)
           => `edgy...untu0_i386.deb'
Resolving 3v1n0.tuxfamily.org... 212.85.158.4
Connecting to 3v1n0.tuxfamily.org|212.85.158.4|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:26:39 ERROR 404: Not Found.


Are the links working or is it my ubuntu?

---

### Post by riven0 on 2007-01-14
:-k Yeah, they were working fine yesterday. Now I'm also getting a 404 error. Alright, we can try going directly through Adobe.

So, in the terminal again, remove the old one, if you have any:

> sudo apt-get remove flashplugin-nonfree; sudo rm /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/firefox/plugins/flashplayer.xpt

To download the new one from Adobe:

> wget [http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin](http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin)

Then to unpack and install:

> tar xf FP9_plugin_beta_112006.tar.gz && cd flash-player-plugin-9.0.21.78/ && 
sudo mv libflashplayer.so /usr/lib/firefox/plugins/

Hopefully, this will work.

---

### Post by BioGene on 2007-01-14
Here is a pic of the error box [not terminal]:

[IMG]http://i118.photobucket.com/albums/o117/BioGene_07/screenshot.jpg[/IMG]
[COLOR="Red"]
EDIT:[/COLOR]

Ok I just tried to install it through adobe and again I get a 404 error! I don't understand why it is doing this!

---

### Post by riven0 on 2007-01-14
Very weird. I'm guessing it only does this when trying to view a quicktime file? As a last resort, try installing these codecs:

> sudo apt-get install gstreamer0.8-pitfdll gstreamer0.10-pitfdll libquicktime0 quicktime-x11utils

EDIT: BTW, I've just checked the link through Adobe, and it loaded fine. Is your network connection okay?

---

### Post by BioGene on 2007-01-14
> **riven0 said:**
> Very weird. I'm guessing it only does this when trying to view a quicktime file? As a last resort, try installing these codecs:



EDIT: BTW, I've just checked the link through Adobe, and it loaded fine. Is your network connection okay?

Well its loading all website perfectly and quickly so no really problems from the browser aspect! Not sure about anything else!

I just installed the libraries a few minutes ago and I restarted firefox but no luck! Oh should I be using the automatix2 alongside synaptic package manager, I mean if I installed something from one app will the other auto. notice the installation?

EDIT:
Ok so when I try the link in my browser to the plug-in it will load adobe and as well it will say error: page not found! I guess it is something with my connection, what I have no clue but I will try to find out!

[COLOR="SeaGreen"]EDIT:[/COLOR]
Anyone know why the partitioning app in my linux ubuntu installer is not graphical? Sorry to be bothersome but I just really wanted to know!

---

### Post by BioGene on 2007-01-18
Um hey everyone, Yup still having this issue! Can someone help me out here please or can give me some more feedback! I thik I am missing some type of codecs but not sure which ones. Oh and I think the codecs should be for Totem as that is the default one! I did not try to install any other one yet!

---

