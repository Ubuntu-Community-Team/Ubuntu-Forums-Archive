---
title: "iMac G4 24-bit Color"
date: 2011-08-04
forum: Apple Hardware Users
---

### Post by svtguy88 on 2011-08-04
Alright, this issue is staring to get a bit annoying.  I've got several PPC Mac's that I'm playing with Linux on.  Each of them is a G4, and the two that I'm toying with now use nVidia graphics (Geforce 6200 in PowerMac, and a Geforce 4 440 Go in a iMac G4).

On both machines, when I install from the debian netinstall CD, I end up with what looks like a 16 bit environment.  I've played a little with Xorg.conf (after creating it), but still end up with ugly colors.  

My Xorg.conf is as follows (for the iMac - 17''):

```
Section "Device"
Identifier "Configured Video Device"
BusID   "PCI:0:16:0"
Driver  "nouveau"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
SubSection "Display"
		Depth		24
		Modes		"1440x900" "1152x720" "1024x768" "1024x640" "800x600"
	EndSubSection
		Depth		1
		Modes		"1440x900" "1152x720" "1024x768" "1024x640" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection
```

DRI is commented out right now, just to see if it was causing issues.  

Running 'lsmod' shows that the nouveau module is loaded, but 'glxinfo' lists 'Software Rasterizer' and 'Mesa Project' for the 'renderer string' and 'vendor string' fields, respectively.

Am I missing something obvious, or just too tired?  I saved this 800 mhz iMac from a dumpster earlier (just needed a hard drive), and am looking to put it to use.  It's future may have a mini-ITX x86 swap, but for now, I'd like to see what it is capable of.

---

### Post by Furball588 on 2011-08-04
Maybe just adding 

DefaultDepth     24 

right before SubSection "Display" will give you the results you're looking for.

---

### Post by svtguy88 on 2011-08-04
I'll give that a try in the morning.  I figured deleting the other sections (Depth=16, 8 and 4) would have been sufficient.  I didn't even have an Xorg.conf to start.  I tried running Xorg -configure from a chroot'ed shell, but it didn't do any good...gave me some error.  I started my Xorg.conf from a file someone else posted that was a semi-similar setup.

---

### Post by EkuquoL on 2011-08-04
Remember--- ***to save configurations you have to be root. ***

Since you possibly are using VM ware you might not get the full recognition of driver support. It shows that you are only using default drivers. Meaning you are not loading the correct or absolute drivers for Ubuntu. I'm not too sure of how you would go about that since I am not on a Mac and never used a Mac OSx.

You could try a workaround of Looking for hex conversion tools then attempt to *COPY*[*Don't move or delete location file*] and paste the driver for your monitor into the loader after you use a conversion tool.

You can find Mac OSX conversion tool... Mainly their only used in Terminal.

You can also use the Terminal to mount the Mac OSX hard drive... You will need a MAC OSX mounter. You would tell it
# mount  <OSX drive>

 That would *possibly* help Ubuntu see the Macintosh shell... You can insert an auto mount command( If it works when mounting the OSX shell) in the fstab loader.
The fstab.conf is located in the /etc/ folder.

The fstab is loader that tells the shell to automount drives
You would insert a command into your fstab like...

/dev/<MACOSX drive>    /proc     <sda1 / ext4 /ubuntu partition>    fs  0   1

**The * < > *show that you need to insert your CPU specific variable. **

To learn more information about the use of fstab... 
Do a manual lookup
 type
$ man fstab 
in your Terminal console. That will tell you some tid bit of the mounter.


[COLOR=Red]**Do not remove anything or add/change other variables in your fstab UNLESS the mount helps ubuntu work with it better.**[/COLOR]

---

### Post by Furball588 on 2011-08-04
> **pkmgarf said:**
> I figured deleting the other sections (Depth=16, 8 and 4) would have been sufficient. 

That just fills the various optionsl like the dropdown the gui.  You still need to tell it where to start.

what's Xorg -configure tell you?

---

### Post by Furball588 on 2011-08-04
> **EkuquoL said:**
> Remember--- ***to save configurations you have to be root. ***

Since you possibly are using VM ware you might not get the full recognition of driver support. It shows that you are only using default drivers. Meaning you are not loading the correct or absolute drivers for Ubuntu. I'm not too sure of how you would go about that since I am not on a Mac and never used a Mac OSx.

You could try a workaround of Looking for hex conversion tools then attempt to *COPY*[*Don't move or delete location file*] and paste the driver for your monitor into the loader after you use a conversion tool.

You can find Mac OSX conversion tool... Mainly their only used in Terminal.

You can also use the Terminal to mount the Mac OSX hard drive... You will need a MAC OSX mounter. You would tell it
# mount  <OSX drive>

 That would *possibly* help Ubuntu see the Macintosh shell... You can insert an auto mount command( If it works when mounting the OSX shell) in the fstab loader.
The fstab.conf is located in the /etc/ folder.

The fstab is loader that tells the shell to automount drives
You would insert a command into your fstab like...

/dev/<MACOSX drive>    /proc     <sda1 / ext4 /ubuntu partition>    fs  0   1

**The * < > *show that you need to insert your CPU specific variable. **

To learn more information about the use of fstab... 
Do a manual lookup
 type
$ man fstab 
in your Terminal console. That will tell you some tid bit of the mounter.


[COLOR=Red]**Do not remove anything or add/change other variables in your fstab UNLESS the mount helps ubuntu work with it better.**[/COLOR]

He's not running a vm

Nor are they running OS X

anf whats the fstab have to do with xorg?

---

### Post by linuxopjemac on 2011-08-04
You don't have a "Monitor" Section, while it is mentioned in the "Screen" Section...

You can also fall back to the nv driver, have a look here:

[http://mac.linux.be/content/xorgconf-ilamp-g4-1-ghz](http://mac.linux.be/content/xorgconf-ilamp-g4-1-ghz)

---

### Post by svtguy88 on 2011-08-04
^^^I knew you'd chime in eventually.

I found that page on your site yesterday.  I tried falling back to nv, but it didn't get installed by default, and I can't find it in the repos either.  I haven't looked at sources.list at all, but I could have sworn nv was in the standard debian PPC repos.

I don't have time to play with this thing right now, but I'll try some things after work.  I don't remember the exact error that Xorg -configure threw, but I think it was because I tried to run it while chrooted into my system from the debain rescue CD.

I will try Xorg -configure again from the actual install, and not the rescue CD.  How do I stop the Xserver?  I tried the standard init.d/gdm stop or whatever it is, but it appears that that doesn't stop gdm3?

I guess I could login single user, but I'd like to know how to stop GDM.

---

### Post by svtguy88 on 2011-08-05
I added "DefaultDepth" as well as a "Monitor" section, following the link above.  I still get nasty colors, and glxinfo reports using a software rasterizer.

When I tried running Xorg -configure, it complains about "number of created screens does not match number of detected devices."

I'm off to work again for the day...hopefully I can tinker more when I get home.

---

### Post by linuxopjemac on 2011-08-05
I would turn off KMS (kernel mode setting) and use the nv driver...

---

### Post by svtguy88 on 2011-08-05
I'll give nv a try tomorrow.  It just strikes me as odd that it isn't installed by default or even in the repo...

---

### Post by Stratosmacker on 2011-08-21
> **pkmgarf said:**
> I'll give nv a try tomorrow.  It just strikes me as odd that it isn't installed by default or even in the repo...

Did you ever get this working? I have a 17" imacg4 that I put Debian on and have the same problem.

---

### Post by svtguy88 on 2011-09-01
I did not end up trying it.  I did download a Debian Squeeze CD, which includes nv.  

I double checked on the Debian website, and Wheezy does not include a package for nv, but there is one in Squeeze.  Maybe nv is being phased out in favor of nouveau?  Or just not ready for Wheezy..who knows.

Anyway, I installed Squeeze on my G4 tower, and it works well.  I had the same "less than 24-bit color" problem as I have on the iMac when using nouveau; changing xorg.conf to nv fixes this.  I'll try to give it a try on the iMac tomorrow and see how it looks/works.

I'll report back after I try it.

---

### Post by linuxopjemac on 2011-09-02
This is why I recommend Debian.

---

### Post by svtguy88 on 2011-09-02
Just tried the Squeeze disc on the iMac, and after creating a Xorg.conf file and pointing it to nv, everything works fine.

I do still wonder why nouveau won't do 24bit color...strange.

---

### Post by svtguy88 on 2011-09-07
In case anyone happens to be following this, I've been trying to get nouveau working for me (mainly on my Powermac, but the iMac shows similar problems, so this thread seems relevant).

I compiled a kernel (giving much needed SMP support) and it contains nouveau as a staging driver, so I installed it as a module (along with nv as a backup).  

Nouveau still refuses to work.  Does anyone have nouveau working on a PPC machine?  For now, I turned off KMS and activated nv, but I'd like to get nouveau working, if at all possible.

I did take a peek at the unstable (sid) repos, hoping that maybe an updated version of nouveau and it's dependencies might fix my problem, and noticed that there isn't even a libdrm-nouveau package yet...

---

### Post by rsavage on 2011-09-07
People have certainly been reporting that they are using nouveau [http://ubuntuforums.org/showpost.php?p=11088825&postcount=18](http://ubuntuforums.org/showpost.php?p=11088825&postcount=18) , although I couldn't say whether with your card.  Since it is apparently inseparable from kms, i assume they have had it fully working?

---

### Post by pauljwells on 2011-09-07
G5 PowerMac Dual core with NVidia 6600LE running fine with nouveau 2D

---

### Post by svtguy88 on 2011-09-07
Hmmm...looks like most people having good luck with nouveau are using Lubuntu?

Did you have to do any xorg.conf tweaking, or does nouveau work right out of the box for you?

---

### Post by rsavage on 2011-09-08
> **pkmgarf said:**
> Hmmm...looks like most people having good luck with nouveau are using Lubuntu?

I don't think that is true.  You could maybe say they are Natty users, but it could be the case that lucid and maverick work too.  Nouveau uses kms I believe, so you have to disable other frame buffer devices for it to work.  Natty must take care of this for you.  I posted a lot of good links about drivers on my lubuntu thread so have a look at them.  

Btw, if you install unity check out pauljwells posts.  You need to compile a new version otherwise you get strange colours (I didn't want that to fool you!).

---

### Post by svtguy88 on 2011-09-08
I'm running a Debian Squeeze install, not Ubuntu, and I'm not using Unity.  Could someone with a working nouveau tell me what versions of the xserver-xorg-video-nouveau and libdrm-nouveau are installed?  If it's the same/close as what's in Debian Squeeze - which I imagine it being, it's got to be some sort of configuration issue on my end.

---

### Post by linuxopjemac on 2011-09-08
Could you tro booting with the following kernel argument:
```
video=nvidiafb:off
```
and make sure nouveau is the driver in xorg.conf

---

### Post by svtguy88 on 2011-09-08
Great minds think alike.  When I read that all of the other fb devices need to be off, I thought about adding that argument.  As soon as my system is done burning this disc (Lubuntu live-CD for trial on my Powerbook, coincidentally), I'll switch back to nouveau, turn KMS on and try adding that kernel argument.  I'll report back soon.

---

### Post by svtguy88 on 2011-09-08
No go.  The last line of output I see on bootup is something DRM related, but it flashes to a black screen quickly afterwords.  It looks like the Xserver tries to start (the monitor flashes from the text console, to black, sits for a little while, and then the monitor goes into standby).

Strange.  I am installing Lubuntu off the Live-CD right now on my Powerbook (nVidia card, as well).  It booted to a shell, logged in as "ubuntu," but simply issuing "startx" gets things going as expected - and it's using nouveau...

---

### Post by linuxopjemac on 2011-09-08
aha, interesting indeed! So you can get nouveau to work, except with a display manager like gdm...

---

### Post by svtguy88 on 2011-09-08
Well, I'm not sure the display manager is the issue, although it could be, especially because both the Powermac and Powerbook seem to have issues when it comes time to show the login screen.  I just don't understand why the live-CD (in the Powerbook) puts me at a text login prompt, while the Powermac (with a newer kernel, with nouveau and KMS on) just goes to a black screen.

I'll try to Lubuntu live-CD in the Powermac as soon as the Powerbook is done installing.

---

### Post by svtguy88 on 2011-09-08
More oddities...I tried disabled the login manager using rcconf, but I am still left with a blank screen when trying to boot.  I was thinking disabling GDM would leave me with the text login that the Powerbook gives me on the Lubuntu live-CD, and I could then try to startx from there, but I still end up with nothing...just a black screen.

I also just tried booting the live-CD on the Powermac.  It starts to boot, goes to a white Open Firmware-like screen that shows the path to the nVidia card along with something like "opening screen."  Then it all goes black, and the monitor shuts off.

The only thing I can think of, is that maybe it's defaulting to the VGA port and not the DVI port?  I'll have to try and find a cable...

---

### Post by linuxopjemac on 2011-09-08
let us know, interesting thread.....

---

### Post by rsavage on 2011-09-08
This maybe of interest to you [http://nouveau.freedesktop.org/wiki/KernelModeSetting](http://nouveau.freedesktop.org/wiki/KernelModeSetting) .

And interesting that you tried the live lubuntu cd!!  Maybe you are the first?!

---

### Post by svtguy88 on 2011-09-08
I know I'm not the first, as I got the idea in another thread.  The installation from the live-CD fails though, complaining that the lubuntu mirror contains errors.

I'm looking for a VGA cable right now, to see if nouveau is defaulting to VGA on the Powermac.  The Powerbook seems to be okay, other than the mirror problem.

---

### Post by svtguy88 on 2011-09-08
Well, I couldn't find a VGA cable, but I did notice in kern.log, that it looked like the card was trying to output on the TV-out (an output my card doesn't even have).

That link to KMS info helped a lot.  I already knew how to enable/disable it, but there's a short section on forcing different modes from kernel arguments, and it demonstrates how to force the card to use the DVI connector.  

Booting with ```
video=DVI-I-1:1440x900@60
```
as a kernel argument gets me further than before.  Now the screen doesn't go black, instead the Xserver fails to load, and I'm left with a text login.  I tried logging in and starting X, but, as expected, I get the same error as when X tries to load itself on boot. 

I attached my Xorg.log file, and the part where it seems to go bad is below:

```
II) Primary Device is: PCI 00@00:10:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:10.0
(EE) [drm] failed to open device
(EE) No devices detected.

Fatal server error:
no screens found
```

The only thing that I can see, is that it looks like nouveau is looking to PCI address 00@00:10:0, which is not the address specified for the graphics card in Xorg.conf (0:0:16:0).  I'm kind of beyond my skills here.  Is nouveau looking to the wrong PCI address, or am I misreading the log?

I think I'm going to make a new thread for the Powermac.  Both the Powerbook and iMac all will boot the live-CD and run X from it using nouveau.  The Powermac (with a Geforce 6200) is the only one I can't get to run the live-CD.  I can now get it to boot the CD to a text login by appending the kernel argument I posted earlier, but as soon as I "startx" it all goes to hell again.  Nouveau really doesn't like this card for some reason or another...



**edit**
Just realized 00@00:10:0 is the PCI address listed by lspci for my graphics card...

---

