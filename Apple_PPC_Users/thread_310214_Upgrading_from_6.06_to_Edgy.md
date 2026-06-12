---
title: "Upgrading from 6.06 to Edgy"
date: 2006-11-30
forum: Apple PPC Users
---

### Post by meshica7 on 2006-11-30
Hello folks,
 I have been trying to upgrade from dapper to edgy on my PowerMac G4 using apt-get.Here is the result of my attempts:

[B][COLOR="RoyalBlue"]desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[/COLOR][/B]

 I am assuming that the upgrade was not performed.How can I get this to work?
 Thanx folks!

Juan

---

### Post by 3rdalbum on 2006-11-30
Have you changed your sources.list, so all instances of the word "dapper" now read "edgy"?

---

### Post by meshica7 on 2006-12-01
Aha!:-D  How do I do this?

---

### Post by peal on 2006-12-02
alter /etc/apt/sources.list

---

### Post by meshica7 on 2006-12-02
Thanx Peal and 3rd!
 I was not able to alter my sources list as I encountered the following:

 It seems that my initial attempt to upgrade did indeed install and remove packages.Last night I was prompted to update software on my system and this is what Synaptic presented me with:
[IMG]http://myspace-505.vo.llnwd.net/01506/50/54/1506414505_l.jpg[/IMG]

As you can see,the list of items is very extensive! So I did "Mark all upgrades" and proceeded with the updates.This took about 2 hours so I figured that the upgrade to Edgy was in progress.I was not asked to resart the system at this time but did anyway. The next time I logged into Gnome (my default session) Nautilus would not start and I could not get a terminal to launch either. I was then prompted to update again and I did figuring it may "fix" the problem.I made sure that Nautilus was re-installed and continued.This time I was prompted to restart in order for updates to take effect.When I restarted my Mac,Gnome was no longer on my system,XFCE is the default with KDE and Enlightenment as other options,and I can't get any internet access (I am posting this via OS X,which is slow as heck compared to Linux!).To top it off,I am not even sure that Edgy was even installed!If I want to go back to Dapper,am I going to have to re-install from the disc (assuming that I do not get my internet in Linux back)?
 Any ideas?

---

### Post by jpyanowski on 2006-12-02
If you were able to change your apt/sources.lst from dapper to edgy it's easier to do the dist-upgrade in a terminal than Synaptic. BUT... you have to update apditude first.

code (in a terinal): sudo aptitude update

then: sudo aptitude dist-upgrade

Answer the questions (all yes for me) and away you go. Hope this helps.

---

### Post by Tipo on 2006-12-02
Ahh, yes, jpyanowski is right.... you seed sudo power to edit the sources.list

---

### Post by meshica7 on 2006-12-03
> **Tipo said:**
> Ahh, yes, jpyanowski is right.... you seed sudo power to edit the sources.list

 Thanx guys!
 Unfortunately,I am unable to acces the terminal or the web from within XFCE or KDE,seems to have bene corrupted somehow (along with Evolution and a few other apps that I have to reconfigure).](*,) Even when I type in the commands withinthe command line at start up,I get "Unable to Access" errors,no internet.I tried the Live CD and still had internet in this fashion so that rules out a hardware problem.So....
 I booted up into XFCE and I installed my Dapper disk and added it as a repository in order to re-install essential packages (like Gnome base and the Networking applications).I really did not want to do this as I did not want to overwrite any of my settings (network,e-mail,preferences,etc.) but without an internet connection,I did not know what else to do.Once I re-installed Gnome,Nautilis,etc,I rebooted (again) and NOTHING.:-k .Black screen.I rebooted a couple more times and still nothing.Well,after a few more frustrating sessions of personal restraint,saving my Mac's life in the process,I decided to re-install **everything**...I know that this is a last resort option in most cases but I am not sure if I was too hasty here.I have only been using Linux for about 6 months now so I still don't know all the ins and outs. I have read about the "Rescue" options from the Live CD but it is my understanding that this does not work on a Power PC (I read it somewhere).After about 30 mins, everything is back up and running.I installed EasyUbuntu (God send,that) and am beginning the slow process of downloading all those lil' customizations (thems,login screens,icons,wallpapers) that made this *my* Ubuntu,along with all the cool apps like XMMS,Listen, and Xine.
 Could I have done something different,not having an internet connection?Any opinions would be greatly appreciated!!!:-D

---

### Post by linear on 2006-12-03
> **meshica7 said:**
> Could I have done something different,not having an internet connection?Any opinions would be greatly appreciated!!!:-D

There is a workable rescue option on the alternate install CD (I used it after a botched upgrade from Breezy to Dapper).

With this, you can:
- Get booted with a working network connection.
- Get a command line and chroot to your broken Ubuntu install.
- Add/remove packages as needed to fix.

---

### Post by meshica7 on 2006-12-05
> **linear said:**
> There is a workable rescue option on the alternate install CD (I used it after a botched upgrade from Breezy to Dapper).

With this, you can:
- Get booted with a working network connection.
- Get a command line and chroot to your broken Ubuntu install.
- Add/remove packages as needed to fix.

Thanx Linear! I will keep this in mind.:-D 

And thanx to all who responded to this thread.This is the best community on the net!

 Juan

---

### Post by stream303 on 2006-12-05
> **meshica7 said:**
> Could I have done something different,not having an internet connection?Any opinions would be greatly appreciated!!!:-D

Highly recommended (APTonCD):

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Easy .deb install.  Perfect for those situations where you have to reinstall your system and had gotten all your updates etc via the internet somehow, but no longer have access to the net.  It saves and restores all your .deb cache files into an iso which you can burn to cd etc.  Nice.

In my case, after blowing a few installs on my G5, it was nice to use this and not tie up any Canonical resources re-downloading all my former updates.

---

### Post by magnolia fan on 2006-12-08
Hi,
I upgraded from Dapper to Edgy on a G4 Power Mac 800 Mhz Quicksilver Tower using the GUI method rather than the apt-get method.  I'm multi-booting with Yaboot.  I highly recommend this upgrade method if you have broadband and a relatively clean install of 6.06.  The full instructions can be found here:  [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

**Step 1 (my short instructions):**

In Terminal enter: gksu "update-manager -c" 

The Update Manager will come up on its own and at the top will be an UPGRADE button.  Whatever you do, do NOT close the terminal once you run this.  It will shut down the Update Manager during the install.  The install takes over an hour.


**Step 2 (Not in the instructions):**

After the upgrade finished and a reboot, I had to edit the yaboot.conf file settings in the etc folder so that it pointed to the new Kernel.  

(OLD yaboot.conf)

image=/boot/vmlinux-2.6.15-26-powerpc
	partition=23
	label=ubuntu606
	read-only
	initrd=/boot/initrd.img-2.6.15-26-powerpc
	root=/dev/hdb23
	append="quiet splash"

(NEW yaboot.conf)

image=/boot/vmlinux-2.6.17-10-powerpc
	partition=23
	label=ubuntu610
	read-only
	initrd=/boot/initrd.img-2.6.17-10-powerpc
	root=/dev/hdb23
	append="quiet splash"

After entering ybin -v in the Terminal to apply the changes, I was good to go.

-good luck

---

### Post by meshica7 on 2006-12-09
Cool! I will check on the AptonCD app ASAP.
Magnolia Fan,I am a bit leary of upgrading to Edgy now after what I went through!I am upgrading my Power Mac AGP "Sawtooth" G4's (from the installed 400mhz processor to a  PowerLogix PowerForce Series 100 DUAL G4-7455/1.0GHz,should be nice!) and will probably hold off on Edgy untill I do this,I will refer to your instructions when I do.If I run into any problems,can I e-mail you for help?:-D 
 Thanx !
 Juan

---

### Post by meshica7 on 2006-12-09
[B]"Highly recommended (APTonCD):

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Easy .deb install. Perfect for those situations where you have to reinstall your system and had gotten all your updates etc via the internet somehow, but no longer have access to the net. It saves and restores all your .deb cache files into an iso which you can burn to cd etc. Nice."[/B]

I checked out the site,downloaded the deb and this is what I got:

[COLOR="Red"]**Error Dependency is not satisfiable python-dbus**[/COLOR]

Bummer! Not even at all knowing how to fix this.:-? 
Any ideas on this one?

---

### Post by stream303 on 2006-12-09
So far, APTonCD seems to work with Edgy only.  It is only a .01 release so maybe it will work with older releases in the future...

---

