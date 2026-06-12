---
title: "nehalem based mac pro"
date: 2009-03-29
forum: Apple Hardware Users
---

### Post by bluecitabria on 2009-03-29
i have a new nehalem (core i7) based mac pro (4,1?) and am having some difficulties. am wondering whether anyone has experienced similar and if there are proposed solutions:
1)video anomolies on the console. console only works correctly when i set a vga mode for the vesa fb. otherwise it seems to just scroll back the contents of its buffer until i issue some keystroke that returns “command not found”
2)no accelerated 3d graphics on the nvidia GeForce GT 120 (the drivers install and the nvidia settings app reports a 9500GT) glxgears reports almost 8000fps under OSX and a little better than 2000fps under linux.
3)strange flashes and spots when starting X.
4)no sound. the modules load but there is no output via either the headphone jack or the read jack.
when i try the options snd_hda_intel=”macpro” the drivers fail to load.
5)no ethernet. i did download and compile the “latest” drivers from the intel site.
6)CD burning doesn't work. the drive just starts spinning and doesn't stop. whatever program i try issues and i/o error.

as far as configuration goes, i made a small OSX partion. installed OSX into it. repartioned with parted.  booted the refit non-OSX cd and synced the partitions. installed any number of distos. installed grub on the linux partition. each disto has an initrd with what appears to be every available module.

i see that there is an upcomming patch for the e1000 PCI ID [(0x10F6) as a 82574 NIC]. and it is reported to work. i haven't fully investigated the sound options.

 i'd be deeply grateful if anyone can shed some additional light on any of this stuff. a sample kernel .config would also be very helpful.

thanks for any help.

---

### Post by runexe on 2009-03-31
> **bluecitabria said:**
> i have a new nehalem (core i7) based mac pro (4,1?) and am having some difficulties. am wondering whether anyone has experienced similar and if there are proposed solutions:
1)video anomolies on the console. console only works correctly when i set a vga mode for the vesa fb. otherwise it seems to just scroll back the contents of its buffer until i issue some keystroke that returns “command not found”
2)no accelerated 3d graphics on the nvidia GeForce GT 120 (the drivers install and the nvidia settings app reports a 9500GT) glxgears reports almost 8000fps under OSX and a little better than 2000fps under linux.
3)strange flashes and spots when starting X.
4)no sound. the modules load but there is no output via either the headphone jack or the read jack.
when i try the options snd_hda_intel=”macpro” the drivers fail to load.
5)no ethernet. i did download and compile the “latest” drivers from the intel site.
6)CD burning doesn't work. the drive just starts spinning and doesn't stop. whatever program i try issues and i/o error.



I had the same vga console issues - I similarly found that using a vesa mode (i.e. setting vga=<mode> where mode was something like 0x318 or similar) in the grub menu.lst worked great. I haven't investigated the underlying weirdness (scrolling, etc.) further since I got it working.
I ran in the ethernet issues right away as well - if you are brave and don't mind patching and compiling a new kernel module, I posted my solution at [http://ubuntuforums.org/showpost.php?p=6966791&postcount=4]("http://ubuntuforums.org/showpost.php?p=6966791&postcount=4"). I can investigate making a deb that others can share, but while I can deal with source code, I haven't dealt with making a .deb (much less a kernel module .deb) in a long time. My kernel .config is the default Jaunty server: I'm running 2.6.28-11-server #38 Ubuntu right now.

As far as X goes - I'm not currently really dealing with graphical applications, so most of my work on the machine is either on the console, or via SSH right now. I did get X working though - and it loads using the nv module (i.e. I'm not using proprietary drivers). I haven't benchmarked anything, so I don't know what kinds of speeds thing like OpenGL get.

I also haven't tried sound - although I see the intel hda module is loaded, I don't think I have sound working either. Similarly, haven't tried CD burning yet.

---

### Post by bluecitabria on 2009-03-31
> **runexe said:**
> I had the same vga console issues - I similarly found that using a vesa mode (i.e. setting vga=<mode> where mode was something like 0x318 or similar) in the grub menu.lst worked great. I haven't investigated the underlying weirdness (scrolling, etc.) further since I got it working.
I ran in the ethernet issues right away as well - if you are brave and don't mind patching and compiling a new kernel module, I posted my solution at [http://ubuntuforums.org/showpost.php?p=6966791&postcount=4]("http://ubuntuforums.org/showpost.php?p=6966791&postcount=4"). I can investigate making a deb that others can share, but while I can deal with source code, I haven't dealt with making a .deb (much less a kernel module .deb) in a long time. My kernel .config is the default Jaunty server: I'm running 2.6.28-11-server #38 Ubuntu right now.

As far as X goes - I'm not currently really dealing with graphical applications, so most of my work on the machine is either on the console, or via SSH right now. I did get X working though - and it loads using the nv module (i.e. I'm not using proprietary drivers). I haven't benchmarked anything, so I don't know what kinds of speeds thing like OpenGL get.

I also haven't tried sound - although I see the intel hda module is loaded, I don't think I have sound working either. Similarly, haven't tried CD burning yet.
i don't have any problem with compiling a custom module for the nic and i'm glad to see that it is working, but i need to solve the sound, video, and the cd burning issues before i decide whether to keep it or not.
it has been back in the box, ready to go back to apple for a few days. i didn't want to unpack it again until i got some sense of whether i'd ever be able to get it to work properly.

i would like to figure out the other stuff, particularly the sound and the cd burning problems.

is it feasible for you to see whether you can burn a cd from the console?

if so, i'll unpack the damn think tomorrow and see if i can get the rest of the stuff to work.

---

### Post by KuroRyuu on 2009-04-01
> **bluecitabria said:**
> 
2)no accelerated 3d graphics on the nvidia GeForce GT 120 (the drivers install and the nvidia settings app reports a 9500GT) glxgears reports almost 8000fps under OSX and a little better than 2000fps under linux.
I don't know about the performance issues, but the GT 120 is just a renamed 9500 GT.
> **bluecitabria said:**
> 
4)no sound. the modules load but there is no output via either the headphone jack or the read jack.
when i try the options snd_hda_intel="macpro" the drivers fail to load.
Try options snd_hda_intel model=macpro

---

### Post by bluecitabria on 2009-04-01
> **KuroRyuu said:**
> I don't know about the performance issues, but the GT 120 is just a renamed 9500 GT.

Try options snd_hda_intel model=macpro
yes, that's what i meant about the sound, which is to say that is what i had in the config for the alsa modules "options snd_hda_intel=macpro" no joy.
on the other hand, i did get the ethernet driver to load (thank you runexe!)
and i seem to have fixed the accelerated 3d driver problem. i disabled the vesa framebuffer in the kernel configuration, compiled the nvidia drivers for my running kernel and now i get a whopping 11,000+ fps from glx gears, which is about 3500fps MORE than i got from osx.
i still have video buffer problems, but less since i disabled the option to use ram for the buffer scrollback. i'm sure there's an option somewhere to get it to disable the video scrollback buffer altogether.
altogether it looks like progress...
i'll issue a final report when i'm finished.

---

### Post by cyberdork33 on 2009-04-02
> **bluecitabria said:**
> now i get a whopping 11,000+ fps from glx gears, which is about 3500fps MORE than i got from osx.
glxgears is really not a good way to compare hardware performance... especially between two completely different Operating Systems.

---

### Post by bluecitabria on 2009-04-02
> **cyberdork33 said:**
> glxgears is really not a good way to compare hardware performance... especially between two completely different Operating Systems.

you know, it is what i had available and it is an okay way to see whether you're getting accellerated 3d or not.

you got any suggestions for the continuing problem with the sound?

---

### Post by cyberdork33 on 2009-04-02
> **bluecitabria said:**
> you know, it is what i had available and it is an okay way to see whether you're getting accellerated 3d or not.It certainly is. I am just saying that you should not rely on that output as an indicator of the performance. It may very well be that things are better in OSX, or that they are completely the same.

> **bluecitabria said:**
> you got any suggestions for the continuing problem with the sound?
it is most likely not supported in alsa yet (new hardware, or new ID, much like the ethernet).

You can run the ALSA information script:
[http://hg.alsa-project.org/alsa/raw-file/tip/alsa-info.sh](http://hg.alsa-project.org/alsa/raw-file/tip/alsa-info.sh)

and post the output in a Bug along with a description of the problem... i.e. nothing works.

---

### Post by bluecitabria on 2009-04-02
> **cyberdork33 said:**
> It certainly is. I am just saying that you should not rely on that output as an indicator of the performance. It may very well be that things are better in OSX, or that they are completely the same.


it is most likely not supported in alsa yet (new hardware, or new ID, much like the ethernet).

You can run the ALSA information script:
[http://hg.alsa-project.org/alsa/raw-file/tip/alsa-info.sh](http://hg.alsa-project.org/alsa/raw-file/tip/alsa-info.sh)

and post the output in a Bug along with a description of the problem... i.e. nothing works.

partial resolution of the sound issue:

works through the rear port if the sound card is set to:
options snd-hda-intel model=imac24 (that might not be the correct sequence)

i've solved the accelerated video issue and the cd burning issue.

i'll provide a custom kernel config for 2.6.29 to anyone who'd like it.

i still have problems with unwanted text scrolling back on the console. i'll post a more complete report when i'm finished testing

---

### Post by cyberdork33 on 2009-04-03
> **bluecitabria said:**
>  i still have problems with unwanted text scrolling back on the console. i'll post a more complete report when i'm finished testing
runexe posted that this was resolved by passing a vga parameter on the kernel line. Did that not work for you?

You should document your findings on the Mac Pro wiki...
[https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

---

### Post by bluecitabria on 2009-04-03
> **cyberdork33 said:**
> runexe posted that this was resolved by passing a vga parameter on the kernel line. Did that not work for you?

You should document your findings on the Mac Pro wiki...
[https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

sure, that gets you a console you can use, but if you load vesafb at boot or compile it into the kernel then it seems that the X nvidia-drivers don't perform as well (by an order of 5). i compiled my last kernel (number 8 so far) with support for only the efi based framebuffer. i'm sure there's a kernel parameter that will stop the unwanted scrollback but i haven't found it yet.

so far i have accelerated X, sound from the rear speaker, CD burning, and network. i'm sending the machine back to apple. life's too short for this.

---

### Post by PabloSau on 2009-04-17
> **runexe said:**
> I had the same vga console issues - I similarly found that using a vesa mode (i.e. setting vga=<mode> where mode was something like 0x318 or similar) in the grub menu.lst worked great. I haven't investigated the underlying weirdness (scrolling, etc.) further since I got it working.
I ran in the ethernet issues right away as well - if you are brave and don't mind patching and compiling a new kernel module, I posted my solution at [http://ubuntuforums.org/showpost.php?p=6966791&postcount=4]("http://ubuntuforums.org/showpost.php?p=6966791&postcount=4"). I can investigate making a deb that others can share, but while I can deal with source code, I haven't dealt with making a .deb (much less a kernel module .deb) in a long time. My kernel .config is the default Jaunty server: I'm running 2.6.28-11-server #38 Ubuntu right now.

As far as X goes - I'm not currently really dealing with graphical applications, so most of my work on the machine is either on the console, or via SSH right now. I did get X working though - and it loads using the nv module (i.e. I'm not using proprietary drivers). I haven't benchmarked anything, so I don't know what kinds of speeds thing like OpenGL get.

I also haven't tried sound - although I see the intel hda module is loaded, I don't think I have sound working either. Similarly, haven't tried CD burning yet.

I'am having problems trying to install Ubuntu Jaunty Server, first I installed Ubuntu amd64 8.10, with no sound and  no ethernet, as
I want to use it as a headless server I don't care about graphics issues, but the ethernet card is for me the main issue. 
I tried without success to patch(following your instructions)  and compile the current 8.10 Ubuntu Kernel.
I've installed 5 1TB HD (one in the second DVD bay) and I'd like to tray the SSD disk to hold the OS and use 6 HD in RAID. Anyone has tried the SSD disk in a Nehalem Mac Pro? It is offered as optional in Xserve. Any help would be appreciated!

---

### Post by cyberdork33 on 2009-04-17
> **PabloSau said:**
> I'am having problems trying to install Ubuntu Jaunty Server, first I installed Ubuntu amd64 8.10, with no sound and  no ethernet, as
I want to use it as a headless server I don't care about graphics issues, but the ethernet card is for me the main issue. 
I tried without success to patch(following your instructions)  and compile the current 8.10 Ubuntu Kernel.
I've installed 5 1TB HD (one in the second DVD bay) and I'd like to tray the SSD disk to hold the OS and use 6 HD in RAID. Anyone has tried the SSD disk in a Nehalem Mac Pro? It is offered as optional in Xserve. Any help would be appreciated!
This is fixed in Jaunty. I'd suggest waiting for it's final release.

---

### Post by nooBuntew on 2009-05-01
Anyone know how to turn off hyper-threading on the Nehalem Mac Pro?

---

### Post by loganj on 2009-05-05
So, what's the current status of Ubuntu on the Nehalem Mac Pro?  Does Intrepid work?  Does Jaunty?  If not, what's broken?

I'm working with a group that needs NVidia's CUDA (among other things) and would like to qualify the Nehalem Mac Pro.  CUDA only supports up to Intrepid at the moment, hence my interest.

Would anyone who has a Nehalem Mac Pro be willing to try the Intrepid live disc on it?

---

### Post by nooBuntew on 2009-05-05
I have installed Ubuntu 8.10 on a disk partition on a Nehalem MacPro.  Much like the other flavors of Linux that I have installed on this machine thus far, I needed to recompile the drivers for the ethernet card ([http://ubuntuforums.org/showthread.php?t=1106385](http://ubuntuforums.org/showthread.php?t=1106385)).  Anything you would like me to try out?

Personally, I would still like to know if anyone knows how to turn off hyperthreading.

---

### Post by cyberdork33 on 2009-05-05
Try adding 'noht' on your kernel line.

---

### Post by loganj on 2009-05-05
Thanks nooBuntew.  Did you need to do anything else, like the vga fix referenced above?  The install go smoothly/normally?

Also, are you booting a 32-bit or 64-bit kernel?  Can you see all of your memory?  (Looks like the 32-bit 8.10 kernel doesn't have PAE enabled.)

Wish I had an answer for you on the hyperthreading.  If I find anything on that I'll certainly report back.  We may want it disabled as well.

---

### Post by bluecitabria on 2009-06-01
well, i did get another mac pro (the first one had a loose screw trapped underneath the system board or whatever apple calls it)
i've had reasonable success with jaunty amd64 and have posted my findings at [https://help.ubuntu.com/community/MacPro]("htts://https://help.ubuntu.com/community/MacPro")
i still have some issues:

1) the sound works from the rear port with "options snd_hda_intel model=imac24" appended to the alsa-base.conf file. evidently requiring the "model=" requirement is considered a bug by the alsa developers and a kind fellow among that group is looking into it.

2) i can't get a vga console of any kind. if i append the bootloader command with vga=xxx the system just reboots. so every time i make a new kernel i have to ssh into the box to reinstall the nvidia drivers, which i install straight from the nvidia package. i couldn't figure out how to adjust the "debian rules" file to enable me to install the ubuntu nvidia-drivers package. does anyone know of an up-to-date, user friendly how-to on this "debian rules" nonsense?

3) when i switched from gnome-based ubuntu to kubuntu i lost the very cool functionality of the cd keyboard button. (anyone know what the people at apple have against that poor, little button on the cd/dvd that opens the tray when you push it?!?!?! the keyboard button is a real pain...)
so, if anyone knows how to get that mac-keyboard functionality in kde please let me know.

i'm on the 6th or 7th reconfiguration of 2.6.30-rc6. if there is anyone who could have a look at the .config and offer suggestions

all in all, i'm very reasonably happy running ubuntu on this box. ubuntu is twice as fast as leopard (though a little slower than gentoo, which has gotten to flaky to use) and infinitely more configurable... i only need osx to run this idiotic music notatation software that i use!

---

### Post by cyberdork33 on 2009-06-01
> **bluecitabria said:**
> 1) the sound works from the rear port with "options snd_hda_intel model=imac24" appended to the alsa-base.conf file. evidently requiring the "model=" requirement is considered a bug by the alsa developers and a kind fellow among that group is looking into it.
Yes there are few bugs filed about it.

> **bluecitabria said:**
> 2) i can't get a vga console of any kind. if i append the bootloader command with vga=xxx the system just reboots. so every time i make a new kernel i have to ssh into the box to reinstall the nvidia drivers, which i install straight from the nvidia package. i couldn't figure out how to adjust the "debian rules" file to enable me to install the ubuntu nvidia-drivers package. does anyone know of an up-to-date, user friendly how-to on this "debian rules" nonsense?
you should only need to remove the "silent" and "quiet" options from the kernel line in grub to get a console. If it still doesn't work, then there is some issue with getting the display initialized for some reason. I am pretty sure that people have got it working when booting via EFI (with grub-efi). There is a thread linked in the FAQ about this.

> **bluecitabria said:**
> 3) when i switched from gnome-based ubuntu to kubuntu i lost the very cool functionality of the cd keyboard button. (anyone know what the people at apple have against that poor, little button on the cd/dvd that opens the tray when you push it?!?!?! the keyboard button is a real pain...)
so, if anyone knows how to get that mac-keyboard functionality in kde please let me know.
Are you just talking about getting the Eject key working, or is there some other function you are referring to? You can try removing the mouseeemu package.

---

### Post by bluecitabria on 2009-06-02
the vga=xxx parameter just causes the machine to reboot
and, yes, i'd like to get the eject key to work in kde the way it did in gnome.

---

### Post by cyberdork33 on 2009-06-02
> **bluecitabria said:**
> the vga=xxx parameter just causes the machine to reboot so don't add the vga parameter...
> **bluecitabria said:**
> and, yes, i'd like to get the eject key to work in kde the way it did in gnome.
did you remove mouseemu?

---

### Post by bluecitabria on 2009-06-02
yes mouseemu is gone

---

### Post by bluecitabria on 2009-06-02
if there is no vga parameter there is no working console. all you get is garbage from the buffer.
when i did this with gentoo id COULD enter vga=xxx and get a working console. when i try it with a kernel compiled "the ubuntu way" any kernel parameter i enter causes the machine to reboot.

---

### Post by cyberdork33 on 2009-06-02
> **bluecitabria said:**
> if there is no vga parameter there is no working console. all you get is garbage from the buffer.
when i did this with gentoo id COULD enter vga=xxx and get a working console. when i try it with a kernel compiled "the ubuntu way" any kernel parameter i enter causes the machine to reboot.
could be the framebuffer driver being used? IDK

If you can compile a kernel the "non-Ubuntu way" and it works, then just do that...

---

### Post by bluecitabria on 2009-06-02
thanks for all of your help

---

### Post by bluecitabria on 2009-06-03
turns out that the problem with the inability to set a console mode had to do with the initrd, which, one doesn't actually need an initrd except for the UUID nonsense in the grub.conf so the answer here would be:
DON'T USE UUID's in grub.conf !!

uuid and labels are all very good for removable drives, and labels are particularly good in fstab for environments in which one wants to just swap one disk for another. but in grub.conf (menu.1st) switching back to good old /dev/sdxn for the internal disk let me dispense with the initrd which enabled a working vga console. now when i build a new kernel (and i have a feeling that there are several more kernels in my future) i'll be able to just drop to a (working!) console, install the nvidia-drivers for the new kernel and be on my way.

it is interesting that the /boot/grub/menu.1st makes the 2nd internal drive (hd0,2) on the root=line, but on the kernel line it is /dev/sdb3. i'd expect hd0 to translate to /dev/sda. so the actual line looks like:
title     title
root      (hd0,2)
kernel    /boot/kernel root=/dev/sdb3

i couldn't find the info on how to build an initrd with specific modules. if there is a document describing this for debian/ubuntu initrd's and someone could point it out, i'll be grateful.

---

### Post by jruths on 2009-06-03
I'm glad to see these posts regarding the nehalem mac pros. I'm new to linux, but in general I'm a pretty competent user (especially when armed with useful posts like these - got the ethernet driver working). I've had major issues with the graphics configuration.  I have two NVIDIA GT 120 cards and I'd love to be able to display on 3-4 screens. I've tried installing the 180 NVIDIA driver through Envy (this usually gets stuck part way through), through the "Hardware Drivers" Administration menu option, and also by downloading the NVIDIA *.run package.  I'm running Ubuntu 9 (Jaunty), the 64bit version.  Have I doomed myself by installing Ubuntu 9, rather than 8?  Each time I try these various methods, I reboot after a "successful" installation and can't get into the X graphics interface - I'm stuck on the terminal (which isn't exactly my strongest area).  I revert back and try a different method.  Is it the dual graphics card?  Has anyone else gotten this configuration working? Thanks for the help.

---

### Post by bluecitabria on 2009-06-03
> **jruths said:**
> I'm glad to see these posts regarding the nehalem mac pros. I'm new to linux, but in general I'm a pretty competent user (especially when armed with useful posts like these - got the ethernet driver working). I've had major issues with the graphics configuration.  I have two NVIDIA GT 120 cards and I'd love to be able to display on 3-4 screens. I've tried installing the 180 NVIDIA driver through Envy (this usually gets stuck part way through), through the "Hardware Drivers" Administration menu option, and also by downloading the NVIDIA *.run package.  I'm running Ubuntu 9 (Jaunty), the 64bit version.  Have I doomed myself by installing Ubuntu 9, rather than 8?  Each time I try these various methods, I reboot after a "successful" installation and can't get into the X graphics interface - I'm stuck on the terminal (which isn't exactly my strongest area).  I revert back and try a different method.  Is it the dual graphics card?  Has anyone else gotten this configuration working? Thanks for the help.

please let us know the actual errors you are getting, which will be more helpful. 

i have nvidia drivers built in a custom kernel in my i7 mac pro. don't bother with all the gui helper tools like the "Hardware Drivers" admin stuff.

if you've got a working console, do the following to build the modules for the kernel you are running

1) let ubuntu re-configure X for the "default" configuration
2) reboot
3) uninstall all nvidia drivers and modules and get rid of envy
4) put the downloaded NVIDIA-Linux-x86_64-180.51-pkg2.run in your home directory (/home/username)
5) install the nvidia-settings tool
6) log out and from the menu screen select "console login"
7) log in on the command line and type "sudo -i" and enter your password
8 ) make the nvidia package executable: chmod 775 NVIDIA-Linux-x86_64-180.51-pkg2.run
9) type ./NVIDIA-Linux-x86_64-180.51-pkg2.run, accept the license and tell it to build you your modules
10) after building your modules, type nvidia-xconfig and tell it to replace your xorg.conf file
11) type reboot

after the reboot you should be able to use the nvidia-settings program to configure your displays.

you need a working console to do this. i you aren't starting with a working console, try adding vga=0x318 to the kernel= line in /boot/grub /menu.1st and get rid of "quiet splash" while at it.

---

### Post by jruths on 2009-06-04
Wow, the vga modification makes the console so much better.  Thanks so much for the reply.  I'm still having trouble, though.  I'm pretty sure I got envy completely uninstalled.  I'm not exactly sure how to get rid of the previous installations of the drivers (I have tried the sequence of going to console, running the NVIDIA....run file and going through the installation).  I think there are remnants of these installations that are lurking somewhere, but the nvidia-uninstall tool doesn't find them.  I seem to install the .run file just fine and then use nvidia-xconfig to configure the xorg.conf file.  But when I reboot, starting up the Display Manager fails and I'm stuck on the console.  I looked at the /var/log/Xorg.0.log file and it finds the two graphics cards (I think):

(!!) More than one possible primary device found
(--) PCI: (0@5:0:0) nVidia Corporation GeForce 9500 GT rev 161, ... , BIOS @ 0x????????/524288
(--) PCI: (0@6:0:0) nVidia Corporation GeForce 9500 GT rev 161, ... , BIOS @ 0x????????/524288

but later it logs:

(II) Primary Device is:
(EE) No devices detected.

Fatal server error:
no screens found

... So I'm not sure exactly what's wrong - the driver or the xorg.conf?  Here is a copy of the pertinent parts of the xorg.conf

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Thanks again for your help.  Any tips would be very appreciated.

---

### Post by jruths on 2009-06-04
A quick update... I added a Busid for the device to distinguish between the graphics cards and now the Xorg.0.log file gets further, but still aborts.  It gets to a part where is logs,

Failed to initialize the NVIDIA kernel module!  Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.

I checked the installation with "nvidia-installer --sanity" and it came back ok.  Thoughts?

---

### Post by bluecitabria on 2009-06-09
> **jruths said:**
> Wow, the vga modification makes the console so much better.  Thanks so much for the reply.  I'm still having trouble, though.  I'm pretty sure I got envy completely uninstalled.  I'm not exactly sure how to get rid of the previous installations of the drivers (I have tried the sequence of going to console, running the NVIDIA....run file and going through the installation).  I think there are remnants of these installations that are lurking somewhere, but the nvidia-uninstall tool doesn't find them.  I seem to install the .run file just fine and then use nvidia-xconfig to configure the xorg.conf file.  But when I reboot, starting up the Display Manager fails and I'm stuck on the console.  I looked at the /var/log/Xorg.0.log file and it finds the two graphics cards (I think):

(!!) More than one possible primary device found
(--) PCI: (0@5:0:0) nVidia Corporation GeForce 9500 GT rev 161, ... , BIOS @ 0x????????/524288
(--) PCI: (0@6:0:0) nVidia Corporation GeForce 9500 GT rev 161, ... , BIOS @ 0x????????/524288

but later it logs:

(II) Primary Device is:
(EE) No devices detected.

Fatal server error:
no screens found

... So I'm not sure exactly what's wrong - the driver or the xorg.conf?  Here is a copy of the pertinent parts of the xorg.conf

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Thanks again for your help.  Any tips would be very appreciated.

i don't know exactly what you have installed from the ubuntu packages. but i got rid of everything execpt "nvida-settings" if you don't know whether you're sure you've gotten rid of everything in a package, the gui way to find out would be to use something like "synaptic" package manager and find the package you want to know about. if you get the properties for a package in the list you can get a list of installed files. just check that those files aren't there. and you'll know how much was de-installed.
if the package is still installed, you can also select "mark for complete removal" in synaptic, itself, but you probably still want to check for stray configuration files and the like.


running the Nvidia-Linux.xxx.xxx package from the console just builds the module for your kernel. in fact you can build it for a non-running kernel, too. the package file that you download from nvidia is "compressed". if you type "NVIDIA-Linux-x86_64-180.51-pkg2.run --help" you'll get an elementary list of options. if you type NVIDIA-Linux-x86_64-180.51-pkg2.run -A --help", you'll get a list of "advanced options". reading these help files can be very useful. 

the nvidia-xconfig program also has elementary and advanced options. the command "nvidia-xconfig -h" will show you the options.

what kernel are you running? how did you patch the kernel for the network drivers? the command lspci -v -v, will print details of the video cards. an example of mine, with the driver running looks like this:
05:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
        Subsystem: Apple Computer Inc. Device 00b3                            
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0                                                                                           
        Interrupt: pin A routed to IRQ 16                                                                    
        Region 0: Memory at 8a000000 (32-bit, non-prefetchable) [size=16M]                                   
        Region 1: Memory at 80000000 (64-bit, prefetchable) [size=128M]                                      
        Region 3: Memory at 88000000 (64-bit, non-prefetchable) [size=32M]                                   
        Region 5: I/O ports at 3000 [size=128]                                                               
        [virtual] Expansion ROM at 8b000000 [disabled] [size=512K]                                           
        Capabilities: <access denied>                                                                        
        Kernel driver in use: nvidia                                                                         
        Kernel modules: nvidia, nvidiafb                               

if you're going to post a lot of output to these threads, it is better to use a "pastebin" and just post the link! you should collect the output from several commands (i see that you already have some of this): lspci -v -v; dmesg; xorg.conf; lsmod; /var/log.xorg.1.log /var/log/xorg.0.log; /var/log/xorg.99.log; it seems to me that in the old days there was xorg.0.log for success and xorg.1.log for errors. now i think xog.99.log may be for errors). anyway you can compare the logs for successful and unsuccessful boots.

this link provides some general info on configuring dual displays with nvidia drivers.
[http://tuxradar.com/content/modify-xorgconf-better-performance]("http://tuxradar.com/content/modify-xorgconf-better-performance")

you can also try booting to just the console with no (x)(g)(k)dm. just tell that service not to automatically start. this will give you a console login, so if X wont start, you can tweek the config and keep screwing around with the configuration files.

again, you should "pastebin" if you have a lot of output.

---

### Post by agb32 on 2009-07-01
Hi,
has anyone any suggestions how I can get ethernet working, without a network connection on the mac?  ie I can't do any apt-get stuff.

Could someone post a working kernel or something online so that I could download, transfer by usb-stick, and then get network access working...

Thanks...

---

