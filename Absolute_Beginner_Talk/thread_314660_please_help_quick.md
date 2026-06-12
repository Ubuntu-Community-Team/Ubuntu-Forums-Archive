---
title: "please help quick"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by billybag on 2006-12-07
some how, after updating my ubuntu linux, my gnome desktop will not startup on my laptop.

i get the ubuntu loading screen but then i get

[17179724.520000]hda: drive not ready for command
[17179724.3322000]hda: drive not ready for command

EAX is 0xB10A
CALLING INT 0x1A (F000:FE6E) *esque*

messages

Then it lets me login through terminal commands. Please help me get my gnome desktop back! !!!

---

### Post by lemonsCC on 2006-12-07
What did you update from and which method did you follow?

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> some how, after updating my ubuntu linux, my gnome desktop will not startup on my laptop.

i get the ubuntu loading screen but then i get

[17179724.520000]hda: drive not ready for command
[17179724.3322000]hda: drive not ready for command

EAX is 0xB10A
CALLING INT 0x1A (F000:FE6E) *esque*

messages

Then it lets me login through terminal commands. Please help me get my gnome desktop back! !!!

Sounds like something from the harddrive. But just to be sure, when you get to the terminal type *sudo dpkg-reconfigure xserver-xorg*. Just hit enter through the options if you don't know what to put in and then restart the comp. See what happens...

---

### Post by billybag on 2006-12-07
i simply used the update notifier on my gnome-panel. i am not sure what screwed it up. anyway... bare with me because i have only one ethernet cable so i have to go back and forth from my pc and laptop.

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> i simply used the update notifier on my gnome-panel. i am not sure what screwed it up. anyway... bare with me because i have only one ethernet cable so i have to go back and forth from my pc and laptop.

No problem, but do you remember what you upgraded?

---

### Post by lemonsCC on 2006-12-07
I think he may have clicked the button for distro upgrade...this lead to nothing but problems for my system.

---

### Post by billybag on 2006-12-07
The xserver reconfiguration didnt work. I think it was a destro upgrade. That would make sense... i really don't remember what it was exactly.

---

### Post by riven0 on 2006-12-07
> **lemonsCC said:**
> I think he may have clicked the button for distro upgrade...this lead to nothing but problems for my system.

Alright, that sounds pretty bad. Especially since he is using 5.10; I foresee a lot of problems. If that's the case, though, wouldn't it be better to just go ahead an upgrade the whole system with update-manager -c -d?:confused: Maybe it'll correct the problems.

---

### Post by billybag on 2006-12-07
Okay so my PC is configured pretty much the same as my laptop and i looked up the list of upgrades:

  gimp gimp-data gimp-helpbrowser gimp-python gnome-games gnome-games-data 
  gnome-system-tools gtk2-engines-pixbuf kcontrol kdebase-bin kdebase-data 
  kdebase-kio-plugins kdesktop kfind khelpcenter kicker konqueror konsole 
  ksplash kwin libgimp2.0 libgnomeprintui2.2-0 libgnomeprintui2.2-common 
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libkonq4 libruby1.8 ruby1.8 
  vino x11-common xbase-clients xlibs-data xorg xserver-xorg 
  xserver-xorg-input-all xserver-xorg-video-all xutils 

i bet it was the xserver things. i am trying to think of why exactly i even have these as upgrades.... i kind of find this odd...

anyway... any ideas on what to do next?

---

### Post by lemonsCC on 2006-12-07
Is it possible to move /home folders to a new partition?

Then he could just start from scratch without loosing personal files.  I suggest this because the more I attempted to fix my upgrade isssues the more messed up they got.

---

### Post by scrooge_74 on 2006-12-07
> **riven0 said:**
> Alright, that sounds pretty bad. Especially since he is using 5.10; I foresee a lot of problems. If that's the case, though, wouldn't it be better to just go ahead an upgrade the whole system with update-manager -c -d?:confused: Maybe it'll correct the problems.

Put a Live CD of 6.10 in the tray and start over?

---

### Post by lemonsCC on 2006-12-07
bilybag do me a favor and enter the following commands
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

if it asks you to upgrade between 40-60 things say yes.  if it wants you to install more than that or remove anything post back

---

### Post by lemonsCC on 2006-12-07
> **scrooge_74 said:**
> Put a Live CD of 6.10 in the tray and start over?

Haha...not just yet.  What about his /home folder?

---

### Post by scrooge_74 on 2006-12-07
> **lemonsCC said:**
> Haha...not just yet.  What about his /home folder?

He can just think he is using Windows and he is wiping all his data due to a problem with the computer LOL

---

### Post by billybag on 2006-12-07
It wants me to upgrade libruby1.8 and ruby1.8

..and that is all...

---

### Post by riven0 on 2006-12-07
> **lemonsCC said:**
> Haha...not just yet.  What about his /home folder?

:) I was just gonna say that.

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> It wants me to upgrade libruby1.8 and ruby1.8

..and that is all...

Alright, can you post your xorg.conf? It may still be the xserver since you can log into the terminal. BTW, did you have any official nvidia/ati drivers installed before?

---

### Post by lemonsCC on 2006-12-07
have we attempted crtl + alt + F2 >> log in >> startx ?

---

### Post by billybag on 2006-12-07
> **scrooge_74 said:**
> He can just think he is using Windows and he is wiping all his data due to a problem with the computer LOL
hahaha... ugh i would rather not think of those windows days...

---

### Post by scrooge_74 on 2006-12-07
> **billybag said:**
> hahaha... ugh i would rather not think of those windows days...

i still get the occasional nightmare from clueless friends how keep doing dumb things with their PCs, and then say Linux looks interesting, but I can-t use this program.  What antivirus you use in Linux? Can I use my webcam with MSN?

No you can't use your camera, but at least my PC is still running and yours is not LOL

---

### Post by billybag on 2006-12-07
how do i retrieve my xserver configuration in terminal? and i think i had nvidia drivers

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> how do i retrieve my xserver configuration in terminal? and i think i had nvidia drivers

First open your xorg.conf file, and check what is listed under the driver. If it says 'nvidia' change it to 'nv' without the quotes and restart. Tell us what happens...


EDIT: sorry, I meant to say what is listed under the driver section. :D

---

### Post by scrooge_74 on 2006-12-07
just in case  /etc/X11/xorg.conf

---

### Post by billybag on 2006-12-07
i don't know the command to get xserver.conf...

---

### Post by billybag on 2006-12-07
-bash: /etc/X11/xorg.conf: Permission Denied

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> i don't know the command to get xserver.conf...

sorry, should have been clearer. :D Do a 'sudo nano /etc/X11/xorg.conf' without the quotes. To save the file, press alt + ctrl + X

---

### Post by billybag on 2006-12-07
nothing about nvidia or ati. should i run dpkg-reconfigure -phigh xserver.xorg?

---

### Post by lemonsCC on 2006-12-07
you can try it but the command I use is dpkg-reconfigure xserver-xorg

not sure what the -phigh is for.

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> nothing about nvidia or ati. should i run dpkg-reconfigure -phigh xserver.xorg?

But it does say 'nv' under the Device section, right? something should be listed under the driver. For example:

Section "Device"
	Identifier	"GeForce"
	Driver		"nv"   <--or 'nvidia' here. It should have one or the other.


But you can run the dpkg-reconfigure -phigh xserver.xorg, and then type startx.

---

### Post by billybag on 2006-12-07
okay well i figured out how the problem started. for some reason i have the PROPOSED UPDATES box checked. i think this is where i screwed up originally.

---

### Post by riven0 on 2006-12-07
> **lemonsCC said:**
> you can try it but the command I use is dpkg-reconfigure xserver-xorg

not sure what the -phigh is for.

If I remember correctly, the xorg.conf file says to do -phigh if you want it to be updated automatically without restart, or something like that.

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> okay well i figured out how the problem started. for some reason i have the PROPOSED UPDATES box checked. i think this is where i screwed up originally.

Awesome! :KS  Did you get your xserver back?

---

### Post by billybag on 2006-12-07
> **riven0 said:**
> But it does say 'nv' under the Device section, right? something should be listed under the driver. For example:

Section "Device"
	Identifier	"GeForce"
	Driver		"nv"   <--or 'nvidia' here. It should have one or the other.


But you can run the dpkg-reconfigure -phigh xserver.xorg, and then type startx.
mine says trident...

---

### Post by billybag on 2006-12-07
> **riven0 said:**
> Awesome! :KS  Did you get your xserver back?
No :( i just found out how the problem arose. i have[now HAD] that same box checked on my PC. Luckily i cought it before i upgraded my PC

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> mine says trident...

Trident? :confused: I never heard of such a driver! Are you sure you have a nvidia card? If so, change it to 'nv' and reboot.

EDIT: Alright, I just did a check on google. Apparently, there is a trident video card, though this is the first I've heard of them. Perhaps you have the proVidia card?

---

### Post by billybag on 2006-12-07
> **riven0 said:**
> Trident? :confused: I never heard of such a driver! Are you sure you have a nvidia card? If so, change it to 'nv' and reboot.

EDIT: Alright, I just did a check on google. Apparently, there is a trident video card, though this is the first I've heard of them. Perhaps you have the proVidia card?
i thought i had nvidia... but i am not 100% positive. I did the dpkg reconfigure and the Trident driver was what it detected automatically

---

### Post by billybag on 2006-12-07
should i manually just change it to nvidia? or leave it at the autodetection settings?

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> should i manually just change it to nvidia? or leave it at the autodetection settings?

If it detects trident, then most likely it is correct... however, after checking out some other threads, apparently a lot of other people have problems with the trident video cards. What happens if you change it to 'vesa'?

BTW, when you restart type *sudo /etc/init.d/gdm start*

---

### Post by billybag on 2006-12-07
> **riven0 said:**
> If it detects trident, then most likely it is correct... however, after checking out some other threads, apparently a lot of other people have problems with the trident video cards. What happens if you change it to 'vesa'?
i am not sure what i should list under 'identifier' right now it is Trident Microsystems CyberbladeXPAi1

---

### Post by riven0 on 2006-12-07
> **billybag said:**
> i am not sure what i should list under 'identifier' right now it is Trident Microsystems CyberbladeXPAi1

Don't worry about the identifier. I don't think it should make a difference. Just change the driver to vesa and reboot with *sudo shutdown -r now*.


EDIT: As a last resort, redo the sudo dpkg-reconfigure xserver-xorg, and when it gets to graphics card section select 'vesa'.

---

### Post by billybag on 2006-12-07
sudo /etc/init.d/gdm start
* Starting GNOME Display manager... 
[17179879.61000] hda: drive not ready for command
[17179879.61000] hda: drive not ready for command
[17179879.61000] hda: drive not ready for command
[17179879.61000] hda: drive not ready for command
                                           [fail]

ubuntu@billybag:~$

sad face

---

### Post by billybag on 2006-12-08
ALSO!!! i forgot to update my profile...
i am using edgy!

---

### Post by billybag on 2006-12-08
well i really have to get going to bed. i have to work early in the morning. Thank you for all the help and i hope we can continue this tomorrow evening...

i am trying to think of any further info i can give... i hope i can fix this soon... i really need my laptop.

thanks again

---

### Post by riven0 on 2006-12-08
got busy for a moment there...

Just gotta say there is one last thing I would do in this case and that's to reinstall the xserver.

1. *sudo apt-get install –reinstall xserver-xorg*

2. *sudo shutdown -r now*

3. After it reboots, type *starx*

4. If it still doesn't work, try *sudo apt-get install –reinstall ubuntu-desktop*

5. To be sure, do another *sudo shutdown -r now*

Can't think of anything else right now...](*,)

---

### Post by billybag on 2006-12-08
Hey i am back

for some reason it wil not let me use the command '-reinstall'
E: command line option 'r' [from -reinstall] is not known
other errors i gave ben getting a lot while fiddling around are

Updating the IM modules list for GTK+-2.10.0...Bus error (core dumped)

this error seems to be a commoin trend. here it is in full


Updating the IM modules list for GTK+-2.10.0...Bus error (core dumped)
dpkg: error processing libgtk2.0bin (--configure):
subprocess post-installation script returned error exit status 135
Errors were encountered while processing:
libgtk2.0-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by riven0 on 2006-12-08
> **billybag said:**
> Hey i am back

for some reason it wil not let me use the command '-reinstall'
E: command line option 'r' [from -reinstall] is not known
other errors i gave ben getting a lot while fiddling around are

Updating the IM modules list for GTK+-2.10.0...Bus error (core dumped)

this error seems to be a commoin trend. here it is in full


Updating the IM modules list for GTK+-2.10.0...Bus error (core dumped)
dpkg: error processing libgtk2.0bin (--configure):
subprocess post-installation script returned error exit status 135
Errors were encountered while processing:
libgtk2.0-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

Hmmm, errors seem to be popping up all over the place. Thankfully, I recently had problems with dpkg and fixed it by reinstalling it from the debian homepage.

Try copying these commands in the terminal, one by one:

wget [http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.13.24_i386.deb](http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.13.24_i386.deb)

sudo dpkg -i dpkg_1.13.24_i386.deb

sudo dpkg --configure -a

sudo apt-get clean

sudo apt-get update

sudo apt-get dist-upgrade

If this doesn't work, we'll have to compile the dpkg package from source... which is a big headache.

---

### Post by billybag on 2006-12-08
Blar.

after the --configure -a command, i get that IM Module error again

sudo dpkg --configure -a
Setting up libgtk2.0-bin (2.10.6-ubuntu3)
Updating the IM M\modules list for GTK+-2.10.0...Bus error (core dumped)
dpkg: error processing libgtk2.0-bin (--configure):
subprocess post-installation script returned error exit status 135
Errors were encountered while processing:
libgtk2.0-bin

:(

---

### Post by riven0 on 2006-12-08
> **billybag said:**
> Blar.

after the --configure -a command, i get that IM Module error again

sudo dpkg --configure -a
Setting up libgtk2.0-bin (2.10.6-ubuntu3)
Updating the IM M\modules list for GTK+-2.10.0...Bus error (core dumped)
dpkg: error processing libgtk2.0-bin (--configure):
subprocess post-installation script returned error exit status 135
Errors were encountered while processing:
libgtk2.0-bin

:(

Alright, could be a dependency problem. What happens when you run:

sudo apt-get remove -f libgtk2.0-bin --purge

and then:

sudo apt-get install libgtk2.0-bin

---

### Post by billybag on 2006-12-08
sudo apt-get remove -f libgtk2.0-bin --purge

Since you only requested a single operation it is extremely likely that the package is simply not installable  nd a bug report gainst that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>=2.0.4~rc3) but it is not going to be installed or
language-support-en but it is not going to be installed
Depends: openoffice.org-common (<2.0.5) but it is not going to be installed or
language-support-en but it is not going to be installed
openoffice.org-l10n-en-za: Depends: openoffice.org-comon (>=2.0.4~rc3) but it is not going to be installed or
language-support-en but it is not going to be installed
Depends: openoffice.org-common (<2.0.5) but it is not going to be installed or
language-support-en but it is not going to be installed
E: Broken packages

and after install libgtk2.0-bin
i basically get told i have the newest version and then that same IM Module error that i keep getting

---

### Post by billybag on 2006-12-08
it was suggesteds that i run a memtest and i got this:
allocated 1240465408 bytes...trying mlock...[17184033.516000] Out of memory: kill process 8892 (memtest) score 303470 amd children.
{17184033.516000] Out of memory: Killed process 8892 (memtest).
killed

... i am not to sure what this means but it seems like i am out of memory... somehow........?

---

### Post by riven0 on 2006-12-08
> **billybag said:**
> sudo apt-get remove -f libgtk2.0-bin --purge

Since you only requested a single operation it is extremely likely that the package is simply not installable  nd a bug report gainst that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>=2.0.4~rc3) but it is not going to be installed or
language-support-en but it is not going to be installed
Depends: openoffice.org-common (<2.0.5) but it is not going to be installed or
language-support-en but it is not going to be installed
openoffice.org-l10n-en-za: Depends: openoffice.org-comon (>=2.0.4~rc3) but it is not going to be installed or
language-support-en but it is not going to be installed
Depends: openoffice.org-common (<2.0.5) but it is not going to be installed or
language-support-en but it is not going to be installed
E: Broken packages

and after install libgtk2.0-bin
i basically get told i have the newest version and then that same IM Module error that i keep getting

Definitely a dependency problem. Alright, first we have to uninstall all the programs that are broken. Try running these commands one at a time:

sudo apt-get remove -f openoffice.org-core

sudo apt-get remove -f openoffice.org

sudo apt-get remove -f openoffice.org-common

sudo apt-get remove -f libgtk2.0-bin

Tell me if you get anymore errors.

BTW, this is really important: when you did sudo dpkg-reconfigure xserver-xorg, did you notice any errors when you got back to the command prompt? Something related to dpkg, perhaps? :-k

---

### Post by riven0 on 2006-12-08
> **billybag said:**
> it was suggesteds that i run a memtest and i got this:
allocated 1240465408 bytes...trying mlock...[17184033.516000] Out of memory: kill process 8892 (memtest) score 303470 amd children.
{17184033.516000] Out of memory: Killed process 8892 (memtest).
killed

... i am not to sure what this means but it seems like i am out of memory... somehow........?

At the moment, let's not worry about this. First let's try to fix the dependency problems.

---

### Post by billybag on 2006-12-08
"BTW, this is really important: when you did sudo dpkg-reconfigure xserver-xorg, did you notice any errors when you got back to the command prompt? Something related to dpkg, perhaps? "

nope i didnt. i am going to remove those packages now tho

---

### Post by billybag on 2006-12-08
all the commands turned up that same broken packages message EXCEPT sudo apt-get remove -f openoffice.org. this one removed a bunch of stuff, probably related to it, and the gave me the Updating IM Modules list error again...

---

### Post by riven0 on 2006-12-08
> **billybag said:**
> "BTW, this is really important: when you did sudo dpkg-reconfigure xserver-xorg, did you notice any errors when you got back to the command prompt? Something related to dpkg, perhaps? "

nope i didnt. i am going to remove those packages now tho

Alright, also, try these commands if you still get errors:

sudo apt-get remove -f openoffice.org-l10n-en-gb

sudo apt-get remove -f openoffice.org-l10n-en-za

then do sudo apt-get remove -f libgtk2.0-bin --purge

---

### Post by billybag on 2006-12-08
> **riven0 said:**
> Alright, also, try these commands if you still get errors:

sudo apt-get remove -f openoffice.org-l10n-en-gb

sudo apt-get remove -f openoffice.org-l10n-en-za

then do sudo apt-get remove -f libgtk2.0-bin --purge
then do sudo apt-get remove -f libgtk2.0-bin --purge didnt give me any errors but now it appears s though it is removing <b>everything</b>....

---

### Post by riven0 on 2006-12-08
> **billybag said:**
> then do sudo apt-get remove -f libgtk2.0-bin --purge didnt give me any errors but now it appears s though it is removing <b>everything</b>....

At the moment, I don't see that there is much of a choice. Dependency problems are a headache. We'll have to reinstall the xserver-xorg and ubuntu-desktop after it is finished. Tell me if you get anymore errors in the end.

---

### Post by billybag on 2006-12-08
> **riven0 said:**
> At the moment, I don't see that there is much of a choice. Dependency problems are a headache. We'll have to reinstall the xserver-xorg and ubuntu-desktop after it is finished. Tell me if you get anymore errors in the end.
okie dokie this will probably take a few more minues ;-)

---

### Post by billybag on 2006-12-09
..okay now what? sorry i fell asleep on you last night :( this is driving me CRAZY. i really REALLY appreciate your help

---

### Post by riven0 on 2006-12-09
> **billybag said:**
> ..okay now what? sorry i fell asleep on you last night :( this is driving me CRAZY. i really REALLY appreciate your help

Hehe... no problem.:)  I'm guessing everything uninstalled fine. So run this command one more time and see if it brings up an error message:

> sudo dpkg --configure -a

IF there is no error message, then try this:

> sudo apt-get install --reinstall xserver-xorg

And then:

> sudo apt-get install ubuntu-desktop

---

### Post by billybag on 2006-12-09
wesome. that seemed to complete fine. What shall i do next? should i just restart?

---

### Post by riven0 on 2006-12-09
> **billybag said:**
> wesome. that seemed to complete fine. What shall i do next? should i just restart?

As long as there were not error messages, go ahead an do a **sudo shutdown -r now** and pray...:)

---

### Post by billybag on 2006-12-09
YAY. i am on my laptop now! thank you so much for your time and patience.

---

### Post by riven0 on 2006-12-09
> **billybag said:**
> YAY. i am on my laptop now! thank you so much for your time and patience.

Well, I'm glad it worked. It took long enough! :KS

---

