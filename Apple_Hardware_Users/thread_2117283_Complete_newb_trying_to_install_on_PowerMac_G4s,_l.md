---
title: "Complete newb trying to install on PowerMac G4s, liveboot iso failing"
date: 2013-02-18
forum: Apple Hardware Users
---

### Post by talonts on 2013-02-18
I'd love to test on 2 PowerMac G4s, but I can't even get the PPC ISOs to boot. I have tried Lubuntu 12.10 and Ubuntu 12.04, both for PPC, and both stop at the same point - the screen goes white with black text ending in "returning from prom_init", then goes pure black and sits there. I've let it stay there for hours on end, and nothing. 

This is a 733MHz with 1Gig RAM, running whatever card it came with in the Digital Audio version (it is unmarked, definitely not a Rage128), through the VGA port.  I don't have a Mac monitor or adapter cable for the Mac DVI port.

I've tried:
<Enter>
live video=ofonly (or whatever it recommends)
test-powerpc
live-powerpc
live-config-powerpc  (or was it live-test-powerpc?)
and a few others (these are all from memory, don't have it fired up right now). They all have the same symptoms.  There was ONE time that I got an "Ubuntu 12.xx" screen afterwards but then it black screened later.

I'll dig through the forums some more, but I'd really like to get 12 working.  But if impossible, I suppose I'll move back to 10.x to see if I can get that working.

Trying live video=ofonly nouveau.modeset=0 right now...
Booted into GUI, but psychedelic, straining my eyes to run through the install to HD, to see if updating will fix it...

System boots back into OS X, and looking in /etc, there is no yaboot.conf.  Booting with Option held down only shows Tiger, so I don't see any way to run yabootconfig.

And since I could barely read the screens, I didn't get to pick the partition I wanted to install on.  Blech.  I may Restore the OS X partition that I Restored to a spare drive before I started this, and start over.  Not sure.

I'll have to pick this up in a day or 2.  But if anyone has tips before then, I'm all ears.

---

### Post by imacg3ppc on 2013-02-18
I am still having problems with my install, had to mess with many many options, partitions, software packages failing.... but im past the point you're stuck at. Boot the alternate iso and do run cli-expert-powerpc

the expert setting is not as difficult as you would expect. you will have to pick which kernel you want and different kernel (3) total of them will give you different result. do of couse add video=ofonly. Do not install sshserver, print server, or email server if you get a install package error. im also having problems after the install but try alternate iso for better results.

if you get stuck on install press alt+cmd f2 to go to a console. from there you can reboot.
also to get into your firmware settings you can hit alt+cmd+o+f before screen turns on. you can type eject cd if its stuck. you can type 'words' to get full list of commands to use in open firmware but most of those are beyond me.

---

### Post by talonts on 2013-02-20
So since it installed to the same first partition as Tiger, and didn't complete, I'd like to remove it (I'll be installing 10.10 later on the last partition, and work up upgrading to 12.x afterwards, I need to work on the Leopard install next).

Can I just delete the directories it created from within Tiger?  Tiger is booting fine, and shows the Ubuntu directories.  But I don't want to delete them if there is a chance it will leave stuff behind (yaboot never completed setup).

---

