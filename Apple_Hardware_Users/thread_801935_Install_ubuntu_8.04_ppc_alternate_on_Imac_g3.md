---
title: "Install ubuntu 8.04 ppc alternate on Imac g3?"
date: 2008-05-21
forum: Apple Hardware Users
---

### Post by thebestintech on 2008-05-21
how do I Install ubuntu 8.04 ppc alternate on Imac g3 400mhz ?

I tried to install it and it said it was missing some files during the install, It would not let me continue I got the ubuntu 8.04 alternate install cd for ppc

is there a different image i need? or can somebody help me install it?

it is a 
Imac G3 400MHZ
768MB of ram
112GB HD

---

### Post by mandyb on 2008-05-21
For an iMac G3 500: got there (finally) by starting with Xubuntu 7.04 PPC alt and using update-manager and apt-get dist upgrades; at 8.04 booted Linux single to fix the modprobe ide-core and copied xorg.conf from this thread to get DRI

[http://ubuntuforums.org/showthread.php?p=2321892](http://ubuntuforums.org/showthread.php?p=2321892)

Got to 8.04 by using upgrades on a PB Lombard also, need to go back to that one and try the forcePCImode as it seems quite a bit snappier.  I've fixed up 4 or 5 old Apple machines for people and Hardy is the best yet.

---

### Post by frog_pilot on 2008-05-21
First you have to check out, what kind of mac you own, [old world]("https://wiki.ubuntu.com/PowerPCFAQ#head-3f24dcedc36978ee03f9d317e24efa01e9a82c85") or [new world]("https://wiki.ubuntu.com/PowerPCFAQ#head-6b2faa0d86d3136075bf337a5809dad01738f83d"). There are several sites on the internet about apple product history, where you could figure it out. For OS X there is also the small free programm database "Mactracker" which provides many useful information.

I would say its an iMac 5 Flavors (Machine ID: iMac, 1), shipped from Jan 1999 until Oct 1999. For this machine is a [firmware update]("http://docs.info.apple.com/article.html?artnum=60384") available. And it seems to be a new world mac, as it has openfirmware as firmware (and not mac os rom).

For other issues with ubuntu on iMac G3 look at [PowerPCKnownIssues]("https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8").

//edit: maybe [this thread]("http://ubuntuforums.org/showthread.php?t=801703") is useful for you

---

### Post by avtolle on 2008-05-21
> **thebestintech said:**
> how do I Install ubuntu 8.04 ppc alternate on Imac g3 400mhz ?

I tried to install it and it said it was missing some files during the install, It would not let me continue I got the ubuntu 8.04 alternate install cd for ppc

is there a different image i need? or can somebody help me install it?
I think it appropriate to inquire first whether you checked the md5sum of the downloaded iso before burning it to a CD for the install attempt. It sounds like, from your description, that you may have a corrupted image. If the md5sum check shows no errors, then may I suggest burning the iso again to a "name brand" CD-R at slow (4x) speed. Then, try to boot from it (the new CD-R) and see what happens, and, of course, let us know of problems.

EDIT: just thought of this. How much RAM does your imac have?

---

### Post by thebestintech on 2008-05-21
> **avtolle said:**
> I think it appropriate to inquire first whether you checked the md5sum of the downloaded iso before burning it to a CD for the install attempt. It sounds like, from your description, that you may have a corrupted image. If the md5sum check shows no errors, then may I suggest burning the iso again to a "name brand" CD-R at slow (4x) speed. Then, try to boot from it (the new CD-R) and see what happens, and, of course, let us know of problems.

EDIT: just thought of this. How much RAM does your imac have?

The detailed specs of it are
Imac G3 400MHZ
768MB of ram
112GB HD

---

### Post by stream303 on 2008-05-22
Great, you should be good to go!  There are several 400mhz iMacs, so you might want to get more detailed specs from here:

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Give it a shot and let us know how it goes.

---

### Post by bslash on 2008-05-22
It should work, I just did it on an Imac G3. There are some hoops to go through, though:

- install with the alternate CD. It should work, if the CD burned properly
- but reboot failed, the Imac shut itself down after showing the 'white screen'.

This is because Hardy seems to get the timings for the monitor all wrong. You need to:
- when the yaboot prompt comes up, type "Linux nosplash". Later, fix this properly in /etc/yaboot.conf, see [http://ubuntuforums.org/showthread.php?t=674700&highlight=imac+g3+horizsync&page=2](http://ubuntuforums.org/showthread.php?t=674700&highlight=imac+g3+horizsync&page=2)
- when it boots, but fails to open GDM, enter Ctrl-F1 to open a terminal, login, and do "sudo nano -w /etc/X11/xorg.conf" and add the following to the "Monitor" section:
    HorizSync 58-60
    VertRefresh 75-110

Now, that should give you a nicely working Imac G3 Hardy.

---

### Post by stream303 on 2008-05-23
This is great news!  I'm glad to see you got it running and welcome aboard!

Brick'ed G3's can often be found when someone tries to install OSX or use an OSX utility when they haven't upgraded the firmware first when running the older Mac-Os.

Was this the case, or was the unit second-hand?

If so, looks like Ubuntu to the rescue..

---

### Post by Jammy4041 on 2008-05-23
I would recommend that you install Xubuntu, due to the speed of your processor. Your iMac only has a 400MHZ processor compared to today's 2000MHZ+ processors. The installation would be 

You would probably need to update your iMac's firmware- that's OK- 

Have a look at

[http://docs.info.apple.com/article.html?artnum=75130](http://docs.info.apple.com/article.html?artnum=75130)

to download the firmware update

and

[http://www.jamesspace.net/About%20Ubuntu/PPC_Page_3.html](http://www.jamesspace.net/About%20Ubuntu/PPC_Page_3.html)

for even more help.

> **Apple's Website]About the iMac Firmware Update 4.1.9

The iMac Firmware Update 4.1.9 will only run on iMac computers with slot-loading CD or DVD drives running Mac OS 9.1 or later from a local drive. If you are using Mac OS X you must boot from a local Mac OS 9.1 or later writeable partition (not a CD, or network disk) prior to following the update instructions.

Firmware updates are also available for Power Mac G4 and Power Mac G4 Cube models.

Firmware Update 4.1.9 includes improvements to starting up Mac OS X from the local hard disk, Firewire target disk mode, starting up from the local hard disk, network startup, and system stability. This update also adds support for additional security options which allow the Open Firmware to be password protected.

Before you install the iMac Firmware Update 4.1.9, read the instructions below. You may want to print them for reference.

Note: After you install this update, the parameter RAM (PRAM) is reset. This may reset some of your control panels to default settings. See Mac Help, available in the Help menu, for more information on changing your control panel settings.

1. Double-click the iMac Firmware Updater icon.

Note: If a message says your firmware is up-to-date with version 4.1.9 of the iMac Firmware Updater, or that this version of the iMac Firmware Updater will not run on this computer, then you do not need this update. If a message says you need to install Mac OS 9.1, the firmware updater will not run until you install Mac OS 9.1 or later.

2. Follow the onscreen instructions. When prompted, click Shut Down in the dialog box to shut down your iMac.

3. Locate the programmer's button on the side of the iMac, to the right of the reset button. Press and
hold in the programmer's button. You may need to use a pen or a straightened paper clip.


4. While you hold in the programmer's button, press the Power button to start up your iMac.

5. Continue to hold in the programmer's button until you hear a long tone.
Release the programmer's button when you hear the tone. The update starts automatically.

A status bar shows the progress of the update. When a message says your computer's firmware has been successfully updated to version 4.1.9, you are finished.[/QUOTE]


Note updating your iMac's firmware needs to be done in Classic Mac OS, running version 9.1 or later. You cannot install it in OSX, because you  need the firmware update to install OSX and dual boot.

[QUOTE=frog_pilot said:**
> First you have to check out, what kind of mac you own, [old world]("https://wiki.ubuntu.com/PowerPCFAQ#head-3f24dcedc36978ee03f9d317e24efa01e9a82c85") or [new world]("https://wiki.ubuntu.com/PowerPCFAQ#head-6b2faa0d86d3136075bf337a5809dad01738f83d").

All iMacs are new world, so the installation of PPC Linux is almost a snap, compared to what it would be if it was old world. Generally, old world machines are beige coloured, new world machines are generally funky or snow coloured.

---

### Post by stream303 on 2008-05-23
> **Jammy4041 said:**
> I would recommend that you install Xubuntu, due to the speed of your processor. Your iMac only has a 400MHZ processor compared to today's 2000MHZ+ processors.

Due to the ppc architecture, a functional equivalent for G3's would be to double the processor speed if you want to compare it to an Intel box.  Thus a 400mhz G3 could be roughly compared to an 800mhz intel.

I think the bigger issue is the amount of ram installed.  Xubuntu is a fine choice, although as of this date, it hasn't made an official Hardy-release, only a late-beta.  It will be interesting to see if they ever come out with an official release, or possibly come out with one at the next spin, ie 8.04.1

While Xubuntu may provide a faster desktop, it won't increase the speed of running resource-heavy apps like Gimp or OpenOffice.  Otherwise, yes, Xubuntu is a very nice option.

Nice job on the site regarding firmware upgrades!

> Note updating your iMac's firmware needs to be done in Classic Mac OS, running version 9.1 or later.

And it has to be done with Mac OS running on the hard drive - it can't be done with a boot disk. :(

---

### Post by bslash on 2008-05-25
in terms of 'felt response time', the Imac G3's (yes, i have ubuntified 2 units now) cope surprisingly well with fullblown Gnome.
One is 400 mhz, the other 500 mhz, both have 256 megs of ram. Quite adequate as surfing stations and the like.

The (original) harddisks are very slow, though. Either replace, or at least make sure you kill trackerd and other disk-searching software.

---

### Post by Scientia on 2008-05-26
Oh btw can the same be done(install 8.04) on a iBook G3 PowerPC 700mhz?
Because it seemed there wasnt a supported package for PowerPC.

Forgive a Noob.

---

