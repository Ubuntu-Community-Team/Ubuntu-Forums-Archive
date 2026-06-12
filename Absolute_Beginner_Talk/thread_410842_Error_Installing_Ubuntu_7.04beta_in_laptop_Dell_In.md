---
title: "Error Installing Ubuntu 7.04beta in laptop Dell Inspiron E1505 VIdeo Card ATI x1400"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by ozwolverine on 2007-04-16
Hello,

I'm trying to installa Ubuntu 7.04 beta in my laptop Dell Inspiron E1505 which has a VIdeo Card ATI x1400. I got a message: "Couldn' start X server" or something like that. What should I do?

I have the video card driver installer for Linux, I used it with my actual distro CentOS4, but with Ubuntu what should I do to install drivers? I thought that I can generate .debs and put them into a CD, then try the installation with the option Install CD Driver Update, but I cannot generate .debs, cause I get this error message: 

$ ./ati-driver-installer-8.35.5-x86.x86_64.run --buildpkg Ubuntu/7.04


Created directory fglrx-install.yL5914
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.35.5.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/7.04
./packages/Ubuntu/ati-packager.sh: 178: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.yL5914

Why? In the download page the said this driver installer is for 32 and 64 bits. I tried to run the same command not only in my CentOS installation, but also in a Feisty Fawn 7.04 beta that I have at work.

Please help me, I really want to have Ubuntu in my laptop :)

Thanks a lot,
Ozwolverine

---

### Post by lamalex on 2007-04-16
you're using feisty? why not use the restricted drivers manager? its in system adinistration

---

### Post by Terl on 2007-04-16
You may want to check here:  [ATI Installation How-to]("http://http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")  It is for Edgy but I imagine it would be essentially the same for Feisty.

Yes, you can make debs using alien but they don't always work as one may think.

---

### Post by lamalex on 2007-04-16
ok nm i read that post wrong. try doing
```
sudo dpk -reconfigure -phigh xserver-xorg
```
and pick vesa, or ati, or radeon, try all 3 until 1 works (vesa will definitely work but is slowest).
that should get you at least some sort of X environment.

---

### Post by ozwolverine on 2007-04-16
Thanks Terl and Iamalex,

The problem is that I couldn't get the installation work, I mean,  I start Installation it shows options, then it loads things into memory (I guess), but when it tries to show me the Installation Screen is when I get Xserver problem. so I haven't been able to install it, I don't even get the language selection for the installation :(  

I guess your nice tips work when the system is already installed but cannot open Xserver, is that right? 

I tried to change resolution "F4 VGA" option in installer Menu, but it only allows me to change resolution, and if I select a low one everything get bigger on screen, but the problem of the Xserver remains 

What should I do?

Thanks a lot,
ozwolverine

---

### Post by lamalex on 2007-04-16
try adding nolapic and noacpi into the boot flags, that fixed it for me on my ati desktop.

---

### Post by Terl on 2007-04-16
> **ozwolverine said:**
> Thanks Terl and Iamalex,

The problem is that I couldn't get the installation work, I mean,  I start Installation it shows options, then it loads things into memory (I guess), but when it tries to show me the Installation Screen is when I get Xserver problem. so I haven't been able to install it, I don't even get the language selection for the installation :(  

I guess your nice tips work when the system is already installed but cannot open Xserver, is that right? 

I tried to change resolution "F4 VGA" option in installer Menu, but it only allows me to change resolution, and if I select a low one everything get bigger on screen, but the problem of the Xserver remains 

What should I do?

Thanks a lot,
ozwolverine

Maybe I misunderstood your initial post.  Is Ubuntu installed on your pc or are you getting errors when you try to install Ubuntu?  Or have you installed ubuntu and the ati installation is erroring out?

---

### Post by ozwolverine on 2007-04-16
> **Terl said:**
> Maybe I misunderstood your initial post.  Is Ubuntu installed on your pc or are you getting errors when you try to install Ubuntu?  Or have you installed ubuntu and the ati installation is erroring out?

I cannot get the installation of Ubuntu work, So I tried generating debs with ati drivers in another Ubuntu installation, but it doesn't work either. So what else should I to to be able to make the installer of Ubuntu work?

I was able to install feisty fawn at work, but at home in my laptop I couldn't because Xserver doesn't want to start.

Thanks a lot,

---

### Post by bwhite82 on 2007-04-16
> **ozwolverine said:**
> 
$ ./ati-driver-installer-8.35.5-x86.x86_64.run --buildpkg Ubuntu/7.04


That should be:

> ......... --buildpkg Ubuntu/feisty

---

### Post by Terl on 2007-04-16
Does the live cd version boot or are you getting the error at that point also?  You should be able to boot from the cd and get to a working desktop without installing a thing.  Is this working?

---

### Post by ozwolverine on 2007-04-16
> **soldierboy101st said:**
> That should be:

Same error message generating debs with: --buildpkg Ubuntu/feisty 

:(

---

### Post by bwhite82 on 2007-04-16
> **Terl said:**
> Does the live cd version boot or are you getting the error at that point also?  You should be able to boot from the cd and get to a working desktop without installing a thing.  Is this working?

I have the exact same PC, I've had no luck with feisty livecd OR feisty alternate (always hangs at 85%, no matter which option i tried). I finally just had to reinstall edgy, then do an upgrade through the alternate cd.

---

### Post by bwhite82 on 2007-04-16
> **ozwolverine said:**
> Same error message generating debs with: --buildpkg Ubuntu/feisty 

:(

Make sure you have the proper compiling tools:
> 
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r)

I have the same PC as you and have compiled this same driver many times, something simple you aren't doing right.

---

### Post by ozwolverine on 2007-04-16
> **Terl said:**
> Does the live cd version boot or are you getting the error at that point also?  You should be able to boot from the cd and get to a working desktop without installing a thing.  Is this working?

Which is that Live CD version? I only found these:

Desktop CD
Server install CD
Alternate install CD

What I have is Desktop CD version, 
None of the options of the install menu work, I even tried the option Ubuntu in safe graphics mode, and didn't work either :(

Thanks for your interest in helping me put this working on :)

---

### Post by bwhite82 on 2007-04-16
> **ozwolverine said:**
> Which is that Live CD version? I only found these:

Desktop CD
Server install CD
Alternate install CD

What I have is Desktop CD version, 
None of the options of the install menu work, I even tried the option Ubuntu in safe graphics mode, and didn't work either :(

Thanks for your interest in helping me put this working on :)

For now, I think you may have to go the install-route that I did. That is, install an earlier version of Ubuntu (Edgy), then with a copy of the Feisty Alternate CD burned, upgrade with the feisty cd while logged into edgy. That was the only way I could get Feisty installed on my pc, if you find another way, please let me know.

After you've installed Edgy, do this to upgrade to feisty:

1) Insert your Feisty Alternate CD
2) Type the following command into a console (or Press ALT+F2 and enter it there):
> gksu "sh /cdrom/cdromupgrade" 

---

### Post by Terl on 2007-04-16
Based upon what Soldierboy101st has said, I would download the desktop version of 6.10 (Edgy) and try that one instead of the newest (still beta) version.  Boot from the cd and boot with fist option.  It should go to a desktop once it is all loaded.  You can actually use it as it is to try it out a bit.  There is an install icon on the desktop which you can click to install Ubuntu if all works well to this point.

[Edit]:  I think soldierboy101st can help you better as he has the same pc.

---

### Post by ozwolverine on 2007-04-16
Thank you guys: Terl and soldierboy101st,

I will try soldierboy101st recommendation, Installa 6.10 then, try to install 7.04 from 6.10.
One question soldierboy101st, did you have to make any particular settings to be able to install 6.10 or just install it the normal way?

Againg, Thanks a lot,

ozwolverine

P.S: I will try installation at night, cause I didn't bring my laptop to work today, so till I arrive home I will be able to test.
Thanks a lot,

---

### Post by bwhite82 on 2007-04-16
The Edgy LiveCD booted up without a hitch, then once you're on the desktop, simply click on the "Install" icon and it will install it to your harddisk. Be careful not to wipe your Windows partitions if you plan on dual booting! If you're not dual booting, then it's a snap.

---

### Post by ozwolverine on 2007-04-17
hello soldierboy101st and Terl,

I installed kbuntu 6.06, then I inserted feisty fawn CD, but I didn't get any install icon, just CD icon, so I inserted edgy 6.10 CD, then Installed it, restart then tried again with feisty fawn, but nothing. So now, I'm updating my new edgy 6.10 installation, maybe after updating all the system to the latest files I will probably get the option to install 7.04 from 6.10 interface. 

I guess I won't be able to tell you until night if this worked, cause the updating is going to take about 1 and a half hour, and I've got to go to work in a few.

Hope to tell you soon, what happens.

Ozwolverine

---

### Post by bwhite82 on 2007-04-17
If you already have Edgy installed and a Feisty Alternate CD burned, then there is no reason to update until AFTER the upgrade. While logged into Edgy, insert your Feisty CD, goto a console and type:

> gksu "sh /cdrom/cdromupgrade"

And it will proceed to upgrade your Edgy Installation to Feisty. You cannot do this if all you have burned is the LiveCD version (Desktop).

---

### Post by ozwolverine on 2007-04-17
Hello,

Well, I don't have the alternate CD, so I will download it to try the upgrade.

Thanks a lot,

---

### Post by ozwolverine on 2007-04-18
Hello Soldierboy,

Bad News, Your tip didn't work either, I downloaded alternate CD, and after I had my edgy (6.10) installed and up to date and even with ATI drivers installed. I executed the command you told me with alternate CD inside, and it appeared a message saying that it was about to update to feisty 7.04, so I did all procedure, when I reboot, I got the same error message. something about microcode not found, X Server not initialized, etc. Now I cannot log in graphic mode, I was able to log in text mode, but everytime I got the same microcode error message in console once, and onces again.

Any more ideas?

Thanks a lot for your kind help.

ozwolverine

---

### Post by bwhite82 on 2007-04-19
Good! The fact that you can get to a command prompt tells me that your upgrade went fine, now all you have to do is configure your video hardware. Uninstall your current video card drivers, make sure your /etc/apt/sources.list is updated with feisty (change edgy to feisty everywhere you see it), then reinstall your video card drivers.

---

### Post by sirownzalot on 2007-04-27
I have the same laptop and I'm having the exact same problem. The live install cd doesn't even load into ubuntu. It has a x server crash. I successfully installed fiesty with the alternate cd but it doesn't boot. It has an x server crash. I tried installing it with the AMD64 alternate CD and it successfully booted. But I want to get the i386 version working.

---

### Post by shuttleworthwannabe on 2007-04-27
Guys, I am also struggling to install Feisty from Desktop Feisty; it just does not load the GDM because of x-server error;

Perhaps this is what the problem is: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

My Specs HP Compaq nw8240 Laptop Centrino 2.13GhZ 2G RAM, ATI fglx V5000

---

### Post by sirownzalot on 2007-04-27
I need ndiswrapper in order to get my wireless working, so I guess I won't be installing Fiesty. This looks really bad for Ubuntu for not catching a bug like that. Now some people won't be able to install fiesty. I hope this doesn't happen with 7.10.

---

### Post by on.journey on 2007-04-27
Got the same problem with my ATI X1400, why the hell do I even need a graphic card? 

Downloaded the alternate installing CD yesterday and burned it, unfortunately it was too late to yet try it out for longer, but I encountered the problem that I naturally can't connect to my wireless within the text mode installation and that's what I need to make the upgrades and changes described in the solution thread of this problem, right?

So what I would have to do is connect it directly to the router when I get home from school today, correct?

---

