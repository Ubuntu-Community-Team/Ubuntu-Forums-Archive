---
title: "Fiesty Fawn Live CD doesnt work ;  &quot;can't access tty&quot;"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by medya on 2007-04-20
hey 
I have two hard disk, I have win xp and ubuntu edgy on each of them .
when I try to boot from Fiesty Live CD , to install the new ubuntu , after showing ubuntu logo it says
 /bin/sh: can't access tty; job control turned off

mind that I can run Dapper Live CD  and it works fine . (strange just Fiesty Live CD has this problem)
I re-installed the Grub , but it doesnt work yet.

what to do ?

---

### Post by Sef on 2007-04-20
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Did you check the disk instead of booting it? (In the same menu as boot the Live CD.)

---

### Post by medya on 2007-04-20
1- what is md5sum ?
2- I burnt the CD with maximum speed.

---

### Post by NewJack on 2007-04-20
> **medya said:**
> 2- I burnt the CD with maximum speed.

Re-burn the iso using no more than x4 speed.  That might fix the problem right off the bat.

---

### Post by akniss on 2007-04-20
Don't worry about re-burning.  This is not your fault, or a problem with the iso.  Its a bug.  I think it has to do with the ata drivers in the kernel.  See below for people having the exact same problem (me being one of them).

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/78380](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/78380)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864)
[https://www.stgraber.org/ubuntu/isotesting/result/154/3](https://www.stgraber.org/ubuntu/isotesting/result/154/3)

---

### Post by Johnny_Too_Bad on 2007-04-20
I'm having a somewhat similar problem.

I downloaded and burned Feisty (4x speed) but every time I try to boot from CD, it skips the CD and goes right to Dapper.  What am I doing wrong?

---

### Post by medya on 2007-04-20
> **NewJack said:**
> Re-burn the iso using no more than x4 speed.  That might fix the problem right off the bat.

I re-burnt the CD with lowest speed possibe  (8x)  and i still get the same error.
and I DID check the CD's integrity and it said the CD has 0 errors .

by the way guys, I did something , I have a DVD-ROM and CD-RW  , I un-pluged the CD-RW and the error changed....

this time I didnt get those erros but the Ubuntu Logo went forever and I didnt go forward ...

I hitted CTR+ALT+F1 and it said something like "error running install command binfmt_0000"


the biggest shame is, I have to talk about ubuntu on a Radio show tomorrow and tell peopel how cool the new ubuntu is .

I dont know what I am gonna tell them. (hi peopel good morning I myself couldnt even install it ...but I have heared it is Great and Easy to install.... sigh)

---

### Post by medya on 2007-04-20
I posted my experieance in this Bug Report u should do the same if u have somethin usefull , so they can fix the problem sooner .

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/44993](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/44993)

I wonder after they fix the problem will we have to download the whole CD agian ? ( I have a slow interent)

---

### Post by ray_nix on 2007-04-20
I'm having the exact same problem.

I have two IDE hard drives, and two SATA drives. I'm trying todo a fresh  install on a SATA drive.

On the Live CD, it appears the CDROM is no longer being accessed, as I can eject it and the bootup still hangs with the error message "Can't access TTY; job control stopped...." During this time (if I leave the CD in or not), it appears to be trying to access the floppy drive. I put a blank disk in it and I still got the same error message. I did read that someone did have luck by putting some read-only text files on the floppy disk and it booted that way. I have yet to try this.

After searching the forums, no one seems to have a good fix for it. It all seems to point to the new Kernel.

As a side note, I have been unable to install any other new Linux distro, or even a very recent BSD distro on my machine. Anything from the Ubunutu 6.10 era does work fine.

I will attempt to upgrade my BIOS, and maybe just detach all other drives that aren't necessary for the install.

Originally I thought my 2GB of memory was the problem, as that is the only thing that has changed since I installed 6.10 when it was first released.....

Hopefully someone has a fix!

---

### Post by darrenm on 2007-04-20
Do you have any other Ubuntu CD's (Dapper / Edgy) ? If so you could install one of those and update the install?

---

### Post by darrenm on 2007-04-20
AFAIK it should have been fixed for the RC release.

---

### Post by medya on 2007-04-20
> **darrenm said:**
> Do you have any other Ubuntu CD's (Dapper / Edgy) ? If so you could install one of those and update the install?

I have dapper , how can I update install what do you mean exactly ? can u explain ?

---

### Post by akniss on 2007-04-20
> **darrenm said:**
> AFAIK it should have been fixed for the RC release.

It obviously has not been completely fixed.  There are still numerous people having issues with the final release.     Some comments in the System76 forums make it sound like the problem is known by the devs, and they have some ideas on how to fix it, but it is still a very real problem for a select few.

---

### Post by akniss on 2007-04-20
> **medya said:**
> I posted my experieance in this Bug Report u should do the same if u have somethin usefull , so they can fix the problem sooner .

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/44993](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/44993)

I wonder after they fix the problem will we have to download the whole CD agian ? ( I have a slow interent)

Your bug report link takes me to a page with an openoffice bug...

---

### Post by lamalex on 2007-04-20
> **Johnny_Too_Bad said:**
> I'm having a somewhat similar problem.

I downloaded and burned Feisty (4x speed) but every time I try to boot from CD, it skips the CD and goes right to Dapper.  What am I doing wrong?

you  need to set your bios to boot from cd, it sounds like that's not done. go into your bios and change the boot order.

---

### Post by 11hjpphty76lkjj on 2007-04-20
I'm having the same problem. LiveCD works great on one pc and not the other.  I'm getting the can't access tty problem.

PC that is broke is: HP workstation xw6000

PC that works is:  HP d530 cmt

On the broke PC I've tried changing the hd configuration, disabled and disconnect disk drive, com ports, ide1 and ide2, etc.  Same thing.

A

---

### Post by lamalex on 2007-04-20
have you tried the alternate install cd? some machines just don't play well with the live.

---

### Post by akniss on 2007-04-20
> **medya said:**
> I have dapper , how can I update install what do you mean exactly ? can u explain ?

First install Dapper, then upgrade to edgy:
from: [https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0](https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0)
[QUOTE=https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0]
Upgrade from 6.06 LTS
If you want to upgrade from 6.06 LTS to 6.10, run the following command (either via ALT-F2 or a terminal):
```
gksu "update-manager -c"
```
The "-c" switch instructs Update Manager to look for upgrades. By default, the Ubuntu 6.06 LTS release will not offer that automatically because of its long support cycle and high stability.
If you have a working network connection, it should then inform you about a new release and offer to upgrade your system.[/QUOTE]

Then follow the instructions on this page to upgrade from Edgy to Feisty:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Some notes on upgrading:
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

---

### Post by 11hjpphty76lkjj on 2007-04-20
Fixed.

Alternative CD works great.

A

---

### Post by medya on 2007-04-20
> **kalosaurusrex said:**
> Fixed.

Alternative CD works great.

A

whats that alternative CD ?

---

### Post by 11hjpphty76lkjj on 2007-04-20
It's just the install cd.  not the live/install cd.  It's like the breezy install cd if you ever used that.

---

### Post by medya on 2007-04-20
> **akniss said:**
> First install Dapper, then upgrade to edgy:
from: [https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0](https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0)


Then follow the instructions on this page to upgrade from Edgy to Feisty:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Some notes on upgrading:
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

hey man thats lots of works and also still not BEST .
becasue everybody says u always better have a clean install .

means doing lots lots of works and still not getting best of it !

---

### Post by medya on 2007-04-20
> **kalosaurusrex said:**
> It's just the install cd.  not the live/install cd.  It's like the breezy install cd if you ever used that.
where I can get that cd?

---

### Post by steve.horsley on 2007-04-20
The alternate CD is available from normal download sources. See this page:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
and notice the checkbox for the alternate desktop CD just below the big green download button. Check this box **before** clicking download.

---

### Post by akniss on 2007-04-20
> **medya said:**
> hey man thats lots of works and also still not BEST .
becasue everybody says u always better have a clean install .

means doing lots lots of works and still not getting best of it !

Yes, I realize its not the BEST way to do it.  The BEST way would be to install Feisty from the LiveCD. If a clean install of Feisty will not work, upgrading from a previous release may be the only option.  You stated that you had the Dapper install CD, and did not want to download another ISO.  This might be the only way that you can install Feisty unless you 1) download the Edgy CD and upgrade, or 2) download the alternate install CD for Feisty.  If the alternate CD does not work, then you can either try upgrading Dapper > Edgy > Feisty, or download Edgy and upgrade to Feisty.  No matter how you look at it, you will need to download a lot of bits.

---

### Post by gabrielp on 2007-04-20
Hi
I had serious problems to install Feisty ,probably because I tried to leave my home directory
from prior install ,so check it ,if so pls back it and try clean install

---

### Post by akniss on 2007-04-20
Some evidence that the Alternate install CD may not work either...

[http://ubuntuforums.org/showthread.php?t=415751](http://ubuntuforums.org/showthread.php?t=415751)

---

### Post by akniss on 2007-04-20
Another thread filled with users having the same trouble:
[http://ubuntuforums.org/showthread.php?t=413675](http://ubuntuforums.org/showthread.php?t=413675)

---

### Post by tumnus on 2007-04-20
I have a similar ATA issue with my floppy drive and although I can get around it either by sticking a floppy in the drive (?!?!?) or disconnecting it altogether, it causes the Live CD to be even slower to boot.

Does anyone know whether this just affects the Live/Install CDs and not a permanent harddrive installation?

I would be doing an online upgrade from my current Edgy install anyway via Adept and its new upgrade tool, but I wouldn't want the same issues with my permanent installation.

Looks like they need to make an updated release to me as there are all sorts of critical problems with Network Manager too for some people still (like either not working at all and/or even blocking KDE apps from accessing the internet while running).

...and yes I reported all of my Live CD issues when I tested the betas...

---

### Post by medya on 2007-04-20
Hey Guys Update !

as I said I have two hard disk and a DVD-ROM and a CD-RW
I un-pluged the CD-RW and the Windows Hard Disk .

and I installed the ubuntu fiesty sucessfully, but the problem is , now when I plug  the CD-RW or windows Hard Disk (which all my important files are there) i get the same error which I used to get in Live CD .

it is a very serious issue ubuntu guys must solve it !

---

### Post by medya on 2007-04-20
and here is the link for the Bug report in the launchpad 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864)

---

### Post by los_lobos on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				From the bug report (written by Ben Collins):
> 
The quick workaround for this on an installed system is to add "piix" to /etc/initramfs-tools/modules, and run "sudo update-initramfs -u"

For installing a system, add break=top to the kernel cmdline via the bootgfx menu. Once at a busybox prompt, run "modprobe piix". Then "exit" the shell. Once the system is installed, the above work around will also be needed.

We are working on an update to fix this.


Could someone explain these in detail? Where do I actually do this "add break=top to the kernel cmdline via the bootgfx menu."? What and where are kernel cmdline and bootgfx menu?

---

### Post by entangled on 2007-04-21
los-lobos
When you boot from cd you get a boot: prompt
Type in 'live break=top"
(obviously you don't type the quotes)
 then enter
You'll immediately get the busybox prompt and there you can type
"modprobe piix"
"exit"
From here the live CD boot should carry on.

I think you can then install but I expect the same piix problem occurs when rebooting - so do the same again and finish by editing modules.
Good luck - I'm trying it now and have got the live boot working.

---

### Post by ajifans on 2007-04-21
It's "break-top" not "break=top".

When given the option on whether to boot Ubuntu, press F6 and then add "break-top" to the end of the line and then start Ubuntu.  Worked for me.

---

### Post by darrenm on 2007-04-21
Ben Collins says its break=top 

Was it only break-top that worked for you?

---

### Post by starcraft.man on 2007-04-21
Hi, I recently stumbled onto this thread... this seems to be a very serious problem. I was doing a new install of feisty and no matter whether I used the Live installer or the Alternate CD after selecting Boot/Text install respectively I got the same error.
```

/bin/sh: can't access tty; job control turned off
...failed to set xfer mode (err_mask=0x4)
```

I'm now upgrading to 7.04 through 6.10 which doesn't bother me that much, but I would like to have the cd in future if new clean install is needed. Is there a place where I can watch the status/ do devs know when they can fix it?

---

### Post by Wolfiebad on 2007-04-21
i tried the break-top method but it does absolutly nothing. I tried in with f6 at the menu and when I got the can't access tty error. Am i doing something wrong or what?

---

### Post by darrenm on 2007-04-21
Try break=top

---

### Post by Wolfiebad on 2007-04-21
Tried break=top (with F6) also nothing. This time the I got the error immediately I then typed break=top <enter> modprobe piix <enter> exit <enter>. The moving line appeared for a short time then the same error again.

---

### Post by medya on 2007-04-21
hey , when I press F6 , when ubuntu boots, NOTHING happens ? where should I enter that "break=top command  ?

can you please help ? where should I enter those commands ?

---

### Post by 3rdgear on 2007-04-21
I had trouble with my live CD too. Then I saw where some people are using the alternate CD and so I tried that. Works pretty good.

---

### Post by entangled on 2007-04-21
If you are on the F6 (or any) screen you just type
live break=top
and you'll see it echoed after the boot: prompt near the bottom of the screen

---

### Post by entangled on 2007-04-22
By the way, if anyone has been using the modprobe piix fix -
For me, it works OK to boot the live cd
however, after installing, then editing initramfs modules then rebooting, the same busybox prompt happens.
So, I can boot the live cd and install to hard disk, but every boot up still needs "modprobe piix" to be typed in.

For me, editing initramfs modules with piix does not fix the boot problem. Maybe Ben Collins has another idea?

---

### Post by bucaneer on 2007-04-22
[This thread]("http://ubuntuforums.org/showthread.php?t=415009") is about the same problem and has some fixes (although none of them worked for me)

---

### Post by los_lobos on 2007-04-22
> **entangled said:**
> By the way, if anyone has been using the modprobe piix fix -
For me, it works OK to boot the live cd
however, after installing, then editing initramfs modules then rebooting, the same busybox prompt happens.
So, I can boot the live cd and install to hard disk, but every boot up still needs "modprobe piix" to be typed in.

For me, editing initramfs modules with piix does not fix the boot problem. Maybe Ben Collins has another idea?
I had exactly similar experience with my older PC. Every boot requires a "modprobe piix" and "exit" even after editing initramfs thingy.

On my newer PC (C2D E4300, Abit AB9, Radeon X1950 Pro, 2GB DDR2, 320GB WDC SATA, Phillips DVD/RW) the success of boots seem pretty random. Sometimes when I get to GUI there is no any harddisks visible and sometimes the mouse pointer is extremely sluggish/laggy. I even tried an old CD-drive but that didn't help.
Installing Ubuntu 6.10 worked perfectly.

---

### Post by DoricMan on 2007-04-22
I have exerienced  this problem this afternoon with the following error message.
"/bin/sh: cant access tty; job control turned off".
I have been using Ubuntu 6.10 Desktop's  live  CD in the last few weeks to get familiar with Ubuntu. No  error messages happened with the 6.10 live CD.
I thought that my KVM switch was the problem, any thoughts on KVM's being the culprit?
Anyhow I will try the above tests and see if they hold the answer.
Many thanks.

---

### Post by starcraft.man on 2007-04-23
Hi again, I've been trying several ways the past few days including the command fixes and none seem to work for me at least. It seems that its just the new kernel that is incompatible with my new hardware, even did the upgrade through the manager and it refused to boot after that. I hope it gets fixed soon >.< Anyone happen to know if they are releasing a fixed kernel soon?

---

### Post by n3tfury on 2007-04-23
> **medya said:**
> hey 
I have two hard disk, I have win xp and ubuntu edgy on each of them .
when I try to boot from Fiesty Live CD , to install the new ubuntu , after showing ubuntu logo it says
 /bin/sh: can't access tty; job control turned off

mind that I can run Dapper Live CD  and it works fine . (strange just Fiesty Live CD has this problem)
I re-installed the Grub , but it doesnt work yet.

what to do ?

how long did you let it sit at the error message?  i get the same thing on my Dell C600 laptop but let it sit there for about 5+ minutes and it finally continues.

---

### Post by Macuyiko on 2007-04-23
> **entangled said:**
> By the way, if anyone has been using the modprobe piix fix -
For me, it works OK to boot the live cd
however, after installing, then editing initramfs modules then rebooting, the same busybox prompt happens.
So, I can boot the live cd and install to hard disk, but every boot up still needs "modprobe piix" to be typed in.

For me, editing initramfs modules with piix does not fix the boot problem. Maybe Ben Collins has another idea?

It worked for me (finally the only solution that worked :)  ). Did you do a 
sudo update-initramfs -u
after adding it to initramfs-tools?

---

### Post by ray_nix on 2007-04-23
I have a solution for my problem:

I moved the CDROM from Secondary Slave to Secondary Master, and I received no errors what-so-ever with the Live CD.

Not sure if it would work for anyone else though!

---

### Post by linuxman1 on 2007-04-24
Yea, but this takes "forever" even with a high speed connection - mine ran overnight and then some.

---

### Post by medya on 2007-04-24
here is a solution for this problem explained in[ this blog ]("http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html")

---

### Post by starcraft.man on 2007-04-24
Gah... seems like a bit of work just to get this installed ><. Maybe I will try it in a bit.

---

### Post by klytu on 2007-04-24
FYI,  there is another thread going on about this [[COLOR="Red"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=415009").

---

### Post by los_lobos on 2007-04-26
I got it finally working:

1. Installed 7.04 from alternate CD in text mode and booted. (removed quiet and splash from boot options)
2. Disabled JMB363 SATA, LAN1 and Firewire controllers in BIOS. (Not sure if they really made any difference because I had sometimes managed to boot ok before disabling them.)
3. While booting a disk error check was run and PC booted again.
4. I add
```
piix
libata
pata_jmicron
ata_piix
ahci
ata_generic
``` to */etc/initramfs-tools/modules* and ran **sudo update-initramfs -u** .
5. Every boot is ok now even with JMB363 enabled.

Not sure if this helps anyone as it seems people having similar error messages for different hardware errors.

---

### Post by cyb3rj on 2007-08-13
> **medya said:**
> here is a solution for this problem explained in[ this blog ]("http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html")

The bit about permanently fixing this is useful.

I found another LiveCD solution elsewhere which is simply putting a floppy in the drive.  There's nothing special about the floppy, it just gives "something" its "thing" that it needs to bounce off to start.

I don't get it.  It works.  I'll take it; especially knowing how to fix the final install.

---

