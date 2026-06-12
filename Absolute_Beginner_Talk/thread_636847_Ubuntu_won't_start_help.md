---
title: "Ubuntu won't start help"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by seepage87 on 2007-12-10
I have ubuntu installed on an IDE drive.  It starts fine when I have any number of SATA drives attached to my computer, but if I attach my other IDE drive (to the same ribbon.  Also note the drive works with other box, is formatted NTFS) ubuntu freezes at the beginning of the progress screen.  Grub starts fine, it begins to start ubuntu, then the screen with the orange progress meter just sits with out increasing at all.

It may also be worth noting that I have mdadm.conf set up to assemble a RAID5 of 4 SATAs on boot, though this process goes flawlessly when the IDE isn't connected.  This is the only change I've made to the boot process.

Any thoughts?  It works fine if I have SATAs attached, both those in the array and those not.  Thanks in advance

---

### Post by Ctrl+Alt+Del on 2007-12-10
try removing the the quiet and splash options from the ubuntu entry in grub. This may reveal some additional info

---

### Post by meborc on 2007-12-10
your ide hdd is probably recognized as hda... and the sata hdd's as sda sdb etc... so if you add another sata drives, nothing changes to the hda part... but if you add another ide drive, the hda might change to hdb :) i hope i make sence

so try to swith the drives on the ribbon... so that the ide you have ubuntu on will be at the place you wanted to connect the ide drive and the new ide drive is connected to the socet the ubuntu drive was used to be connected

not sure if it will work or not :D

if not you will have to modify your GRUB to point to the correct drive during boot

---

### Post by rockinlinux on 2007-12-10
im not sure about this but i think it has something to do with you raid setting in the mdadm.conf . do you always use the raid set up or did you take the drives out to put in the ide? if you took them out try to make a backup f the mdadm file, them from the actaul on remove the raid settings and reboot. also maybe can you attacth the ide to a different ribbon? Just a couple ideas not sure if they will work. What is you goal here?

---

### Post by rockinlinux on 2007-12-10
> **meborc said:**
> 

if not you will have to modify your GRUB to point to the correct drive during boot

that too :)

---

### Post by seepage87 on 2007-12-10
> **meborc said:**
> your ide hdd is probably recognized as hda... and the sata hdd's as sda sdb etc... so if you add another sata drives, nothing changes to the hda part... but if you add another ide drive, the hda might change to hdb :) i hope i make sence

so try to swith the drives on the ribbon... so that the ide you have ubuntu on will be at the place you wanted to connect the ide drive and the new ide drive is connected to the socet the ubuntu drive was used to be connected

I was thinking something like that, but I haven't tried switching the drives on the ribbon.  I'll try that, why not?  When I don't have it attached, the IDE drive boots as sde though, not hda.  Not sure why, other installations have done hdx for IDE and sdx for SATA in the past.

> **meborc said:**
> If not you will have to modify your GRUB to point to the correct drive during boot
I've tried that, though I'm not entirely sure I'm doing it right.  Basically I'm it says something like (HDD x,y) and I switch the x to point to the right drive, the y to the right partition.  I figured I did it right since I got to the ubuntu logo screen and there would be some error before that if I pointed to a non ubuntu partition.

---

### Post by seepage87 on 2007-12-10
> **rockinlinux said:**
> im not sure about this but i think it has something to do with you raid setting in the mdadm.conf . do you always use the raid set up or did you take the drives out to put in the ide? if you took them out try to make a backup f the mdadm file, them from the actaul on remove the raid settings and reboot. also maybe can you attacth the ide to a different ribbon? Just a couple ideas not sure if they will work. What is you goal here?

I figured it could be the mdadm.conf (that's why I mentioned it).  My goal is to move stuff from my IDE drive onto my new RAID so  I add the IDE with the RAID still there, though I've tried booting without the RAID as well.

I'm thinking I might boot with a live CD and remove (rename) the mdadm.conf file to see if this changes anything.  I feel like I've booted with both IDE drives attached before I built the RAID, though I'm not sure.

---

### Post by seepage87 on 2007-12-10
> **Ctrl+Alt+Del said:**
> try removing the the quiet and splash options from the ubuntu entry in grub. This may reveal some additional info

I'll definitely do this when I get home and post the results.  As it is now, when I leave it for a long time (over 5 min) it exits the splash screen and gives cryptic messages that kinda look like failed attempts at something to me.  Don't remember what, but the numbers at the end change each new one that comes up (each maybe a minute or so apart).  I'll post those too if I can't get it to work.  Thanks a bunch.

---

### Post by 369gnl on 2007-12-10
just downloaded Ubuntu via inter net and all was good but when i start up it askes for my login and password but dosn' t seem to give me enough time to enter and it is at the bottom of my screen what can i do  this is a first for me i' am a newbe

---

### Post by seepage87 on 2007-12-10
> **369gnl said:**
> just downloaded Ubuntu via inter net and all was good but when i start up it askes for my login and password but dosn' t seem to give me enough time to enter and it is at the bottom of my screen what can i do  this is a first for me i' am a newbe

You should consider starting a new thread since this is on a pretty specific topic despite the general title.  Also, more information on what is happening would help as well.  I'm not sure what you mean by it not giving you enough time to enter your login and password or what you mean by bottom of the screen.  This is about what the login screen typically looks like:

[http://farm3.static.flickr.com/2129/1657633031_7ac0a7ae04.jpg](http://farm3.static.flickr.com/2129/1657633031_7ac0a7ae04.jpg)

Are you getting this far or is something else happening?

Enter your user name, hit tab, enter pass, enter and it normally works.

Start a new thread and private message me the like to it and I'll try to help you there.  Give more detail though.

---

### Post by seepage87 on 2007-12-10
This is the screen output if I let it sit long enough (screen goes from splash to terminal with error messages):

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.

[218.740078] Buffer I/O error on device sdd, logical block 0
(initramfs) [218.487542] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[278.722634] ata3.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 cbd 0x0 cta 4096

Then the numbers at the beginning of the line keep changing while repeats the last two lines over an over (save the difference in number) 

Any ideas?

---

### Post by seepage87 on 2007-12-10
Weird.  If I take off quiet in grub I get nothing.  Though if I sit around long enough I might get that same error log screen I mentioned above.

---

### Post by seepage87 on 2007-12-10
Wow, ok, so the boot messes up even with the live cd, so I gather it's probably the drive.  Unfortunately I don't have a good method of fixing the drive if I can't even boot to the live cd.  Any suggestions?

---

### Post by Gazneth on 2007-12-10
The only two options I can think of are unplug all drives except your IDE drive and boot from a live CD to check the drive.  It sounds like your IDE system always wants to be the default boot device.  If you just want to copy data off the drive you could try a USB external drive enclosure.  Then when you are done you have a handy external hard drive.

---

### Post by seepage87 on 2007-12-10
Well, good news for me, bad news for the community that might have gained something for from this.  A pin on the IDE port was broken.  I managed to fix it and now everything works.  Thanks and sorry to everyone who helped.

---

