---
title: "Mint 15: I am scared to uninstall packages"
date: 2013-09-08
forum: Any Other OS
---

### Post by Coder88 on 2013-09-08
If I mark some packages (hit or miss) in Synaptic Package Manager (or even if using 'sudo apt-get remove somepackage') the system will say that several or many other packages will also be removed-- and sometimes that just does not look like a good thing to do. For example, uninstalling something as simple as a media player might say that gnome will also be removed. Gnome? wtf, GNOME? Why would the gnome desktop need to be removed just to uninstall a media player?!? I have to say I have diminished confidence in uninstalling any app that also wants to uninstall a desktop manager like gnome. Am I missing something here other than the obvious which feels like synpatic or apt-get have deep problems with this? I sincerely hope I am wrong and that somehow some way it is actually safe to remove apps that also choose to remove what would seem like critical additional apps like gnome.

---

### Post by stinkeye on 2013-09-08
Note what is being uninstalled.
There are meta-packages for the different desktop environments.
These meta-packages only install the applications to run that complete environment.

If you uninstall a package that is deemed to be part of that environment it will also uninstall the meta-package.  
eg if you uninstall a component of the Gnome desktop environment it will also uninstall the **gnome** meta-package.

Re-installing the **gnome** meta-package will pull in all the default packages for Gnome desktop environment.
**ubuntu-desktop** is also a meta-package.

---

### Post by Coder88 on 2013-09-08
> **stinkeye said:**
> Note what is being uninstalled. There are meta-packages for the different desktop environments. These meta-packages only install the applications to run that complete environment. If you uninstall a package that is deemed to be part of that environment it will also uninstall the meta-package.  eg if you uninstall a component of the Gnome desktop environment it will uninstall the **gnome** meta-package. Re-installing the **gnome** meta-package will pull in all the default packages for Gnome desktop environment.
**ubuntu-desktop** is also a meta-package.

So for example I selected Abiword (word processor) for removal in Synpatic Package Manager and am notified that gnome will also be removed. Wtf?!? Why would the gnome desktop system need to be removed just to remove a word processor that has nothing to do with the gnome desktop system? This makes no sense to me and I suspect to others, and only can cause grief for unsuspecting linux noobs who think removing Abiword should cause no more damage to the desktop system than e.g. using the MS Windows control panel to remove Abiword for Windows.  The elephant in the room seems to be that there is an inherent flaw with the package (app) removal system.

---

### Post by stinkeye on 2013-09-08
From [**_[COLOR="#B22222"]CommonQuestions[/COLOR]_**]("https://help.ubuntu.com/community/CommonQuestions#About_Ubuntu")
A meta-package is a package that doesn't contain applications within itself, but simply depends upon particular versions of other packages, so that when it is installed, it drags all of them in too. The package manager uses it to know which particular packages to install. For example, the ubuntu-desktop metapackage installs the full GNOME desktop environment, with all the other packages that are in a default Ubuntu install. The existence of meta-packages makes it very easy to install other Ubuntu derivatives on your desktop; see below for more information. 

It is technically just fine to remove a meta-package, if required, and this shouldn't necessarily cause any problems. However, it is strongly recommended that you reinstall that package if you decide to manually upgrade to another version of Ubuntu. The package manager requires those packages to be installed for it to successfully perform the upgrade.
[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by Coder88 on 2013-09-08
Hmm. I have to admit I am not ready to execute the removal of Abiword given that it wants to remove the gnome metapackage-- not until I do a full backup of my Ubuntu system. Maybe someone with more faith in this could give it a try-- remove Abiword and report back that your gnome desktop is still intact and that nothing else is broken?

---

### Post by stinkeye on 2013-09-08
-
> **[SIZE=3]A meta-package is a package that doesn't contain applications within itself[/SIZE]**
A meta-package is basically just a list of applications that it depends upon.
So when you uninstall one of the applications on the list, the meta-package is
uninstalled also, because you no longer have the complete list. 
Want the complete list again, simply reinstall the meta-package.

---

### Post by Petro Dawg on 2013-09-08
Difference between a meta package and a package?...  click below to find out...[URL="http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package"]

http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package[/URL]

Knowledge is power, and knowing is half the battle.

---

### Post by CaptainMark on 2013-09-08
I can see Coder88's point of view, it is annoying that some programs have been packaged in such a way to have completely bizarre dependencies, for example on Xubuntu which already has lightdm and all of its required libraries installed, you try to install the unity-greeter package which is essentially just a different theme for lightdm, and shouldn't require hardly any dependencies that are not already installed, yet it pulls in the ubnutu-desktop meta package which in turn pulls in the likes of gnome-control-centre and the entire gnome3 libraries, even rhythmbox is pulled in as a dependency of unity-greeter, yet if you were to claim that unity-greeter needs rhythmbox to be installed to function, you would be a fool.

Unfortunately its just the way that canonical have built the packages and there is very little that can be done about it. Apt-get is very good at balancing all the necessary packages unfortunately it's not up to apt-get as to what is classed as necessary.

---

### Post by Coder88 on 2013-09-08
Anybody using Gnome up for removing their Abiword (install it if you do not have it), and letting me know if your Gnome desktop system stays intact? I read all the theory here, but (apt-get remove) trust needs to be earned, :)  I just don't have the faith yet to remove Abiword when it hints of losing my Gnome desktop which would be disastrous. If I hear Abiword removal does not damage Gnome from someone who takes that leap of faith, then I might actually believe it. :)  so who wants to do an Indiana Jones and step out onto that invisible walkway over (Indiana Jones and the Last Crusade)?
:)

---

### Post by CaptainMark on 2013-09-08
Well the simple way is to test it yourself but use this little trick. So on my Linux Mint system if I try to uninstall gnome-settings-daemon you'll see it tries to remove cinnamon, which is my desktop environment, just like gnome```
mark@desktop ~ $ sudo apt-get remove gnome-settings-daemon 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  gnome-control-center-data libgnome-control-center1 python-gpgme
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED
  cinnamon cinnamon-control-center cinnamon-screensaver gnome-power-manager gnome-settings-daemon mint-meta-cinnamon nemo nemo-dropbox
  nemo-fileroller nemo-share
0 upgraded, 0 newly installed, 10 to remove and 4 not upgraded.
After this operation, 13.6 MB disk space will be freed.
Do you want to continue [Y/n]?
```So if before I try this I copy and paste everything just after the line "The following packages will be REMOVED" and before the line "0 upgraded, 0 newly installed, 10 to remove and 4 not upgraded" and save it to /home/mark/Desktop/packages.txt
Lets say I go ahead and remove this package and everything goes wrong and I can't log in, I can merely switch to a Ctrl+Alt+F6 terminal log in and run```
sudo apt-get install $(cat /home/mark/Desktop/packages.txt)
sudo reboot
```and bam, everything is back exactly as it was, no harm done

---

### Post by VMC on 2013-09-08
> **Petro Dawg said:**
> Difference between a meta package and a package?...  click below to find out...[URL="http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package"]

http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package[/URL]

Knowledge is power, and knowing is half the battle.

In the beginning, this was always confusing. It appears to the new user, everything I need is being uninstalled, when in fact, its just references.

---

### Post by speartip on 2013-09-08
coder88,
Why don't you list here all the packages that removing abiword wants to uninstall, then someone may be able to offer more help.

---

### Post by Coder88 on 2013-09-08
> **speartip said:**
> coder88,
Why don't you list here all the packages that removing abiword wants to uninstall, then someone may be able to offer more help.

```
$ sudo apt-get remove abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  blender-codecs-ffmpeg1.0 libboost-date-time1.49.0 libcelt0-2 libcmis-0.2-2
  libgnome2-gconf-perl libltcsmpte1 libopenimageio1.1 libreoffice-common
  libreoffice-style-tango linux-headers-3.5.0-25
  linux-headers-3.5.0-25-generic uno-libs3 ure
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-style-human
Suggested packages:
  kde-icons-crystal crystalcursors
Recommended packages:
  libreoffice-core
The following packages will be REMOVED:
  abiword abiword-plugin-grammar abiword-plugin-mathview **gnome**
The following NEW packages will be installed:
  libreoffice-style-human
0 upgraded, 1 newly installed, 4 to remove and 53 not upgraded.
Need to get 2,022 kB of archives.
After this operation, 2,223 kB disk space will be freed.
Do you want to continue [Y/n]? 
```

---

### Post by santosh83 on 2013-09-08
> **CaptainMark said:**
> I can see Coder88's point of view, it is annoying that some programs have been packaged in such a way to have completely bizarre dependencies, ... 

Yeah for example here on my 10.10 system the package plymouth, which is totally unnecessary and distracting to me, has been made to depend on every package in the system, as far as I can see! Remove it, and you remove the whole system!!

I don't understand why things like these are done.

---

### Post by stinkeye on 2013-09-08
> **Coder88 said:**
> ```
$ sudo apt-get remove abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  blender-codecs-ffmpeg1.0 libboost-date-time1.49.0 libcelt0-2 libcmis-0.2-2
  libgnome2-gconf-perl libltcsmpte1 libopenimageio1.1 libreoffice-common
  libreoffice-style-tango linux-headers-3.5.0-25
  linux-headers-3.5.0-25-generic uno-libs3 ure
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-style-human
Suggested packages:
  kde-icons-crystal crystalcursors
Recommended packages:
  libreoffice-core
The following packages will be REMOVED:
  abiword abiword-plugin-grammar abiword-plugin-mathview **gnome**
The following NEW packages will be installed:
  libreoffice-style-human
0 upgraded, 1 newly installed, 4 to remove and 53 not upgraded.
Need to get 2,022 kB of archives.
After this operation, 2,223 kB disk space will be freed.
Do you want to continue [Y/n]? 
```

As expected....removing abiword and plugins, and the meta-package **gnome**

---

### Post by Coder88 on 2013-09-08
> **VMC said:**
> In the beginning, this was always confusing. It appears to the new user, everything I need is being uninstalled, when in fact, its just references.

So a few days ago I installed Linux Mint 15 (Olivia), was running great, then I uninstalled a minor app and suddenly my gnome desktop icons were gone and worse, blah blah blah. So more than just references were uninstalled against my desire. So I switched and did an ArtistX (Ubuntu) install and it is working fantastic. But based on what happened with Mint I am have no desire to risk uninstalling apps until I get to the bottom of this.

---

### Post by Coder88 on 2013-09-08
> **santosh83 said:**
> Yeah for example here on my 10.10 system the package plymouth, which is totally unnecessary and distracting to me, has been made to depend on every package in the system, as far as I can see! Remove it, and you remove the whole system!!

I don't understand why things like these are done.

Exactly. Maybe as some experts here say, only 'references' are uninstalled (not my experience though), but in the LEAST it is not something noobs should have to see or deal with if linux is to evolve to become even more mainstream.

---

### Post by santosh83 on 2013-09-08
> **Coder88 said:**
> Exactly. Maybe as some experts here say, only 'references' are uninstalled (not my experience though), but in the LEAST it is not something noobs should have to see or deal with if linux is to evolve to become even more mainstream.

That is why Canonical has long been favouring their Software Center and deprecating Synaptic. In Software Center I doubt even programs like plymouth are listed, seeing as they are at a 'system' level.

But I guess it would be good practice as far as possible to modularize each program, so they can be added/removed with minimal impact on the rest. Anyway for the life of me I can't understand why plymouth has to depend on hundreds of packages!

---

### Post by buzzingrobot on 2013-09-08
I'm with Coder88.  

While meta-packages are good ways to install complex software with many dependencies, insisting on removing something like Gnome when one has asked to remove only a single package with nothing that depends on it is decidely not clever.

What is in Abiword that all of Gnome depends on it? (News to me.  I'm running Gnome Shell and Abiword isn't installed. ;))

From my own experience, the workaround of immediately reinstalling the metapackage is not foolproof.

This issue isn't Ubuntu-specific, btw.

---

### Post by santosh83 on 2013-09-08
> **buzzingrobot said:**
> I'm with Coder88.  

While meta-packages are good ways to install complex software with many dependencies, insisting on removing something like Gnome when one has asked to remove only a single package with nothing that depends on it is decidely not clever.

What is in Abiword that all of Gnome depends on it? (News to me.  I'm running Gnome Shell and Abiword isn't installed. ;))

From my own experience, the workaround of immediately reinstalling the metapackage is not foolproof.

This issue isn't Ubuntu-specific, btw.

Isn't it rather the fact that the meta-package (for some reason best known only to the maintainer) depends on the package being removed, and hence it too is removed? And wouldn't reinstalling the meta-package pull in the just removed package once again? Just speculating...

---

### Post by Coder88 on 2013-09-08
> **buzzingrobot said:**
> I'm with Coder88.  

While meta-packages are good ways to install complex software with many dependencies, insisting on removing something like Gnome when one has asked to remove only a single package with nothing that depends on it is decidely not clever.

What is in Abiword that all of Gnome depends on it? (News to me.  I'm running Gnome Shell and Abiword isn't installed. ;))

From my own experience, the workaround of immediately reinstalling the metapackage is not foolproof.

This issue isn't Ubuntu-specific, btw.

Or how about if apt-get / synaptic say something like: "The following will be removed blah blah blah **gnome-references**"
Instead of "The following will be removed blah blah blah **gnome**" 
The former would not strike fear into me, the latter would. I know we are approaching horror season (October, though I start watching scary flicks in September), but I would rather be scared by *Halloween* than by Synaptic, lol.

---

### Post by buzzingrobot on 2013-09-08
> **santosh83 said:**
> Isn't it rather the fact that the meta-package (for some reason best known only to the maintainer) depends on the package being removed, and hence it too is removed? And wouldn't reinstalling the meta-package pull in the just removed package once again? Just speculating...

I'll guess that some packages listed in a meta-package may be there because a developer wants to make it very easy to install a collection of software. Many components will have dependencies on each other.  But, some become part of the dependency chain only because the packagers are trying to make life easy for users.

---

### Post by stinkeye on 2013-09-08
> **Coder88 said:**
> Or how about if apt-get / synaptic say something like: "The following will be removed blah blah blah **gnome-references**"
Instead of "The following will be removed blah blah blah **gnome**" 
The former would not strike fear into me, the latter would. I know we are approaching horror season (October, though I start watching scary flicks in September), but I would rather be scared by *Halloween* than by Synaptic, lol.
The unknown causes fear.
It's very easy to find out what a package is by looking at it's description in synaptic.
I've had no issue with uninstalling certain apps which also uninstall meta-packages.
Still fail to see your problem with uninstalling a meta-package when all it's
doing is removing a dependency list, not actual software.

> So a few days ago I installed Linux Mint 15 (Olivia), was running great, then I uninstalled a minor app and suddenly my gnome desktop icons were gone and worse, blah blah blah.
How do we know if this has anything at all to do with a meta-package if you 
don't state the "minor app" and describe the consequences as "blah blah blah"?

---

### Post by VMC on 2013-09-09
> **stinkeye said:**
> The unknown causes fear.
It's very easy to find out what a package is by looking at it's description in synaptic.
I've had no issue with uninstalling certain apps which also uninstall meta-packages.
Still fail to see your problem with uninstalling a meta-package when all it's
doing is removing a dependency list, not actual software.


How do we know if this has anything at all to do with a meta-package if you 
don't state the "minor app" and describe the consequences as "blah blah blah"?

I think this is the whole crux of the problem. It appears the OP doesn't trust that removing meta-anything will only remove lists and not the program itself.

---

### Post by santosh83 on 2013-09-09
> **VMC said:**
> I think this is the whole crux of the problem. It appears the OP doesn't trust that removing meta-anything will only remove lists and not the program itself.

Since Ubuntu is marketed actively to those new to Linux and the less technical people in general, and also aims to be as user-friendly as possible, a message in the GUI indicating a said package is only a meta-package and will not remove any actual stuff would be useful. This will allay the fears many people like coder88.

---

### Post by Coder88 on 2013-09-09
> **stinkeye said:**
> ...How do we know if this has anything at all to do with a meta-package if you don't state the "minor app" and describe the consequences as "blah blah blah"?

You don't. But I was not taking notes at the time. Linux Mint was a nightmare I never care to relive. I have installed linux perhaps 100x in the past 20 years. I was excited at installing linut mint given it was rated #1 at distrowatch. Installed great on my desktop on a dedicated drive. Installed great on my laptop as a virtual machine. Installed great on my Windows 7 as a virtual machine. It broke on all three over a few days-- remove a minor app (i was not taking notes) and i lost icons (i got them back by reinstalling icon packages) and on one machine i lost my desktop. Frustrating. I removed all Mint installs. I remembered I had ArtistX installed on a sata drive; ArtistX has been good to me the past few days. And I remember never having such issues ever with perhaps a dozen straight up Ubunu installs.

All you have is blah blah blah because again I was not taking notes on any of the three Mint installs. You can do whatever you want; i might have bad breath but i am staying clear of anything and everything Minty forever. :)

---

### Post by Coder88 on 2013-09-09
> **santosh83 said:**
> Since Ubuntu is marketed actively to those new to Linux and the less technical people in general, and also aims to be as user-friendly as possible, a message in the GUI indicating a said package is only a meta-package and will not remove any actual stuff would be useful. This will allay the fears many people like coder88.
^^^
  +1

---

### Post by philinux on 2013-09-09
> **Coder88 said:**
> If I mark some packages (hit or miss) in Synaptic Package Manager (or even if using 'sudo apt-get remove somepackage') the system will say that several or many other packages will also be removed-- and sometimes that just does not look like a good thing to do. For example, uninstalling something as simple as a media player might say that gnome will also be removed. Gnome? wtf, GNOME? Why would the gnome desktop need to be removed just to uninstall a media player?!? I have to say I have diminished confidence in uninstalling any app that also wants to uninstall a desktop manager like gnome. Am I missing something here other than the obvious which feels like synpatic or apt-get have deep problems with this? I sincerely hope I am wrong and that somehow some way it is actually safe to remove apps that also choose to remove what would seem like critical additional apps like gnome.

Mine is a default Ubuntu install. Neither abiword or gnome packages are installed on my system. 

If i attempt to install abiword it does not pull in the meta package gnome. 

What was your original install and what else did you install that pulled in the full gnome dependencies.

---

### Post by Coder88 on 2013-09-09
> **philinux said:**
> What was your original install and what else did you install that pulled in the full gnome dependencies.

Linux Mint 15.
I was not taking notes, so I can not say what I installed. Usually I install Eterm, Songbird, Dropbox, wallpapers.

I am currently using ArtistX (Ubuntu 12.04), working fantastic. No nightmare issues like those that happened with Mint on three separate installs.

---

### Post by howefield on 2013-09-09
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by buzzingrobot on 2013-09-09
The problem is not that of removing a meta-package.  

The problem is removing a single application that has been made, perhaps artificially, part of the dependency chain in a meta-package.  So, removing that single package also prompts the removal of the entire meta-package it belongs to. This is irritating and inexplicable to users who, logically, can't think of a reason why this should be happening.

Here's another common scenario:  User installs a Cute Little App. One file, that's it.  User decides the Cute Little App needs to go.  User runs "sudo apt-get remove Cute Little App" and is presented with a notice that a range of other software, perhaps core components, will also be removed.  Why?  How can any kind of dependency links exist between those components and Cute Little App?

---

### Post by philinux on 2013-09-09
> **Coder88 said:**
> Linux Mint 15.


In that case I can't comment or help you as 
I've no idea what mint's default install is.  Maybe ask on the mint forums.

---

### Post by CaptainMark on 2013-09-09
I actually find Mint to be much better than Ubuntu for this, when I was searching for an example to give in my earlier post I actually tried to remove several packages which I thought would uninstall essential desktop components only to find that they acutally just un-installed fine without removing other packages. I still agree with you though about the excessive dependencies of some packages, I don't think it's a specific problem to meta-packages

Ps: I suppose my post probably makes more sense if I mention that Mint is my main OS

---

### Post by santosh83 on 2013-09-09
> **CaptainMark said:**
> I actually find Mint to be much better than Ubuntu for this, when I was searching for an example to give in my earlier post I actually tried to remove several packages which I thought would uninstall essential desktop components only to find that they acutally just un-installed fine without removing other packages.

If possible, can you try uninstalling (just simulating not actually doing it) the 'plymouth' package (if present in Mint) and see what else synaptic reports will get uninstalled along with it as well? On my Ubuntu 10.10 here plymouth seems to depend on hundreds of core system packages! :-(

---

### Post by stinkeye on 2013-09-09
> **santosh83 said:**
> If possible, can you try uninstalling (just simulating not actually doing it) the 'plymouth' package (if present in Mint) and see what else synaptic reports will get uninstalled along with it as well? On my Ubuntu 10.10 here plymouth seems to depend on hundreds of core system packages! :-(
I do not fully understand what plymouth does.
Do you?
I do believe it's more than a pretty splash screen.
I leave it to those who know more than me to decide dependencies.
If I did understand plymouth and felt the dependencies were not necessary I would submit a bug.

As it is, I regard plymouth as an essential component not to be removed.
Why would you want to remove plymouth anyway?
You can disable the splash screen in grub.

Yet to see a good example of some of the complaints in this thread.

---

### Post by CaptainMark on 2013-09-10
The plymouth in Mint is the very same package thats built by canonical so it has the same effect.

---

### Post by santosh83 on 2013-09-10
> **stinkeye said:**
> I do not fully understand what plymouth does.
Do you?
I do believe it's more than a pretty splash screen.
I leave it to those who know more than me to decide dependencies.
If I did understand plymouth and felt the dependencies were not necessary I would submit a bug.

A brief web search shows that bugs have been filed, and Canonical have so far refused to resolve the issue, citing that although the "splash screen" part of plymouth is not essential, other parts of it (allowing access to console) are needed during boot. But at least one commentator observed that his system does fine during boot without plymouth as well, so it's still unclear what exactly plymouth does, and how much of it is really essential and how much is just the will of Canonical.

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/556372](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/556372)
[http://askubuntu.com/questions/120416/how-to-safely-remove-or-repair-plymouth-package](http://askubuntu.com/questions/120416/how-to-safely-remove-or-repair-plymouth-package)
[http://askubuntu.com/questions/54176/why-is-plymouth-required](http://askubuntu.com/questions/54176/why-is-plymouth-required)


> As it is, I regard plymouth as an essential component not to be removed.
Why would you want to remove plymouth anyway?
You can disable the splash screen in grub.

Yet to see a good example of some of the complaints in this thread.

I did disable the splash screen, but fact remains that unless plymouth delivers functionality without which booting would be impossible or severely impaired, it ought to be removable without having half the system packages depending on it.

---

### Post by oldos2er on 2013-09-10
Some of you might be interested in [http://www.kieranoshea.com/2013/03/30/removing-plymouth/](http://www.kieranoshea.com/2013/03/30/removing-plymouth/)
I haven't personally removed plymouth though.

---

### Post by philinux on 2013-09-10
> **oldos2er said:**
> Some of you might be interested in [http://www.kieranoshea.com/2013/03/30/removing-plymouth/](http://www.kieranoshea.com/2013/03/30/removing-plymouth/)
I haven't personally removed plymouth though.

Very neat.

---

### Post by Mephisto Pheles on 2013-09-13
Coder88 has a very good point. Despite it being as it is now, I think it really should be reconsidered using a bit of common sense.
 Gnome should be a metapackage. Everything required and needed for that desktop and nothing more.
No other apps.. leave alone some basic system utilities.

On windows they'd call that "crapware".
Just like ADOBE always wants to install Chrome or McAfee when all I want is to update Flash.
That always pisses me off. Even if I have Chrome already installed they still want to install it!
They could at least make an effort to get it right and sort it out!
If I didn't ask for it... shove it.

Abiword and Gnumeric etc don't belong in a meta package that is in essence a DE.
Put them in a smaller Gnome Office metapackage then.

Or at least give users the choice of what to install when installing a meta package.. CHOICE the big argument for Linux and FOSS, remember?
Why not be consistent about it and do so all the way.
What's the point of having 4 media players I will never use, and I still have to get VLC myself because that's what I want.
Why do we need a nanny that decides for us what we need and should have installed?
The least one can ask for is to be able to uninstall it again without wrecking the DE.

If I want Libre Office on xubuntu then I have no use for Abiword anymore so why can't I just uninstall it?

I better leave that Abiword on Xubuntu then, after reading this.

---

### Post by stinkeye on 2013-09-13
> **Mephisto Pheles said:**
> Coder88 has a very good point. Despite it being as it is now, I think it really should be reconsidered using a bit of common sense.
 Gnome should be a metapackage. Everything required and needed for that desktop and nothing more.
No other apps.. leave alone some basic system utilities.

On windows they'd call that "crapware".
Just like ADOBE always wants to install Chrome or McAfee when all I want is to update Flash.
That always pisses me off. Even if I have Chrome already installed they still want to install it!
They could at least make an effort to get it right and sort it out!
If I didn't ask for it... shove it.

Abiword and Gnumeric etc don't belong in a meta package that is in essence a DE.
Put them in a smaller Gnome Office metapackage then.

Or at least give users the choice of what to install when installing a meta package.. CHOICE the big argument for Linux and FOSS, remember?
Why not be consistent about it and do so all the way.
What's the point of having 4 media players I will never use, and I still have to get VLC myself because that's what I want.
Why do we need a nanny that decides for us what we need and should have installed?
The least one can ask for is to be able to uninstall it again without wrecking the DE.

If I want Libre Office on xubuntu then I have no use for Abiword anymore so why can't I just uninstall it?

I better leave that Abiword on Xubuntu then, after reading this.
Understand that uninstalling abiword uninstalls one extra package...."gnome" (formerly named "gnome-desktop-environment"), **if it is installed.**
The meta-package...."gnome" contains **no actual applications**.
Uninstalling the **60kB** meta-package "gnome" uninstalls no actual applications.
Installing abiword **does not** pull in the meta-package "gnome" or any of it's dependencies.

Take the time to understand what a meta-package is and it's purpose.
**_[COLOR="#B22222"]https://help.ubuntu.com/community/MetaPackages[/COLOR]_**

Yes I agree it may alarm new users when they choose to remove something like gedit 
and notice that ubuntu-desktop is also going to be removed.
It alarmed me the first time I came across it.
Solved with a quick forum search.
No need for a message because it's removal is not harmful.
Just a learning process.

---

### Post by buzzingrobot on 2013-09-13
If no actual packages are removed, why are users presented with a list of packages and the warning they will be removed?

It should not require a "learning process" to discover you're being lied to.

---

### Post by stinkeye on 2013-09-13
> **buzzingrobot said:**
> If no actual packages are removed, why are users presented with a list of packages and the warning they will be removed?

It should not require a "learning process" to discover you're being lied to.
Relax...a bit over the top.
You will be shown packages that depend on the package you are removing.
eg if I choose to remove nautilus it will remove packages that depend on nautilus...one of those packages is ubuntu-desktop.
Remember the ubuntu-desktop meta-package contains no actual software.
Now if you decide to upgrade to a new release all you need to do is reinstall ubuntu-desktop which will pull in nautilus as a dependency to ensure you have
all the default packages for a smooth upgrade.

---

### Post by buzzingrobot on 2013-09-13
Knowing that  "ubuntu-desktop" is a meta-package that does not contain any actual packages is counter-intuitive knowledge we ought not to expect users to have.  And, as you indicate, its deletion is not impact free.

Still... I have tried to remove single packages and been presented a list of real, non-meta, packages with no obvious dependencies.

I have also installed single packages that brought in no dependencies, but whose attempted removal triggered display of a list of dependencies marked for deletion.

---

### Post by stinkeye on 2013-09-13
> **buzzingrobot said:**
> Knowing that  "ubuntu-desktop" is a meta-package that does not contain any actual packages is counter-intuitive knowledge we ought not to expect users to have.  And, as you indicate, its deletion is not impact free.

Still... I have tried to remove single packages and been presented a list of real, non-meta, packages with no obvious dependencies.

I have also installed single packages that brought in no dependencies, but whose attempted removal triggered display of a list of dependencies marked for deletion.
Yep maybe true, but with no example it's hard to comment on or test.
Not doubting you I'm just trying to explain what a meta-package is.

From the first post....
> **Coder88 said:**
> For example, uninstalling something as simple as a media player might say that **gnome** will also be removed. Gnome? wtf, GNOME? Why would the gnome desktop need to be removed just to uninstall a media player?!? 

---

### Post by CaptainMark on 2013-09-13
Actually I think they call it "Bloatware" on Windows, also I think that always "cheeses" you off.
At least according to forums code of conduct it does.

---

### Post by Coder88 on 2013-09-13
> **stinkeye said:**
> Relax...a bit over the top.
You will be shown packages that depend on the package you are removing.
eg if I choose to remove nautilus it will remove packages that depend on nautilus...one of those packages is ubuntu-desktop.
Remember the ubuntu-desktop meta-package contains no actual software.
Now if you decide to upgrade to a new release all you need to do is reinstall ubuntu-desktop which will pull in nautilus as a dependency to ensure you have
all the default packages for a smooth upgrade.

So if I go to install Dropbox from its .deb file off dropbox.com, and that triggers an install warning/listing that over 200+ packages will be REMOVED-- are you saying all of those 200+ packages to be 'removed' are just reference metas and not actual package removals?

---

### Post by stinkeye on 2013-09-13
> **Coder88 said:**
> So if I go to install Dropbox from its .deb file off dropbox.com, and that triggers an install warning/listing that over 200+ packages will be REMOVED-- are you saying all of those 200+ packages to be 'removed' are just reference metas and not actual package removals?
No it tells me you need to post a new thread on what is actually happening when you go to install dropbox
because the deb installs fine for me on 13.04 without the removal or addition of any extra software.
If your using the cinnamon desktop it may have to do with you using nemo instead of nautilus as the file browser.
The deb from the website is probably wanting to install nautilus. 
I think there's a package **nemo-dropbox**.

---

### Post by Coder88 on 2013-09-13
> **stinkeye said:**
> No it tells me you need to post a new thread on what is actually happening when you go to install dropbox
because the deb installs fine for me on 13.04 without the removal or addition of any extra software.
If your using the cinnamon desktop it may have to do with you using nemo instead of nautilus as the file browser.
I think there's a package **nemo-dropbox**.

This is on Ubuntu 13.04 where the .deb for Dropbox wanted to remove 200+ packages. No spices, no cinnamon. Just plain ubuntu 13.04. Nautilus, not nemo. I ditched Linux Mint after removal of apps removed a bunch of other apps/libs that broke the sytem. Put Ubuntu 13.04 on both my desktop and (yesterday) laptop.
I decided NOT to install the .deb and risk losing 200+ packages. Instead: sudo apt-get install nautilus-dropbox which only installed dropbox and did not say it would remove any packages/libs.

---

### Post by stinkeye on 2013-09-13
> **Coder88 said:**
> This is on Ubuntu 13.04 where the .deb for Dropbox wanted to remove 200+ packages. No spices, no cinnamon. Just plain ubuntu 13.04. Nautilus, not nemo. I ditched Linux Mint after removal of apps removed a bunch of other apps/libs that broke the sytem. Put Ubuntu 13.04 on both my desktop and (yesterday) laptop.
I decided NOT to install the .deb and risk losing 200+ packages. Instead: sudo apt-get install nautilus-dropbox which only installed dropbox and did not say it would remove any packages/libs.
nautilus-dropbox downloads the binary from dropbox.com, so they install pretty much the same thing.

As both install fine here, again it's hard to comment on what's happening without actual error/install messages.

---

### Post by philinux on 2013-09-13
To the OP. Please start a new thread regarding ubuntu and dropbox say in general help or the beginners forum.

I'm closing this one now.

---

