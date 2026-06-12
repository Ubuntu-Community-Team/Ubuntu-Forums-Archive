---
title: "macbook pro: fedora 6 vs edgy"
date: 2006-09-10
forum: Apple PPC Users
---

### Post by goneskiing on 2006-09-10
Things I'm reading say Fedora 6 is more or less completely compatible with MacBooks - are these patches in the linux stock kernel and thus will be in Edgy or are they Red Hat specific and thus, Fedora 6 might be a better choice for running on the MacBook?  I'd rather stay with Ubuntu since I like apt-get so much more.  Right now running Dapper, I still don't have sound (15"), suspend doesn't work (hibernation does), and it reboots after so many minutes on screensaver when re-activated, and battery seems to drain fast (maybe hard drive not sleeping, display not dimming).  I haven't tried the camera yet.

---

### Post by jimmygoon on 2006-09-10
It goes without saying that Edgy will be better... whether or not all of your problems will be solved... no one (or at least I don't) know[s].

I would, though, say at least stick around until edgy, install it ... and then decide ;)

---

### Post by goneskiing on 2006-09-11
The screensaver bug has caused me to lose work now 3 or 4 times (just happened again 5 mins ago), so I need to do something different - My choices are 1) try edgy knot and see if fixed (which I haven't heard), 2) try Fedora 6 test and see if fixes (which others say works), or 3) can the Mac and buy a Thinkpad.  And Parallels is not the way I want to go for several reasons.

---

### Post by nhemingway on 2006-09-20
"It goes without saying that Edgy will be better"

Although I love apt, and have been happy with both Dapper and Edgy for a while now, this is BS. Linux is Linux, and the difference between the major distros is shrinking as technology improves -- both yum and apt are being overhauled for the latest distro releases, evolution is evolution, openoffice is openoffice, etc.

The distro that will be "better" for the MacBook will be the one that best supports the hardware platform without compiling custom kernels, pulling software from CVS, or otherwise hacking the system. So far, (as of September 20th) Edgy falls short in this area in several ways. I haven't tried FC6(testX) on the MacBook yet, but if Edgy doesn't make it come official release, then that might be a very good way to go. Of course, the ideal being "Macbuntu" -- although, I don't know if there's enough community support to maintain a pseudo-distro for a single vendor's hardware. Even if it is the best hardware out there :)

---

### Post by syxbit on 2006-09-23
best heardware out there ?
they have major overheating problems.
my buddy is on his 4th macbookpro
and all cause they wanna make it 1mm thinner???
i'll stick with Lenovo and Asus thanks

---

### Post by goneskiing on 2006-09-23
Edgy is not workable yet (at least on my Mac) and doesn't seem to have some of the support built in yet.  FC6 T3 crashed on X and won't recognize any display drivers like vesa.  I even tried FC6 T2 and that install hung on error not finding display.  

So I'm cutting my losses, accepting that the Mac was a bad decision, selling my MacBook Pro for a $1000 loss, and buying a Thinkpad.  I've probably lost an additional $4000 in productivity the last month.  Ouch.  Luckily Dapper on my Dell keeps working (though my Dell overheats and the CD is broken).

---

### Post by undead-monkey on 2006-09-25
Unfortunatly, i ont think anyone should have bought a new Macbook specificaly with Linux in mind. Windows on intel macs is still beta (fully suppored beta that works great mind you, but its still windows). I gave up on Ubuntu dual boot installs on my Black 2 GHz Macbook for now and just run Parallels until the support is better.

Sorry to hear you are ditching your Macbook, but for Linux right now, you are better of with a Thinkpad.

---

### Post by Entity on 2006-10-04
> **undead-monkey said:**
> Unfortunatly, i ont think anyone should have bought a new Macbook specificaly with Linux in mind. Windows on intel macs is still beta (fully suppored beta that works great mind you, but its still windows). I gave up on Ubuntu dual boot installs on my Black 2 GHz Macbook for now and just run Parallels until the support is better.

Sorry to hear you are ditching your Macbook, but for Linux right now, you are better of with a Thinkpad.

I did buy my black MacBook for Linux only in mind and Edgy works fine for me except on certain points :

- Suspend/Resume works only if I add exit 0 at the begining of /usr/sbin/laptop-detect ;

- I get weird kernel panics on system startup half of the time(that really sucks!) ;

- I still can't install Ubuntu alongside with Mac OS X and Windows because GRUB won't install to /boot instead of MBR even using the alternate CD (at least, the last time I tried)

I was able to install Ubuntu alone and even wrote an Howto regarding this -> [http://www.ubuntuforums.org/showthread.php?t=233243](http://www.ubuntuforums.org/showthread.php?t=233243)

Beside that the MacBook works a charm and it's a great machine and it will become more and more widespread, the Ubuntu devs will have to focus on these machines.

---

### Post by nhemingway on 2006-10-05
*"- I get weird kernel panics on system startup half of the time(that really sucks!) ;"*

add "noapic acpi=force irqpoll" to your kernel. This fixes the random panics on boot, and for me made suspend work 100% -- this came from the Gentoo wiki.

As for this Linux doesn't work BS, I was running Dapper, now Edgy, and there are forums confirming Gentoo and Fedora work. Edgy now doesn't even require any GRUB patching to install. I also bought a MacBook with the sole purpose of running Linux, and it is a much better put-together laptop than anything produced by Lenovo. Finally, as for the heat, 2GHz dual-core's produce heat. You can either have a loud fan blowing all the time or a laptop that heats up if you don't keep the CPU throttled down. This is not an Apple thing, but an Intel thing that affects all fast laptops. Mac users are used to slow but quiet machines (powerPC), so I think Apple tuned the cooling system on these laptops to be conservative with the fans. This makes them hot but quieter.

---

### Post by goneskiing on 2006-10-05
*As for this Linux doesn't work BS, I was running Dapper, now Edgy,* 

Which model are you running - it seems to matter.  My 15" pro did not have sound, I had trouble writing to DVD, the constant kernel panics, no suspend, ...) I had trouble with grub with dapper.  and knot 3 wasn't working.

It sounds like the new Edgy is working?  also does the kernel statements require a kernel recompile ?  Can you share details ?  

In desperation to get work done, I went out and bought a Lenovo 3000 - it was less than 1/2 the cost of the macbook - it runs Dapper great.  Sure it is slow (celeron dual core) and the res isn't the best 1200x800 but is quiet, cooler, 4 usb slots, card reader, vga outlet (no dongle required for LCD projectors).  

I'm deciding any day now to sell my new Mac - I don't want to run OSX and if I can't get the above things to work in Ubuntu, I don't want the machine.

---

### Post by nhemingway on 2006-10-05
I have a plain MB (not pro) -- and I'm sure that does matter. Edgy does work without hacking or recompiling things now, although it is still not perfect. As I've migrated from kernel to kernel towards the official Edgy release, suspend has taken various forms of broken. Also, my touchpad doesn't work in synaptics mode. As for the sound, what the different controls do in Linux is a little strange, but ultimately it all worked on the MB out of the box (both Dapper and Edgy). So, the point being, things ARE far from perfect on the MB at this point -- for me the recessed ports, trayless CD drive, magnetic power and lid, and lack of a "Made for Windows" sticker make up for it.

As a solution to these problems, well, at this point I'm strongly considering going back to Gentoo, just because it doesn't look like any of the bin distros are quite there yet. I think where I'm at right now is about as good as it's going to get on Edgy. And, Fedora, well, I find it very hard to believe their "we support MacBooks" stance, considering some of the hoops people are jumping through just to get things functional. I will still try FC 6 on October 11th, but my expectations are low. And, as for Gentoo, can't say I miss watching source code scroll by for hours, but "sometimes you just gotta race"

---

### Post by Entity on 2006-10-07
nhemingway :

> add "noapic acpi=force irqpoll" to your kernel. This fixes the random panics on boot, and for me made suspend work 100% -- this came from the Gentoo wiki.

Thanks! ;-)

> Edgy now doesn't even require any GRUB patching to install.

So I tried to install Edgy Beta using the alternative CD and GRUB doesn't install to /boot (/dev/sda3) on this GPT type disk but it works fine on MS-DOS type disk.

Were you actually able to install Edgy alongside with Mac OS X (and Bootcamp) on your MacBook? If yes which version and what method (alternative or live/install) did you use?

---

### Post by nhemingway on 2006-10-07
Entity:

I don't dual boot, so have always used an msdos disk label. I guess if removing OS X, this would make an extra step in the install, but it's been a while since I had OS X on my MB. 

Basically, I was referring to the fact that you no longer have to install the patched GRUB -- these patches have either been integrated or rendered obsolete by code changes. 

And, thanks for the how-to; that's how I found out about the disk label thing.

---

### Post by undead-monkey on 2006-10-07
I didnt mean to say Linux doesnt belong on MacBooks (I am running Fedora Core 6 Test 3 right now on my "BlackBook") I was just saying  buying a Macbook for linux isn't your best bet when many other decent laptops out there have better support for various distros.

Once Edgy has its final release, I will try that also, and  decide between Ubuntu and Fedora for my 'book.

---

### Post by stevetsai on 2006-10-17
My MBP is running dapper now. There are only two problems I have. I just can use webcam with ekiga, but I can not use it with kopete. I still can not use suspend.

Right now I set the FAN minimum speed to 3500 rpm and I got the  lower temperatur(45C).

---

### Post by martinbures on 2006-10-25
I have installed Dapper and Edgy on my macbook as well as Fedora Core 6.  Fedora just worked.  I didn't have to do anything.  As for saying that obviously edgy would be better, that is crazy.  Edgy is the most unstable thing that I have used in a while.  I had it on a desktop as well and while installing a package, it hung and never came back.  I used to use Fedora but tried ubuntu out and stayed with it for a while.  Recent investigation leads me to believe that the fedora product is more polished and consistent.

apt-get is just a package manager, by the way.  It works on fedora also.

---

### Post by Technoviking on 2006-10-25
Anyone managed to get Edgy to work on a Macbook Pro, that dual boots into OS X.

Mike

---

### Post by nhemingway on 2006-10-25
So, this thread was theoretical until yesterday AM when FC6 was released. I'd say this is probably the exclamation point on the end of the conversation. I installed FC6 today on my macbook and promptly went back to Edgy. I can understand that some things wouldn't work, but I'm seriously annoyed by the "first major distro to support intel based macs" (maybe not verbatim) comments in the offical Fedora wiki. This is just plain BS. These were broken (I'm sure there are more but this was pretty major):

1: GRUB installed broken, had to rerun grub setup
2: Touchpad broken -- works same as every other distro (sans Gentoo)
3: No wireless out of the box. So Atheros/madwifi may violate some free software policy -- then don't say the platform is supported.
4: Suspend to RAM/sleep broken
5: Had to copy my custom binary over for backlight control and bind F1/F2 to call it
6: Sound control didn't work via function keys
7: Compiz installed by default, but Fedora apparently doesn't include gconf-editor by default, so don't expect any out-of-the-box control over it
8: The one app Fedora has that Ubuntu needs (external monitor support) didn't work. The OK button stopped working if any non-VESA modes were selected, and if a VESA mode was selected the app would say something about xorg.conf being rewritten and tell you to restart X. WTF!!! If I wanted to change my xorg.conf and restart X, what good is the app?

My advice, OS X (w/ Parallels and/or Fink) or Edgy Eft.

---

### Post by martinbures on 2006-10-26
Lets not be silly here.  I'll make a deal with you - I'll stop using Fedora and switch back to Ubuntu until they include the wireless drivers if you stop using Ubuntu and switch to Fedora until Ubuntu includes the madwifi drivers in the default installation.

With respect to the installation, I must appologize.  I re-installed this morning(been pretty busy lately) and am VERY disappointed.  I used FC6, Test 2 and had no problems - I just couldn't get the madwifi drivers to compile.  Now, after installing the release, i get a kernel panic on boot.  Not cool.  I am going to do a network install tonight with the newest packages and see if this is fixed.  So I am sorry that I recommended it without trying it first - I figured that something like that would be safe.  

With respect to the compiz - I don't understand the problem.  Do you really use all of this eyecandy?  Besides the basic stuff, it is pretty obnoxious - I think that the first thing that I do is turn off the silly wobbly-windows.  The basic stuff is fine.  Look at the mac - they really only have basic subtle effects enabled.

GRUB installed fine - I had no problems there.

With FC6,T2, suspend worked no problem.  Maybe this is another regression problem.

I must admit that I never messed with the brigtness or sound level keys, so I don't know.

The nice thing that I have found with Fedora in the past is the developers are more accessable - in my opinion.  Every time I have filed a bug on Dapper or Edgy, be it standard PC or the macbook, I get very little response.  Of several bugs that I have filed against various Fedora versions, I have had lengthy back-and-forth help from the developer to resolve the problem.

In all seriousness, I just want a stable, clean linux that "just works" so that I can get work done.  I am tired of having to mess with it.  There really is not a whole lot of difference between the two distros.

---

### Post by martinbures on 2006-10-26
Entity - 

With respect to installing Edgy on a macbook, I don't think that it is possible to do.  A few people have posted that they did it but after asking them how they did it, either I got no response, or the response that came was "I did a dist-upgrade from Dapper."  That is fair but not really the same thing.

Additionally, I and others filed a few bugs against Ubiquity, the Dapper/Edgy installer, to see if they would fix it - thinking that Edgy is supposed to, well, push the edge.  No luck.  The developers said that it was not a priority.  Also, after reading about it on several forums, it sounds like Ubiquity is not an optimum solution.  It kind of sounds like it works fine for now but is going to need a substantial overhaul going forward.

---

### Post by paulnation on 2006-10-26
I could not get the GRUB to load correctly to dual boot OSX and Edgy.  I chose the largest free space and then let the installer choose defalts from there.  The problem is loading GRUB onto HD0.  It will not let you do it and I do not know where else to tell it.

---

### Post by nhemingway on 2006-10-26
martinb...

I've installed Edgy (not upgraded from Dapper) several times now as I've bounced between different distros, and the install is pretty near flawless. I did change the disk label to an msdos disk label manually, passed "noapic acip=force irqpoll" to the kernel, and I don't dual-boot. Maybe that's where the problem comes in for you/others. All three of these things (amongst others) were required to make Fedora work as well.

Edgy installs madwifi automatically for me, Fedora did not. Not sure I understand what is gained/lost here. It seems like one "just works", one just doesn't.

Compiz isn't critical, but this is late 2006 and this is a Mac that I'm pulling OS X off of. I used to exclusively run fluxbox, ROX filer, and Gentoo, but now I expect more from my computer. I have a job and real work to do, and I expect a modern OS that works as well and looks as good as its commercial competitors. That means Compiz, GNOME, and a binary distribution with a somewhat complete package list. I also turn off wobbly windows, but I do find the other "eye-candy" makes me more productive. It also makes me feel like I'm not fighting for somebody's free software principles, but making a sound choice for the best all-around OS.

Brightness and sound -- well, brightness requires a custom and hacked binary on all distros and sounds is just a matter of proper gnome keybinding config. I don't consider these to be that big of deal for Fedora. My problem is more that so many things didn't work, and I couldn't find a single thing that Fedora did better than Ubuntu. I still have a list of things I would lose by choosing the "officially supported" distro, and have yet to find something I would gain. 

Also, if you look back to the begining of this thread, you'll see that I was defending Fedora as a viable option because, well, Linux is Linux. It was very real technical experience that lead me to change my mind. Fedora is still probably a perfectly viable option on the Macbook, but technical demerits asside, I personally wouldn't go that way just because of the big lie on their wiki.

---

### Post by kruppa on 2006-10-27
Well I waited until the official release of Edgy before upgrading Dapper  on my MacBook (you cannot speak out about a system in alpha, beta or even release candidate).
The upgrade failed, but that was my fault (I'm combing Mac OS X, Ubuntu and Windows, that last one mainly for my BCD2000 :-( ) and the disk filled up with updates (stupid me).

The APIC problems were solved by adding "noapic acpi=force irqpoll" to the boot options of the kernel (nhemingway: maybe correct your message acip=acpi, could mislead searching users who don't look further than your message), so in lilo.conf add the line: append="noapic acpi=force irqpoll".
Previously I tried just "noapic" but that resulted in very slow mouse and keyboard input (because neither APIC neither ACPI was used I asume), booting Dapper in a normal way worked if no USB mouse was connected, that wasn't true for Edgy - so thanks a lot people for the solution! And again it came from the Gentoo forums, they are so good!

Grub has to be patched or replaced by lilo only if you combine EFI with MS-DOS filesystem tables - which is the case if you install Mac OS X too (wich only understands EFI).

Check the thread "MacBook triple boot success!" on this forum for a good howto with links to external background info, pretty interesting to know about when tweaking you MB, just keep in mind that the kernel options are really crucial for Edgy.
Also [http://bin-false.org/?p=17](http://bin-false.org/?p=17) gives a good and simple install.
And [http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453) gives some hacks for the backlight and a Belgian layout Xmodmap.

Combing different howto's/guides/tips resulted in a perfect install described in the guide (well skipped some things and did some things in another way). The only glitch I have is that sometimes booting results in a black screen before even lilo is started, rebooting solves it off course.

So with this information in mind, why does FC6 work out of the box?
Is it just because it uses ACPI or it picks the right one at boot time?
And is it because it uses lilo? Or patched grub for supporting EFI?
Or does it only install out of the box when installing only FC6, not dual or triple?
I don't and won't use Fedora (apt and portage I like, the lesser RPM's on my system the happier I am ;-) ), but am curious about this...

---

### Post by frigaut on 2006-10-27
kruppa: does your sound work? and mike?
I have a macbook pro 15" and have the usual issue with speakers and microphone not working. Curious to know if this has been solved with edgy.
(how about hibernate/suspend???).

---

### Post by idn on 2006-10-28
Mic does not work for me either which is really annoying coz i cant use gizmo or gaim

---

### Post by frigaut on 2006-10-29
...or skype, yes.
Well, the situation is not better with edgy (as far as microphone is concerned). I installed it yesterday and no change in sound status.

---

### Post by Technoviking on 2006-10-29
> **frigaut said:**
> kruppa: does your sound work? and mike?
I have a macbook pro 15" and have the usual issue with speakers and microphone not working. Curious to know if this has been solved with edgy.
(how about hibernate/suspend???).

Seem to be.

---

### Post by anzevi on 2006-11-12
My 2 cents about this matter...

I had both, FC6 and edgy on my MacBook (13"). Here are my experiences:

1) Ubuntu edgy:
- install went fine, installer crashed at grub install, corrected by hand, rebooted, and all went well
- by default sound worked, hotkeys for sound worked, wifi worked (atheros chipset), Function keys worked, eject key worked, the only thing that i needed to install was "915resolution" for the resolution to appear correctly. Also made some small hack to get hotkeys for brightness working (as described here [https://wiki.ubuntu.com/MacBook)](https://wiki.ubuntu.com/MacBook)). Overall I'm very satisfied with the edgy on MacBook.

2) Fedora Core 6:
- install went without a problem, rebooted and it worked fine. The sound and resolution worked fine, however non of the hotkeys worked, there were no wifi drivers included, had a lot of problems with media codes, although they worked fine on other PC, Function keys (F1 - F12) didn't worked, eject key didn't work... 

Overall i would say edgy really has a great support from the box for MacBook and on the other hand, Fedora is just not there yet...

Thanks for reading ;)

---

