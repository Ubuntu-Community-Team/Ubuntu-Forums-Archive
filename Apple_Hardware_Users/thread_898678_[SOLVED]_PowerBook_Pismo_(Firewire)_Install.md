---
title: "[SOLVED] PowerBook Pismo (Firewire) Install"
date: 2008-08-23
forum: Apple Hardware Users
---

### Post by DGortze380 on 2008-08-23
Just goes to show you, you can never be prepared for everything.

I got my new old Pismo yesturday and have spent i don't know how many hours trying to do this install now. I first tried to use the Ubuntu 7.10 PPC Alternate CD (seemed to be the most stable install based on my research). Installer could not find my CD Drive. Errr. So now it's off to 8.10, froze at finding network hardware. Figured it was a bad disk, wrote a new one as slow as possible, stalled at finding disks.

So unfortunately (don't shoot me), gave up on Ubuntu, decided to go even more basic with a commandline Debian install then add XFCE over it. Install worked fine, got greedy and decided to try Gnome. Gnome crashed the system, neither desktop would work correctly. SO I went for a fresh install... big mistake... I can't get anything to install anymore. No matter what version of what distro with any options I try (video=ofonly (or whatever it is), expert install) it will stall out at some point (seemingly randomly) during the install.

What can I do here?? I just need to get a system installed. Preferably Ubuntu, Debian is fine, rather not venture into any other distro's right now.

---

### Post by gaussian on 2008-08-23
> **DGortze380 said:**
> Just goes to show you, you can never be prepared for everything.

I got my new old Pismo yesturday and have spent i don't know how many hours trying to do this install now. I first tried to use the Ubuntu 7.10 PPC Alternate CD (seemed to be the most stable install based on my research). Installer could not find my CD Drive. Errr. So now it's off to 8.10, froze at finding network hardware. Figured it was a bad disk, wrote a new one as slow as possible, stalled at finding disks.

So unfortunately (don't shoot me), gave up on Ubuntu, decided to go even more basic with a commandline Debian install then add XFCE over it. Install worked fine, got greedy and decided to try Gnome. Gnome crashed the system, neither desktop would work correctly. SO I went for a fresh install... big mistake... I can't get anything to install anymore. No matter what version of what distro with any options I try (video=ofonly (or whatever it is), expert install) it will stall out at some point (seemingly randomly) during the install.

What can I do here?? I just need to get a system installed. Preferably Ubuntu, Debian is fine, rather not venture into any other distro's right now.

Have you tried Feisty (7.04)? I had hard time get Hardy to load up on my Pismo (random lockups during live boot related to cd drive), but Feisty live CD loaded just fine. I installed Feisty and upgraded to Gutsy with zero problems. The only trick was that to get Feisty Live-CD to boot you needed video=ofonly and to get Gutsy to work perfectly (suspend, brightness keys etc) you needed to remove that.

One of these days I will get greedy and try update to Hardy. But I think I'll do a full backup of the disk before that.

---

### Post by DGortze380 on 2008-08-23
> **gaussian said:**
> Have you tried Feisty (7.04)? I had hard time get Hardy to load up on my Pismo (random lockups during live boot related to cd drive), but Feisty live CD loaded just fine. I installed Feisty and upgraded to Gutsy with zero problems. The only trick was that to get Feisty Live-CD to boot you needed video=ofonly and to get Gutsy to work perfectly (suspend, brightness keys etc) you needed to remove that.

One of these days I will get greedy and try update to Hardy. But I think I'll do a full backup of the disk before that.

I had been using alternate CD's. just tried both Hardy and Gusty Live CD's. Gusty was a bust, presumably not finding my CD drive again. Hardy booted with all sorts of funky psychedelic colors, tried it with video=ofonly and X failed. Thinking about trying Fedora at this point, but it's a 7 CD download. Do you happen to have a Feisty ISO? or know where I can find one?

---

### Post by gaussian on 2008-08-23
> **DGortze380 said:**
> I had been using alternate CD's. just tried both Hardy and Gusty Live CD's. Gusty was a bust, presumably not finding my CD drive again. Hardy booted with all sorts of funky psychedelic colors, tried it with video=ofonly and X failed. Thinking about trying Fedora at this point, but it's a 7 CD download. Do you happen to have a Feisty ISO? or know where I can find one?

I used the live-cd from here:
[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

---

### Post by DGortze380 on 2008-08-23
Thank, downloading now. 

What are people successfully running on Pismo's (or similar). I'm bummed that it's been two days trying to get this thing going with only one successful install (which I promptly toasted). Everything I read said 7.10 would work, and if not, at least Debian would.

---

### Post by DGortze380 on 2008-08-23
Bah... 7.04 won't go either! Same weird colors on default boot, same failed X on video=ofonly, error is no screen found. I'm at a loss at this point. Going to try Fedora I guess, unless anyone has any thoughts.

---

### Post by gaussian on 2008-08-24
> **DGortze380 said:**
> Bah... 7.04 won't go either! Same weird colors on default boot, same failed X on video=ofonly, error is no screen found. I'm at a loss at this point. Going to try Fedora I guess, unless anyone has any thoughts.

This brings back memories of my own install. Maybe there was a step to get rid of the weird colors. Try following: boot into Feisty. Wait for X-server to fail to get to command prompt. Do 

```
sudo pkill gdm
```
```
sudo vim /etc/X11/xorg.conf
```
(I don't know if any other editors are available at this stage if you are uncomfortable with vim).

Find the section of xorg.conf stating something like 
Option "UseFBDev" "true"

change that to false and save. Now do 

```
sudo gdm &
```

P.S. If the X failing does not give you command prompt hit alt+ctrl+F1 to get a command prompt. Simularly if sudo gdm does not bring you a graphical environments try alt+ctrl+Funtion key combinations to find it. Let me know if this works.

---

### Post by gaussian on 2008-08-24
One more thing:

When editing xorg.conf, you'll need to add HorizSync and VertRefresh lines to monitor section

```

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

```

---

### Post by DGortze380 on 2008-08-25
> **gaussian said:**
> This brings back memories of my own install. Maybe there was a step to get rid of the weird colors. Try following: boot into Feisty. Wait for X-server to fail to get to command prompt. Do 

```
sudo pkill gdm
```
```
sudo vim /etc/X11/xorg.conf
```
(I don't know if any other editors are available at this stage if you are uncomfortable with vim).

Find the section of xorg.conf stating something like 
Option "UseFBDev" "true"

change that to false and save. Now do 

```
sudo gdm &
```

P.S. If the X failing does not give you command prompt hit alt+ctrl+F1 to get a command prompt. Simularly if sudo gdm does not bring you a graphical environments try alt+ctrl+Funtion key combinations to find it. Let me know if this works.


Ok, so when I boot 7.04 Live normally, I get a normal loading bar, says UBUNTU, colors, resolution are correct. The bar starts loading, the word UBUNTU disappears, it seems to load all the way to the desktop, but I get hundreds of fast moving colored horizontal lines going up the screen. I tried the xorg changes above (from both posts), saved, restarted gdm, nothing happened, restarted X and got the same error, X failed "No Screens Found". I can get more terminal output if it will help.

I tried booting 7.04 Live with video=ofonly, I get a loading bar and the word UBUNTU in all sorts of wacky colors, loads up but not all the way to the desktop, X fails before I hear to 'startup music'. Tried changing xorg, saved, restarted gdm, nothing. Restarted X, X fails, same as before.

---

### Post by gaussian on 2008-08-25
I am kind of out ideas. One thing to try: change DefaultDepth in xorg.conf to 16 or 15 instead 24 and try. Might be worth trying.

---

### Post by DGortze380 on 2008-08-25
> **gaussian said:**
> I am kind of out ideas. One thing to try: change DefaultDepth in xorg.conf to 16 or 15 instead 24 and try. Might be worth trying.

Yeah, tried that, tried most everything I know how to do. Thanks for the help anyways. I'll leave this open just incase.

---

### Post by DGortze380 on 2008-08-26
Ok, some progress. Reset PRAM. On 7.04, I did a normal live boot, added HorizSync and VertRefresh to xorg.conf, left UseFBDev true and force 24bit 1024x768 resolution. Seems like the problem with the live cd was xorg trying to use 800x600 resolution.

Now i've got x working, trying the install as I type this.

---

### Post by gaussian on 2008-08-26
Good luck. If I remember correctly that thing should go smoothly. And I think you need to get rid of video=ofonly after the install to get screen brightness, suspending and other goodies working.

If you decide to update to Gutsy here is what I experienced
1) The kernel does not contain ide-core, so you need to do the following:
[http://ph.ubuntuforums.com/showthread.php?t=581280&page=7](http://ph.ubuntuforums.com/showthread.php?t=581280&page=7)

2) liboil in Gutsy causes gnome-settings-daemon to crash. See
[https://bugs.launchpad.net/ubuntu/+source/liboil/+bug/163255](https://bugs.launchpad.net/ubuntu/+source/liboil/+bug/163255)

My solution I think was to use Feisty liboil

3) DVD/CD-drive is not recognized. There is no functionality and not even a device is created. Only workaround found so far (noticed this tomorrow): boot into old Feisty kernel. I really don't need the drive.

Keep us posted how the install went.

---

### Post by DGortze380 on 2008-08-26
> **gaussian said:**
> Good luck. If I remember correctly that thing should go smoothly. And I think you need to get rid of video=ofonly after the install to get screen brightness, suspending and other goodies working.

If you decide to update to Gutsy here is what I experienced
1) The kernel does not contain ide-core, so you need to do the following:
[http://ph.ubuntuforums.com/showthread.php?t=581280&page=7](http://ph.ubuntuforums.com/showthread.php?t=581280&page=7)

2) liboil in Gutsy causes gnome-settings-daemon to crash. See
[https://bugs.launchpad.net/ubuntu/+source/liboil/+bug/163255](https://bugs.launchpad.net/ubuntu/+source/liboil/+bug/163255)

My solution I think was to use Feisty liboil

3) DVD/CD-drive is not recognized. There is no functionality and not even a device is created. Only workaround found so far (noticed this tomorrow): boot into old Feisty kernel. I really don't need the drive.

Keep us posted how the install went.

Thanks for the info. If I get installed I'll stick with this for a while before I get bored and try to upgrade. Right now I'm worried I'm hung up at 'Configuring Hardware 94%'. Been about 15 minutes with no visual progress, and only a really quick spin of the cd drive ever 5 minutes or so.

Side note, I was able to boot and get this far in the install without video=ofonly.

EDIT: installing yaboot, getting closer.

---

### Post by DGortze380 on 2008-08-26
Installed, boots, runs. A little slower than I'd like, maybe back to trying fluxbox tomorrow, after some extensive backups. If there is anyone out there crazy/stupid enough that still wants to try this (aka. me), my problem was needing to reset PRAM, and edit xorg.conf.

---

