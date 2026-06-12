---
title: "Dumb Dual Boot Question..."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by john wagner on 2007-07-21
Okay, so here it is...

I'm running Dapper (6.06.15-28-386 {686}) on an HP Pavillion notebook, 2 gig ram, 160 gig SATA HD.  No Windblows at all.  I recently purchased a Western Digital 500 gig backup external HD.  For about 4 months I've been just using Dapper (nuttin like jumping in blind!).

What I need (not want to) is too install Windblows XP on the external HD and have a dual boot system (found out I need Windblows for several apps that dont have Linux equivelents, and for accessability tween machines).  I DO NOT WANT Windblows on the laptop itself.  Much rather just use Dapper as much as I can, Hook up the external HD when I NEED the Windblows, is it possible to do this?  And still have all the drivers etc for Windblows do what they need too?

All the threads I've checked into tell how to install both on single HD with a quick finger selecting which one to boot to.  

Oh yeah, I aint gonna waste the entire 500 gig space on Windblows, was gonna also install Mandiva, SUSE, Knoppix, Ubuntu 7.04 so's I can play with em too.  Heh.  Or should I just go LIVECD for those?  Am I overcomplicating things?

HELP!!!!!!

Thanx in advance!

I really LOVE the speed, the ease and the convienence of Dapper, the more I use it the more I HATE Windblows!

john

---

### Post by Ocxic on 2007-07-21
yes, you can install to a usb hardrive and do what you wish, I'm just unsure if you can install windows to it, I've never attempted such a thing. you'll just have to make sure that you select the poper OS to load, when your not using the USB drive.

the guide to installing on a single, or dual Hard drive setup is basically the same, just chose your other drives partitions, when your installing.

I'm just unsure if you can install windows onto a usb/external drive..

---

### Post by koganinja89 on 2007-07-21
whether or not you can install windows... if you do... In linux you need to make sure that your GRUB or LILO bootloader has the entry for the windows partition should look nothing close to this but have the same general idea:

blah blah blah about linux and its stuff... hda1 or whatever (0,0)

then you add your crap about windows, it should NOT be a "hd'x'" it should be like a "sd'x'" something

Sorry I am so vague it's just that when you look at it in the /boot/grub/ folder you will understand what to edit. and I am on my win pc right now.

BTW. it is at the very bottom of the file that you edit.

this is if you already have Linux installed.
__________________________________________

---

### Post by pyros on 2007-07-21
I personally doubt that windows will install to a usb drive without some ammount of trickery on your part.
Take a look here for some instructions:
[http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)

---

### Post by john wagner on 2007-07-21
Yeah, that's what I'm wondering.  Everything I've seen points to internal Master/slave deals.  I suppose I could install Windblows on the laptop, partition the HD, then use the USB drive as storage for both OS's...  But I really DON'T want Windblows on the laptop at all, just too vulnerable, too long to boot, just crappy overall heh....  Rather have option to select it when/if I need it, away from internet access until then, you know.......  Don't have the external drive yet, it's on the way (just bought, about 2 hrs ago...), so I can't tell you if it has an option built in to do this....

Any one know if what I want can be done?  Is it possible to install Windblows into a partion on an external USB drive?  As slave to the laptop Linux HD?

---

### Post by kc5hwb on 2007-07-21
Why not just run VMware or VirtualBox with XP in it?  That is what I am doing, with VB, and it works great.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by pyros on 2007-07-21
> **john wagner said:**
> Any one know if what I want can be done?  Is it possible to install Windblows into a partion on an external USB drive?  As slave to the laptop Linux HD?

See my previous post for a link to instructions on installing windows xp to a usb drive.

---

### Post by koganinja89 on 2007-07-21
you could use a BARTPE version of windows to make it bootable from the external... but the downside is that it is crappy dumb, and you will berly get to use it's "winblows" functions

It is ment to be plung and play though :)


oh yeah and use the PEBuilder prog to make it.

---

### Post by john wagner on 2007-07-21
> **pyros said:**
> I personally doubt that windows will install to a usb drive without some ammount of trickery on your part.
Take a look here for some instructions:
[http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)

Took a look, I think this MAY work.  Won't know for sure until I get my HD delivered.  It looks promising tho, very promising!  Looks like work too.  Sigh.  Thanks!

Keep em coming!  I intend to be thoroughly grounded in many diverse ways to try this by the time I get my HD!  Preparation!

Anyone reading this, do you know of anyone that has had success at this?

Thanx!

john

---

### Post by john wagner on 2007-07-21
> **kc5hwb said:**
> Why not just run VMware or VirtualBox with XP in it?  That is what I am doing, with VB, and it works great.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Thought about this one too!  I just haven't used any VMWare at all, no clue abt it.  I read several articles and How Too's on installing and using VMWare tho.  Quick question, where do you get the virtual Windblows from???  A location on laptops HD?  Don't understand that part at all, seems like it should be impossible, kinda like perpetual motion...  I'm probably missing something very simple and obvious here tho...

john

---

### Post by Nekiruhs on 2007-07-21
> **john wagner said:**
> Thought about this one too!  I just haven't used any VMWare at all, no clue abt it.  I read several articles and How Too's on installing and using VMWare tho.  Quick question, where do you get the virtual Windblows from???  A location on laptops HD?  Don't understand that part at all, seems like it should be impossible, kinda like perpetual motion...  I'm probably missing something very simple and obvious here tho...

john
You just install from the windows CD. VMWare Server reads your real CD, and makes the "Fake" computer see it to "boot" from.

---

### Post by john wagner on 2007-07-21
> **Nekiruhs said:**
> You just install from the windows CD. VMWare Server reads your real CD, and makes the "Fake" computer see it to "boot" from.

Then what?  Does the VMWare permanently store the virtual Windblows somewhere on laptop?  Or do you need to load cd prior to each session?

If the later, how do you whip apps in and out on other cd's?  I must be overcomplicating this....  Heh...


john

---

### Post by koganinja89 on 2007-07-21
just like installing something on your hard drive it takes up space. An entire virtual drive... however much information you have on it... so it will take up about 4 gigs when you first install it.

---

### Post by kc5hwb on 2007-07-21
"virtual machine" basically means a fake OS.  It is like running an app... except that this app is the entire Windows XP OS.  Under that OS, you can install and run ANYTHING that a windows machine will do.  You can also install other Linux versions or MAC, FreeBSD, etc...

---

### Post by jayson.rowe on 2007-07-21
Yeah - I use VMWare Server - love it - I have XP, Vista, 2003 Server, PCLinuxOS and Fedora loaded - I even have 2Gigs of ram allocated to the Vista machine when it's running - (I have 4 gigs on my box) and when I load up the vista virtual machine, and look at it's Windows Experience Scores, they are almost the same as when I had vista running on my machine clean w/ the exception of the video scores (which are a 1, and VMware+Vista = No Aero, so I have the Vista "Basic" interface, which is fine w/ me)

---

### Post by john wagner on 2007-07-21
Okay, VMWare is all virtual, I get that.  BUT, I have read (Linux Magazine, July [I think]) that the virtual Windblows are open to a virtual virus (jeez that sounds weird).  So, do you have to load a virtual virus blocker too?  I have read that it CAN (altho how likely it is I don't know) create a backdoor into Linux.  Allowing evil, vile virii into the clean pure system of Linux.

Weird...  Yes, I know I am overcomplecating things...  I went to the VM website listed on page one herein this thread, and it says the VMWare is designed for developers etc..and is incomplete as is.(the free version).  Is the system available in a complete form somewhere (as free software), all libraries/repositories/installation requirements etc...

May give her a try too....  But it still bugs me that Windblows will be on the laptop HD.

john

---

### Post by john wagner on 2007-07-21
> **john wagner said:**
> Okay, VMWare is all virtual, I get that.  BUT, I have read (Linux Magazine, July [I think]) that the virtual Windblows are open to a virtual virus (jeez that sounds weird).  So, do you have to load a virtual virus blocker too?  I have read that it CAN (altho how likely it is I don't know) create a backdoor into Linux.  Allowing evil, vile virii into the clean pure system of Linux.

Weird...  Yes, I know I am overcomplecating things...  I went to the VM website listed on page one herein this thread, and it says the VMWare is designed for developers etc..and is incomplete as is.(the free version).  Is the system available in a complete form somewhere (as free software), all libraries/repositories/installation requirements etc...

May give her a try too....  But it still bugs me that Windblows will be on the laptop HD.

john

Just thought of something...  If I use VMWare, can I load it into a Linux partition on the External HD?  Then open it and load a virtual Windblows onto it?  Anyone know?
Desperately trying to keep Windblows creepy fingers off my pie!

john

---

### Post by koganinja89 on 2007-07-21
theoretically anything is possible, don't be so peraniod and trust us:

there are like 20 viruses for linux
there are literally billions of viruses for windows

and how many of those do you think actually target the vmware xp to harm linux

come on...

---

### Post by koganinja89 on 2007-07-21
> **john wagner said:**
> Just thought of something...  If I use VMWare, can I load it into a Linux partition on the External HD?  Then open it and load a virtual Windblows onto it?  Anyone know?
Desperately trying to keep Windblows creepy fingers off my pie!

john

flawless idea. should work perfectly.

---

### Post by john wagner on 2007-07-21
> **koganinja89 said:**
> theoretically anything is possible, don't be so peraniod and trust us:

there are like 20 viruses for linux
there are literally billions of viruses for windows

and how many of those do you think actually target the vmware xp to harm linux

come on...

LOL!  Yes I know, I'm not really this paranoid re virii.  They are valid questions tho, does the virtual Windblows create an actual backdoor to your machine?  The literature says yes.  BUT, out of zillions of machines, what kind of actual numbers are we looking at?

I DO, however, want Windblows off the laptop.  I want to be able to physically disconnect it from my laptop.  I have had waaay too many nasty things happen via Windblows (and yes, I ran all the aftermarket firewalls, blockers, checkers, router firewalls out the butt...still they got in...).  When the last attack killed the laptop's HD, I bought a bigger (120 to 160) HD and formated it with Dapper.  Haven't touched Microsnnot since on that machine.  But, I need to use it, sigh.  Been using the wifes laptop for that, but she's been giving me the fisheye.....

So, can I install VMWare in external HD then load virtual Windblows on it?  If yes, how?  Do I need to load Dapper onto the new HD, then have 2 versions of Dapper( Laptop and external HD), or can I just load it on as a USB storage thingee?


john

---

### Post by pyros on 2007-07-21
While it is technically possible, virii have seldom caused physical damage to hardware (the only example I know of is chernobyl), but to get to the point, virtual machines are rather secure. many servers run in virtual machines for that very reason. Look at it this way, vm's are used by developers for the very reason that if the software in the vm fails spectacularly, it will not affect the non-virtual environment. And, yes, you can put the vmware image on another physical volume, like the usb hard dirve.

---

### Post by john wagner on 2007-07-21
> **pyros said:**
> While it is technically possible, virii have seldom caused physical damage to hardware (the only example I know of is chernobyl), but to get to the point, virtual machines are rather secure. many servers run in virtual machines for that very reason. Look at it this way, vm's are used by developers for the very reason that if the software in the vm fails spectacularly, it will not affect the non-virtual environment. And, yes, you can put the vmware image on another physical volume, like the usb hard dirve.

Thanks!  So, next question....  How hard is it to round up all the libraries/repositories and program needed for a VMWare install on Dapper?

Just go to the VMWare site and load the one for Dapper?

 ( [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) )

Will it have everything I need?

john

---

### Post by pyros on 2007-07-21
try taking a look at this forum postin the tutorials howtos section:
[Run a Native Windows Installation on Ubuntu with Vmware Player](http://ubuntuforums.org/showthread.php?t=380699)

---

### Post by john wagner on 2007-07-21
> **pyros said:**
> try taking a look at this forum postin the tutorials howtos section:
[Run a Native Windows Installation on Ubuntu with Vmware Player](http://ubuntuforums.org/showthread.php?t=380699)

Thanx!  Was just downloading from the site and got a vmod missing notice, gotta read some more!

john

---

### Post by Tegdap on 2007-07-21
I tried to set up an external HD as well so that I could boot to XP from it.....my hardware supports booting from a USB device.  I thought this would work, just install it on the external then choose boot from USB however that did not work.  Please post if you find a way to do it.

---

### Post by john wagner on 2007-07-21
> **Tegdap said:**
> I tried to set up an external HD as well so that I could boot to XP from it.....my hardware supports booting from a USB device.  I thought this would work, just install it on the external then choose boot from USB however that did not work.  Please post if you find a way to do it.

Sure will!  Did ya look at this link?  [http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)  Provided by Pyros.  Looks the most complete, other than going virtual I mean.

thanx

john

---

### Post by john wagner on 2007-07-21
If nothing else, the Virtual route will work.  My Dapper (apparently) had the libraries and VM.  All I had to do was install and get out of the way.

Gonna hold off with installing Windblows into the VMPlayer however.  Gonna wait until I get my HD and try Pyro's suggestion first (via USB etc..., the link).

Thanx all, if you guys can come up with more ideas I'd LOVE to hear them!  Whatever I end up with, I'll bump the thread and let you all know what and if it works...

Again, thanx


john

---

### Post by bselk on 2007-07-21
Has anybody tried the vmware in add programs? it sort of works, but it says it can't open a supporting file. how do you fix this?

---

### Post by Ocxic on 2007-07-22
"sudo apt-get instsall vmware-server"  
you need vmware-server not vmware-player, I believe add/remove installs the latter

---

### Post by john wagner on 2007-07-24
> **Ocxic said:**
> "sudo apt-get instsall vmware-server"  
you need vmware-server not vmware-player, I believe add/remove installs the latter

So, VMPlayer aint the right one?  I need to dump it and do VMServer?  Why?  I'm not running off a server....

john

---

### Post by Ocxic on 2007-07-25
vmware-server, wil let you create, delete and manage your virtual machine's vmware-player, will only run an already created machine.

---

