---
title: "Any suggestions on older computer"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-01-29
Anybody have suggestions on which version of Ubuntu or Kubuntu I can use on an older computer?

Right now I have a freebie I recieved from a co-worker that has W/98 on it now but I would like to try a linux based OS.

I tried a Ubuntu 7.10 version but I think the ram was unadequate at 128. If I add a couple more memory sticks at 128 each would it work?

The basic system is a gateway 750 MH pentium 3 processor.  What might be a good OS for the machine? I really only want to have a good fast web browser and a descent e-mail account. I also would like to be able to load pictures from my digital camera to it as well. No gamer here, just internet browsing basically.

I hope I'm posting on the right forum.

Thanks and please post your thoughts. Here are some pics.

[IMG]http://i187.photobucket.com/albums/x152/Indy452/cstuff3.jpg[/IMG]
[IMG]http://i187.photobucket.com/albums/x152/Indy452/cstuff4.jpg[/IMG]

---

### Post by aysiu on 2008-01-29
Stay at 128 MB of RAM: Use IcewM or Fluxbox
Move to 256 MB of RAM: Xubuntu
Move beyond 256 MB of RAM: Kubuntu or Ubuntu

---

### Post by brettg on 2008-01-29
The extra RAM will make a huge difference, 128Mb works but it is unusably slow (IMO)

For low spec systems try xubuntu, which uses xfce window manager. You can download the ISO or simply do a base server install and then install xubuntu-desktop with;

apt-get install xubuntu-desktop 

Good luck

---

### Post by bloodniece on 2008-01-29
[LIST]
[*]Xubuntu is lite and legacy friendly
[*]Puppy Linux  ([http://www.puppylinux.org/]("http://www.puppylinux.org/"))
[*]Damn Small Linux  ([http://damnsmalllinux.org/]("http://damnsmalllinux.org/")
[*]make it a home server  ([http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver"))
[/LIST]

---

### Post by Nythain on 2008-01-29
aysiu ftw
fluxbox is amazing though it requires one to be a .conf .rc addict (translation, it requires a bit of "configuring")
xfce wich as mentioned is the Xubuntu window manager of choice is pretty slick, the xubuntu version i consider nothing more than a lightweight gnome though...
if you want a hardcore linux experience to brush up on/learn those vital bash commands then a command line system install or server install would be the way to go...

my personall choice would be a command line system installation with a minimal fluxbox added on...
on the Damn Small Linux site, and somewhere on the Ubuntu site, is a list of lightweight apps for low spec systems... very usefull

---

### Post by Indy452 on 2008-01-29
> **brettg said:**
> The extra RAM will make a huge difference, 128Mb works but it is unusably slow (IMO)

For low spec systems try xubuntu, which uses xfce window manager. You can download the ISO or simply do a base server install and then install xubuntu-desktop with;

apt-get install xubuntu-desktop 

Good luck

What does download the ISO mean? I don't have a cd burner, will I need to burn an install cd to install xubuntu?

Thanks, Neal

---

### Post by Indy452 on 2008-01-29
> **Nythain said:**
> aysiu ftw
fluxbox is amazing though it requires one to be a .conf .rc addict (translation, it requires a bit of "configuring")
xfce wich as mentioned is the Xubuntu window manager of choice is pretty slick, the xubuntu version i consider nothing more than a lightweight gnome though...
if you want a hardcore linux experience to brush up on/learn those vital bash commands then a command line system install or server install would be the way to go...

my personall choice would be a command line system installation with a minimal fluxbox added on...
on the Damn Small Linux site, and somewhere on the Ubuntu site, is a list of lightweight apps for low spec systems... very usefull

Uuuuh, I'm sorry man I just don't really understand that much about the linux projects. I've been using windows based systems for too long now and for some reason I'm drawn to this linux thing. The very few experiences I've had with ubuntu have been neat. I like the way they look and feel. I just don't know a whole lot about it. I need something lightweight and verry user friendly. Does it exist??

Thanks, Neal

---

### Post by dhughes on 2008-01-29
Most of those suggestions are for "light" versions of Linux, a light version related to Ubuntu is called Xubuntu it is small and doesn't use as much resources as Ubuntu or Kubuntu.

 In Windows once the OS is installed you see the GUI also known as a window manager in Linux speak, it's the way you interact with the OS (you can use a command line aka DOS in Windows), Linux has quite a few choices as well for the GUI some are GNOME (used by Ubuntu), KDE (used by Kubuntu), Fluxbox, Xfce (used by Xubuntu).

 Distributions (types) of Linux are usually downloaded as an .iso an exact image of what will be put on your hard drive when you install. You can do it other ways such as a network install but that usually requires you to download a small boot disk, and you can also (I guess) install from a USB stick if the computer supports booting from USB and if the .iso is set up correctly on the USB stick.

---

### Post by Nythain on 2008-01-29
you dont HAVE to download an iso... you can order free cd's from ubuntu's official website i believe, not sure if they charge for shipping or not though.

As far as all this "lightweight" "desktop environment" "window manager" "xubuntu, fluxbuntu, ubuntu, kubuntu" business it works like this.

The most lightweight (small resource consuming and requirement) system you are going to get is a pure "command line" system. it just installs the basic core of the os, with no Graphical User Interface (gui)... this is obviously not a good recomendation for you.

Next we have systems with no official Desktop Environment (a collection of programs designed around the same graphical libraries to run well together, examples KDE and Gnome) and a very lightweight Window Manager (In charge of actually creating/drawing/manipulating/decorating all the "windows") such as Openbox, IceWM, Fluxbox... This would be the best suggestion with your current specs

The next step up on resource consumption would be a lightweight system setup like Xubuntu (wich uses the Xfce desktop environment<?>)... its not as much of a resource hog as gnome and kde, but not as simple as *box, icewm, and others. This is a great idea if you upgrade your ram with another 128mb for a total 256mb

If you can manage to get 512 or more, the Ubuntu and Kubuntu become more of an option... Ubuntu uses gnome and gtk (graphical library<?>) apps whereas Kubuntu uses KDE and qt3/4 apps... Wich one of those you prefer is totally up to you. Some will argue one is faster than the other, and others will argue vice versa... Some will argue one is more customizable than the other and vice versa... once you get to Gnome vs KDE it really boils down to personall prefrence.

hope that helped clarify things a little bit

---

### Post by oedha on 2008-01-29
xubuntu will work on yours....i have tried on 500MHz w/ 128MB of RAM and riva tnt2 nvidia w/64mb graphic card
i made 1GB of harddisk space as the swap partition to help your RAM acceleration

to start Linux : you have to have the installation cd on your hand
you can download it, borrow, buy it

regards;
~E~

---

### Post by Inxsible on 2008-01-29
I would also recommend Zenwalk which is another Xfce based distro.

I run it on a P3 -600 Mhz with 256 MB RAM and 20 GB HDD. Looks neat too. I find Xubuntu very slow on the same machine.

If you are newbie, you would want to keep away from Fluxbuntu for now.

Of course the smaller OSes like DSL and Puppy remain hugely popular, if you like the look and feel of it.

---

### Post by Redptc on 2008-01-29
I have an old computer but have added enough ram to bring me just over the 256 mark by the existing 64 meg to a total of 320. I will add the next bit soon, that is, I will buy another batch to bring it to 512.

At my 320 level I am running 7.10 Ubuntu and it is what I suggest you do. Add enough ram, which is not all that expensive these days, to allow the use of Ubuntu, it is worth it.

You may have other issues but I feel that this is the best way to go!

I also added a hard drive so that Ubuntu has it's own drive and I can Dual boot with the existing windows.

The amount of software that is available is difficult to appreciate!

Another big issue with Ubuntu is this forum that will help you through most problems.

---

### Post by DMK62 on 2008-01-30
Xubuntu with 256 mb of ram would be a good choice. It will meet your requirements for browsing and email.

As far as the install CD goes You can try the methods posted before my post. Do you know anyone that has an external cd writer ? There is a couple important things to do when you have downloaded the ubuntu iso file. Do a checksum check on the file you downloaded ( instructions on how to do that is on the download page ). Also burn the cd at a low rate such as 4x.

I just checked the Xubuntu site and unfortunately Xubuntu is not available through Ubuntu ShipIt where they mail you the install CD. Ubuntu, Kubuntu, and Edbuntu cd's are available through that method. 

Dale

---

### Post by Redptc on 2008-01-30
> **DMK62 said:**
> Xubuntu with 256 mb of ram would be a good choice. It will meet your requirements for browsing and email.

As far as the install CD goes You can try the methods posted before my post. Do you know anyone that has an external cd writer ? There is a couple important things to do when you have downloaded the ubuntu iso file. Do a checksum check on the file you downloaded ( instructions on how to do that is on the download page ). Also burn the cd at a low rate such as 4x.

I just checked the Xubuntu site and unfortunately Xubuntu is not available through Ubuntu ShipIt where they mail you the install CD. Ubuntu, Kubuntu, and Edbuntu cd's are available through that method. 

Dale

Xubuntu is 'part' of the Ubuntu disk....once you have one you have the other!

---

### Post by DMK62 on 2008-01-30
Please correct me if I am wrong concerning the Ubuntu cd. The Ubuntu cd contains the Ubuntu base and the gnome DE. The Xubuntu cd contains the Ubuntu base and the Xfce DE. You can install additional DE's once you have installed it. 

Dale

---

### Post by Redptc on 2008-01-30
> **DMK62 said:**
> Please correct me if I am wrong concerning the Ubuntu cd. The Ubuntu cd contains the Ubuntu base and the gnome DE. The Xubuntu cd contains the Ubuntu base and the Xfce DE. You can install additional DE's once you have installed it. 

Dale

You boot Ubuntu, go to synaptic and locate xubuntu, load it and the next time you boot you have a choice to run xubuntu or ubuntu. 

redptc

---

### Post by DMK62 on 2008-01-30
Ok. I just wanted to make it clear to the OP that Xubuntu is not included on the Ubuntu CD. It requires the additional download and installation of the xubuntu-desktop package after Ubuntu is installed.

Dale

---

### Post by Nythain on 2008-01-30
> **Redptc said:**
> You boot Ubuntu, go to synaptic and locate xubuntu, load it and the next time you boot you have a choice to run xubuntu or ubuntu. 

redptc
This works fine and dandy ceptin that fact that well, that system might not install/run ubuntu very well... thus all the recomendation of downloading/ordering Xubuntu... so the new to linux/ubuntu user doesnt have to bother installing a DE just to install another one, and attempt to remove the old one...

a better similar suggestion would have been, put in ubuntu cd, choose install command line system (if thats an option on the 7.10 non alternate disc) then from command line run sudo apt-get install xubuntu-desktop or whatever its called, that way no Gnome clutter...

---

### Post by Redptc on 2008-01-30
> **Nythain said:**
> This works fine and dandy ceptin that fact that well, that system might not install/run ubuntu very well... thus all the recomendation of downloading/ordering Xubuntu... so the new to linux/ubuntu user doesnt have to bother installing a DE just to install another one, and attempt to remove the old one...

a better similar suggestion would have been, put in ubuntu cd, choose install command line system (if thats an option on the 7.10 non alternate disc) then from command line run sudo apt-get install xubuntu-desktop or whatever its called, that way no Gnome clutter...

Gee, I didn't have any trouble, clutter or nothin, it just works and I can use either on bootup. Comes up blue or brown!  Besides, it wasn't my creation, they, the people on xubuntu web site, told me to do it! Who am I.....!:neutral:

---

### Post by Indy452 on 2008-01-30
Thanks for the suggestions folks. I think I may just download the ISO image and have a friend burn it to cd at low rate.

If I can't load the current version of ubuntu now I don't see how I could get xubuntu out of it right?
So I'll have to get it via a cdrom.

I think I'll try the xubuntu or kubuntu after I add more ram because all the others scare me quite franklly.
I would really screw up an install especially since I really don't know all the terms and such.

I'm sure you have not heard the last of me. Thanks for the help and is there a good place to read up on xubuntu in lamens terms?](*,)


Neal

---

### Post by nitemann on 2008-01-30
How much RAM do you have and the also the Video Card?
I have Gutsy running on an even Older PII 400MGZ with 300 megs of
Ram and an 8 Meg AGP... I ts runs ok.. I  did install  Linux Mint 4.0 on same partion and it runs a little smoother.. But I think your PIII will run UB2
just fine..

---

### Post by philinux on 2008-01-30
Ubuntu 7.1 running fine here.

---

### Post by OldLinuxGuy on 2008-01-30
The key thing you need is RAM.  Upgrade your RAM to 512 meg as for processor speed anything about a 350MHz can run Kubuntu which has all the bells and whistles.   I have it running here on a 350 MHz K6 with 378 meg of RAM and performance is acceptable.

---

### Post by jonabyte on 2008-01-30
> **Indy452 said:**
> What does download the ISO mean? I don't have a cd burner, will I need to burn an install cd to install xubuntu?

Thanks, Neal

DO you know someone who has broadband internet and a cd burner, try to ask them. Or you can order a cd, or even try your local mag stand and see if there are any Linux mags with cds in them. Not sure what is currently out these days.

---

### Post by eriqjaffe on 2008-01-30
Indy:

Since your system only has 128mb or RAM you'll have to use the Alternate Install CD, as the regular LiveCD requires 256MB of RAM to run the installer.

---

### Post by aysiu on 2008-01-30
> **eriqjaffe said:**
> Indy:

Since your system only has 128mb or RAM you'll have to use the Alternate Install CD, as the regular LiveCD requires 256MB of RAM to run the installer.
Even 256 MB of RAM is sometimes not enough to run the installer. I'd vote for a minimum of 384 MB.

---

### Post by Jerry N on 2008-01-30
FYI, [http://www.linuxcd.org/](http://www.linuxcd.org/) sells installation cds for several linux distributions at a very low price.  I haven't bought anything from them myself.  

Jerry

---

