---
title: "&quot;do-release-upgrade&quot; &quot;fails to fetch&quot; trying to upgrade Xu12.04 -14.04 on iMac 800?"
date: 2017-09-02
forum: Apple Hardware Users
---

### Post by este.el.paz on 2017-09-02
Folks:

After a couple of years of sitting on the floor due to relentless "kernel panics" I tried to boot the olde G4 iMac 800 . . . and, it ran.  Looks like the reason for the "kernel panics" on OSX side, and "system crash" on the Xu 12.04 side is that the HD is "pre-failure" . . . .  So, I did a fresh install of OSX 10.4 and that is "OK" . . . on the Xu side, I couldn't find the boot params that got me passed the green-black screen . . . and after some trying I was able to get the 12.04 system "upgraded" to as far as it will go.

Problem is that the 12.04 browsers aren't up to date . . . besides taking a looonnnngggg time to launch the app . . . it takes a loooonnnngggg time to get into a webmail site . . . .  I fiddled with a number of lu & U-Mate PPC 14 & 16 options . . . mostly leading to green-black or low resolution screen.  I'm thinking that whatever choice I would make would have to be installed, and then the usual routine of finding the driver for video, and setting up xorg.conf file . . . .  Since the HD is in the process of failing I didn't want to waste time going through the fresh install process, so I tried "Software Updater" to see if it would upgrade itself via GUI . . . gambling that the "nv" driver and the xorg.conf file that are there would be preserved . . . or, if not . . . something would perhaps be "learned."

But, from the Xubuntu base install that method "errored" out . . . ```
"problem during update. this is usually due to some network problem . . ."  W. Failed to fetch http//ports.ubuntu.com/ubuntu-ports/dists/trusty/release.  Unable to find expected entry-partner/binary-powerpc/Packages   in release file (wrong sources.list entry or malformed file)

E.  Some index files failed to download they have been ignored or old ones are used instead.
```

Reading another thread here where abtabt mentions that using Lubuntu with nvidia driver is the only choice after 14.04, I remembered that I had an LXDE DE option, so I rebooted in LXDE and tried again . . . same result.  Then, while messing with the console it showed "9 updates" available . . . so I ran "dist-upgrade" . . . and the console said "put the Lubuntu 14.04 CD/DVD in the drive and hit enter"  ????  so, I did that and it ran a bunch of "update" lines, then started showing "trusty" sources . . . but along with that was "Ign CD/DVD . . . so, I figured it wasn't going to access anything from the DVD . . . and, again the upgrade errored out.  I did try to boot a Lu 16.04 DVD using some of abtabt's boot params added to what I was doing "live nouveau.modeset=0 nvidfb mode_option=1024x768-16" . . . whereas for the other DVD OSs I was using . . . 1024x768-32@60 . . . and the "16" got to a low resolution display with double images and splashy colors, but I could read what I was clicking on, whereas before often I couldn't.

I'd like to be able to use the GUI upgrade if possible to avoid the time messing with the drivers/xorg.conf . . . is this "failure to fetch" due to something like the dropping of support for PPC, or the PPC ports aren't being maintained or cleansed on a regular basis?  On the last extant PPC computer other than the iMac that I have, an iBook G4 running Lu 16.04 via 933 Mhz cpu and 646MB RAM I often see a few "error" "failed to fetch" lines on the update/upgrade via terminal . . . I'm wondering if the ability to "upgrade" for PPC units has been . . . severed?  slashed and burned?  The 12.04 Updater still "believes" that it can do what it needs to do, but the upstream connections are gone?

TIA

e.e.p.

---

### Post by abtabt on 2017-09-03
move to 16.04 lubuntu 
and follow [https://ubuntuforums.org/showthread.php?t=2367523&](https://ubuntuforums.org/showthread.php?t=2367523&)

---

### Post by este.el.paz on 2017-09-03
> **abtabt said:**
> move to 16.04 lubuntu 
and follow [https://ubuntuforums.org/showthread.php?t=2367523&](https://ubuntuforums.org/showthread.php?t=2367523&)

@abtabt:

Thanks for the reply . . . I did see that linked thread, recommending the OP to also "move to Lubuntu 16.04" and your suggestions about the driver.  Curiously the image you linked shows "Ubuntu-Mate" as the installed system . . . I have U-MATE installed on my now "temporarily" defunct PowerMac, but that machine has a faster cpu and **twice** the RAM than that of my now "revived" iMac 800's 1 GB of RAM . . . .  It did seem that the LXDE session in 12.04 was able to "do stuff" rather than having the cpu "max out" into catatonia of non-response that seems to hit the Xubuntu side, especially on the browser.  Even in 10.4 the TFF browser seems to "freeze" . . . due to the high demand placed on the lowly 800 mHz cpu.

So, as we have played with ways to get linux installed on the iMac for what is now possibly seven years going back to the mintppc days of yore??  The question of this post was looking for some insight into the why of the "fail to fetch" using the GUI Software Updater and using console commands, both initiate the process, get a bunch of files, and then . . . "fail to fetch" . . . ???  

I was hoping to get from 12 to 14 and then to 16 . . . "the easy way" . . . using the GUI approach.  Knowing that the HD will likely "die" in the nearing future and probably was responsible for the many kernel panics starting from three or four years back, I didn't want to go through the fresh install and xorg.conf and driver nonsense to get the low spec machine running 16.04, to then find the same, "The system has crashed now or recently" . . . as I get with each boot of the machine.  If I get to replacing the HD at some point, just for the "education" I would then see the value of the fresh install, in the meanwhile I'm wondering if there is a way to get the upgrade to "successfully fetch" the files needed to get to 14.04, and then try for 16.04 using the xorg.conf file that is installed now?

e.e.p

---

