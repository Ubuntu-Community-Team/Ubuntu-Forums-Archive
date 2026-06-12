---
title: "Power Mac G5 + Nvidia Card Guide"
date: 2015-08-26
forum: Apple Hardware Users
---

### Post by saberblaze on 2015-08-26
I had Power Mac G5 that was being used in a small office before the hard drive died. It is a dual core with 4gb ram and an Nvidia 6600. It had MacOSX with outdated programs and running pretty slow at that. I decided I was going to install Linux on it to give it up to date programs and OS. I put in a hard drive and installed UbuntuMATE.
 
After spending about 2 weeks with it and reading blogs and forum posts, I would like to put together that steps that worked for me to get it working and stable with 2d acceleration.  Most of this information is scattered around so apologies if it's redundant for some of you.
 
I decided to install the 14.04 LTS release so that it can continue to receive security updates for 5 years at least. No need bleeding edge software or shorter release cycles for a simple office computer. It's nice that 15.04 is an official ppc release, but it wouldn't even boot off the live-cd, spitting out an error about 'unable to open rtc device (rtc0)'.
 
Now, these powerpc releases are known for having graphics issues, so I will outline as well what I did to get a working desktop with 2d acceleration. When booting up the computer with the live-cd, I used
```
live-powerpc64 toram nouveau.noaccel=1
```
The toram argument loads the live-cd into ram so you don’t have to keep waiting while the disk drive keeps churning when loading programs etc. The nouveau.noaccel=1 argument is very important, it disables hardware acceleration, which fixes graphical issues and random freezing.  Go ahead and install it, I just picked the defaults and let it do its thing.  Go ahead and reboot.  Remember to add the nouveau.noaccel=1 argument again, so the prompt will look like
```
boot:Linux nouveau.noaccel=1
```
Now, I hadn’t really used Linux for a couple years so I was bit rusty, and I wasn’t really up to date on the whole PPA’s business. So I did a dist-upgrade and broke the system, I had to reinstall. So when you do a dist-upgrade, remember to comment out the PPA sources for apt. I believe just a regular apt-get upgrade would also work without disabling the PPA sources, maybe someone can chime in here.
 

[SIZE=3][U][B]Wireless
[/B][/U][/SIZE]
Now, sound and wireless won’t work out of the box. For the wireless airport card, just do
```
apt-get install firmware-b43-installer
```
Now, I learned Linux using Debian-based distros so I’m used to using a root shell and not typing sudo a million times, so for sudo, to get a root shell just do
```
sudo –i
```
Of course, I know most of you probably don’t want to be in a root shell so just add sudo when needed when running these commands.
 
Now, you can reboot or do
```
modprobe –r b43
modprobe b43
```
 
to get wireless working.
 

[SIZE=3]_**Hotspot**_[/SIZE]

To get wifi hotspot working, read this user's answer and the answer below it:
 
[http://askubuntu.com/a/439530](http://askubuntu.com/a/439530)
 
Basically the gnome-frontend for the network manager didn’t implement ap  mode, which makes the wireless card act like a router so that mobile  phones can also connect to it. As stated in the post, you edit the  configuration file to change mode to ap or install the KDE connection manager, although it  does pull in quite a few KDE libraries.
 
I tested this in a live-cd environment and the hotspot worked fine. I  was able to connect to it using my android phone and the internet worked  fine. However when I set up the G5 at the office we were able to  connect to the hotspot but internet did not work. The G5 is connected to  a Clear modem by Ethernet. I would like to point out that at first the  internet did not work at first, but after many tries we were rerouted to  Clear page and then finally the internet worked. Even apt-get had  complained about “clearsigned file isn't valid got 'nodata'” error, but  that went away. I’m assuming there must be DNS issues at play, since I  worked on the G5 at home and now it’s at the office, maybe Ubuntu had to  get new DNS servers from the new ISP. Although the internet works now,  it does not work for devices connected to the hotspot, if anyone has any  idea how I can get it working it would be greatly appreciated. The  problem seems to be that it doesn’t pass the connection from Ethernet to  wifi correctly. My android phone complained that the wifi may not supply an internet connection. I checked the Ethernet settings and things are still at  their defaults.

[SIZE=3]_**Sound**_[/SIZE]

For sound, I only had to add
```
snd-aoa-i2sbus
 
```
to the /etc/modules files. If for some reason that doesn’t work, you can also try adding
```
snd-aoa-fabric-layout
snd-aoa-codec-tas
snd-aoa-codec-onyx
```
You can reboot or use modprobe.
 

[SIZE=3]_**2D Acceleration**_[/SIZE]

Now, as for 2d acceleration, I suggest you read this blog post:
 
[G5: Nouveau & 2D Acceleration]("http://powerpcliberation.blogspot.com/2015/07/g5-nouveau-2d-acceleration.html")

It explains what’s going on in regards to nouveau not working. Basically some kernel configurations cause issues with the nouveau driver (pagesize and msi interrupts). You can either compile the kernel yourself or download the precompiled kernel that fixes these issues for you:
 
 [Debian Jessie 8.1 PPC64 Kernel]("https://drive.google.com/folderview?id=0B8pqd5Ots1vffmY5ZnpGUDg4UGNnVFk2M05tQUtEUUkwUmhmQWdLMWpfZGVraDIxSFltb1k&usp=drive_web")

It’s for Debian but it works great in Ubuntu :D
 
After you install using the .deb files, make sure you add the appropriate entries in your /etc/yaboot.conf for your new kernel, then do
```
ybin –v
```
Make sure to add the new kernel entry first as that will be the default kernel Ubuntu will use. Also check that the default kernel parameters match the other entries, I believe for mine it was "quiet splash toram" although I think toram isn't needed. I would also recommend adding the nouveau.noaccel=1 parameter to the stock kernel entry in case you ever need to boot using your old kernel. I will post my yaboot.conf here the next time I can get a hold of the G5. 

One more thing, you have to add
```
i2c-powermac 
```
to your /etc/modules file with this kernel for fan control so they don't run at full blast all the time. Reboot and enjoy 2d acceleration :).
 

[SIZE=3][U][B]Splash Animation
[/B][/U][/SIZE]
Now, for me the boot splash animation did not work anymore, it would show UbuntuMATE text, no logo, with the colored background and garbled text all around. The shutdown animation worked fine. I believe it happened after dist-upgrading, but at any rate, there is a very simple fix. There’s all kinds of advice to fixing the Plymouth splash animation but all you have to do is create this file
```
/etc/initramfs-tools/conf.d/splash
```
and add this line exactly
```
FRAMEBUFFER=y
```
It basically makes Plymouth use an older technique for accessing video memory instead of KMS. After that do
```
update-initramfs -u
```
I always throw in a
```
ybin –v
```
just in case.
 
Reboot and enjoy a working boot splash animation.
 

[SIZE=3]_**Miscellaneous**_[/SIZE]

Here's some useful information regarding the LTS release

[URL="https://ubuntu-mate.community/t/ubuntu-mate-14-04-lts-useful-information/25"]Ubuntu MATE 14.04 LTS Useful Information
[/URL]
I like the Windows desktop layout with the MATE menu and indicators, so I used
```
mate-panel --reset --layout redmond-indicators-fresh
```
To get the the default yuyo theme that comes with 15.04 do
```
apt-get install yuyo-gtk-theme 
``` 
I will post a pic of the desktop next time I'm able to use the G5.

Firefox in powerpc seems to have a few issues or quirks but it’s not a dealbreaker. Tab groups don’t work for me. If you disable Firefox Hello by toggling loop.enabled then session restore doesn’t work. In Debian Jessie, Iceweasel wouldn’t install any extensions, complaining that it couldn’t modify the needed file, however it seems to be fixed in Ubuntu.

 
Hopefully this guide was able to help someone out with a Power Mac G5 with an Nvidia card. Maybe the modified kernel might even help ATI users if they have issues, who knows.

---

### Post by xeno74 on 2015-08-26
Thank you!

---

### Post by rsavage on 2015-08-26
I would ignore what that powerpcliberation link says.  The Ubuntu kernel doesn't have 64k page sizes and you can disable MSI with the boot parameter
```

nouveau.config=NvMSI=0

```

I wouldn't mix a debian kernel with Ubuntu, things like wifi can be affected by doing such things.

Do you get the full graphical splash screen?  And are the colours correct?

---

### Post by saberblaze on 2015-08-26
When I ran the ```
 getconf PAGESIZE
``` command listed to test the page size it showed a 64k size for me. Of course I would prefer to compile my own kernel but it would have taken too much additional time for me to figure out. If someone would like to compile a Ubuntu kernel for us that would be great. And yes I get a full graphical splash screen, everything shown correctly by using the FRAMEBUFFER=y as I did.

I will try booting with the old kernel to test the WiFi Hotspot when I get a chance, although I suspect that particular problem is dns/gateway related.

---

### Post by rsavage on 2015-08-27
In the directory /boot there should be lots of config files.  They should have

```

CONFIG_PPC_4K_PAGES=y
# CONFIG_PPC_64K_PAGES is not set

```

---

### Post by rsavage on 2015-08-28
A couple of more things:

The Ubuntu kernel has the i2c_powermac module built in so if you use the default kernel then the fans should work okay.  Is that right?

I would also try a Ubuntu 12.04 iso, and if nouveau works better in that then you can downgrade the xorg/mesa drivers to the 12.04 versions.  Well you can do that with radeon anyway.

---

### Post by saberblaze on 2015-08-28
Correct, the fans work out of the box with the default Ubuntu kernel, it's only the Debian kernel that needs the i2c-powermac module added to /etc/modules. As far testing the older version of nouveau that doesn't sound like a bad idea, I'll see if I can test the older ppc release. Since the Mac is back in its office I only have a chance to look at it on Saturdays. Only downside I can see is if older versions have less performance than newer versions or any relevant bugs.

---

### Post by saberblaze on 2015-08-31
Thanks for the help rsavage, definitely helped in fixing the WiFi hotspot issue :smile:   You were right about the Debian kernel, although WiFi worked, the  hotspot feature was broken. Booting with the Ubuntu kernel fixed it  right up.  I booted using the ```
nouveau.config=NvMSI=0
``` and  checked the PAGESIZE parameter, and indeed it was 4k. I'm not sure why I  got 64k get last time, perhaps disabling MSI knocks it down to 4k? I  didn't have time to test booting a Ubuntu kernel with MSI enabled so I  can't know for sure, however I did find some interesting things I'd like  to share.

Without using the ```
FRAMEBUFFER=y
``` in  /etc/initramfs-tools/conf.d/splash file the boot splash animation works  fine using the 3.13 kernel, but it is broken in the 3.16 kernel. There  wasn't a 3.18 powerpc64 kernel in the repositories but there was a 3.19  from vivid. The system won't boot using that kernel, same reason why  15.04 release wouldn't boot for me. It just displays that  'unable to  open rtc device (rtc0)' error. Now, I believe the system boots in the  background, since the hotspot shows up and works on my phone, it's just  the video output is frozen. I had to connect a pc keyboard and use the  magic sysrq sequence to reboot.

Using FRAMEBUFFER=y from before will fix boot splash animation in the  3.16 kernel. It also displays the rtc device error but still boots  normally. I had decided to just leave the 3.13 kernel with the  nouveau.config=NvMSI=0 boot option. Unfortunately, after about 10  minutes of use, the mouse cursor became that psychedelic box, which  usually signals that sooner or later the system would freeze or have a  broken display. I tested this by locking the screen, which invokes the  screensaver. Sure enough, I get a black screen with only the mouse  cursor. Switching to a terminal just shows a black screen. After a  little while that system fans start to rev up.  Again, the system is  running in the background, but graphical output is worthless.  I can't  remember if the magic sysrq sequence worked or not.

At this point it would seem that even with 4k PAGESIZE and MSI disabled  it's still susceptible to graphical issues. Now, I tried using the  FRAMEBUFFER=y again for the boot splash and running ```
update-initramfs -u -k all
``` to apply it to all the kernels.  I rebooted  and tested both the 3.13 kernel and the 3.16 kernels. After 20 minutes  of doing different things, such as browsing, playing videos, logging out  and locking the screen, everything kept running fine with no issues. It  would appear to be fixed (fingers crossed), although I'm not sure why  the method of displaying the boot animation would impact the desktop.  For now, I left the 3.13 kernel with the nouveau.config=NvMSI=0 option  as the default boot kernel with the FRAMEBUFFER=y option. I told them to  let me know if there's any issues later on, although hopefully  everything works now.

I'd like to update my first post with the additional info and add tags but it's not letting me :sad:  If there's no further issues reported this might just be the fix to get  working 2D acceleration on a G5 without resorting to using a Debian  kernel.

As a side note, does anyone know if there is a keyboard layout for the 109 key mac keyboard that comes with the G5? 
Here's a pic: [G5 Keyboard]("http://media.engadget.com/img/product/14/b5i/keyboard-n46.jpg")
Unfortunately it wasn't listed in any of the Apple keyboard layouts that came with Ubuntu. I chose one of them that shared some of the keys so that at least the clear key wouldn't act as a num lock key using the the default pc keyboard layout.  Some of the high f keys sometimes don't work or are mapped to other codes. It's no big deal, for most purposes it works fine, but it'd be nice to have a correct layout.

---

### Post by rsavage on 2015-08-31
Glad it is working!

Can you check if framebuffer=y is causing something to be disabled?

Also, can you update the known issues wiki page with the fix please?

---

### Post by saberblaze on 2015-09-02
I updated the known issues wiki with fixes for issues for the Power Mac G5. It was a pain in the butt getting the wiki login to work to allow me edit. I'm not sure how to check all the changes that FRAMEBUFFER=y makes. [Searching online]("http://askubuntu.com/a/79959") states that it uses an older method to directly access the graphics video memory and it's recommended to use for cards that have issues with KMS. Maybe that carries over into the desktop somehow. It would make sense since Nouveau is known to have issues in PPC Macs. So far no problems reported with this fix...

---

### Post by rsavage on 2015-09-03
Thanks!  Yeah logging in is a pain, I'm failing at the moment.

I just wondered if you noticed any differences in the Xorg.0.log with framebuffer=y that is all.  The order of the modules loaded could have changed, and that sometimes disables things because of race issues.

---

### Post by saberblaze on 2015-09-05
Yeah, apparently according to [this]("https://help.ubuntu.com/community/WikiGuide/Registration"), I needed to create a launchpad account to be able to edit the wiki, not sure if it might be the case with you too. I do wish the wiki had an advanced editor though, seems very rudimentary.

And I had forgotten about Xorg.0.log, next time I can tinker with the G5 I'll see if I can take a look and compare the differences and post them on here. It might not be for quite some time though.

---

### Post by saberblaze on 2015-09-14
Ok, so I had a chance to stop by and try the Mac and check out the Xorg.0.log. First thing's first, unfortunately the graphical errors still occur occasionally. It was reported that it was on the entire day and then towards the end the mouse became the multicolored box again. When I tried it, it had issues after about 5 minutes.  It's not often it seems, just every once in a while the Mac will still show graphical issues, so perhaps the FRAMEBUFFER=y decreases the likelihood of problems arising, or it could just be random :(  I will note that problems seem to be occurring more often, I'll have to update the Ubuntu wiki again. I've read that the nv driver worked good in the past, maybe compiling for the new Ubuntu's would yield better results? At any rate, the Mac still functions good most of the time.

Here are the logs, not much difference to be honest:

with FRAMEBUFFER=y```
[   505.488] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   505.488] X Protocol Version 11, Revision 0
[   505.488] Build Operating System: Linux 3.13.0-45-powerpc64-smp ppc Ubuntu
[   505.488] Current Operating System: Linux Power-Mac-G5 3.13.0-62-powerpc64-smp #102-Ubuntu SMP Tue Aug 11 14:59:38 UTC 2015 ppc64
[   505.488] Kernel command line: root=UUID=a6d50d72-be0e-4a51-a4b9-11a0be5673c0 ro quiet splash toram nouveau.config=NvMSI=0 
[   505.488] Build Date: 12 February 2015  02:53:48PM
[   505.488] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[   505.488] Current version of pixman: 0.30.2
[   505.488]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   505.488] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   505.489] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 14 17:11:06 2015
[   505.489] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   505.489] (==) No Layout section.  Using the first Screen section.
[   505.489] (==) No screen section available. Using defaults.
[   505.489] (**) |-->Screen "Default Screen Section" (0)
[   505.490] (**) |   |-->Monitor "<default monitor>"
[   505.490] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   505.490] (==) Automatically adding devices
[   505.490] (==) Automatically enabling devices
[   505.490] (==) Automatically adding GPU devices
[   505.490] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   505.490]     Entry deleted from font path.
[   505.490] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   505.490]     Entry deleted from font path.
[   505.490] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   505.490]     Entry deleted from font path.
[   505.490] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   505.490]     Entry deleted from font path.
[   505.490] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   505.490]     Entry deleted from font path.
[   505.490] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   505.490] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   505.490] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   505.490] (II) Loader magic: 0x203f1694
[   505.490] (II) Module ABI versions:
[   505.490]     X.Org ANSI C Emulation: 0.4
[   505.490]     X.Org Video Driver: 15.0
[   505.490]     X.Org XInput driver : 20.0
[   505.490]     X.Org Server Extension : 8.0
[   505.491] (II) xfree86: Adding drm device (/dev/dri/card0)
[   505.493] (--) PCI:*(0:10:0:0) 10de:0141:10de:0010 rev 162, Mem @ 0xa1000000/16777216, 0x90000000/268435456, 0xa0000000/16777216, BIOS @ 0x????????/131072
[   505.493] Initializing built-in extension Generic Event Extension
[   505.493] Initializing built-in extension SHAPE
[   505.493] Initializing built-in extension MIT-SHM
[   505.493] Initializing built-in extension XInputExtension
[   505.493] Initializing built-in extension XTEST
[   505.493] Initializing built-in extension BIG-REQUESTS
[   505.493] Initializing built-in extension SYNC
[   505.493] Initializing built-in extension XKEYBOARD
[   505.493] Initializing built-in extension XC-MISC
[   505.493] Initializing built-in extension SECURITY
[   505.493] Initializing built-in extension XINERAMA
[   505.493] Initializing built-in extension XFIXES
[   505.493] Initializing built-in extension RENDER
[   505.494] Initializing built-in extension RANDR
[   505.494] Initializing built-in extension COMPOSITE
[   505.494] Initializing built-in extension DAMAGE
[   505.494] Initializing built-in extension MIT-SCREEN-SAVER
[   505.494] Initializing built-in extension DOUBLE-BUFFER
[   505.494] Initializing built-in extension RECORD
[   505.494] Initializing built-in extension DPMS
[   505.494] Initializing built-in extension Present
[   505.494] Initializing built-in extension DRI3
[   505.494] Initializing built-in extension X-Resource
[   505.494] Initializing built-in extension XVideo
[   505.494] Initializing built-in extension XVideo-MotionCompensation
[   505.494] Initializing built-in extension SELinux
[   505.494] Initializing built-in extension XFree86-VidModeExtension
[   505.494] Initializing built-in extension XFree86-DGA
[   505.494] Initializing built-in extension XFree86-DRI
[   505.494] Initializing built-in extension DRI2
[   505.494] (II) LoadModule: "glx"
[   505.494] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   505.496] (II) Module glx: vendor="X.Org Foundation"
[   505.497]     compiled for 1.15.1, module version = 1.0.0
[   505.497]     ABI class: X.Org Server Extension, version 8.0
[   505.497] (==) AIGLX enabled
[   505.497] Loading extension GLX
[   505.497] (==) Matched nvidia as autoconfigured driver 0
[   505.497] (==) Matched nouveau as autoconfigured driver 1
[   505.497] (==) Matched nvidia as autoconfigured driver 2
[   505.497] (==) Matched nouveau as autoconfigured driver 3
[   505.497] (==) Matched modesetting as autoconfigured driver 4
[   505.497] (==) Matched fbdev as autoconfigured driver 5
[   505.497] (==) Assigned the driver to the xf86ConfigLayout
[   505.497] (II) LoadModule: "nvidia"
[   505.498] (WW) Warning, couldn't open module nvidia
[   505.498] (II) UnloadModule: "nvidia"
[   505.498] (II) Unloading nvidia
[   505.498] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   505.498] (II) LoadModule: "nouveau"
[   505.498] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   505.498] (II) Module nouveau: vendor="X.Org Foundation"
[   505.498]     compiled for 1.15.0, module version = 1.0.10
[   505.498]     Module class: X.Org Video Driver
[   505.498]     ABI class: X.Org Video Driver, version 15.0
[   505.498] (II) LoadModule: "modesetting"
[   505.499] (WW) Warning, couldn't open module modesetting
[   505.499] (II) UnloadModule: "modesetting"
[   505.499] (II) Unloading modesetting
[   505.499] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   505.499] (II) LoadModule: "fbdev"
[   505.500] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   505.500] (II) Module fbdev: vendor="X.Org Foundation"
[   505.500]     compiled for 1.15.0, module version = 0.4.4
[   505.500]     Module class: X.Org Video Driver
[   505.500]     ABI class: X.Org Video Driver, version 15.0
[   505.500] (==) Matched nvidia as autoconfigured driver 0
[   505.500] (==) Matched nouveau as autoconfigured driver 1
[   505.500] (==) Matched nvidia as autoconfigured driver 2
[   505.500] (==) Matched nouveau as autoconfigured driver 3
[   505.500] (==) Matched modesetting as autoconfigured driver 4
[   505.500] (==) Matched fbdev as autoconfigured driver 5
[   505.500] (==) Assigned the driver to the xf86ConfigLayout
[   505.500] (II) LoadModule: "nvidia"
[   505.501] (WW) Warning, couldn't open module nvidia
[   505.501] (II) UnloadModule: "nvidia"
[   505.501] (II) Unloading nvidia
[   505.501] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   505.501] (II) LoadModule: "nouveau"
[   505.501] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   505.501] (II) Module nouveau: vendor="X.Org Foundation"
[   505.501]     compiled for 1.15.0, module version = 1.0.10
[   505.501]     Module class: X.Org Video Driver
[   505.501]     ABI class: X.Org Video Driver, version 15.0
[   505.501] (II) UnloadModule: "nouveau"
[   505.501] (II) Unloading nouveau
[   505.501] (II) Failed to load module "nouveau" (already loaded, 0)
[   505.501] (II) LoadModule: "modesetting"
[   505.502] (WW) Warning, couldn't open module modesetting
[   505.502] (II) UnloadModule: "modesetting"
[   505.502] (II) Unloading modesetting
[   505.502] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   505.502] (II) LoadModule: "fbdev"
[   505.502] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   505.502] (II) Module fbdev: vendor="X.Org Foundation"
[   505.502]     compiled for 1.15.0, module version = 0.4.4
[   505.502]     Module class: X.Org Video Driver
[   505.502]     ABI class: X.Org Video Driver, version 15.0
[   505.502] (II) UnloadModule: "fbdev"
[   505.502] (II) Unloading fbdev
[   505.502] (II) Failed to load module "fbdev" (already loaded, 0)
[   505.502] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[   505.502] (II) NOUVEAU driver for NVIDIA chipset families :
[   505.502]     RIVA TNT        (NV04)
[   505.503]     RIVA TNT2       (NV05)
[   505.503]     GeForce 256     (NV10)
[   505.503]     GeForce 2       (NV11, NV15)
[   505.503]     GeForce 4MX     (NV17, NV18)
[   505.503]     GeForce 3       (NV20)
[   505.503]     GeForce 4Ti     (NV25, NV28)
[   505.503]     GeForce FX      (NV3x)
[   505.503]     GeForce 6       (NV4x)
[   505.503]     GeForce 7       (G7x)
[   505.503]     GeForce 8       (G8x)
[   505.503]     GeForce GTX 200 (NVA0)
[   505.503]     GeForce GTX 400 (NVC0)
[   505.503] (II) FBDEV: driver for framebuffer: fbdev
[   505.503] (++) using VT number 7

[   505.504] (II) [drm] nouveau interface version: 1.1.2
[   505.504] (WW) Falling back to old probe method for fbdev
[   505.504] (II) Loading sub module "fbdevhw"
[   505.504] (II) LoadModule: "fbdevhw"
[   505.504] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   505.505] (II) Module fbdevhw: vendor="X.Org Foundation"
[   505.505]     compiled for 1.15.1, module version = 0.0.2
[   505.505]     ABI class: X.Org Video Driver, version 15.0
[   505.505] (II) Loading sub module "dri2"
[   505.505] (II) LoadModule: "dri2"
[   505.505] (II) Module "dri2" already built-in
[   505.505] (--) NOUVEAU(0): Chipset: "NVIDIA NV43"
[   505.505] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   505.505] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   505.505] (==) NOUVEAU(0): RGB weight 888
[   505.505] (==) NOUVEAU(0): Default visual is TrueColor
[   505.505] (==) NOUVEAU(0): Using HW cursor
[   505.505] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[   505.505] (==) NOUVEAU(0): Page flipping enabled
[   505.505] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[   505.537] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[   505.592] (II) NOUVEAU(0): Output DVI-I-2 has no monitor section
[   505.625] (II) NOUVEAU(0): EDID for output DVI-I-1
[   505.625] (II) NOUVEAU(0): Manufacturer: DEL  Model: e009  Serial#: 827736396
[   505.625] (II) NOUVEAU(0): Year: 2005  Week: 25
[   505.625] (II) NOUVEAU(0): EDID Version: 1.3
[   505.625] (II) NOUVEAU(0): Digital Display Input
[   505.625] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
[   505.625] (II) NOUVEAU(0): Gamma: 2.20
[   505.625] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
[   505.626] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   505.626] (II) NOUVEAU(0): First detailed timing is preferred mode
[   505.626] (II) NOUVEAU(0): redX: 0.637 redY: 0.340   greenX: 0.297 greenY: 0.610
[   505.626] (II) NOUVEAU(0): blueX: 0.146 blueY: 0.071   whiteX: 0.313 whiteY: 0.329
[   505.626] (II) NOUVEAU(0): Supported established timings:
[   505.626] (II) NOUVEAU(0): 720x400@70Hz
[   505.626] (II) NOUVEAU(0): 640x480@60Hz
[   505.626] (II) NOUVEAU(0): 640x480@75Hz
[   505.626] (II) NOUVEAU(0): 800x600@60Hz
[   505.626] (II) NOUVEAU(0): 800x600@75Hz
[   505.626] (II) NOUVEAU(0): 1024x768@60Hz
[   505.626] (II) NOUVEAU(0): 1024x768@75Hz
[   505.626] (II) NOUVEAU(0): 1280x1024@75Hz
[   505.626] (II) NOUVEAU(0): Manufacturer's mask: 0
[   505.626] (II) NOUVEAU(0): Supported standard timings:
[   505.626] (II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   505.626] (II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   505.626] (II) NOUVEAU(0): Supported detailed timing:
[   505.626] (II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
[   505.626] (II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[   505.626] (II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[   505.626] (II) NOUVEAU(0): Serial No: T613056M1VAL
[   505.626] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[   505.626] (II) NOUVEAU(0): Monitor name: DELL 2005FPW
[   505.626] (II) NOUVEAU(0): EDID (in hex):
[   505.626] (II) NOUVEAU(0):     00ffffffffffff0010ac09e04c415631
[   505.626] (II) NOUVEAU(0):     190f0103ee2b1b78ea0195a3574c9c25
[   505.626] (II) NOUVEAU(0):     125054a54b008180714f010101010101
[   505.626] (II) NOUVEAU(0):     0101010101017c2e90a0601a1e403020
[   505.626] (II) NOUVEAU(0):     3600b20e1100001a000000ff00543631
[   505.626] (II) NOUVEAU(0):     333035364d3156414c0a000000fd0038
[   505.626] (II) NOUVEAU(0):     4b1e530e000a202020202020000000fc
[   505.626] (II) NOUVEAU(0):     0044454c4c20323030354650570a00a1
[   505.626] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[   505.626] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[   505.626] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   505.626] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   505.626] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   505.626] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   505.626] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   505.627] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   505.627] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   505.627] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   505.627] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   505.627] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   505.684] (II) NOUVEAU(0): EDID for output DVI-I-2
[   505.684] (II) NOUVEAU(0): Output DVI-I-1 connected
[   505.684] (II) NOUVEAU(0): Output DVI-I-2 disconnected
[   505.684] (II) NOUVEAU(0): Using exact sizes for initial modes
[   505.684] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1680x1050
[   505.684] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   505.684] (--) NOUVEAU(0): Virtual size is 1680x1050 (pitch 0)
[   505.684] (**) NOUVEAU(0):  Driver mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
[   505.684] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[   505.684] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[   505.684] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   505.684] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[   505.684] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   505.684] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[   505.684] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   505.684] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[   505.685] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   505.685] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[   505.685] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   505.685] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[   505.685] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   505.685] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[   505.685] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   505.685] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[   505.685] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   505.685] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[   505.685] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   505.685] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[   505.685] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   505.685] (==) NOUVEAU(0): DPI set to (96, 96)
[   505.685] (II) Loading sub module "fb"
[   505.685] (II) LoadModule: "fb"
[   505.686] (II) Loading /usr/lib/xorg/modules/libfb.so
[   505.687] (II) Module fb: vendor="X.Org Foundation"
[   505.687]     compiled for 1.15.1, module version = 1.0.0
[   505.687]     ABI class: X.Org ANSI C Emulation, version 0.4
[   505.687] (II) Loading sub module "exa"
[   505.687] (II) LoadModule: "exa"
[   505.687] (II) Loading /usr/lib/xorg/modules/libexa.so
[   505.688] (II) Module exa: vendor="X.Org Foundation"
[   505.688]     compiled for 1.15.1, module version = 2.6.0
[   505.688]     ABI class: X.Org Video Driver, version 15.0
[   505.688] (II) Loading sub module "shadowfb"
[   505.688] (II) LoadModule: "shadowfb"
[   505.688] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   505.689] (II) Module shadowfb: vendor="X.Org Foundation"
[   505.689]     compiled for 1.15.1, module version = 1.0.0
[   505.689]     ABI class: X.Org ANSI C Emulation, version 0.4
[   505.689] (II) UnloadModule: "fbdev"
[   505.689] (II) Unloading fbdev
[   505.689] (II) UnloadSubModule: "fbdevhw"
[   505.689] (II) Unloading fbdevhw
[   505.689] (--) Depth 24 pixmap format is 32 bpp
[   505.690] (II) NOUVEAU(0): Opened GPU channel 0
[   505.697] (II) NOUVEAU(0): [DRI2] Setup complete
[   505.697] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[   505.697] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[   505.697] (II) EXA(0): Driver allocated offscreen pixmaps
[   505.697] (II) EXA(0): Driver registered support for the following operations:
[   505.698] (II)         Solid
[   505.698] (II)         Copy
[   505.698] (II)         Composite (RENDER acceleration)
[   505.698] (II)         UploadToScreen
[   505.698] (II)         DownloadFromScreen
[   505.698] (==) NOUVEAU(0): Backing store enabled
[   505.698] (==) NOUVEAU(0): Silken mouse enabled
[   505.698] (II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
[   505.698] (II) NOUVEAU(0): [XvMC] Extension initialized.
[   505.698] (==) NOUVEAU(0): DPMS enabled
[   505.698] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   505.699] (--) RandR disabled
[   505.725] (II) SELinux: Disabled on system
[   505.741] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   505.741] (II) AIGLX: enabled GLX_ARB_create_context
[   505.741] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   505.741] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   505.741] (II) AIGLX: enabled GLX_INTEL_swap_event
[   505.741] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   505.741] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[   505.741] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[   505.741] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   505.742] (II) AIGLX: Loaded and initialized nouveau
[   505.742] (II) GLX: Initialized DRI2 GL provider for screen 0
[   505.746] (II) NOUVEAU(0): NVEnterVT is called.
[   505.746] (II) NOUVEAU(0): Setting screen physical size to 444 x 277
[   505.746] resize called 1680 1050
[   505.774] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   505.780] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:0b.0/0000:0a:00.0/drm/card0
[   505.780] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   505.781] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/event0)
[   505.781] (**) PIXART USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[   505.781] (II) LoadModule: "evdev"
[   505.782] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   505.782] (II) Module evdev: vendor="X.Org Foundation"
[   505.782]     compiled for 1.15.0, module version = 2.8.2
[   505.782]     Module class: X.Org XInput Driver
[   505.782]     ABI class: X.Org XInput driver, version 20.0
[   505.782] (II) Using input driver 'evdev' for 'PIXART USB OPTICAL MOUSE'
[   505.782] (**) PIXART USB OPTICAL MOUSE: always reports core events
[   505.782] (**) evdev: PIXART USB OPTICAL MOUSE: Device: "/dev/input/event0"
[   505.782] (--) evdev: PIXART USB OPTICAL MOUSE: Vendor 0x93a Product 0x2510
[   505.782] (--) evdev: PIXART USB OPTICAL MOUSE: Found 3 mouse buttons
[   505.782] (--) evdev: PIXART USB OPTICAL MOUSE: Found scroll wheel(s)
[   505.782] (--) evdev: PIXART USB OPTICAL MOUSE: Found relative axes
[   505.782] (--) evdev: PIXART USB OPTICAL MOUSE: Found x and y relative axes
[   505.782] (II) evdev: PIXART USB OPTICAL MOUSE: Configuring as mouse
[   505.782] (II) evdev: PIXART USB OPTICAL MOUSE: Adding scrollwheel support
[   505.783] (**) evdev: PIXART USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[   505.783] (**) evdev: PIXART USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   505.783] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input8/event0"
[   505.783] (II) XINPUT: Adding extended input device "PIXART USB OPTICAL MOUSE" (type: MOUSE, id 6)
[   505.783] (II) evdev: PIXART USB OPTICAL MOUSE: initialized for relative axes.
[   505.783] (**) PIXART USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[   505.783] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration profile 0
[   505.783] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[   505.783] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[   505.784] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/mouse0)
[   505.784] (II) No input driver specified, ignoring this device.
[   505.784] (II) This device may have been added with another device file.
[   505.785] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event3)
[   505.785] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   505.785] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[   505.785] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[   505.785] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event3"
[   505.785] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x20b
[   505.785] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[   505.785] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[   505.785] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input3/event3"
[   505.785] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 7)
[   505.785] (**) Option "xkb_rules" "evdev"
[   505.785] (**) Option "xkb_model" "applealu_iso"
[   505.785] (**) Option "xkb_layout" "us"
[   505.798] (II) XKB: reuse xkmfile /var/lib/xkb/server-028D4789F599EF7F578C26455F70CBDC81D256F1.xkm
[   505.799] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event4)
[   505.799] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   505.799] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[   505.799] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[   505.800] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event4"
[   505.800] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x20b
[   505.800] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[   505.800] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[   505.800] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.3/2-2.3:1.1/input/input4/event4"
[   505.800] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 8)
[   505.800] (**) Option "xkb_rules" "evdev"
[   505.800] (**) Option "xkb_model" "applealu_iso"
[   505.800] (**) Option "xkb_layout" "us"
[   515.365] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[   515.365] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[   515.365] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[   515.365] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   515.365] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[   515.365] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   515.365] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   515.365] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   515.366] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   515.366] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   515.366] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   515.366] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   515.366] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   515.366] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   515.366] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   515.501] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[   515.501] (II) NOUVEAU(0): Using hsync ranges from config file
[   515.501] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   515.501] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   515.501] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[   515.501] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   515.501] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   515.501] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   515.501] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   515.501] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   515.501] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   515.501] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   515.501] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   515.501] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   515.502] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   515.630] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[   515.630] (II) NOUVEAU(0): Using hsync ranges from config file
[   515.630] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   515.630] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   515.630] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[   515.630] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   515.630] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   515.630] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   515.630] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   515.630] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   515.630] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   515.630] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   515.630] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   515.630] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   515.630] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   515.758] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[   515.758] (II) NOUVEAU(0): Using hsync ranges from config file
[   515.758] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   515.758] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   515.758] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[   515.759] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   515.759] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   515.759] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   515.759] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   515.759] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   515.759] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   515.759] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   515.759] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   515.759] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   515.759] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   516.573] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[   516.574] (II) NOUVEAU(0): Using hsync ranges from config file
[   516.574] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   516.574] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   516.574] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[   516.574] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   516.574] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   516.574] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   516.574] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   516.574] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   516.574] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   516.574] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   516.574] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   516.574] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   516.574] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
```

without FRAMEBUFFER=y```
[    20.785] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    20.785] X Protocol Version 11, Revision 0
[    20.785] Build Operating System: Linux 3.13.0-45-powerpc64-smp ppc Ubuntu
[    20.785] Current Operating System: Linux Power-Mac-G5 3.13.0-62-powerpc64-smp #102-Ubuntu SMP Tue Aug 11 14:59:38 UTC 2015 ppc64
[    20.785] Kernel command line: root=UUID=a6d50d72-be0e-4a51-a4b9-11a0be5673c0 ro quiet splash toram nouveau.config=NvMSI=0 
[    20.785] Build Date: 12 February 2015  02:53:48PM
[    20.785] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    20.785] Current version of pixman: 0.30.2
[    20.785]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.785] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.785] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 14 17:42:14 2015
[    20.813] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.814] (==) No Layout section.  Using the first Screen section.
[    20.814] (==) No screen section available. Using defaults.
[    20.814] (**) |-->Screen "Default Screen Section" (0)
[    20.814] (**) |   |-->Monitor "<default monitor>"
[    20.814] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.815] (==) Automatically adding devices
[    20.815] (==) Automatically enabling devices
[    20.815] (==) Automatically adding GPU devices
[    21.082] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.082]     Entry deleted from font path.
[    21.082] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.082]     Entry deleted from font path.
[    21.082] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.082]     Entry deleted from font path.
[    21.246] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.246]     Entry deleted from font path.
[    21.246] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.246]     Entry deleted from font path.
[    21.246] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    21.246] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.246] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.246] (II) Loader magic: 0x20670694
[    21.246] (II) Module ABI versions:
[    21.246]     X.Org ANSI C Emulation: 0.4
[    21.246]     X.Org Video Driver: 15.0
[    21.246]     X.Org XInput driver : 20.0
[    21.246]     X.Org Server Extension : 8.0
[    21.247] (II) xfree86: Adding drm device (/dev/dri/card0)
[    21.249] (--) PCI:*(0:10:0:0) 10de:0141:10de:0010 rev 162, Mem @ 0xa1000000/16777216, 0x90000000/268435456, 0xa0000000/16777216, BIOS @ 0x????????/131072
[    21.249] Initializing built-in extension Generic Event Extension
[    21.249] Initializing built-in extension SHAPE
[    21.249] Initializing built-in extension MIT-SHM
[    21.249] Initializing built-in extension XInputExtension
[    21.249] Initializing built-in extension XTEST
[    21.249] Initializing built-in extension BIG-REQUESTS
[    21.249] Initializing built-in extension SYNC
[    21.249] Initializing built-in extension XKEYBOARD
[    21.249] Initializing built-in extension XC-MISC
[    21.249] Initializing built-in extension SECURITY
[    21.249] Initializing built-in extension XINERAMA
[    21.249] Initializing built-in extension XFIXES
[    21.249] Initializing built-in extension RENDER
[    21.249] Initializing built-in extension RANDR
[    21.249] Initializing built-in extension COMPOSITE
[    21.249] Initializing built-in extension DAMAGE
[    21.249] Initializing built-in extension MIT-SCREEN-SAVER
[    21.249] Initializing built-in extension DOUBLE-BUFFER
[    21.250] Initializing built-in extension RECORD
[    21.250] Initializing built-in extension DPMS
[    21.250] Initializing built-in extension Present
[    21.250] Initializing built-in extension DRI3
[    21.250] Initializing built-in extension X-Resource
[    21.250] Initializing built-in extension XVideo
[    21.250] Initializing built-in extension XVideo-MotionCompensation
[    21.250] Initializing built-in extension SELinux
[    21.250] Initializing built-in extension XFree86-VidModeExtension
[    21.250] Initializing built-in extension XFree86-DGA
[    21.250] Initializing built-in extension XFree86-DRI
[    21.250] Initializing built-in extension DRI2
[    21.250] (II) LoadModule: "glx"
[    21.439] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.271] (II) Module glx: vendor="X.Org Foundation"
[    22.271]     compiled for 1.15.1, module version = 1.0.0
[    22.271]     ABI class: X.Org Server Extension, version 8.0
[    22.271] (==) AIGLX enabled
[    22.271] Loading extension GLX
[    22.271] (==) Matched nvidia as autoconfigured driver 0
[    22.272] (==) Matched nouveau as autoconfigured driver 1
[    22.272] (==) Matched nvidia as autoconfigured driver 2
[    22.272] (==) Matched nouveau as autoconfigured driver 3
[    22.272] (==) Matched modesetting as autoconfigured driver 4
[    22.272] (==) Matched fbdev as autoconfigured driver 5
[    22.272] (==) Assigned the driver to the xf86ConfigLayout
[    22.272] (II) LoadModule: "nvidia"
[    22.285] (WW) Warning, couldn't open module nvidia
[    22.285] (II) UnloadModule: "nvidia"
[    22.285] (II) Unloading nvidia
[    22.286] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    22.286] (II) LoadModule: "nouveau"
[    22.286] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.294] (II) Module nouveau: vendor="X.Org Foundation"
[    22.294]     compiled for 1.15.0, module version = 1.0.10
[    22.294]     Module class: X.Org Video Driver
[    22.294]     ABI class: X.Org Video Driver, version 15.0
[    22.294] (II) LoadModule: "modesetting"
[    22.295] (WW) Warning, couldn't open module modesetting
[    22.295] (II) UnloadModule: "modesetting"
[    22.295] (II) Unloading modesetting
[    22.295] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    22.296] (II) LoadModule: "fbdev"
[    22.296] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.297] (II) Module fbdev: vendor="X.Org Foundation"
[    22.297]     compiled for 1.15.0, module version = 0.4.4
[    22.297]     Module class: X.Org Video Driver
[    22.297]     ABI class: X.Org Video Driver, version 15.0
[    22.297] (==) Matched nvidia as autoconfigured driver 0
[    22.297] (==) Matched nouveau as autoconfigured driver 1
[    22.297] (==) Matched nvidia as autoconfigured driver 2
[    22.297] (==) Matched nouveau as autoconfigured driver 3
[    22.297] (==) Matched modesetting as autoconfigured driver 4
[    22.297] (==) Matched fbdev as autoconfigured driver 5
[    22.297] (==) Assigned the driver to the xf86ConfigLayout
[    22.297] (II) LoadModule: "nvidia"
[    22.298] (WW) Warning, couldn't open module nvidia
[    22.298] (II) UnloadModule: "nvidia"
[    22.299] (II) Unloading nvidia
[    22.299] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    22.299] (II) LoadModule: "nouveau"
[    22.299] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.299] (II) Module nouveau: vendor="X.Org Foundation"
[    22.299]     compiled for 1.15.0, module version = 1.0.10
[    22.300]     Module class: X.Org Video Driver
[    22.300]     ABI class: X.Org Video Driver, version 15.0
[    22.300] (II) UnloadModule: "nouveau"
[    22.300] (II) Unloading nouveau
[    22.300] (II) Failed to load module "nouveau" (already loaded, 0)
[    22.300] (II) LoadModule: "modesetting"
[    22.301] (WW) Warning, couldn't open module modesetting
[    22.301] (II) UnloadModule: "modesetting"
[    22.301] (II) Unloading modesetting
[    22.301] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    22.301] (II) LoadModule: "fbdev"
[    22.302] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.302] (II) Module fbdev: vendor="X.Org Foundation"
[    22.302]     compiled for 1.15.0, module version = 0.4.4
[    22.302]     Module class: X.Org Video Driver
[    22.302]     ABI class: X.Org Video Driver, version 15.0
[    22.302] (II) UnloadModule: "fbdev"
[    22.302] (II) Unloading fbdev
[    22.302] (II) Failed to load module "fbdev" (already loaded, 0)
[    22.303] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    22.303] (II) NOUVEAU driver for NVIDIA chipset families :
[    22.303]     RIVA TNT        (NV04)
[    22.303]     RIVA TNT2       (NV05)
[    22.303]     GeForce 256     (NV10)
[    22.303]     GeForce 2       (NV11, NV15)
[    22.303]     GeForce 4MX     (NV17, NV18)
[    22.303]     GeForce 3       (NV20)
[    22.304]     GeForce 4Ti     (NV25, NV28)
[    22.304]     GeForce FX      (NV3x)
[    22.304]     GeForce 6       (NV4x)
[    22.304]     GeForce 7       (G7x)
[    22.304]     GeForce 8       (G8x)
[    22.304]     GeForce GTX 200 (NVA0)
[    22.304]     GeForce GTX 400 (NVC0)
[    22.304] (II) FBDEV: driver for framebuffer: fbdev
[    22.304] (++) using VT number 7

[    22.305] (II) [drm] nouveau interface version: 1.1.2
[    22.305] (WW) Falling back to old probe method for fbdev
[    22.305] (II) Loading sub module "fbdevhw"
[    22.305] (II) LoadModule: "fbdevhw"
[    22.305] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.305] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.305]     compiled for 1.15.1, module version = 0.0.2
[    22.305]     ABI class: X.Org Video Driver, version 15.0
[    22.305] (II) Loading sub module "dri2"
[    22.305] (II) LoadModule: "dri2"
[    22.305] (II) Module "dri2" already built-in
[    22.306] (--) NOUVEAU(0): Chipset: "NVIDIA NV43"
[    22.306] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    22.306] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    22.306] (==) NOUVEAU(0): RGB weight 888
[    22.306] (==) NOUVEAU(0): Default visual is TrueColor
[    22.306] (==) NOUVEAU(0): Using HW cursor
[    22.306] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[    22.306] (==) NOUVEAU(0): Page flipping enabled
[    22.306] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[    22.337] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[    22.396] (II) NOUVEAU(0): Output DVI-I-2 has no monitor section
[    22.459] (II) NOUVEAU(0): EDID for output DVI-I-1
[    22.459] (II) NOUVEAU(0): Manufacturer: DEL  Model: e009  Serial#: 827736396
[    22.459] (II) NOUVEAU(0): Year: 2005  Week: 25
[    22.459] (II) NOUVEAU(0): EDID Version: 1.3
[    22.459] (II) NOUVEAU(0): Digital Display Input
[    22.459] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
[    22.459] (II) NOUVEAU(0): Gamma: 2.20
[    22.459] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
[    22.459] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    22.460] (II) NOUVEAU(0): First detailed timing is preferred mode
[    22.460] (II) NOUVEAU(0): redX: 0.637 redY: 0.340   greenX: 0.297 greenY: 0.610
[    22.460] (II) NOUVEAU(0): blueX: 0.146 blueY: 0.071   whiteX: 0.313 whiteY: 0.329
[    22.460] (II) NOUVEAU(0): Supported established timings:
[    22.460] (II) NOUVEAU(0): 720x400@70Hz
[    22.460] (II) NOUVEAU(0): 640x480@60Hz
[    22.460] (II) NOUVEAU(0): 640x480@75Hz
[    22.460] (II) NOUVEAU(0): 800x600@60Hz
[    22.460] (II) NOUVEAU(0): 800x600@75Hz
[    22.460] (II) NOUVEAU(0): 1024x768@60Hz
[    22.460] (II) NOUVEAU(0): 1024x768@75Hz
[    22.460] (II) NOUVEAU(0): 1280x1024@75Hz
[    22.460] (II) NOUVEAU(0): Manufacturer's mask: 0
[    22.460] (II) NOUVEAU(0): Supported standard timings:
[    22.460] (II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    22.460] (II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    22.460] (II) NOUVEAU(0): Supported detailed timing:
[    22.460] (II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
[    22.460] (II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    22.460] (II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    22.461] (II) NOUVEAU(0): Serial No: T613056M1VAL
[    22.461] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    22.461] (II) NOUVEAU(0): Monitor name: DELL 2005FPW
[    22.461] (II) NOUVEAU(0): EDID (in hex):
[    22.461] (II) NOUVEAU(0):     00ffffffffffff0010ac09e04c415631
[    22.461] (II) NOUVEAU(0):     190f0103ee2b1b78ea0195a3574c9c25
[    22.461] (II) NOUVEAU(0):     125054a54b008180714f010101010101
[    22.461] (II) NOUVEAU(0):     0101010101017c2e90a0601a1e403020
[    22.461] (II) NOUVEAU(0):     3600b20e1100001a000000ff00543631
[    22.461] (II) NOUVEAU(0):     333035364d3156414c0a000000fd0038
[    22.461] (II) NOUVEAU(0):     4b1e530e000a202020202020000000fc
[    22.461] (II) NOUVEAU(0):     0044454c4c20323030354650570a00a1
[    22.461] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[    22.461] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    22.461] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    22.461] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.461] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    22.461] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    22.461] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.462] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    22.462] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.462] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    22.462] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.462] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    22.520] (II) NOUVEAU(0): EDID for output DVI-I-2
[    22.520] (II) NOUVEAU(0): Output DVI-I-1 connected
[    22.520] (II) NOUVEAU(0): Output DVI-I-2 disconnected
[    22.520] (II) NOUVEAU(0): Using exact sizes for initial modes
[    22.520] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1680x1050
[    22.520] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.520] (--) NOUVEAU(0): Virtual size is 1680x1050 (pitch 0)
[    22.520] (**) NOUVEAU(0):  Driver mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
[    22.520] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    22.520] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[    22.520] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    22.520] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[    22.520] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.520] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[    22.520] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    22.520] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[    22.520] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    22.521] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    22.521] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.521] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    22.521] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    22.521] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    22.521] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.521] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[    22.521] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    22.521] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    22.521] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.521] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[    22.521] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    22.521] (==) NOUVEAU(0): DPI set to (96, 96)
[    22.521] (II) Loading sub module "fb"
[    22.521] (II) LoadModule: "fb"
[    22.522] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.529] (II) Module fb: vendor="X.Org Foundation"
[    22.529]     compiled for 1.15.1, module version = 1.0.0
[    22.529]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.529] (II) Loading sub module "exa"
[    22.529] (II) LoadModule: "exa"
[    22.530] (II) Loading /usr/lib/xorg/modules/libexa.so
[    22.543] (II) Module exa: vendor="X.Org Foundation"
[    22.543]     compiled for 1.15.1, module version = 2.6.0
[    22.543]     ABI class: X.Org Video Driver, version 15.0
[    22.543] (II) Loading sub module "shadowfb"
[    22.543] (II) LoadModule: "shadowfb"
[    22.544] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    22.573] (II) Module shadowfb: vendor="X.Org Foundation"
[    22.573]     compiled for 1.15.1, module version = 1.0.0
[    22.573]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.573] (II) UnloadModule: "fbdev"
[    22.573] (II) Unloading fbdev
[    22.574] (II) UnloadSubModule: "fbdevhw"
[    22.574] (II) Unloading fbdevhw
[    22.574] (--) Depth 24 pixmap format is 32 bpp
[    22.575] (II) NOUVEAU(0): Opened GPU channel 0
[    22.582] (II) NOUVEAU(0): [DRI2] Setup complete
[    22.582] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    22.582] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[    22.585] (II) EXA(0): Driver allocated offscreen pixmaps
[    22.585] (II) EXA(0): Driver registered support for the following operations:
[    22.585] (II)         Solid
[    22.585] (II)         Copy
[    22.586] (II)         Composite (RENDER acceleration)
[    22.586] (II)         UploadToScreen
[    22.586] (II)         DownloadFromScreen
[    22.586] (==) NOUVEAU(0): Backing store enabled
[    22.586] (==) NOUVEAU(0): Silken mouse enabled
[    22.587] (II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
[    22.587] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    22.587] (==) NOUVEAU(0): DPMS enabled
[    22.587] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.588] (--) RandR disabled
[    22.615] (II) SELinux: Disabled on system
[    22.906] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    22.906] (II) AIGLX: enabled GLX_ARB_create_context
[    22.906] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    22.906] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    22.906] (II) AIGLX: enabled GLX_INTEL_swap_event
[    22.906] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    22.906] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    22.906] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    22.906] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    22.907] (II) AIGLX: Loaded and initialized nouveau
[    22.907] (II) GLX: Initialized DRI2 GL provider for screen 0
[    22.913] (II) NOUVEAU(0): NVEnterVT is called.
[    22.913] (II) NOUVEAU(0): Setting screen physical size to 444 x 277
[    22.913] resize called 1680 1050
[    23.106] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.128] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:0b.0/0000:0a:00.0/drm/card0
[    23.128] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    23.130] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/event2)
[    23.131] (**) PIXART USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    23.131] (II) LoadModule: "evdev"
[    23.131] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.241] (II) Module evdev: vendor="X.Org Foundation"
[    23.241]     compiled for 1.15.0, module version = 2.8.2
[    23.241]     Module class: X.Org XInput Driver
[    23.241]     ABI class: X.Org XInput driver, version 20.0
[    23.241] (II) Using input driver 'evdev' for 'PIXART USB OPTICAL MOUSE'
[    23.241] (**) PIXART USB OPTICAL MOUSE: always reports core events
[    23.241] (**) evdev: PIXART USB OPTICAL MOUSE: Device: "/dev/input/event2"
[    23.242] (--) evdev: PIXART USB OPTICAL MOUSE: Vendor 0x93a Product 0x2510
[    23.242] (--) evdev: PIXART USB OPTICAL MOUSE: Found 3 mouse buttons
[    23.242] (--) evdev: PIXART USB OPTICAL MOUSE: Found scroll wheel(s)
[    23.242] (--) evdev: PIXART USB OPTICAL MOUSE: Found relative axes
[    23.242] (--) evdev: PIXART USB OPTICAL MOUSE: Found x and y relative axes
[    23.242] (II) evdev: PIXART USB OPTICAL MOUSE: Configuring as mouse
[    23.242] (II) evdev: PIXART USB OPTICAL MOUSE: Adding scrollwheel support
[    23.242] (**) evdev: PIXART USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    23.242] (**) evdev: PIXART USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.242] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input2/event2"
[    23.242] (II) XINPUT: Adding extended input device "PIXART USB OPTICAL MOUSE" (type: MOUSE, id 6)
[    23.242] (II) evdev: PIXART USB OPTICAL MOUSE: initialized for relative axes.
[    23.242] (**) PIXART USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    23.242] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration profile 0
[    23.242] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    23.242] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    23.243] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/mouse1)
[    23.243] (II) No input driver specified, ignoring this device.
[    23.243] (II) This device may have been added with another device file.
[    23.244] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event3)
[    23.244] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.244] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    23.244] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    23.244] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event3"
[    23.244] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x20b
[    23.244] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    23.244] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    23.244] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input3/event3"
[    23.244] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 7)
[    23.244] (**) Option "xkb_rules" "evdev"
[    23.244] (**) Option "xkb_model" "applealu_iso"
[    23.245] (**) Option "xkb_layout" "us"
[    23.259] (II) XKB: reuse xkmfile /var/lib/xkb/server-028D4789F599EF7F578C26455F70CBDC81D256F1.xkm
[    23.309] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event4)
[    23.309] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.309] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    23.309] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    23.309] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event4"
[    23.309] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x20b
[    23.309] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    23.309] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    23.309] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.3/2-2.3:1.1/input/input4/event4"
[    23.309] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 8)
[    23.309] (**) Option "xkb_rules" "evdev"
[    23.310] (**) Option "xkb_model" "applealu_iso"
[    23.310] (**) Option "xkb_layout" "us"
[    23.314] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event5)
[    23.314] (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
[    23.314] (II) Using input driver 'evdev' for 'Macintosh mouse button emulation'
[    23.314] (**) Macintosh mouse button emulation: always reports core events
[    23.314] (**) evdev: Macintosh mouse button emulation: Device: "/dev/input/event5"
[    23.314] (--) evdev: Macintosh mouse button emulation: Vendor 0x1 Product 0x1
[    23.314] (--) evdev: Macintosh mouse button emulation: Found 3 mouse buttons
[    23.314] (--) evdev: Macintosh mouse button emulation: Found relative axes
[    23.314] (--) evdev: Macintosh mouse button emulation: Found x and y relative axes
[    23.314] (II) evdev: Macintosh mouse button emulation: Configuring as mouse
[    23.314] (**) evdev: Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    23.314] (**) evdev: Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.314] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    23.314] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE, id 9)
[    23.314] (II) evdev: Macintosh mouse button emulation: initialized for relative axes.
[    23.314] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    23.314] (**) Macintosh mouse button emulation: (accel) acceleration profile 0
[    23.314] (**) Macintosh mouse button emulation: (accel) acceleration factor: 2.000
[    23.314] (**) Macintosh mouse button emulation: (accel) acceleration threshold: 4
[    23.315] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse2)
[    23.315] (II) No input driver specified, ignoring this device.
[    23.315] (II) This device may have been added with another device file.
[    37.150] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[    37.150] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    37.150] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    37.150] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    37.150] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    37.150] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    37.150] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    37.150] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.150] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    37.150] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    37.150] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    37.150] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    37.150] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    37.150] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    37.150] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    37.275] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[    37.275] (II) NOUVEAU(0): Using hsync ranges from config file
[    37.275] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    37.275] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    37.275] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    37.275] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    37.275] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    37.275] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.275] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    37.275] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    37.275] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    37.275] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    37.275] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    37.275] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    37.275] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    37.456] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[    37.456] (II) NOUVEAU(0): Using hsync ranges from config file
[    37.456] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    37.456] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    37.456] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    37.456] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    37.456] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    37.456] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.456] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    37.456] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    37.456] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    37.456] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    37.456] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    37.456] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    37.456] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    37.578] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[    37.578] (II) NOUVEAU(0): Using hsync ranges from config file
[    37.578] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    37.578] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    37.578] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    37.578] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    37.578] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    37.578] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.578] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    37.578] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    37.578] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    37.578] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    37.578] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    37.579] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    37.579] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    39.695] (II) NOUVEAU(0): EDID vendor "DEL", prod id 57353
[    39.695] (II) NOUVEAU(0): Using hsync ranges from config file
[    39.695] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    39.695] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    39.695] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    39.695] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    39.695] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    39.695] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    39.695] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    39.695] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    39.695] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    39.695] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    39.695] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    39.695] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    39.695] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
```

Well at least we tried. Worst case scenario I'll have to disable 2D acceleration.

---

### Post by rsavage on 2015-09-15
I'm confused.... did you have the freezing problem with the debian kernel? If you didn't then that is something to look at.

You could try turning off hardware cursor.

I suggest you also try and talk to a nouveau dev on IRC.

Nv packages are on a thread I started the other day.

And from the xorg.0.log it looks like you should have 3d?

---

### Post by saberblaze on 2015-09-16
No, there were no freezing problems with the Debian kernel, however it wasn't used too much until I switched back to the Ubuntu kernel. It took quite a while for graphical glitches to manifest themselves, so perhaps the Debian kernel would have showed problems somewhere down the line as well. Using framebuffer=y just seemed to lower the chances of it happening significantly with Ubuntu kernel though it could all be pure chance. Although, again the Debian kernel breaks the wifi hotspot and may have other unforeseen consequences.

Disabling hardware cursor sounds like a good idea... I'm assuming it's hardware acceleration of just the mouse cursor? Pretty much when graphical issues occur, it always starts with the mouse cursor. I tried restarting the X Server using ht ctr-alt-backspace sequence and the screen goes black and the monitor shows no signal, although everything else is still running fine in the background, such as wifi etc. I'm assuming the kernel parameter is nouveau.hwcursor=0?

As far as 3D acceleration, no, there's none, I believe it's not supported yet in nouveau to begin with, but running glxinfo shows there's no 3D. Just checked out the other thread, I might try the nv driver later on, from what I understand it used to work fine in older Ubuntu releases, I'm assuming without extra parameters? It might not be for some time since the Mac is low priority now but it's good to give feedback for potential users.

---

### Post by Saml01 on 2015-09-18
Hello. I just joined to say that I have followed the instructions in this thread and have been able to get a working GUI on a 2005 Imac G5 running Lubuntu 14.04.

The only thing I would mention is that I had a hard time including nouveau.config=NvMSI=0 in yaboot. After much reading I learned that the parameter has to be added like this append="nouveau.config=NvMSI=0" under the vmlinux section. If someone has access to update the FAQ, this could potentially be useful to more people.

Thanks rsavage and saberblaze.

---

### Post by rsavage on 2015-09-19
I think you turn off hwcursor in the xorg.conf.  If the debian kernel works without a freeze then it should be possible to make the ubuntu kernel work without a freeze, for example by compiling the newer nouveau module....

@Saml01  I'm not really sure what you want changing in the FAQ.  There is already a section on making yaboot parameters permanent?

---

### Post by Saml01 on 2015-09-19
> **rsavage said:**
> I think you turn off hwcursor in the xorg.conf.  If the debian kernel works without a freeze then it should be possible to make the ubuntu kernel work without a freeze, for example by compiling the newer nouveau module....

@Saml01  I'm not really sure what you want changing in the FAQ.  There is already a section on making yaboot parameters permanent?

Just to add that the parameter its self has to be in an append=" " string. If you just enter it as written it will error out on boot.

Btw. Been using the computer on and off the last 24 hours and hasnt crashed once.

Only thing I noticed is that if I leave it unattended it brings me to a lock screen and then I need to enter my user password 3 times before it lets me back to the desktop. Each time I enter the PW it crashes briefly to console and then back to the login screen. When its briefly on the console it complains about nouveau drm clock...something.

---

### Post by rsavage on 2015-09-20
I must be being thick or summat, but doesn't it say that already?

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F)

---

### Post by Saml01 on 2015-09-21
> **rsavage said:**
> I must be being thick or summat, but doesn't it say that already?

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F)

I sincerely apologize. I meant to say that the extra information should be added to the power ppc known issues page for Trusty.

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by rsavage on 2015-09-21
No problem.  I've updated both the Known Issues and FAQ, see what you think.

---

### Post by Saml01 on 2015-09-21
Awesome. Also turns people onto the FAQ if they had not seen it before.

---

### Post by saberblaze on 2015-10-11
> **rsavage said:**
> I think you turn off hwcursor in the xorg.conf.  If the debian kernel works without a freeze then it should be possible to make the ubuntu kernel work without a freeze, for example by compiling the newer nouveau module....

Apologies for not responding earlier. It's my understanding that you have to manually create a xorg.conf in newer distros including Ubuntu correct? I assumed a boot parameter would work using the same boot parameter conventions but I could be wrong. As far as the Mac, I haven't had a chance to tinker with it further however there have not been any new reported graphical glitches, though again it's not used intensively.  Just one unrelated sound bug that was fixed by logging out. I updated the known issues page with a caveat that there might still be occasional glitches, depending on individual hardware etc ymmv.

It's my understanding that to use the nv driver you have to downgrade xorg, correct?

---

### Post by andy.ody on 2015-11-04
Apologies if this is not thought to be relevant, but Ive been struggling with this for a bit, and still have a way to go I think.

I have a few G5 Power Macs, and I've been attempting to install on a dual 2.3GHz model with an NVIDIA 6600.

I could not get the machine to boot from DVD and struggled trying to install from the mini ISO via the Open Firmware command line.

I later checked the DVD drive on another machine and found the drive itself could not read the DVD, so swapped it out for another model of DVD drive, and problem solved

Now able to boot from the DVD by holding the Option key and selecting the DVD that now shows up.

The drive that did not work was an Apple supplied Pioneer DVR-110DBK. Came with firmware 1.37, but even flashing to latest 1.41 it still does not recognise my Sony DVD's.

The drive that did work was an Apple supplied Hitachi-LG Data Storage Inc drive. Can't find the model number.

Hope that helps some of you.

Andy

---

### Post by andy.ody on 2015-11-05
So,

I'm hoping for some help if I can with my dual core G5+NVIDIA 6600

I've managed to get a working install of Lubuntu 14.04.03 from the Live ISO, and it works if I use the 

[COLOR=#333333][FONT=Ubuntu Beta]*nouveau.noaccel=1* 

at the boot page whilst loading. Without this the install always give graphical corruption and I have to drop into a TTY terminal (if it lets me) to reboot.

So, I figured I'd try the 2D fix, and edited /etc/yaboot.conf to

append="quiet splash nouveau.config=NvMSI=0"

and then created a file */etc/initramfs-tools/conf.d/splash* and added
[/FONT][/COLOR][I]
FRAMEBUFFER=y[/I][COLOR=#333333][FONT=Ubuntu Beta]
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]
I then updated both with

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]*sudo ybin -v* 
[I]
sudo update-initramfs -u

and rebooted.

Still got graphical corruption, so guessing I've not got this right.

Absolute Linux noob, here, so apologies if this is glaringly obvious.

kind regards

Andy[/I][/FONT][/COLOR]

---

### Post by rsavage on 2015-11-05
> **andy.ody said:**
> [COLOR=#333333][FONT=Ubuntu Beta]

So, I figured I'd try the 2D fix, and edited /etc/yaboot.conf to

append="quiet splash nouveau.config=NvMSI=0"

[/FONT][/COLOR]

Did you put it on the right append line?  There are usually two in the file.

---

