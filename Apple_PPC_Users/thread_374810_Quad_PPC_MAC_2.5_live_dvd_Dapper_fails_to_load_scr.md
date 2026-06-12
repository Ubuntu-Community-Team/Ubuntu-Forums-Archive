---
title: "Quad PPC MAC 2.5: live dvd: Dapper fails to load screen and KPs?"
date: 2007-03-03
forum: Apple PPC Users
---

### Post by Uncle7 on 2007-03-03
Hi

dapper drake ppc64 dvd iso check sumed OK
Boots into firmware (black box?)
tab for options.

I've tried several of these after just hitting return, nosplash *live etc etc They all get to the point of loading a screen and then freeze up with a hard re-boot required. (fans) et al

I'm new to this and would appreciate a heads up to current resources. ie is it a confirmed bug.

I've found this but it's dated 06 with no Answer. [https://launchpad.net/ubuntu/+bug/56342](https://launchpad.net/ubuntu/+bug/56342)

I've also read the linked bug report on imacs. However this is a freeze from an instalation. [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23445](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23445)


I'm getting put off a litte as you seem to have to know quite a lot to even boot the os  however I've used the terminal a little so I'm not afraid to have a go if some one will point me in the right direction.


B

---

### Post by grazie on 2007-03-03
You've done a fair bit of investigation before posting which is most encouraging. You're using a fairly new high spec machine with a version of Ubuntu that's approaching a year old. Although Canonical have formally annouced that they're no longer supporting ppc, it appears to me that support has been winding down for some time. Having said that, if dapper is supposed to work on that machine, it should be fixed if there is a bug.

I don't know a solution to your problem, but [this]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html") is a good source of troubleshooting steps that can be followed.

---

### Post by stmiller on 2007-03-03
Ubuntu PPC does not work out of the box on G5 machines. Even though it is advertised on the ubuntu.com homepage 'for G5, G4, etc. macs..." 

The live CD does not work for powermac G5s; you have to install with the alternative CD. Among other steps to get thermal working... There are threads in this section if you search for info on getting it to run on a powermac G5. 

The ubuntu developers could care less about PPC. I've contacted them in the past with issues on powermac G5s and iMac G5s, but the kernel devs who make the ppc images don't give a crap, and told me so.

---

### Post by Uncle7 on 2007-03-03
Thanks for replying to you both.

I've got as far as installing the system from the dvd using the expert option from boot prompt.

Unfortunatly I chose to install to an external firewire disk only to discover when yaboot failed to install that this was as problamatic as live  failing to boot. (I found the lines on one attempt to boot into live showing that gnome display manager had failed and an error before saying that, "The file'/dev/PMU' dosn't exist")

Anyway I started mucking about trying to reinstall yaboot. I selected each of the partions it listed as possible root and one came up offering several options one of which was to open a shell script on this root partion.

I did and was able to login to the user I'd set up previously.

I've been looking at a lot of posts re the yaboot issue and I'm afraid it's mostly beyond me I 'feel' like I'm in the middle of a very complicated discourse with no idea of the concepts that have been defined at its start but also not realy knowing how to find the start.](*,) 

Any way.... is the fact I can login to the user on the instilation of any real help here.?

I'll continue to read around some more but again if some one could give me a walk through. ie if its going to help me get yaboot to work on the external disk a starting point would be helpful.

The post I've read are going to need a primer.

Thanks again
B

ps

I am aware that attempting to get things to work isn't wasted as a lot of learning takes palce in the proccess however given the official unsupported ness of ubuntu on ppc should I cut my losses here and look for another os. I tried to install net bsd several years ago on an old 8600 but got completley foxed by the device tree couldn't find the boot device etc etc. Is gentoo a long term option?

edit:

Have seemingly found boot device via open Firmware. Comes up with "
sbp2:Open ->login?
speed=ffffffff 2 2
spb2-startit=0 MAC-parts: LOAD (noninterposed) not supportedload-size=0 adler32=1

LOAD-size is too small

I'm assuming from this it _may_ be possible to manuely boot from OF?

Any advise greatly appreciated.

---

