---
title: "Hangup during package installation"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by johnnymo87 on 2005-12-13
I'm new to linux, and I'm having trouble installing it.

I have gotten past the first phase of the installation. I'm at the point where I take out the CD and my CPU reboots. This is where I hit my first problem.

Ubuntu "fails" to load some of the modules, and I have to reboot it for a second time. Then, all the modules load successfully, and the packages start to install. When this gets to 43%, the screen is on "Preparing to configure gstreamer0.8-jpeg" and it is unable to continue. 

After about 5 minutes of no activity, a screen pops up and tells me that the package cannot install, but that I can continue install the package manually later. How do I do this?

Right now, when I boot up my computer, I can't access the graphical interface. All I get is the ~$ prompt. What can I do here to finish the installation of the packages?

BTW, I don't think the file on the boot CD is corrupted. I downloaded the .iso from twice from two different mirrors, and burnt the .iso(s) to two different CDs correctly (as an image ... my computer recognized them), and tried the installation a few times with each. I get exactly the same results each time.

---

### Post by amohanty on 2005-12-13
```
sudo apt-get install gstreamer0.8-jpeg
```

On the prompt. This will prompt you for your password. Enter it and continue.

HTH

---

### Post by johnnymo87 on 2005-12-13
After command and password prompt, computer says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I type: ```
sudo dpkg --configure -a
```

Computer scrolls throw many lines very quickly. After a few seconds it stops. All of the visible lines look very similar. Here is a quote of the ending few lines:

dpkg: error processing libcamel1.2.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: ../../src/pakages.c:191: process_queue: Assertion 'dependtry <= 4' failed.
Aborted

What should I do?

By the way, ubuntu often fails at "calculating module dependencies" during startup. After that a few others fail, related to the network, but I can't quite remember their name ...

Edit: 

For some reason, after I tried the commands you recommended again, the computer said to try: ```
sudo apt-get -f install
```.

I tried it, and it said something about 'Building packahe lists' 'Building dependency tree' and 'Correcting dependencies'. It also said something about install new packages with names like 'gnome-desktop-data' 'gnome-icon-theme' etc. It then said after unpack it would use 22.2mb of diskspace and prompted (y/n) for it to continue.

I accepted, and many lines flew by. It ended by saying 'Errors were encountered while processing:' and about 10 lines beneath it like '/usr/cache/apt/achives/gnome-mime-data_2.4.2-1_all.deb'. Underneath this was the final line saying: 'E:Sub-process /usr/bin/dpkg returned an error code (1)'

I hope this helps.

---

### Post by amohanty on 2005-12-13
Try:

> sudo apt-get autoclean
sudo apt-get --reinstall install ubuntu-desktop

If that doesnt work try:

> sudo apt-get -f install
sudo dpkg --configure -a

If that doesnt work either try 

> sudo apt-get -f
 
to get a list of broken packages.
Then remove each package using:

> sudo apt-get remove <package name>
sudo apt-get install <package name>

Somehow I think the CDs are a problem. Try the following, burn a brand new CD, verify the write. Then when Ubuntu installer boots and shows you the prompt, type:

> expert

After a few initial screens you should get a long list of things, one of which is something like 'verify install cd', select that and go through it. You can do it with the cds you currently have too. 

btw how are you burning the images. I have had trouble with the nautilus burner int he past and have since switched to gnomebaker.

HTH

---

### Post by johnnymo87 on 2005-12-14
I verified my boot cd. It's valid.

Just for the heck of it, I re-installed and repartitioned. I increased the size of my 'swap' partition to 1 GB, which is about a 25% increase. During re-installation, I only got 1% on phase 2 (no CD), but I was able to run GNOME, get on firefox (which I'm writing from now) etc. But I still seem to be missing some functionality (no 'windows manager', I can't minimize, resize, or close windows, and other problems with random buttons)

I tried the commands you suggested. The computer kept on giving me errors while running them, talking about dependency problems with certain applications. With the ```
sudo apt-get -f install
``` command, I some useful info. I'll reprint it here:
[I]
jcm05003@Zenith:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  cupsys libcupsimage2 libcupsys2-gnutls10 libdv4 mime-support
Suggested packages:
  cupsys-bsd foomatic-bin foomatic-filters-ppds xpdf-korean xpdf-japanese
  xpdf-chinese-traditional xpdf-chinese-simplified cups-pdf hplip
Recommended packages:
  smbclient libdv-bin
The following NEW packages will be installed:
  cupsys libcupsimage2 libcupsys2-gnutls10 libdv4 mime-support
0 upgraded, 5 newly installed, 0 to remove and 30 not upgraded.
31 not fully installed or removed.
Need to get 0B/9205kB of archives.
After unpacking 17.1MB of additional disk space will be used.
Do you want to continue [Y/n]?
[/I]

It seems that the applications [cupsys libcupsimage2 libcupsys2-gnutls10 libdv4 mime-support] are critical to the rest of the applications I want to load. But, there's a problem. When I hit [Y], all I get is *0% [Working]*. It never moves beyond that point. I also can't type any commands. I have to close the terminal and start over.

Any idea on how to get these critical applications to install?

---

### Post by amohanty on 2005-12-14
> (no 'windows manager', I can't minimize, resize, or close windows, and other problems with random buttons)

If you have gnome you have a window manager. Regardning minimizing try fire up the gnome-panel

> killall gnome-panel

That should bring up the menu bar and task bar on the top. Now that you have an internet connection, you can remove the CD from your source.list
Do the following:

> sudo gedit /etc/apt/sources.list

Comment out the topmost line that looks like this:

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

ie put '#' without the quotes in the front of that line.

If you dont have gedit try the following:
> visudo /etc/apt/sources.lst

then press the following keys in the _exact_ order (in case you dont know how to use vi). Stuff in caps are keyboard keys. The dashes separate the stuff you need to type, ignore them while typing

ESC - a - LEFT ARROW - # - ESC - : - wq - ENTER

Then do:

> sudo apt-get update

and the rest of the stuff I provided above.

HTH

---

### Post by johnnymo87 on 2005-12-14
Hey, thanks! I've made some progress.

I commented out the CD in my sources list. (BTW, is # or ## standard?)

This code ran smoothly: ```
sudo apt-get update
```

This code almost ran smoothly: ```
sudo apt-get -f install
``` It was running fine, but ran into a hitch. Here's an excerpt of the last bit of output.

[I]
Setting up foomatic-db-gimp-print (4.2.7-10) ...
Setting up hpijs (2.1.5+0.9.5-2ubuntu2) ...

Setting up foomatic-db-hpijs (1.5-20050705-1) ...
Setting up cupsys-driver-gimpprint (4.2.7-10) ...
No Gimp-Print PPD files to update.
 * Restarting Common Unix Printing System: cupsd                         [ ok ]

Setting up gs-common (0.3.7ubuntu1) ...
Updating font configuration of gs...
Cleaning up category psprint..
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category gsfontderivative..
Cleaning up category type3..
Cleaning up category type1..
Updating category type1..
Updating category type3..
Updating category gsfontderivative..
Updating category truetype..
Updating category cid..
Updating category cmap..
Updating category psprint..

dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
[/I]

I tried another command: ```
sudo dpkg --configure -a
``` and got the same error message: [I]dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted
[/I]

I ran another an update for my applications: ```
sudo apt-get upgrade
```
Just as during the 'install', it hit the same hitch after some progress. Here's the excerpt:

[I]
Setting up libpoppler0c2-glib (0.4.2-0ubuntu6.4) ...

Setting up libgtk2.0-bin (2.8.6-0ubuntu2.1) ...
Updating the IM modules list for GTK+-2.4.0...done.
Updating the gdk-pixbuf loaders list for GTK+-2.4.0...done.

dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
[/I]
---------------------------------------------------------------------------------------------------------

What I mean by some parts and buttons don't function is this:

When I open FireFox, I get the message *The file /usr/share/ubuntu-artwork/home/index/html cannot be found. Please check the location and try again.* Then when I click ok, no homepage loads, so I just have to type in a URL and go from there.

When I click the desktop icon on my bottom-most panel, I getthe message *Your window manager does not support the show desktop button, or you are not running a window manager.*

The window issue was really bugging me (no close or minimize button, all windows stuck in upper-left corner), so I tried to get to the window manager prefrences. I got the message ***Cannot start the preferences application for your window manager.** Window manager "unknown" has not registered a configuration tool.*

So it looks to me like I've got a defunct window manager.

---

### Post by amohanty on 2005-12-14
Try

> dpkg --configure --force-depends -a

---

### Post by johnnymo87 on 2005-12-14
[I]
jcm05003@Zenith:~$ dpkg --configure --force-depends -a
dpkg: requested operation requires superuser privilege
jcm05003@Zenith:~$ sudo -i
Password:
root@Zenith:~# dpkg --configure --force-depends -a
dpkg: blt: dependency problems, but configuring anyway as you request:
 blt depends on blt-common; however:
  Package blt-common is not installed.
Setting up blt (2.4z-3ubuntu1) ...

root@Zenith:~#
[/I]

I took it into the root to execute this command. I don't know what it did.

Since it said something about "blt-common" missing, I tried to install that. No results.

[I]
jcm05003@Zenith:~$ sudo apt-get install blt-common
Reading package lists... Done
Building dependency tree... Done
Note, selecting blt instead of blt-common
blt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
jcm05003@Zenith:~$
[/I]

So apparently when I asked it to install "blt-common", it tried to install "blt" instead. Then it said "blt is already the newest version", which is strange because I thought it just had told me "blt" had dependency problems. So I decided to remove it and then reinstall it. This is the text I got from removing it:

[I]
jcm05003@Zenith:~$ sudo apt-get remove blt
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  blt
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 5046kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: blt: dependency problems, but removing anyway as you request:
 blt depends on blt-common; however:
  Package blt-common is not installed.
  Package blt which provides blt-common is to be removed.
(Reading database ... 40786 files and directories currently installed.)
Removing blt ...
jcm05003@Zenith:~$
[/I]

Then here's the text for when I tried to reinstall it. Apparently it ran into an error:

[I]
jcm05003@Zenith:~$ sudo apt-get install blt
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  blt-demo
The following NEW packages will be installed:
  blt
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 2050kB of archives.
After unpacking 5046kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main blt 2.4z-3ubuntu1 [2050kB]
Fetched 2050kB in 3s (646kB/s)

Preconfiguring packages ...
Selecting previously deselected package blt.
(Reading database ... 40701 files and directories currently installed.)
Unpacking blt (from .../blt_2.4z-3ubuntu1_i386.deb) ...
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
jcm05003@Zenith:~$
[/I]

Even though it looked like the installation of "blt" failed, I tried to install blt-common. Apparently, it decided to try to install "blt" instead, and ran into the same error:

[I]
jcm05003@Zenith:~$ sudo apt-get install blt-common
Reading package lists... Done
Building dependency tree... Done
Note, selecting blt instead of blt-common
blt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
jcm05003@Zenith:~$
[/I]

---

### Post by amohanty on 2005-12-14
No I meant
> 
sudo dpkg --configure --force-depends -a
sudo apt-get -f install

Also take a look at this:
[http://ubuntuforums.org/showthread.php?t=11373&highlight=blt](http://ubuntuforums.org/showthread.php?t=11373&highlight=blt)

However I think if you do the two above that should fix your problems.
Hopefully that will finish up your install properly and then reboot. 

HTH

---

### Post by johnnymo87 on 2005-12-14
Thank you. The packages installed.

---

### Post by mohapi on 2006-01-09
Hi. I thought I would post another possible solution to this problem. I had a similar glitch on an older system that was compounded by the fact that I lacked an Internet connection. No *sudo apt-get update*, and no *sudo apt-get upgrade*. :shock: Life was looking bad.

I was able to install the Ubuntu desktop by finishing a server installation first, then [creating a repository]("http://ubuntuforums.org/showthread.php?t=42862") of the ubuntu-desktop files on another machine (actually, a virtual machine on a WinXP laptop running VMWare WorkStation).

I then created an ISO of the repository with Gnomebaker then burned the ISO to disc in Windows. Then, moving to the old machine, added the CD to my sources.list file with

```
sudo apt-get clean
sudo apt-cdrom add
```

I could complete the installation with 

```
sudo apt-get install ubuntu-desktop
```

That's it. I'm afraid I have no explanation of why the hangup happens or how to properly correct it, but this is a possible workaround. 

Cheers! :)

---

