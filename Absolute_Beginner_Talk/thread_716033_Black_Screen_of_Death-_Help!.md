---
title: "Black Screen of Death- Help!"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by philosophicscience on 2008-03-05
I just installed Ubuntu (dual boot with windows xp) 7.10 on my Acer Aspire 5670. I'm not sure, but I think the graphics card is an ATI mobility radeon. When I loaded up, I got a notice from the unprotected drivers manager saying something about my card. When I clicked the driver update i got an error and looked through the forums for a fix.

 Someone had suggested clicking an option in the software manager to use unprotected drivers, so I did that and my driver manager froze. Couldn't get the windows to close so I shut down and now when I boot up, I see my usual Acer boot up screen, followed by a brief DOS-style text saying grub and the option to boot in safe mode if I hit esc.

If I boot in safe mode I get a command prompt with which I have no clue what to do, and if I boot normally I get a back-lit black screen of death. From the black screen, nothing works.

Please help! I waited for ever to switch to linux, hope I haven't 'bricked' my laptop...

---

### Post by taurus on 2008-03-05
```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by philosophicscience on 2008-03-05
I followed your instructions, selected ATI for the name, 1600X800 for the resolution (a guess) and did the reboot. Still hitting a blackscreen. :(

---

### Post by fiskking on 2008-03-05
hey taurus, I'm curious as what the first line does and I was wondering if you could give a brief synopsis.  Would greatly appreciate it.

Fisk

---

### Post by philosophicscience on 2008-03-05
Alright, I tried the code again and this time just selected the defaults, Now I'm back in my machine and am wondering how to get the ATI drivers to work so I can utilize the visual effects. Right now if try to enable them it just says "desktop effects cannot be enabled" and   the ATI drivers are not being used under driver manager. I'm afraid to try anything after the last black screen, is there a way to utilize my graphics card?

My graphics card is: Radeon Mobility X1600

---

### Post by lswest on 2008-03-05
you can try installing it manually from [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) if you need any help with that, feel free to ask

---

### Post by philosophicscience on 2008-03-05
I have that file downloading right now, but I looked through this wiki:[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) and feel really lost. What do I have to do to install this?

---

### Post by lswest on 2008-03-05
this is actually easier to install than it used to be :P

my way:
step 1:
```
cd [path to file]
```

step 2:
```
chmod o+x ati-driver-installer-8-02-x86.x86_64.run
```

step 3:
```
sudo sh ./ati-driver-installer-8-02-x86.x86_64.run
```

to install do this (according to the guide):
step 1:
```
cd [path to file]
```

step 2:
```
chmod o+x ati-driver-installer-8-02-x86.x86_64.run
```

step 3:
```
sudo sh ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

step 5:
blacklist the fglrx driver from the restricted driver manager
```
gksudo gedit /etc/default/linux-restricted-modules-common
```
add this to it:
```
DISABLED_MODULES="fglrx"
```

step 6:
```
gksudo gedit /etc/modprobe.d/blacklist-restricted
```
and if there is a "blacklist fglrx" line, put a # in front of it, so that it loads the proper module for 3d acceleration

step 7:
```
sudo rm /usr/src/fglrx-kernel*.deb
```
to get rid of any old drivers

step 8:
```
sudo dpkg -i xorg-driver-fglrx_8.455.2-0*.deb fglrx-kernel-source_8.455.2-0*.deb fglrx-amdcccle_8.455.2-0*.deb
``` to install the actual driver

step 9:
```
sudo aptitude install linux-headers-$(uname -r)
```
if you encountered any errors, this command should fix it for you

okay, so to explain (never learn anything if you just copy and paste ;))
step 1 changes the directory to the place in which the file is saved, step 2 makes the script executable (since it is meant to be run in a terminal) and the last step executes the script and creates a .deb file for ubuntu which is located in the active directory (thus the "./" before the name)  hope i explained it well :P

*EDIT* also, the guide you'd need is here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by philosophicscience on 2008-03-05
Lswest, thanks for the help.

I'm trying to follow your directions but the second command doesn't seem to do anything and the third command gives me:

sh: Can't open ./ati-driver-installer-8-02-x86_64
micah@brain:~/Desktop$ 

I tried the directions in the wiki for 'installing the ubuntu way' and I got a dependency error stating: Broken Packages

What's next?

oops, just saw I missed part of the code in step 2, will try again


edit: alright, tried it and got the same error:
sh: Can't open ati-driver-installer-8-02-x86_64.run

---

### Post by lswest on 2008-03-05
i've been editing it along the way XD i read through the ubuntu gutsy guide, and it seems to have been doing it the hard way, so i edited my guide to that, since i've got an nvidia card atm, i can't check to see if my method would work, but try it first, it's less work :P

once you get the driver installed you have to reboot then you can configure it as stated in the guide under the section "Configure the Driver"

---

### Post by philosophicscience on 2008-03-05
> **lswest said:**
> i've been editing it along the way XD i read through the ubuntu gutsy guide, and it seems to have been doing it the hard way, so i edited my guide to that, since i've got an nvidia card atm, i can't check to see if my method would work, but try it first, it's less work :P

once you get the driver installed you have to reboot then you can configure it as stated in the guide under the section "Configure the Driver"

When you say path to file you mean on /micah/desktop/ right?

---

### Post by lswest on 2008-03-05
it depends where you save your downloaded files to, for example i save mine all to a folder "downloads" but by default, yes the path would be /home/micah(if that's your username)/Desktop  and the desktop has to be capitalized, as linux is case-sensitive
so the code would be: ```
cd /home/micah/Desktop/
```

hope i'm not too confusing :P

---

### Post by philosophicscience on 2008-03-05
Well everything was working until step six and then the commands didn't seem to be doing anything at all. I restarted and am not sure what to do now... guess i'll try the steps over again

edit: ok I retried it and an error occurs during step 3:

micah@brain:~/Desktop$ sudo sh ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.kJ5915
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.455.2....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 311: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/filenoya4H': not found
Unable to install dpkg-dev and build-essential.  Please manually install and try again.
Removing temporary directory: fglrx-install.kJ5915

edit: also how do I reboot in windows?

---

### Post by lswest on 2008-03-05
step 6 SHOULD open a window with a lot of text, where one line may or may not have "blacklist fglrx", and if it's not there, you can ignore that line of code,  and if everything worked before that, step 9 is unneccesary

ah that error means that you're missing stuff you need to complete it.  you can install it with ```
sudo aptitude install dpkg-dev build-essential
```

what do you mean with reboot in windows? you mean reboot into windows?  while the computer is loading and you see the grub info about hitting esc, hit esc and there should be an entry at the bottom of the list for your windows install, if not, we can fix that too :P

---

### Post by philosophicscience on 2008-03-05
> **lswest said:**
> step 6 SHOULD open a window with a lot of text, where one line may or may not have "blacklist fglrx", and if it's not there, you can ignore that line of code,  and if everything worked before that, step 9 is unneccesary

ah that error means that you're missing stuff you need to complete it.  you can install it with ```
sudo aptitude install dpkg-dev build-essential
```

what do you mean with reboot in windows? you mean reboot into windows?  while the computer is loading and you see the grub info about hitting esc, hit esc and there should be an entry at the bottom of the list for your windows install, if not, we can fix that too :P


Alright, this seems to be getting worse but I really appreciate you helping me! I execute the command to install essentials and then tried to repeat step 3 and got the following error:

edit: Yes, boot into windows. I think the grub info page only gives me three options, regular boot, safe boot, and some other thing that doesn't say windows. I'll try that third option and get back to you :)

micah@brain:~/Desktop$ sudo aptitude install dpkg-dev build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch 
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7934kB of archives. After unpacking 31.9MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)' in the drive '/cdrom/' and press [Enter].

Selecting previously deselected package linux-libc-dev.
(Reading database ... 88932 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.46_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu9_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.22-14.46) ...
Setting up libc6-dev (2.6.1-1ubuntu9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
micah@brain:~/Desktop$ sudo sh ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.oE6199
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.455.2....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Resolving build dependencies...
./packages/Ubuntu/ati-packager.sh: 311: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/file0lCajZ': not found
Unable to resolve  debhelper  fakeroot.  Please manually install and try again.
Removing temporary directory: fglrx-install.oE6199
micah@brain:~/Desktop$

---

### Post by lswest on 2008-03-05
haha, we're starting to deviate from the plan a little :P first off the message about the cdrom means your repositories still list your CD go to system-->administration-->software sources and uncheck the cdrom entry (at the bottom of the main tab) and then check all the boxed above that (in the one tab) except for the source code box.

Now, about that error during the builddpkg:
```
sudo aptitude install debhelper fakeroot
``` (it installs the files that are missing) but i have a question...did this work the first time you ran it?  If so, why don't you just re-try step 6 and on-wards?

and no problem about helping out, i'm always happy to help anyone learn, and if you have MSN or something, feel free to add me, might make this easier for us :P

---

### Post by philosophicscience on 2008-03-05
Well, I'm not really sure. The first run through, I kind of just assumed step 3 was working when I saw the ATI logo and moved onto step 6. I think it probably didn't work however. I checked those boxes and the system is now auto downloading some packages. After that i'll try your new command prompt and see if we can get back on the plan!

I have google talk and AIM, do you have either of those?

---

### Post by lswest on 2008-03-05
haha, sounds good^^ gonna probably head to bed in like 30 or so minutes (it's 10:10pm in Germany) but if you want you can add me to your MSN (quantum@viralcoders.com) or just email me if you need more help, otherwise i'll check back here tomorrow sometime during the day.
ah, yeah i have google talk: [email]lucas.westermann@gmail.com[/email]

---

### Post by philosophicscience on 2008-03-05
should I be worried if step 6 doesn't seem to do anything? smooth sailing up to this point

---

### Post by lswest on 2008-03-05
nope, no output is the best output^^

---

### Post by philosophicscience on 2008-03-05
> **lswest said:**
> nope, no output is the best output^^

Well I got all the way through the thing, the last 4 steps had no output but I'm rebooting now, hoping for the best!

---

### Post by lswest on 2008-03-05
okay^^ good luck *crosses fingers* :P

---

### Post by philosophicscience on 2008-03-05
Alright well I realized that after stage 4 or so it was taking me out of the desktop directory, so I cd'd back to that and tried step after the rm command again (install actual driver) and it spit back at me that the three modules where faulty, so i ran the last step and it said it removed fglrx-amdccle, kernel-source and xorg-driver-fglrx.... does this mean the driver isn't installed or should I reboot?

---

### Post by lswest on 2008-03-05
huh, wait, wait, wait, did you run the dpkg -i command before that? if you did, you just deleted what you installed XD if that's the case, run the dpkg -i command again and the rm command had a different filepath to it anyways, so it didn't matter where you ran it from.

---

### Post by philosophicscience on 2008-03-05
> **lswest said:**
> huh, wait, wait, wait, did you run the dpkg -i command before that? if you did, you just deleted what you installed XD if that's the case, run the dpkg -i command again and the rm command had a different filepath to it anyways, so it didn't matter where you ran it from.

Yes, it was the dpkg command that produced the errors. I'll run again and post them.

---

### Post by philosophicscience on 2008-03-05
micah@brain:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_8.455.2-0*.deb fglrx-kernel-source_8.455.2-0*.deb fglrx-amdcccle_8.455.2-0*.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 91374 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.455.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.455.2-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of xorg-driver-fglrx:
 xorg-driver-fglrx depends on libstdc++5; however:
  Package libstdc++5 is not installed.
dpkg: error processing xorg-driver-fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx-kernel-source (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xorg-driver-fglrx
 fglrx-kernel-source
 fglrx-amdcccle
micah@brain:~/Desktop$ 

 Your move :)

Edit; Unfortunately I have to go. I'll check back tonight to see if you posted a solution, and pending any other problems send you an email. Thanks so much!

---

### Post by lswest on 2008-03-05
lol, gee... try this:
```
sudo aptitude install libstdc++5
```
and then run the dpkg command again

okay, well, g'night, and no problem about the help, if it works don't forget to thank me using the blue medal at the bottom of my post :P and mark the thread as solved using the thread tools menu at the top of the thread.

haha, thanks for the thanks ^^ always nice to know the help is appreciated ^^

---

### Post by philosophicscience on 2008-03-05
Alright, tried that and here is where we are:

micah@brain:~$ sudo aptitude install libstdc++5
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
micah@brain:~$ sudo dpkg --configure -a
Setting up xorg-driver-fglrx (8.455.2-0ubuntu1) ...

Configuration file `/etc/xdg/compiz/compiz-manager'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/xdg/compiz/compiz-manager ...
 * Starting atieventsd                                                   [ OK ] 

Setting up fglrx-amdcccle (8.455.2-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
micah@brain:~$ cd /home/micah/Desktop
micah@brain:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_8.455.2-0*.deb fglrx-kernel-source_8.455.2-0*.deb fglrx-amdcccle_8.455.2-0*.deb
(Reading database ... 91497 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.455.2-0ubuntu1 (using xorg-driver-fglrx_8.455.2-0ubuntu1_i386.deb) ...
 * Stopping atieventsd                                                   [ OK ] 
Unpacking replacement xorg-driver-fglrx ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb) ...
Preparing to replace fglrx-amdcccle 8.455.2-0ubuntu1 (using fglrx-amdcccle_8.455.2-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Setting up xorg-driver-fglrx (8.455.2-0ubuntu1) ...
 * Starting atieventsd                                                   [ OK ] 

dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx-kernel-source (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-amdcccle (8.455.2-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx-kernel-source

:\ see you tommorow

---

### Post by philosophicscience on 2008-03-05
I feel defeated. I attempted to correct the error by copying your latest command with the file the error said it needed and then redid the dpkg command, it seemed to work except for some errors stating that the files already existed, so I ran the final error correcting command, it ran smoothly without removing the files, rebooted, ran the driver configuration smoothly and tried to enable graphics effects....

"Unable to enable graphics effects"

Is this checkmate?

---

### Post by crjackson on 2008-03-05
Have you thought of installing [[COLOR="Red"]Envy[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html") and letting it do all the leg work?  It seems you're not having much luck right now, so you might want to give it a go.  I use it all the time.

---

### Post by philosophicscience on 2008-03-05
> **crjackson said:**
> Have you thought of installing [[COLOR="Red"]Envy[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html") and letting it do all the leg work?  It seems you're not having much luck right now, so you might want to give it a go.  I use it all the time.


So, I think I managed to get the drivers installed. Under the driver manager it says they are enabled and installed. Now however, when I try to switch the visual settings, it gives me an error saying "the composite extension is not found"

What can I do to get this working?

---

### Post by lswest on 2008-03-06
okay, so, if you enter ```
gksudo gedit /etc/X11/xorg.conf
``` it should open text editor with the file you need, if you scroll down the list and append ```
Section "Extensions"
        Option "Composite" "Enable"
   EndSection

``` to the end of the file, it should enable the composite extension.

so, uh, how did you actually install the driver? using Envy?  if so, good job, but it usually doesn't work for me, so i didn't suggest it :P

---

### Post by philosophicscience on 2008-03-06
No, didn't use envy. I followed all the directions you had given me up to the point of my second to last post and then left my computer alone for a few hours. When I started it back up, it magically seemed to work... got a notice saying the drivers where installed and it let me turn them on in the driver manager. After reboot, the composite extension was bugging so I found a brief guide on installing xdml and compiz, and now I have this nifty rotating cube desktop. 

So I guess it was magic! Now i'm trying to figure out if I accidentally reformatted my hard drive when I installed ubuntu.

---

### Post by lswest on 2008-03-07
if you need help, start a new thread (or continue using this one, though the title doesn't describe your problem) and i'm glad i was able to help out ^^  if you reply to this, or if you start a new thread, be sure to paste the results of ```
sudo fdisk -l
``` (brings up a list of partitions on your drive, it would help anyone trying to help you out with the problem)^^

---

