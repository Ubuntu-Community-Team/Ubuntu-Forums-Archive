---
title: "Uninstalling GNOME\Switching to KDE"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-10-03
I have made the switch From Windblows to Ubuntu officially as far as my Operating System goes but i still use a windows machine for online games since the PC i am running my linux box on still has a stock Graphics card.

Anyway, back to my question about Uninstalling GNOME
I was wondering if it is possible to uninstall the GNOME desktop along with anything related to GNOME.

I use KDE as my main desktop enviroment and instead of taking up space on my H.D. with something i am prolly never going to use (GNOME) is there a way to uninstall all of GNOME even though i used a Ubuntu Install CD that comes standard with GNOME?

Question LIst:
What packages would i have to uninstall To completely remove GNOME and all of GNOME's components?
Would i still be able to use the synaptic package manager?
Would this resort in any catastrophic system failures?

BTW - I am already using KDM.

(The word 'GNOME' has been used 10-Time(s) in this post)

---

### Post by Mustard on 2005-10-03
Hmmm...that's a toughie.  May I ask why you wouldn't try installing Kubuntu rather than Ubuntu, which has KDE as default desktop?

---

### Post by nitricacid on 2005-10-03
Besides the fact that i now have a complete working Linux system and don't want to risk installing the OS again if i don't have to.

I have tried on several occasions to install from a Kubuntu CD and everytime it ends in failure do to some kind of error with the install\ISO.
I have burned and reburned Kubuntu and everytime it never installs rite.

---

### Post by Mustard on 2005-10-03
Ah k..fair enough. :)

I have no experience with trying this so thats my best shot, sorry.

---

### Post by Jussi Kukkonen on 2005-10-04
I don't know if there is a clean way to do this.

I'm pretty sure you can *apt-get remove gnome**, but that'll only be 300 MB or so... You cannot remove all gtk2-stuff if you want to keep using gtk applications like Synaptic.
[edit:] and afterwards, you can use *deborphan* to find unused libraries.

---

### Post by darkmatter on 2005-10-04
Well. To add KDE

```
sudo apt-get install kubuntu-desktop
```

Curing the installation, it will ask you to choose between GDM and KDM for your display manager. In your case, select KDM.

As for removing. If the installation goes well (KDM and KDE function properly), begin by removing GDM and other GNOME components from synaptic is the easiest way. Just select the Gnome components to uninstall , if you see any 'will also be removed' notices, take note of what is being listed.

For example, if you want the GIMP, but selecting a package for removal tells you that the GIMP is also to be uninstalled, then you obviously want to keep that package.

It's somewhat trial and error cleaning out the files you don't need unless you have deborphan installed (installing that will save you a headache, as it will show you which packages no longer have any associations.) Afer that, it's just a matter of purging residual configs from the system.

Hope that helps.

---

### Post by darkmatter on 2005-10-04
[QUOTE=Jussi Kukkonen]*apt-get remove gnome**[/QUOTE]

Not to put you on the spot. But that command should be

```
sudo apt-get uninstall gnome
```;) 

It won't solve his problem, but will help him get a head start.

---

### Post by Mustard on 2005-10-04
Backup first with mondo. :)  *cross fingers and pray*

---

### Post by Hobbsee on 2005-10-04
I tried to do what you were doing...tried to remove some of the programs that would get rid of the desktop environment, but I couldnt find the gnome equivalent for it - I know that if you remove kde-core it removes all the other kde stuff, as all the kde stuff depends on you having that.

I ended up grabbing the kubuntu cd, and just installing from there, and have had no problems...

---

### Post by nitricacid on 2005-10-04
I think what i might end up doing since i have another hard drive in this computer (currently running windows from it) i will wait till the full Breezy (Kubuntu version) comes out. download,burn, & install on to the second hard drive and see how the installation goes.

I use my linux box for basicly everything now but where as my second hard drive runs a server for Wolfenstien Enemy Territory and i would love to be able to run a  Wolf ET server from linux.

Thanks for all the help, I greatly appreciate it :D


P.S.
Ubuntu And The People at Ubuntu Forums Rule.

---

### Post by jonrkc on 2005-10-05
[QUOTE=darkmatter]Not to put you on the spot. But that command should be
```
sudo apt-get uninstall gnome
```;) 
It won't solve his problem, but will help him get a head start.[/QUOTE]
I'm confused at this point.  Half the time when I try to remove something, I type the word "uninstall" instead of "remove" and receive the reply 
```

E: Invalid operation uninstall

```
I just checked the man page for the version of apt-get that I received with Hoary 5.04, and there is no "uninstall" option; there is, though, the "remove" option that I always "correct myself" with when uninstalling something.

Am I missing something?  

(BTW, I too am hoping I can completely remove Gnome eventually.  I got rid of the desktop--that's a start--but there are thousands of items left....)

---

### Post by nitricacid on 2005-10-05
I think that if you installed ubuntu and not Kubuntu then you need most of the Gnome packages since the CORE package is based around gnome and not KDE. I could be wrong though.

---

### Post by snowjunkie on 2005-10-05
I've installed Ubuntu... moved to KDE and then moved back again...

Install KDE first and then remove Gnome.

```
sudo apt-get install kubuntu-desktop
```

You'll be asked which window manager you like to use by default.  Select KDM.

The kubuntu desktop only has a limited amount of apps.  Use ```
sudo apt-get install KDE
``` to get lots more (after using the install kubuntu-desktop command).

If you have the space, leave Gnome on your system for a while to make sure you like KDE enough to dump Gnome.

I used synaptic to remove all Gnome base desktop and related applications.

I have since come back to Gnome and removed most of KDE - just kept a couple of KDE apps on my box.  I'm settled now, just waiting on Breezy to be released!

I'm not at my linux box right now, so hopefully the commands above are correct.  Somebody will correct me anyway if they're not!

---

### Post by nitricacid on 2005-10-05
I have used KDE in every flavor of linux i tryed so i am more used to KDE then GNOME.
I like using the GNOME desktop but i can't stand how every window you open opens in a new window so by the time you find what you are looking for you have 20 windows open.
 Is there any way to make it so everything opens in one window no matter how many folders you click on?

I have more then enough Disk space (40Gig) and don't mind having GNOME installed incase i need to use something in gnome but i really don't use Gnome at all so i just thought i would ask if there was anyway to kill it untill i needed it for something major.

(GNOME word Count = 5)

---

### Post by snowjunkie on 2005-10-05
There is a way to change it so it will open new windows within itself.  I'm not entirely sure what the setting is though.  Do a search through the forums.
Sorry, I thought you were planning to use KDE for the first time.  I totally removed gnome using synaptic like I said in my post above.

---

### Post by cvmostert on 2005-10-21
i have uninstalled gnome* and am bussy installing kde now.. whish me luck.. i have gnome on one hard drive.. tried to install kubuntu on the other... 

the kubuntu install cd did not work.. THEN i installed ubuntu and now am trying to switch from gnome to kde... 

will see

thanx for all the post--helps!

---

### Post by cvmostert on 2005-10-21
hi, i am on the kde hard drive now... and it seems to be working just fine... will report any problems.
ciao

---

