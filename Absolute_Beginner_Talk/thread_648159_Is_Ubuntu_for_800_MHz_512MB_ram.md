---
title: "Is Ubuntu for 800 MHz/ 512MB ram?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by wildnewbie on 2007-12-23
I have XP installed on my Slow computer, and it works fine.  I thought my computer would run a little faster if I install Ubuntu.  But Ubuntu doesn't appear to be faster than XP for the same hardwares.  Also, I am having a little problem with the video driver, well.  I am not even sure what's the problem is, but after I installed GStreamer codec, my display is showing stripes of colors and there was nothing I can do, I did reinstalled Ubuntu.  I tried X-Ubuntu and get the same problem after installing GStreamer.  I haven't get to use X-Ubuntu that much since it got me to the stripes of color screens.  What I want is doing everything I can do in XP, and learning more stuffs about Linux, but my biggest problem is installing flash, java, and other stuffs for basis computer use.  Is there any other way to make my system faster during the installation process.  I have a swap partition 1 gig, and 8 gig partition for "/", Should I be making "/boot", "/usr", etc separately?  Thanks in advance.

---

### Post by Sef on 2007-12-23
10 It's not going to be too fast on your system.   Xubuntu or [Fluxbuntu]("http://fluxbuntu.org") would be faster.

2) What video card do you have?

3) For installing Flash, java, etc, use Add/Remove (Applications > Add/Remove > set top right box to "All Available Applications".)  In the search box then type

a) Sun Java 6 and pick the top option

b) Adobe Flash 

c) What else do you want to install?

---

### Post by Wiebelhaus on 2007-12-23
Yea , I'd go with a smaller distro , Ubuntu is a high end state of the art OS , it is not tailored for slow or old hardware such as many other distro's are.

Debian
CentOS - Choice
Fluxbuntu - For very old hardware
Mint - Choice
PClinuxOS - Choice
Xubuntu - Choice but no native network browser
There's more , those are just more or less the most popular ones.

---

### Post by gn2 on 2007-12-23
For that hardware I would recommend Xubuntu 7.04.

And add all the useful bits with this command:
>  sudo apt-get install ubuntu-restricted-extras 

---

### Post by wildnewbie on 2007-12-23
My Video Card is Intel 810,  I just installed flash thruogh firefox, and still need some codec from GStreamer.  I installed both and watching video on Youtube at one frame per second.  The sound was a little skippy too.  Anway, I am going to reinstall X-Ubuntu soon.  Thanks for your help.  

Does it help my computer to run any faster, if I have different partition for different subdirectories, like /usr and /boot and stuffs, I don't it that much.  I can only allocate 8 gig 8 gig for Ubuntu, 1 gig is already allocated for /swap.

---

### Post by philinux on 2007-12-23
Well maybe my expectations weren't too high but I'm very happy running ubuntu on this old croc. I've been running it since July but come January it's time for a new base unit.

---

### Post by wildnewbie on 2007-12-23
Xubuntu - Choice but no native network browser

What does "no native network browswer" mean?

You can't see other computer on the same network? or can't see files on other computer's in the same network?

---

### Post by Wiebelhaus on 2007-12-23
> **wildnewbie said:**
> Xubuntu - Choice but no native network browser

What does "no native network browswer" mean?

You can't see other computer on the same network? or can't see files on other computer's in the same network?

There's no native network browsing function.

"You can't see other computer on the same network? or can't see files on other computer's in the same network?" 

precisely, not without mounting the network and configuring it to do it at boot , basically doing manually , that's why I don't like it.

Anyway, there's many more out there.

---

### Post by rgb1701 on 2007-12-23
Your plight highlights an ugly secret in the FOSS, and in particular Ubuntu, community.

I build myself machines with 384-512MB of RAM with P3 600MHZ CPUs that run XP SP1 smoothly, in fact, snappier than most multi core Vista boxes!  To most normal people, they never know or care they are running on what would be considered such a low spec machine by today's standards, because the user interaction and GUI response is outstanding, even on an 8MB Matrox G450 video card!

As an example, for a 9 year old niece I am currently building a P3 600Mhz, 384MB box with a GeForce FX5500 video card- more than adequate hardware to run all web sites, Flash, Java and any apps she might need on XP SP1.  I just tested Youtube and a Java games site- Pogo.com, on a similar spec machine (P3 600, 512MB, only a lowly Matrox 8MB G450) with XP SP1, and Flash video (cbs.com, youtube, etc) runs *perfectly*.  

On a stock Ubuntu 7.10 load on another P3 600/384MB/FX5500 box, Youtube/flash video displays in slow motion, choppy, a few frames per second!  Also, Java runs in slow motion on the Ubuntu load, but at full speed on the XP SP1 load with similar hardware. I updated xorg.conf with lots of hardware acceleration and XV options, with no improvement to Flash video.  I am using the nvidia "Restricted driver" that defaults on 7.10.

Folks, this is a HUGE problem in the Linux/Ubuntu community (I haven't tested other distros for Flash and Java speed on these boxes yet).  Flash and Java are integral, critical components of the web now.

It doesn't matter that Adobe and Sun may be at fault- the fact is, I can build XP SP1 machines all day long that would satisfy 95% of the desktop user population re: user interface response time and Flash/Java performance, using 500Mhz-700Mhz P3 CPUs and 256-384MB of RAM.

Ironically, this spec level of machine is the future- the OLPC's, eePC's and similar x86 <1Ghz boxes with around 512MB or less, for either mobile or small form factor desktop uses.  Another company just announced a credit card sized all in one x86 CPU/chipset/motherboard, ripe for handheld uses and Linux exploitation, but not if the current state of bloat and poor resource utilization and user experience performance doesn't improve.

And don't mention FLuxbox or Xfce as alternatives for better GUI performance and/or lower memory requirements- I see NOTHING in Gnome/KDE from a user perspective that stock XP doesn't have re: GUI widgets and GUI functional elements and design (depending on XP theme) from a Joe Six Pack user perspective.  This problem has been festering for a long time in the FOSS window manager space, and some real optimization needs to happen in the Gnome and KDE projects.

While some incredible progress has been made- Compviz, Synaptic package management and repositories, general user friendliness-  the FOSS community *really* needs to focus on optimization.

 The bogey isn't Leopard or Vista- the functional and performance target is XP SP1.  Developers need to keep a real, honest to goodness 600Mhz P3 box (not an emulated one, or a throttled current CPU) around for performance testing against XP SP1- if the Linux distro doesn't boot as fast, run video, Flash, or Java as fast, or execute the same programs (when available for apples-apples, like Oo, etc) as snappy as XP SP1 on the same hardware, someone needs to roll up their sleeves and figure out why  and work to achieve resource and performance parity (or better) with the XP SP1 "reference" platform.

Sorry for the rant, but now I'm up against the wall.  I need to finish the P3 600Mhz box for my niece for Christmas, and I was looking forward to rolling out Linux for the first time to her family (5 member household, parents plus 3 kids), having sung the praises of Linux for years while they used XP and Win98.  They were looking forward to Linux, too.

And now when it's Linuxes' time to shine, it's two steps forward and one step back (better than several years ago when it was one step forward and two back ;) ).

Now I have a bad choice- let the machine go out with poor Flash/Java performance on websites my 9 year old niece will use often, or cave in and put XP Sp1 on the box... :(

---

### Post by Wiebelhaus on 2007-12-23
> **rgb1701 said:**
> Your plight highlights an ugly secret in the FOSS, and in particular Ubuntu, community.

I regularly build machines with 384-512MB of RAM with P3 600MHZ CPUs that run XP SP1 smoothly, in fact, snappier than most multi core Vista boxes!  To most normal people, they never know or care they are running on what would be considered such a low spec machine by today's standards, because the user interaction and GUI response is outstanding, even on an 8MB Matrox G450 video card!

As an example, for a 9 year old niece I am currently building a P3 600Mhz, 384MB box with a GeForce FX5500 video card- more than adequate hardware to run all web sites, Flash, Java and any apps she might need on XP SP1.  I just tested Youtube and a Java games site- Pogo.com, on a similar spec machine (P3 600, 512MB, only a lowly Matrox 8MB G450) with XP SP1, and Flash video (cbs.com, youtube, etc) runs *perfectly*.  

On a stock Ubuntu 7.10 load on another P3 600/384MB/FX5500 box, Youtube/flash video displays in slow motion, choppy, a few frames per second!  Also, Java runs in slow motion on the Ubuntu load, but at full speed on the XP SP1 load with similar hardware. I updated xorg.conf with lots of hardware acceleration and XV options, with no improvement to Flash video.  I am using the nvidia "Restricted driver" that defaults on 7.10.

Folks, this is a HUGE problem in the Linux/Ubuntu community (I haven't tested other distros for Flash and Java speed on these boxes yet).  Flash and Java are integral, critical components of the web now.

It doesn't matter that Adobe and Sun may be at fault- the fact is, I can build XP SP1 machines all day long that would satisfy 95% of the desktop user population re: user interface response time and Flash/Java performance, using 500Mhz-700Mhz P3 CPUs and 256-384MB of RAM.

Ironically, this spec level of machine is the future- the OLPC's, eePC's and similar x86 <1Ghz boxes with around 512MB or less, for either mobile or small form factor desktop uses.  Another company just announced a credit card sized all in one x86 CPU/chipset/motherboard, ripe for handheld uses and Linux exploitation, but not if the current state of bloat and poor resource utilization and user experience performance doesn't improve.

And don't mention FLuxbox or Xfce as alternatives for better GUI performance and/or lower memory requirements- I see NOTHING in Gnome/KDE from a user perspective that stock XP doesn't have re: GUI widgets and GUI functional elements and design (depending on XP theme) from a Joe Six Pack user perspective.  This problem has been festering for a long time in the FOSS window manager space, and some real optimization needs to happen in the Gnome and KDE projects.

While some incredible progress has been made- Compviz, Synaptic package management and repositories, general user friendliness-  the FOSS community *really* needs to focus on optimization.

 The bogey isn't Leopard or Vista- the functional and performance target is XP SP1.  Developers need to keep a real, honest to goodness 600Mhz P3 box (not an emulated one, or a throttled current CPU) around for performance testing against XP SP1- if the Linux distro doesn't boot as fast, run video, Flash, or Java as fast, or execute the same programs (when available for apples-apples, like Oo, etc) as snappy as XP SP1 on the same hardware, someone needs to roll up their sleeves and figure out why  and work to achieve resource and performance parity (or better) with the XP SP1 "reference" platform.

Sorry for the rant, but now I'm up against the wall.  I need to finish the P3 600Mhz box for my niece for Christmas, and I was looking forward to rolling out Linux for the first time to her family (5 member household, parents plus 3 kids), having sung the praises of Linux for years while they used XP and Win98.  They were looking forward to Linux, too.

And now when it's Linuxes' time to shine, it's two steps forward and one step back (better than several yeas ago when it was one step forward and two back ;) ).

Now I have a bad choice- let the machine go out with poor Flash/Java performance on websites my 9 year old niece will use often, or cave in and put XP Sp1 on the box... :(

Good write up , Posts like this make an active board , But I must reiterate....

Ubuntu is a high end state of the art OS , Not designed to run on old hardware , no one would argue that , for old machines there are plenty of choices.

---

### Post by wildnewbie on 2007-12-23
rgb1701,

Just finish installing X-Ubuntu, hate to say this but I don't think Ubuntu is made for my slow comp.  There's also a problem with the terminal too.  I am going to have to make another post for the terminal problem.  Thanks guys, I gonna have to look at some other distributions.

---

### Post by Wiebelhaus on 2007-12-23
> **wildnewbie said:**
> rgb1701,

Just finish installing X-Ubuntu, hate to say this but I don't think Ubuntu is made for my slow comp.  There's also a problem with the terminal too.  I am going to have to make another post for the terminal problem.  Thanks guys, I gonna have to look at some other distributions.

Try [PCLinuxOS]("http://www.pclinuxos.com/") for the most part it's terminal-less , other than media codecs you'll hardly ever touch the terminal.

---

### Post by rgb1701 on 2007-12-23
> **sx66gns said:**
> Good write up , Posts like this make an active board , But I must reiterate....

Ubuntu is a high end state of the art OS , Not designed to run on old hardware , no one would argue that , for old machines there are plenty of choices.

I see nothing in the user interface of Ubuntu 7.10 (Gnome) that should be slower than XP.  On the plus side, with the "Normal" Visual Effects active (Compviz), the 3D-accelerated windows and dialogs appear snappier than an XP load.

Also, keep in mind that the XP SP1 600Mhz box is XP Pro- I think there is content, system &  process services parity between the XP Pro and Ubuntu 7.10 loads on the 600MHz boxes, so I don't buy the claim that Ubuntu is a "high end" distro.  The Ubuntu folks need to send feedback to the upstream projects to get their act together and optimize their routines to achieve XP Pro resource footprint and performance bogeys, preferably better them.  It's pretty scary it's come to this.

Also, Ubuntu 7.10 boot time is over 2 minutes on the 600Mhz box, but only 60 seconds or less  on XP SP1 Pro.  I don't know if Ubuntu optimizes the boot order after several boot/shutdown cycles like XP does -to be fair, the XP 600Mhz machine has been booted/shutdown 50-60 times over the past year, and has self-optimized its system files over that time.

IMO, just like Microsoft dropped everything and did *only* security fixes from 2002-2004, the Ubuntu/FOSS community needs to basically do *nothing* but user interface/window manager/Flash/Java/video driver optimization until they achieve performance parity with Xp Pro.  

And that isn't just *my* opinion- the Mom's, 9 year old nieces nephews, and J6P's of the world want and need to use the Youtubes and Pogo.com's of the world.  And the amount of perfectly good 500Mhz-900Mhz machines out there with 2000-2004 vintage video cards is staggering, and will only *grow* (eePc, OLPC, credit card x86, etc).  This is a HUGE opportunity for Linux to shine, but if something isn't done to address the performance issues by year end 2008, I fear that a lot more XP licenses will be sold for these machines :(

---

### Post by Wiebelhaus on 2007-12-23
> **rgb1701 said:**
> I see nothing in the user interface of Ubuntu 7.10 (Gnome) that should be slower than XP.  On the plus side, with the "Normal" Visual Effects active (Compviz), the 3D-accelerated windows and dialogs appear snappier than an XP load.

Also, keep in mind that the XP SP1 600Mhz box is XP Pro!  So, I think there is content, system &  process services parity between the XP Pro and Ubuntu 7.10 loads on the 600MHz boxes, so I don't buy the claim that Ubuntu is a "high end" distro.  THe Ubuntu folks ned to send feedback to the upstream projects to get their act together and optimize their routines to achieve Xp Pro resource footprint and performance bogeys.  It's pretty scary it's come to this.

also, Ubuntu 7.10 boot time is over 2 minutes on the 600Mhz box, but only 60 seconds or less  on XP SP1 Pro.  I don't know if Ubuntu optimizes the boot order after several boot/shutdown cycles like XP does -to be fair, the XP 600Mhz machine has been booted/shutdown 50-60 times over the past year.

IMO, just like Microsoft dropped everything and did *only* security fixes from 2002-2004, the Ubuntu/FOSS community needs to basically do *nothing* but user interface/window manager/Flash/Java/video driver optimization until they achieve performance parity with Xp Pro.  

And that isn't just *my* opinion- the Mom's, 9 year old nieces nephews, and J6P's of the world want and need to use the Youtubes and Pogo.com's of the world.  And the amount of <1Ghz machines out there with 2000-2004 vintage video cards is staggering.  This is a HUGE opportunity for Linux to shine, but if something isn't done to address the performance issues in 2008, I fear that a lot more XP licenses will be sold for these machines :(

May I ask what Anti-Virus & Anti- Spyware your using? any content protection , firewalls?

---

### Post by rgb1701 on 2007-12-23
> **sx66gns said:**
> Try [PCLinuxOS]("http://www.pclinuxos.com/") for the most part it's terminal-less , other than media codecs you'll hardly ever touch the terminal.

But will *any* other Linux distro alleviate the poor Flash and Java performance on 500Mhz-800Mhz boxes?  Or is this an Adobe/Sun optimization problem?  Or a Linux video API/video driver problem?

---

### Post by rgb1701 on 2007-12-23
> **sx66gns said:**
> May I ask what Anti-Virus & Anti- Spyware your using? any content protection , firewalls?

On which OS?

The XP Pro box has ClamWin (doesn't actively scan), and has Outlook and IE disabled, Firefox only to address spyware, and only Gmail and Yahoo Mail for email (both auto scan attachments for viruses).  No software firewall- only use the NAT in the attached Linksys cable modem router and have never had an issue with any of the XP Pro SP1 clients using this setup.

On the Ubuntu 7.10 load, all defaults, and I don't think any software firewall is running, unless it is enabled by default.  I actually turned off a lot of services on the Ubuntu 7.10 load, like Bluetooth, CPU power management, and any other service I thought it didn't need as a desktop.  Youtube video still runs in frame by frame slow motion.

---

### Post by Wiebelhaus on 2007-12-23
> **rgb1701 said:**
> But will *any* other Linux distro alleviate the poor Flash and Java performance on 500Mhz-800Mhz boxes?  Or is this an Adobe/Sun optimization problem?  Or a Linux video API/video driver problem?

Aye , some would say it's a adobe performance issue and that the linux port isn't getting the attention it deserves and I would mostly agree , but on the other hand Flash runs fine in Fluxbuntu on my test cyrix w/ 192 mb of pc100 , The 95's & 98's we get in the shop where people say "Dude , youtube is jerky" there's honestly no fix for it......those people are not going to pay 200 bucks for an XP key that will still run like crap once the proper protection is put into place , unless the nine year old likes porn pop ups.

---

### Post by rgb1701 on 2007-12-23
> **sx66gns said:**
> Aye , some would say it's a adobe performance issue and that the linux port isn't getting the attention it deserves and I would mostly agree , but on the other hand Flash runs fine in Fluxbuntu on my test cyrix w/ 192 mb of pc100 , The 95's & 98's we get in the shop where people say "Dude , youtube is jerky" there's honestly no fix for it......those people are not going to pay 200 bucks for an XP key that will still run like crap once the proper protection is put into place , unless the nine year old likes porn pop ups.

What "proper" protection?  Firefox with plugins- popup blockers, ad blockers and other spyware blocking plug ins runs fine and smooth on the 600Mhz XP Pro box.

---

### Post by rgb1701 on 2007-12-23
> **sx66gns said:**
> Aye , some would say it's a adobe performance issue and that the linux port isn't getting the attention it deserves and I would mostly agree , but on the other hand Flash runs fine in Fluxbuntu on my test cyrix w/ 192 mb of pc100 , The 95's & 98's we get in the shop where people say "Dude , youtube is jerky" there's honestly no fix for it......those people are not going to pay 200 bucks for an XP key that will still run like crap once the proper protection is put into place , unless the nine year old likes porn pop ups.

Unfortunately, in the real world, the competition isn't $200 XP licenses, it's free darknet XP loads :(

...and no, I don't plan on installing that on her machine.  If she wants XP , she will have to pay for it.  I suspect she won't and simply make do with the Linux load I end up putting on the box, but the HUGE issue still remains- the XP vs Xp-user-equivalent-Linux (user interface and functionality, minus the commercial games issue) performance and resource gap.

And no, you *don't* need any actively running anti-virus, anti-spyware, or software firewall on an XP box- just a hardware NAT firewall, Firefox with a few plugins, web-based email only, Outlook and IE disabled, and ClamWin to scan on demand when needed.

---

### Post by Wiebelhaus on 2007-12-23
> **rgb1701 said:**
> On which OS?

The XP Pro box has ClamWin (doesn't actively scan), and has Outlook and IE disabled, Firefox only to address spyware, and only Gmail and Yahoo Mail for email both auto scan attachments for viruses).  No software firewall- only use the NAT in the attached Linksys cable modem router and have never had an issue with any of the XP Pro SP1 clients using this setup.



That's why your getting such grand performance mate , your obviously savvy and have a great understanding of how to optimize and get the most out of an older machine , but an average user isn't going to have the grand experience you've created from years of getting your hands dirty , most will have something like a busted Norton 360 installation without spyware protection using IE7 with a dirty uncle surfing porn.... it's all in the application.

With the same amount of care that you have put into your windows boxes , you could have a smoking Linux distro compiled to do only what you need it to but then again... that's more than the average user is going to do.

For experimental reasons I set up a 486 and compiled my own kernel for basic internet and communication and flash worked fine , matter of fact you could compile your own kernel for your machines for fun to test this.

---

### Post by rgb1701 on 2007-12-23
> **sx66gns said:**
> Aye , some would say it's a adobe performance issue and that the linux port isn't getting the attention it deserves and I would mostly agree , but on the other hand Flash runs fine in Fluxbuntu on my test cyrix w/ 192 mb of pc100 , The 95's & 98's we get in the shop where people say "Dude , youtube is jerky" there's honestly no fix for it....

Adobe's stated goal for FLash video is no frame drops on a 500Mhz P3 (with the current flv VP6 series codecs).  All my P3 builds with XP prove that, from 500Mhz Celeron through P3 1Ghz.

We need to flood Adobe with requests to improve Flash performance on the biggest Linux distros.

What speed is your Cyrix CPU?

---

### Post by Wiebelhaus on 2007-12-23
> **rgb1701 said:**
> Unfortunately, in the real world, the competition isn't $200 XP licenses, it's free darknet XP loads :(

[COLOR="Red"]In the real world you'll get a "Must activate before...." Breaking the law is not an option , nor does an illegal installation last long maybe without sp2 , but we are not debating a hacked or Tiny xp installation here[/COLOR]

[Buy Xp Pro]("http://www.officedepot.com/ddSKU.do?level=SK&id=774440&cm_mmc=TLShopping-_-PriceGrabber-_-Software%20%26%20Books-_-774440%20Microsoft%20Windows%20XP%20Professio")

...and no, I don't plan on installing that on her machine.  If she wants XP , she will have to pay for it.  I suspect she won't and simply make do with the Linux load I end up putting on the box, but the HUGE issue still remains- the XP vs Xp-user-equivalent-Linux (user interface and functionality, minus the commercial games issue) performance and resource gap.

And no, you *don't* need any actively running anti-virus, anti-spyware, or software firewall on an XP box- just a hardware NAT firewall, Firefox with a few plugins, web-based email only, Outlook and IE disabled, and ClamWin to scan on demand when needed.

[COLOR="Red"]You sir , Are 100% wrong , this is utter rubbish , let's be realistic , I've tried to be very polite and respectful and your trying to have some E-debate , good day , your full of it.

[/COLOR]



I'm done with this fool.

---

### Post by rgb1701 on 2007-12-23
> **sx66gns said:**
> I'm done with this fool.

Sorry- I wasn't trying to debate, just expressing frustration, and the way I see it "on the street".

While the NAT, Firefox and other simple measures have worked fine on the several XP SP1 boxes I've been running for several years, perhaps it *is* foolish to believe this is sufficient for non-techie Mom's and nieces.  Yes, I agree that it's not realistic for "normal" people, moving forward, to use Xp SP1- they would be forced into SP2, with more RAM requirements, more resident programs, coupled with Auto Updates pushing more bloat.

I just reloaded my Mom's machine- a Dell 1.8Ghz Celeron from late 2002 or so, with the XP Home setup disk and license that came with the machine.  I stopped the Auto Updates at the SP2 point (did not load SP2), and gave her a Linksys NAT router to mirror the setup I use at home, with Firefox and other changes.  The box had to be re-loaded due to excessive slowdowns (IE7, too many resident programs, other issues you mention).  I turned off Auto Updates.

I plan to see if she accumulates the spyware or other issues over the next few months.  I had planned to put Ubuntu on her machine instead of re-loading XP Home, but she has 10-15 CD-ROMs worth of store-bought slot machine casino games (Masque and Reel Deal brands) she wanted to reload.  I suspect that some of them might run under Wine, but I didn't have time to test and debug the games for her this round.  I plan to test the casino games under Wine over the winter, so perhaps some Linux distro will be on her machine by year end 2008.  The games are 1998-2004 vintage, which works to Wine's favor.

On a positive Linux note, my sister's 2.4Ghz Celeron box has been doing fine with no issues since I put Ubuntu on it in March/April of this year.

I also appreciate the heads ups on the alternative, lighter Linuxes (PCLinuxOS, Fluxbuntu, Mint)- again no offense intended (I realize now it looks like I was attacking your posts, but it was just venting the state-of-Ubuntu/Gnome/KDE frustration).

---

### Post by louieb on 2007-12-23
> **rgb1701 said:**
> Your plight highlights an ugly secret in the FOSS, and in particular Ubuntu, community...
Really would not call it a secret.  But sales hype - it just works -  
[quote=sx66gns] Ubuntu is a high end state of the art OS , Not designed to run on old hardware[/quote]

Could not agree more. 

[IMG]http://louboldt.com/ptwocents.gif[/IMG] I have a P2-400mHz, 384MB ram - my distro playbox. at one time or the other I've had XP home -SP2, all the Ubuntus', Fedora, and a few others. XP, Ubuntu including xUbuntu, Fedora all run about the same speed -  Survivable but kinda slow. 

There are 3 distributions   that have real pop for basic stuff like email and word processing DSL, Puppy, and PCFluxboxOS.

Right now the PC has  Slackware Linux installed but after using partimage to back it up its going back to my new favorite lightweight Linux distribution. - PCFuxboxOS.

---

### Post by rgb1701 on 2007-12-23
Just another suggestion for the OP-

Over the past several days, I've done a lot of real world testing with Puppy Linux 3.x on a 500Mhz Celeron/i810 box with 192MB of RAM and NO hard disk!  I plan to make Puppy permanent on that box, with an old 4Gb hard disk to boot from and save data to (though it worked fine from bootable CD-ROM and a FLash USB drive to save data to).

It ran very fast, enough to impress an average non-techie using a current multi-core Vista box!

I plan to see if I can get Flash to load in the included Seamonkey and test on the 600Mhz box...

---

### Post by rgb1701 on 2007-12-23
I just tested Puppy Linux 3.x on the 600Mhz P3 box for the niece, and Youtube videos run MUCH better- still not completely smooth like XP, but basically acceptable and FAR faster than under stock Ubuntu 7.10.  I suspect it might be smoother if the nvidia proprietary driver were installed under Puppy.

Another amazing bonus- Puppy has FLash installed by default for Seamonkey!

Totally unbelievable how fast the 600Mhz box runs with Puppy.  I may keep Puppy on that puppy :)

If Vista box owners (or even XP owners) tried Puppy on their machines, they would never go back :D

---

### Post by gn2 on 2007-12-23
> **rgb1701 said:**
> 
On a stock Ubuntu 7.10 load on another P3 600/384MB/FX5500 box, Youtube/flash video displays in slow motion, choppy, a few frames per second!  

Disabled the 3D effects?
Tried Xubuntu 7.04 or Zenwalk 4.8 yet?

As for your claims regarding XP boot times on the quoted hardware, I take it that's not a standard XP installation and does not have adequate anti-virus and firewall loading at start-up?

Either that or there's some other factor to consider......

---

### Post by rgb1701 on 2007-12-23
> **gn2 said:**
> Disabled the 3D effects?
Tried Xubuntu 7.04 or Zenwalk 4.8 yet?

As for your claims regarding XP boot times on the quoted hardware, I take it that's not a standard XP installation and does not have adequate anti-virus and firewall loading at start-up?

Either that or there's some other factor to consider......

Thanks for the heads up re: Zenwalk- hadn't heard nor tried it yet!

I just put the finishing touches on the P3 box for the niece's present tomorrow.  I ended up putting in a nice Slot1 650Mhz Coppermine, overclocking the bus to 112Mhz from 100Mhz for a nice 728Mhz box with 384MB RAM, DVD ROM and FX5500 w/128MB.  I ended up installing the latest Linux Mint- awesome distro!  I loaded up all the Edubuntu educational software from Synaptic, plus all the games I think she'd like from Synaptic, too.

I even tried gOS- nice little Ubuntu derivative, but too stripped down IMO.

It's doing a final Memtest now before wrapping it up...

The 600Mhz P3 XP boot times did not include any anti virus or software firewall.  I use a hardware router with NAT and only Gmail/Yahoo email, no local mail client, as both webmail systems scan all email for viruses.  Outlook and IE are disabled, and Firefox has pop up, adware and spyware blockers.

The 600Mhz XP box is on 24/7 as a fileserver, and has never had an issue with malware with this setup.

---

### Post by irish_flu on 2007-12-23
I've run Ubuntu just fine on slower hardware with less RAM.  It won't be OMG1337FAST, but it'll run well if XP runs well.   I say go for it.

---

### Post by rgb1701 on 2007-12-23
> **irish_flu said:**
> I've run Ubuntu just fine on slower hardware with less RAM.  It won't be OMG1337FAST, but it'll run well if XP runs well.   I say go for it.

The Linux Mint load has changed my opinion about window managers- I probably won't use a distro that isn't Xfce for the forseeable future, at least on <2Ghz machines.

I don't agree totally with the XP runs well = Ubuntu runs well assertion, though.

The biggest issue with 500Mhz-600Mhz machines is that FLash video (Youtube) and Java games (pogo.com) run smoothly on XP, but Ubuntu on the same speed machine *can't* run Flash video and Java at full speed/smoothly.  Ubuntu and Xubuntu (didn't try Kubuntu) were the slowest FLash video and Java players of all the Linuxes I tried- Puppy, gOS, Mint, and PCLinuxOS.  I tried Fluxbuntu twice, but both burned CD's wouldn't boot- their .ISO files on their download links are bad.

The moral of the story is that something in Linux land is not right, and someone or all three need to step up to the plate and achieve performance parity with XP:  Either Adobe and Sun didn't do a proper job porting/optimizing Flash and Java for Linux, and/or Nvidia and ATI drivers aren't up to snuff to accelerate these players, and/or the Linux video APIs/window managers aren't doing what DIrectX/DirectShow on XP has been able to do for 5+ years.  It could also be that some Linux process and/or process scheduling issue is causing the FLash and Java issues on 500-700Mhz machines.

EDIT:  Per my final posts in this thread, it appears that the culprit was the P6BAT-A+ motherboard used on the nieces' 728Mhz box.  Something about the design or Linux drivers for that motherboard chipset was causing the poor Flash/Java performance.

---

### Post by erginemr on 2007-12-24
> **wildnewbie said:**
> My Video Card is Intel 810,  I just installed flash thruogh firefox, and still need some codec from GStreamer.  I installed both and watching video on Youtube at one frame per second.  The sound was a little skippy too.  Anway, I am going to reinstall X-Ubuntu soon.  Thanks for your help.  

Does it help my computer to run any faster, if I have different partition for different subdirectories, like /usr and /boot and stuffs, I don't it that much.  I can only allocate 8 gig 8 gig for Ubuntu, 1 gig is already allocated for /swap.

> **rgb1701 said:**
> ...As an example, for a 9 year old niece I am currently building a P3 600Mhz, 384MB box with a GeForce FX5500 video card- more than adequate hardware to run all web sites, Flash, Java and any apps she might need on XP SP1.  I just tested Youtube and a Java games site- Pogo.com, on a similar spec machine (P3 600, 512MB, only a lowly Matrox 8MB G450) with XP SP1, and Flash video (cbs.com, youtube, etc) runs *perfectly*.  

On a stock Ubuntu 7.10 load on another P3 600/384MB/FX5500 box, Youtube/flash video displays in slow motion, choppy, a few frames per second!  Also, Java runs in slow motion on the Ubuntu load, but at full speed on the XP SP1 load with similar hardware. I updated xorg.conf with lots of hardware acceleration and XV options, with no improvement to Flash video.  I am using the nvidia "Restricted driver" that defaults on 7.10...

My computer is in the same spec range as yours (AMD Athlon 750 MHz, 512 MB RAM, GeForce MX 440), archaic by today's standards, but is running both Ubuntu and Flash (youtube) videos and online Flash games fine with no (or noticeable) frame drop. I have disabled Compiz Fusion, and so far, I am very satisfied with Ubuntu's overall performance.

What I want to say is that, the slow performance you are suffering from is not a general problem in Ubuntu/Linux, but can be a hardware specific one. Are you happy with the general performance / speed of your Ubuntu system? Did you try several ways of installing Flash, say not via Firefox, but from Synaptic? Did it make any difference? You should also make sure that you have installed Adobe Flash plugin (flashplugin-nonfree in synaptic), not the open source Gnash alternative (see the attachment).

One more question, did you try alternatives to Firefox (swiftfox, opera and epiphany comes to my mind) and tried running youtube videos from there? (Sorry if you already did, but this has been a quite long thread - spanning 3 pages so far - and I may have lost the end of the rope.)

---

### Post by chewit on 2007-12-24
I'm running Ubuntu 7.10 on a 700MHz CPU and 256mb RAM. It runs very well. I can browse the web, listen to music and chat on xfire (using wine) very well.

Its not as fast as Xubuntu, but there isn't much in it. I was going to use Xubuntu, but there isn't enough features as there is in Ubuntu.

---

### Post by wildnewbie on 2007-12-24
> **erginemr said:**
> My computer is in the same spec range as yours (AMD Athlon 750 MHz, 512 MB RAM, GeForce MX 440), archaic by today's standards, but is running both Ubuntu and Flash (youtube) videos and online Flash games fine with no (or noticeable) frame drop. I have disabled Compiz Fusion, and so far, I am very satisfied with Ubuntu's overall performance.

What I want to say is that, the slow performance you are suffering from is not a general problem in Ubuntu/Linux, but can be a hardware specific one. Are you happy with the general performance / speed of your Ubuntu system? Did you try several ways of installing Flash, say not via Firefox, but from Synaptic? Did it make any difference? You should also make sure that you have installed Adobe Flash plugin (flashplugin-nonfree in synaptic), not the open source Gnash alternative (see the attachment).

One more question, did you try alternatives to Firefox (swiftfox, opera and epiphany comes to my mind) and tried running youtube videos from there? (Sorry if you already did, but this has been a quite long thread - spanning 3 pages so far - and I may have lost the end of the rope.)

I did tried a few alternatives, but once I get the gstreamer codec I have to reinstall Ubuntu, which takes about 1.5 hour, so I haven't tried all alternatives mentions.  Maybe, I should learn how to back up my system and keep trying other alternatives and see if there's any improvement in streaming video.

For my box with Ubuntu 7.10, the computer is just plain slow.  Even with openning and closing windows.  I can see a pause when windows are minimized or maximized.  

With X-Ubuntu in my box, it's even worse.  The terminal doesn't work, I was log out everytime I started the terminal and after a couple of times all I see are color stripes.  X-Ubuntu just doesn't work on my box.

I just tried to install "Puppy Linux" in my box, it run much faster than Ubuntu, but the graphic is way too ugly compare to Ubuntu.  My graphic card is displaying at 16 bit, instead of its max 24bit.  I am going to try other distributions that you guys are suggesting here.

I think Puppy Linux is best for my box even though I am not too satisfied with the grahic.  I will also try other distributions suggested above.

Thanks you all very much,

---

### Post by gn2 on 2007-12-24
> **wildnewbie said:**
> 
For my box with Ubuntu 7.10, the computer is just plain slow.  Even with openning and closing windows.  I can see a pause when windows are minimized or maximized.  

With X-Ubuntu in my box, it's even worse.  The terminal doesn't work, I was log out everytime I started the terminal and after a couple of times all I see are color stripes.  X-Ubuntu just doesn't work on my box.



It's not the fact that it's Gnome or XFCE that's the problem.

The terminal issue can be cured by using a different terminal app.
XFCE runs better if you disable the Gnome services from starting.
The colour stripes sounds like the screensaver has kicked in?

Your main problem is that the minimum requirements for 7.10 are higher and it causes problems on older hardware of the spec you (and I) have.

7.04 is a much lighter load and you may notice a marked performance boost.
Going from 7.04 to 7.10 Xubuntu rendered my P3 500mhz 192mb RAM Portege 3440CT laptop all but useless.
It runs 7.04 just fine, including YouTube playback.......

I think Puppy uses Fluxbox which isn't to everyone's taste.

Linux Mint Cassandra XFCE Community edition is a good choice, but Zenwalk is faster still.

You still have some learning to do, it's perfectly possible to do all the things you want with the hardware you have in Linux, but probably not with 7.10 X,K,Ubuntu.

EDIT: Just a final thought, you have installed the correct graphics driver for your graphics card?

---

### Post by starcannon on 2007-12-24
Xubuntu 7.04 will run very nicely on your rig.
I installed Xubuntu on an old Gateway Solo 2500 | PII 366mhz 288mb Ram, 10gb HDD, and a freaky old mobile integrated vid card (forget which one google for that :) ) Set it up and checked YouTube and Runescape both worked nicely, boxed it up and shipped it to my grandmother, she loves it; indeed my nieces and nephews love it to. 

Their windows box was down due to STDs and I received a call to help them get their printer installed on Grandma's laptop, 15minutes of phone tech and they were printing out their essay's freshly typed up in Abi Word.

Anyway, if Xubuntu runs smooth on that old beater, yours should do it very nicely, and with the amount of ram and cpu you have, Open Office should run quite nicely as well.

---

### Post by rgb1701 on 2007-12-24
> **erginemr said:**
> My computer is in the same spec range as yours (AMD Athlon 750 MHz, 512 MB RAM, GeForce MX 440), archaic by today's standards, but is running both Ubuntu and Flash (youtube) videos and online Flash games fine with no (or noticeable) frame drop. I have disabled Compiz Fusion, and so far, I am very satisfied with Ubuntu's overall performance.


Could you post your xorg.conf file, from the Athlon 750Mhz/MX440 box, or attach to a post?

I am using the FLash plugin, which auto-installed from Firefox, not Gnash.

---

### Post by rgb1701 on 2007-12-24
> **starcannon said:**
> Xubuntu 7.04 will run very nicely on your rig.
I installed Xubuntu on an old Gateway Solo 2500 | PII 366mhz 288mb Ram, 10gb HDD, and a freaky old mobile integrated vid card (forget which one google for that :) ) Set it up and checked YouTube and Runescape both worked nicely, boxed it up and shipped it to my grandmother, she loves it; indeed my nieces and nephews love it to. 



If "nicely" = smoothly, without jerky video or low frame rates on Youtube, then I am amazed.

Could you also post your xorg.conf?

I just rebooted the 728Mhz P3 machine with Puppy Linux, one of the leanest, meanest Linuxes out there, and Youtube videos on a lean Seamonkey were still not as smooth as Youtube on the XP/600Mhz P3/Firefox box.

There is a *serious*, festering issue of bloat and poor performance in Linux land...

If the FOSS community doesn't address these basic, fundamental performance issues, people will be buying/using used XP licenses from old PCs and ebay...

---

### Post by rgb1701 on 2007-12-24
I just finished testing Zenwalk on the P3 728Mhz machine with FX5500, and YOutube videos appear about the same as Puppy Linux- some tearing, and about half the framerate of the 600Mhz XP box with 8MB Matrox G450. :(

It is obvious after all the Linuxes and video cards I've tried that Flash on Linux is not optimized like the WIndows version.  Maybe Adobe didn't enable MMX, SSE or some other switch when they compiled for Linux?

---

### Post by erginemr on 2007-12-24
> **rgb1701 said:**
> Could you post your xorg.conf file, from the Athlon 750Mhz/MX440 box, or attach to a post?

I am using the FLash plugin, which auto-installed from Firefox, not Gnash.

I am currently at work and will post my xorg.conf file when I get back home, but meanwhile, please kindly answer the following questions to rule out some other possibilities:

1 - Are you happy with the general performance / speed of your Ubuntu system? 

2 - Did you try alternatives to Firefox (esp. Opera and Epiphany) and try running youtube videos from there?

---

### Post by LowSky on 2007-12-24
rgb1701 I dont understand what your looking for, you keep saying that flash is not working that great on old P3 computer? You also keep mentioning that XP SP1 runs circles around ubuntu or xubuntu. But heres the thing, what are you going to do when Microsoft stops selling you licences for XP?

 I respect you for trying to keep older hardware running but at some point it is actually cheaper to buy new technology. I have an old laptop that runs ubuntu/youtube just fine. Its a P3 700/1000mhz (speed stepping) laptop with only 256 ram. I cant see it lasting forever and i expect that ubuntu will not keep pace with it and sooner or later the laptop will hit a wall of upgradability with Ubuntu, but thats is what technology and evolution is all about survival of the fittest, sooner or later, no matter how well you think you can adapt, evolution will beat you.

If you want ubuntu or one of its many flavors to run to your specifications, why not remove some systems from starting like you have in XP.

---

### Post by gn2 on 2007-12-24
> **rgb1701 said:**
> I just finished testing Zenwalk on the P3 728Mhz machine with FX5500, and YOutube videos appear about the same as Puppy Linux- some tearing, and about half the framerate of the 600Mhz XP box with 8MB Matrox G450. 

What version of Flash did you install in Zenwalk?

It runs just fine on my old P3 laptop on Zenwalk, at least as smoothly as it did with W2k Pro.

---

### Post by rgb1701 on 2007-12-24
> **gn2 said:**
> What version of Flash did you install in Zenwalk?

It runs just fine on my old P3 laptop on Zenwalk, at least as smoothly as it did with W2k Pro.

Based on the responses here, there's probably something wrong with the nvidia driver on the P3 728Mhz box.

I allowed Linux Mint (Xubuntu 7.10 variant) to install the "Restricted Driver" from the automatic system tray popup.

What else do I need to do to enable the full acceleration of the FX5500 card?

---

### Post by gn2 on 2007-12-24
I'll ask again:

What version of Flash did you install in Zenwalk?

Haven't a clue about the NVidia driver installation because I only use on-board graphics, Intel on my C2D desktop, I don't even remember what's on the P3 laptop, but I know it's only got 8mb of memory.

---

### Post by rgb1701 on 2007-12-24
> **LowSky said:**
> rgb1701 I dont understand what your looking for, you keep saying that flash is not working that great on old P3 computer? You also keep mentioning that XP SP1 runs circles around ubuntu or xubuntu. But heres the thing, what are you going to do when Microsoft stops selling you licences for XP?

 I respect you for trying to keep older hardware running but at some point it is actually cheaper to buy new technology. I have an old laptop that runs ubuntu/youtube just fine. Its a P3 700/1000mhz (speed stepping) laptop with only 256 ram. I cant see it lasting forever and i expect that ubuntu will not keep pace with it and sooner or later the laptop will hit a wall of upgradability with Ubuntu, but thats is what technology and evolution is all about survival of the fittest, sooner or later, no matter how well you think you can adapt, evolution will beat you.

If you want ubuntu or one of its many flavors to run to your specifications, why not remove some systems from starting like you have in XP.

The only processes I disable on the XP PRo SP1 600Mhz box are Indexing and Messenger.  Other than that, its a stock load, except with Firefox + plugins and IE/Outlook disabled.

I actually tried disabling several processes on the Linux Mint P3 728Mhz P6BAT-A+ load, such as Bluetooth, System logging, and other unnecessary processes for that box.

As I mentioned before, 500Mhz-900Mhz x86 machines will only *grow*, due to eePC, OLPC and other palm and portable x86 devices coming to market.  THe Linux/FOSS community can't bury their heads in the sand forever on the optimization/bloat issue.

---

### Post by gn2 on 2007-12-24
> **rgb1701 said:**
> THe Linux/FOSS community can't bury their heads in the sand forever on the optimization/bloat issue.

Indeed they don't which is why there are distros optimised for low-end hardware.

You just need to find them.

---

### Post by erginemr on 2007-12-24
> **rgb1701 said:**
> Could you post your xorg.conf file, from the Athlon 750Mhz/MX440 box, or attach to a post?

I am using the FLash plugin, which auto-installed from Firefox, not Gnash.

Attached is my "/etc/X11/xorg.conf" file.

The line

```
	Option		"XvmcUsesTextures"	"True"	
```

has been put there to eliminate the horizontal tearing and flickering effect when running full screen videos with Compiz Fusion activated. It may help your situation.

You can also test whether your restricted NVidia drivers have been installed or not by running the following command from the console:
```
glxinfo | grep direct
```
You should get something like
```
direct rendering: Yes
```

[P.S. Also try using Opera & Flash together to check its performance on your system.]

---

### Post by criskat777 on 2007-12-24
I have Ubuntu Gutsy Gibbon on a Old HP with 1ghz Duron and 512mb of Ram it has a el chippo Nvidia Mx4000 128mb that i installed just to see if i could get 3d Compiz+ effects+ kiba dock + 40% trasparency every thing worked and to tell you the truth i was just playing with it to see what i could do with it. since every thing worked so well i ended up giving it to one of my girls. now she has her own PC and dose not have to use my Laptop. I tested it side by side with my Dual core 64 bit and opend Open Office about 4 to 6 sec. after my 64 bit i could live with that when ti comes to a pc that was going to the trash.:popcorn:

---

### Post by starcannon on 2007-12-24
RGB1701 sorry I can't post the xorg.conf file, I'm in Medical Lake WA, and the laptop is with my grandma in Ashland OR. I didn't modify it though, so what ever the default xorg.conf that was created at the time of install is what it has.

I do like to promote Ubuntu, but if your really running into a wall on this, Knoppix is a great distro that is light and fast. FOSS does have bloat free distro's, one of my favorites is Damn Small Linux. When I was using the laptop before setting it up for my grandma I used Damn Small Linux. It is not as "easy" to use as Ubuntu though, so I wiped it off and put something more grandma proof on there for her.

There are also some fast builds of Firefox "swiftfox" I think its called, I never messed with it though.

Anyway, never fear, the FOSS community has not left behind the idea of "lean and mean", indeed its one of the things that rocks about Linux in general, whatever it is you want, you can be sure theres a project out there that wants that as well.

Check out Knoppix and Damn Small (Damn Small is a varient of Knoppix) I think you'll find the fast, lite, and yet feature rich system you want (though in some cases it may require more work to get it just right). I wrote an install guide for the Gateway Solo 2500 at the Damn Small Forums, theres a copy of my xorg.conf there I think, but I may have been using Xfree at the time I forget.

Cheers, Merry Xmas, Happy Holidays, Seasons Greetings, etc...

---

### Post by rgb1701 on 2007-12-24
> **gn2 said:**
> I'll ask again:

What version of Flash did you install in Zenwalk?

Haven't a clue about the NVidia driver installation because I only use on-board graphics, Intel on my C2D desktop, I don't even remember what's on the P3 laptop, but I know it's only got 8mb of memory.

I wil need to reboot from the Zenwalk CD on the P6BAT-A+ box and check.

---

### Post by gn2 on 2007-12-25
> **rgb1701 said:**
> I wil need to reboot from the Zenwalk CD and check.

So you didn't install Zenwalk and run it from the hard drive?

Did you actually even install Flash?

I think you're just posting  a bunch of hostile BS.

Happy Christmas. :)

---

### Post by rgb1701 on 2007-12-25
> **gn2 said:**
> So you didn't install Zenwalk and run it from the hard drive?

Did you actually even install Flash?

I think you're just posting  a bunch of hostile BS.

Happy Christmas. :)

First, to answer your original question, the Flash version in the current Zenwalk LiveCD is 9.0.48.0.  Why would I need to install Zenwalk to hard disk to test Flash/Youtube video playback?  The video is *streaming* via Ethernet and has nothing to do with hard disk access.  

On the positive side, I just booted the Zenwalk LiveCD on a P3 1Ghz/1GB RAM/FX5500 AGP box, and Youtube/Flash 9.0.48.0 ran perfectly from the CD (no HD install)!  Smooth, no frame drops or tearing- as perfect as the XP/P3 600Mhz/512MB/Matrox G450 8MB AGP box ;)   This is the same Zenwalk CD I tried on the P3 728Mhz/384M/FX5500 PCI box.

So, after the large amount of distros, reboots and parts combos I tried on the P6BAT-A+ board (CPU's, RAM amounts, Nvidia, ATI  cards from 32MB to 128MB) over the past several days, it appears the Flash performance issue could be any one of the folllowing:

- Flash Linux version 9.0.48.0 vs 9.0.115.0.  I am typing currently on XP SP1/1G P3/1G RAM/FX5500 AGP with Flash 9.0.16.0- too many Flash versions :(

- Flash efficiency on Linux vs XP (i.e. how it was compiled for each OS)

- EDIT- per a later post, I found that Zenwalk/Flash 9.0.48.0 plays Youtube videos basically fine on a 600Mhz P3/BH6/512M/Matrox 8M G450 AGP box.  The framerate looks slightly lower than XP on the same box, but no tearing and basically consistent- 'good enough" :D

- The 728Mhz P3 box had a 100Mhz bus vs 133Mhz bus on the 1Ghz P3 box, but I doubt that would make a difference with low bitrate video.

- PCI vs AGP issue?  The 728Mhz box had an FX5500 PCI vs an FX5500 AGP in the 1GHz box.  I doubt this would make a difference with the low bitrate of Flash video, though.

- Anything I missed?

Second, thanks to all the people who posted helpful suggestions and the heads up on distros I hadn't known about or tried before like Fluxbuntu and Zenwalk.  Zenwalk looks promising for another nieces' PC I'm updating :D  I don't know if Zenwalk has the repositories like Ubuntu variants do, though.  Easy access to the wealth of software packages available to Ubuntu/Debian based distros is a big reason to stay with them.

Third, I apologize to forum readers and posters if some of my rants and responses appeared too harsh or personal.

My intent was to point out important issues in the FOSS community on the optimization /responsiveness / performance fronts from a user perspective, similar to ESR's CUPs rant over a year ago-

[http://www.catb.org/~esr/writings/cups-horror.html](http://www.catb.org/~esr/writings/cups-horror.html)

[http://www.catb.org/~esr/writings/luxury-part-deux.html](http://www.catb.org/~esr/writings/luxury-part-deux.html)

I think the following passage applies *perfectly* to the performance/optimization issues of FOSS window managers, boot times, system process optimization, and third party plugin (Flash/Java)  performance and related issues:

"But the volume of community reaction that thundered into my mailbox far surpassed what I had been expecting &#8212; and the dominant theme, too, was a bit of a surprise. Not the hundreds of iterations of "Tell it, brother!", nor the handful of people who excoriated me as an arrogant twerp; those are both normal features of the response when I fire a broadside. No, the really interesting part was how many of the letters said. in effect, "Gee. And all this time I thought it was just me..." "

The real question the FOSS community needs to ask itself is, why does it take an ESR rant to motivate the FOSS community to fix fundamental, easily tested issues?  

The Linux printer setup system looks great now- I used the CUPs web based wizards in Puppy Linux over the weekend, and it nearly made me cry with joy how nicely and flawlessly it worked, connecting my die hard, perfect condition LaserJet 4m to a Celeron 500Mhz box via parallel printer port without issue.  Would CUPs have been improved without the ESR rant?  Yeah, but probably over a longer time period and with a lower level of focus.

No, I'm not as smart as ESR, nor have I worked as hard or as long for the FOSS community as ESR and others have.

Building workable, functional computers out of spare parts for people who might not be able to afford their own is one of my contributions to Linux and FOSS.  I just want the Linux experience to be a good one for the recipients of these boxes.  

You should have seen my niece's reaction when she saw her "new" Linux Mint computer last night. :) newly "Minted", so to speak :D

---

### Post by rgb1701 on 2007-12-25
> **erginemr said:**
> Attached is my "/etc/X11/xorg.conf" file.

The line

```
	Option		"XvmcUsesTextures"	"True"	
```

has been put there to eliminate the horizontal tearing and flickering effect when running full screen videos with Compiz Fusion activated. It may help your situation.

You can also test whether your restricted NVidia drivers have been installed or not by running the following command from the console:
```
glxinfo | grep direct
```
You should get something like
```
direct rendering: Yes
```

[P.S. Also try using Opera & Flash together to check its performance on your system.]

Thanks for the info.

Yes, the nvidia drivers were installed and active, as glxinfo reported
direct rendering: Yes

I re-installed the Nvidia driver via the Envy applet in Linux Mint on the P3 728Mhz box, and the install went fine, but it didn't improve Flash video performance.

Opera did not improve the frame rate/tearing issues with Flash 9.0.115.0 on the same Linux Mint 728Mhz P3 box, either.

---

### Post by rgb1701 on 2007-12-25
> **gn2 said:**
> Indeed they don't which is why there are distros optimised for low-end hardware.

You just need to find them.

What distro and window manager would be the feature/function/resident process equivalent to XP?

Puppy Linux runs great on ~500Mhz hardware, but I don't think Puppy Linux has the number of services running and feature content of a stock XP load. Of course, lots of other distros exceed XP's stock feature/functionality content, but at the price of performance on low end hardware.  I guess I want XP's low end hardware performance *plus* features/content  in the same Linux distro.

IMO, Xfce appears to be a functional and visual equivalent of XP's window environment, depending on theme/styles selected, of course.

---

### Post by ugm6hr on 2007-12-25
> **rgb1701 said:**
> What distro and window manager would be the feature/function/resident process equivalent to XP?


I would say IceWM window manager, with thunar file manager and idesk desktop manager.  That should be pretty similar in terms of functions.  You can install with a minimal Ubuntu...

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by rgb1701 on 2007-12-25
> **ugm6hr said:**
> I would say IceWM window manager, with thunar file manager and idesk desktop manager.  That should be pretty similar in terms of functions.  You can install with a minimal Ubuntu...

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

Awesome!

I guess I should have asked the simple question early in the thread ;)

---

### Post by ugm6hr on 2007-12-25
If you really want an XP-like experience - I have just seen this:
[http://lxp.sourceforge.net/](http://lxp.sourceforge.net/)

It uses xfe rather than thunar though.  The thing I like about thunar is the thunar-volman addon, which auto-mounts usb drives etc.

It appears the .deb is for 6.06 too, but might be worth a try if you are looking for stability.

You can also get GDM themes that look like XP's login screen too. [http://www.gnome-look.org/content/show.php/show.php?content=63383](http://www.gnome-look.org/content/show.php/show.php?content=63383)

---

### Post by ugm6hr on 2007-12-25
> **rgb1701 said:**
> Now I have a bad choice- let the machine go out with poor Flash/Java performance on websites my 9 year old niece will use often, or cave in and put XP Sp1 on the box... :(

I just saw this earlier post....

If you are looking for a machine to get online with ease - this OS might be worth looking at:
[http://www.thinkgos.com/](http://www.thinkgos.com/)

I haven't tried it, and I gather the downloaded version doesn't include codec support out-of-the-box, but I think the idea behind it is good (if you are a google / youtube / facebook / skype fan).  Importantly, it is essentially just Ubuntu7.10 with E17 and a load of shortcuts on your desktop.

For a 9-year-old, I think it would be perfect.

---

### Post by rgb1701 on 2007-12-25
> **ugm6hr said:**
> If you really want an XP-like experience - I have just seen this:
[http://lxp.sourceforge.net/](http://lxp.sourceforge.net/)

It uses xfe rather than thunar though.  The thing I like about thunar is the thunar-volman addon, which auto-mounts usb drives etc.

It appears the .deb is for 6.06 too, but might be worth a try if you are looking for stability.

You can also get GDM themes that look like XP's login screen too. [http://www.gnome-look.org/content/show.php/show.php?content=63383](http://www.gnome-look.org/content/show.php/show.php?content=63383)

Thanks for the LXP and thunar tips!  Also, Xfe looks like the file manager I've been dying to have on Linux- lots of experimenting to do...:)

LXP looks great for first time non-techies coming from years of XP use, but I am not really after an exact XP look-alike.  In fact, I think new Linux users like my niece *want* something that looks  "new" and "different" on purpose, as long as it does the functions and tasks (i.e. apps) they want.  It sure would be fun to secretly swap out a non-techie's XP for a good distro with LXP on it, and see if they notice (*evil laughter*).

All my XP vs Linux rants earlier in the thread were related to performance and user-interface responsiveness- boot time, time to open apps, click lag, window and dialog operations lag, speed to open/close windows, etc, all on low end hardware (500Mhz-700Mhz).  XP performs well on this kind of hardware, assuming the simple tweaks I mentioned several times before- disable Outlook and IE, install Firefox + free anti malware plugins, use webmail only (yahoo or gmail for the virus scanning), disable Indexing and Messenger processes, and use a simple theme, plus a hardware firewall in a router in lieu of any software firewall.

---

### Post by rgb1701 on 2007-12-25
> **ugm6hr said:**
> I just saw this earlier post....

If you are looking for a machine to get online with ease - this OS might be worth looking at:
[http://www.thinkgos.com/](http://www.thinkgos.com/)

I haven't tried it, and I gather the downloaded version doesn't include codec support out-of-the-box, but I think the idea behind it is good (if you are a google / youtube / facebook / skype fan).  Importantly, it is essentially just Ubuntu7.10 with E17 and a load of shortcuts on your desktop.

For a 9-year-old, I think it would be perfect.

I thought so too, but after testing gOS on the 728Mhz box for the 9yo niece, I thought it was too stripped down and wanted to give her more flexibility with Mint.  I may change my mind after testing gOS for a longer period- I was under the gun (gnu? ;)) and had to finish the box on Sunday and could only spend so much time on each distro before locking one in.

---

### Post by rgb1701 on 2007-12-25
GREAT news-

I booted the Zenwalk 2007 LiveCD on the 600Mhz P3/512M/Matrox 8M AGP G450 box, and...

Youtube/Flash 9.0.48.0 on IceWeasel plays GREAT!  While not *exactly* 100% as smooth as Flash/XP on the same box, it's by far the best I've ever seen on a 600Mhz box with Linux, and more than "close enough" for Mom's/nieces/J6P's of the world :D  It's good enough for me, too ;)  No perceptible tearing either.

For the life of me, I can't figure out the issues on that 728Mhz P3 box.  It was a P6BAT-A+ board.  I'm thinking the motherboard was the culprit, since I swapped out nearly everything else while testing Youtube/Flash on it.  It could have been the Nvidia driver, too, but the P3 1GHz box with the same GPU (though AGP) had no Flash video issue, but that could have been the CPU speed helping out.  

I think more testing is needed to isolate video card vs Flash version issues, too.

This 600Mhz P3 box has a 100Mhz bus and RAM on a BH6 motherboard- the best Slot1 BX board ever made, IMO.

[http://www.active-hardware.com/english/reviews/mainboard/bh6.htm](http://www.active-hardware.com/english/reviews/mainboard/bh6.htm)
[http://hardware.earthweb.com/chips/article.php/637931](http://hardware.earthweb.com/chips/article.php/637931)

I am typing this right now in IceWeasel on the Zenwalk P3 600 box  :)

Zenwalk appears about as snappy GUI-wise to XP on this 600Mhz box, too.

My Faith is Restored.  

But the rants still stand on the Ubuntu/KDE/Gnome bloat creep and general boot time/responsiveness issues ;).

Now, if only Linux had an Adobe Premiere ELements or Apple iLife video editing/DVD authoring suite (and a native DVDFab HD DVD Decrypter equivalent), but that's a rant for a different day :D

Again, thanks to all the thread contributors- you really helped me out.  When the niece calls me about the jerky Youtube performance, I'll take the machine back and either swap out the motherboard, and/or video card and/or distro with Zenwalk or something else that plays Youtube fine.  Perhaps rolling back Flash to Zenwalk's Flash 9.0.48.0 on Mint might fix the issue, but that will take more testing.

I *really* need to stop doing machine builds under the gun- the stress is too much...

---

### Post by ugm6hr on 2007-12-26
> **rgb1701 said:**
> But the rants still stand on the Ubuntu/KDE/Gnome bloat creep and general boot time/responsiveness issues ;).

Now, if only Linux had an Adobe Premiere ELements or Apple iLife video editing/DVD authoring suite, but that's a rant for a different day :D


The issue of "bloat" is difficult.  Everything is relative.  Hence most Linux users upgrade every 4-8 years, while Microsoft users approx 2-4 years.  To expect an OS to stand still is unrealistic.  Linux users with modern technology want the visual goodies that slow your system down.  If you want to resurrect very ancient boxes, you may be better off sticking with 2.4 kernel distros (e.g. DSL).  Importantly, these are still being developed, unlike in the world of Microsoft, where pre-NT OS are no longer supported at all.

For simple home movie editing - I would strongly recommend kdenlive - it is apparently similar to iMovies, but there are lots of options (including some almost professional quality ones) - you might want to check this thread:
[http://ubuntuforums.org/showthread.php?t=529759](http://ubuntuforums.org/showthread.php?t=529759)

---

### Post by gn2 on 2007-12-26
> **rgb1701 said:**
> 
My Faith is Restored.  

Indeed that is great news.

You might also want to look at Vector Linux.

---

### Post by rgb1701 on 2007-12-26
> **gn2 said:**
> Indeed that is great news.

You might also want to look at Vector Linux.

I've been wanting to try Vector for some time now.  Thanks.

To all: sorry for taking out my PC build/Christmas crunch stress on you guys.

Moral of the story- stay FAR away from the P6BAT-A+ motherboard ;)

(..and try a lot of different LiveCD distros on *several* PCs/mobos before making a judgement )

PPS- I  tried Linux Mint LiveCD this morning on the BH6/600Mhz P3/512M/Matrox G450 box, and it runs amazingly well- Firefox/Flash too :D

---

### Post by rgb1701 on 2007-12-26
> **ugm6hr said:**
> 

For simple home movie editing - I would strongly recommend kdenlive - it is apparently similar to iMovies, but there are lots of options (including some almost professional quality ones) - you might want to check this thread:
[http://ubuntuforums.org/showthread.php?t=529759](http://ubuntuforums.org/showthread.php?t=529759)

Thanks for the audio/video software link. I plan to do a deep dive into Linux video editing/DVD authoring this winter.

Per my post you quoted that I subsequently edited, the single BIGGEST gap that needs to be filled in the Linux DVD area is a native DVD Fab HD Decrypter-

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

There is *no* better code out there to transfer a complete DVD to hard disk, removing all forms of DRM cruft in the process.  Ripping the movie only doesn't cut it- we need a tool that copies the VIDEO_TS folder to hard disk with everything (menus and related structure) in tact, and all intentional DRM errors removed and corrected, like DVD Fab Decrypter does.

But that's a discussion for a different thread

---

### Post by pneaveill on 2007-12-26
> **rgb1701 said:**
> I've been wanting to try Vector for some time now.  Thanks.

 PPS- I  tried Linux Mint LiveCD this morning on the BH6/600Mhz P3/512M/Matrox G450 box, and it runs amazingly well- Firefox/Flash too     Noticed you run a matrox G-450 card -- tried the dual yet? I love mine with ubuntu. Let us know how the vector thing works out please.

---

### Post by rgb1701 on 2007-12-27
> **pneaveill said:**
> Noticed you run a matrox G-450 card -- tried the dual yet? I love mine with ubuntu. Let us know how the vector thing works out please.

No, I haven't tried dual head on the G450 under Ubuntu yet.

I don't really have a need for dual head, nor a monitor available to do the dual head, plus I'm using a very nice 22" 1680x1050 LCD panel right now ;).

But I would like to experiment at some time.

I have too many Linux projects on my plate at the moment-  a Mint box for another niece, a Myth box for my den, a Geexbox for another room, an office PC with Puppy or Mint, and am currently working on a Mame arcade cabinet PC, probably with Mint on an A64 3200...

I think 2008 will go down in history as the Year of desktop Linux, the year Linux 'turned the corner" and broke out on its way to significant market share among average consumers.  

Linux is at the knee in the exponential growth curve at this moment in history for the masses.  It's really fun being a part of it and witnessing the thrashing death throes of the "old guard" :D

---

### Post by pneaveill on 2007-12-27
> **rgb1701 said:**
> No, I haven't tried dual head on the G450 under Ubuntu yet.

I don't really have a need for dual head, nor a monitor available to do the dual head, plus I'm using a very nice 22" 1680x1050 LCD panel right now ;).

But I would like to experiment at some time.


I currently run dual 17's and love it

> **rgb1701 said:**
> 


I have too many Linux projects on my plate at the moment-  a Mint box for another niece, a Myth box for my den, a Geexbox for another room, an office PC with Puppy or Mint, and am currently working on a Mame arcade cabinet PC, probably with Mint on an A64 3200...

Sounding like me now lol. Still wanting webserver on one; media server on another; small gaming system on 3rd and wife's computer for school stuff.


> **rgb1701 said:**
> 
I think 2008 will go down in history as the Year of desktop Linux, the year Linux 'turned the corner" and broke out on its way to significant market share among average consumers.  

Linux is at the knee in the exponential growth curve at this moment in history for the masses.  It's really fun being a part of it and witnessing the thrashing death throes of the "old guard" :D

2008, the year linux comes out of the closet (server closet, that is) and shows just how tough it really is.  Just think . . . we have ringside seats too.

---

### Post by uzybear on 2007-12-28
> **rgb1701 said:**
> 

And now when it's Linuxes' time to shine, it's two steps forward and one step back (better than several years ago when it was one step forward and two back ;) ).

Now I have a bad choice- let the machine go out with poor Flash/Java performance on websites my 9 year old niece will use often, or cave in and put XP Sp1 on the box... :(

you're right on the money

my 1.2ghz pIII 512mb  ibm x30 is running ubuntu 7.10 very poorly; it's certainly usuable, but it's slow, it''s choppy; for the time being, you probably should try xubuntu, but you're right that this issue needs to be  addressed

---

### Post by uzybear on 2007-12-28
> **pneaveill said:**
> 


2008, the year linux comes out of the closet (server closet, that is) and shows just how tough it really is.  Just think . . . we have ringside seats too.

yeah baby; rock on :guitar::guitar::guitar:

---

### Post by rkd on 2007-12-28
> **uzybear said:**
> 
my 1.2ghz pIII 512mb  ibm x30 is running ubuntu 7.10 very poorly; it's certainly usuable, but it's slow, it''s choppy...

If you haven't already tried this, you could open a new thread to ask for help improving the performance of your system. 

From rgb1701's experiences related in this thread, systems with half the clock speed of yours can perform quite well when the software is selected carefully. I expect if you open a new thread with the details of what you are experiencing, you will get plenty of help in finding and fixing the problem.

---

### Post by rgb1701 on 2007-12-29
> **uzybear said:**
> you're right on the money

my 1.2ghz pIII 512mb  ibm x30 is running ubuntu 7.10 very poorly; it's certainly usuable, but it's slow, it''s choppy; for the time being, you probably should try xubuntu, but you're right that this issue needs to be  addressed

Please read the entire thread- my saga revealed that the culprit was the Supercom P6BAT-A+ motherboard I was trying to utilize for my niece's Linux machinewith a P3 650 CPU overclocked to 728Mhz.

Flash/Youtube performance was poor on that mobo with any major LiveCD distro I tried- gOS, Ubuntu 7.10, Mint Darnya, PCLinuxOS, Puppy, and Zenwalk.  In my frenzy to complete the machine last weekend, I was testing the distros on only the P6BAT board, not any of my several other machines.  

However, when I tried Mint Darnya on the 600Mhz P3/BH6/512M/Matrox G450 box, Youtube/Flash was fine, about the same performance as XP SP1 on that same box.

I *highly* recommend Linux Mint Darnya with Xfce edition.  It is based on Ubuntu, has access to the great Ubuntu community and repositories, adds its own impressive Web-based software installation repository, and appears to be better optimized for performance and XP-like functionality, like simple Samba/WIndows shares configuration and other XP-like functionality for those converting over.

I think Ubuntu 7.10 need some optimizing,,  which we'll hopefully see in the Spring '08 release.

I don't know how a motherboard could impact performance so dramatically, other than perhaps poor support for the chipset on the P6BAT-A+ motherboard in the Linux kernal drivers, or simply poor bus/timing design.

Based on all my testing documented in this thread, a P3 600Mhz box should perform about as well as XP on the same box, or better, depending on distro, window manager, services running, though I need to do more benchmarks with Mint loaded on its hard disk to verify boot time and software load times between XP SP1 and Mint.  Of course, you could have a motherboard, video card or some other systemic issue that hurts your performance, as I discovered.

---

### Post by gn2 on 2007-12-29
Sam Linux has released a 2008 RC1 (testing) version which may also be worth a try.
[http://sam.hipsurfer.com/news.php?readmore=13](http://sam.hipsurfer.com/news.php?readmore=13)

---

### Post by Epic Plecostomus on 2007-12-29
Chime in real quick.  I'm running a 666mhz CPU with a gig of RAM and a 64meg Nvida card.  Aside from some minor "stupid operator" errors involving my sound setup I have had no problems.   The Nvidia card doesn't want to set up with "proper" drivers but the default abilities of the default driver are more than adequate for what I do.   I don't have any Flash/Shockwave/Java issues at all either.


You get out of Ubuntu what you put into it.   It's not going to run 100% perfect on 100% of all possible configurations 100% of the time.   Many times you're going to have to roll up your sleeves and learn things.    When I started just (what?) two weeks ago or so I was scared of the Terminal command-line.   Now, I find it almost as easy as DOS which I have worked with since the age of six. 

Not just here but other groups and friends in RL running Linux have been patient as I fiddle with things here and there and break stuff in the process.   Know what?  I've put more time optimizing this box than my laptop and it shows.   It runs (from my pov) just as fast as the dual-core laptop and is just as stable.

So yes, if you have the time and the will you can make Ubuntu run on old hardware just as well as the new hardware.   Patients and a desire to learn are all you need.

Glad the OP was able to solve his issues.   Exactly what I'm talking about.  :)

---

### Post by Pogeymanz on 2008-04-09
Hey there. I just thought I would pop in and ask about this motherboard issue. I have a PIII @ 1GHz Dell PC that has fluxbuntu on it and Flash was being very choppy and slow.

I can't decide if it's because I only have 128MB RAM and the stock video card, or if it's the motherboard that you describe. Where can I find out what kind of motherboard it is? Will it just be on a sticker somewhere on the board itself?

I plan on maxing out the RAM next time I go to my parents' house. Is it possible that it's a RAM issue and not the motherboard?

I was planning on making it my main PC now that I killed my laptop, but no youtube makes the internet boring!

---

