---
title: "Re: Launching lubuntu-14.04.5-desktop-powerpc.iso (DVD-R) freezes a PowerBook G4."
date: 2017-03-04
forum: Apple Hardware Users
---

### Post by antdude on 2017-03-04
Hello.

I downloaded, burned to a DVD, and booted lubuntu-14.04.5-desktop-powerpc.iso to use in a very old (2002) 15" PowerBook G4 1 Ghz with 512 MB of RAM, 60 GB HDD, ATI Radeon video card, etc. I could boot up from the DVD just fine even though very slow as expected. However, (open/launch)ing its installer freezes the computer hard (mouse cursor and DVD stopped (mov/work)ing). I have to hard reboot with the power button. I had no problems with a burned bootable ubuntu-12.04-desktop-powerpc CD-RW though! Is it because of my old hardwares or something else? 

Thank you in advance. :)

I got a little farther up to the time zone selection with its map, but it got stuck. I noticed my screen went black and then back to normal. I could still move my mouse cursor around, but not click anything. Ctrl+alt+F1 showed ATI Radeon messages like "[time]radeon:0000:00:10.0: ring 0 stalled for more than <growing number>msec that goes forever.

OK, it seems like this is a known issue. I tried various yaboot's commands in [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878) like: 
live video=ofonly
live radeon.modeset=0
live radeon.agpmode=-1

Screen still went blank black and back to GUI before freezing. :(

---

### Post by mörgæs on 2017-03-05
Are you able to install the 16.04 [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

---

### Post by antdude on 2017-03-05
[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075")      : No, I have not. I did manage to get Debian PPC (net installer) installed finally. Let me try that first. If not, then I will try Lubuntu's mini iso. I just noticed [http://cdimages.ubuntu.com/lubuntu/releases/xenial/release/lubuntu-16.04.1-desktop-powerpc.iso](http://cdimages.ubuntu.com/lubuntu/releases/xenial/release/lubuntu-16.04.1-desktop-powerpc.iso) (a new version). It was sure a hassle just to install with dual boot. :( Reading your link says to expect a lot of tedious work and not to expect fast results (GUI). :(

> **mörgæs said:**
> Are you able to install the 16.04 [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?I downloaded, burned to a CDRW, and booted  [http://ports.ubuntu.com/dists/yakkety/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ports.ubuntu.com/dists/yakkety/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)  (32-bit). It failed to install with its busybox-initramfs package. I  tried it twice. Argh. [https://imgur.com/a/W69br](https://imgur.com/a/W69br) for the blurry iPhone  4S's photos. :/

---

### Post by mörgæs on 2017-03-07
The netboot installer is more or less the same as the mini ISO. 
If you managed to get the Debian one running then I would just use that and add a GUI.

---

### Post by antdude on 2017-03-07
> **mörgæs said:**
> The netboot installer is more or less the same as the mini ISO. 
If you managed to get the Debian one running then I would just use that and add a GUI.OK and thanks. I do have Debian PPC finally installed and working. Now, I have new issues. Bah. So complex and tedious.

---

