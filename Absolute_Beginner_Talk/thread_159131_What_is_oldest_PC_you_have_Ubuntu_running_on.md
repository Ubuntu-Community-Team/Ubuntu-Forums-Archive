---
title: "What is oldest PC you have Ubuntu running on?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Bristen Bourque on 2006-04-12
I'll be receiving an old PC in a week or two for free... it's a P166MHz, 96MB RAM and has a 1.2GB HD (not sure on disk size)...  Could that machine handle "Ubuntu Lite" perhaps?

Thanks!
  Bristen.

ps: Kubuntu installed on my old IBM ThinkPad Celeron 500MHz, 192MB RAM and 6GB HD and even though it is a tad slow, it works quite well!

---

### Post by Darkriser on 2006-04-12
your memory is a little bit low...(i installed xubuntu on 300MHz + 128MB RAM notebook)...but try looking here for some ideas:

[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)
[https://wiki.ubuntu.com/LowEndSystemSupport](https://wiki.ubuntu.com/LowEndSystemSupport)

---

### Post by gnu2tux on 2006-04-12
maybe this is cheating a little but I have it on a circa 1983 IBM PC XT which runs at approximately 8 MHz, 640K Ram and 10MB hard drive.

Well, I have a headless Pentium II which I connect via serial link from my XT.

It works very well, and means I don't have to set up another monitor in my bedroom, meaning I can play all the old-retro games as well in MS-DOS ;)

Check out my website & blog to see how:

[http://www.aliross.co.uk/museum]("http://www.aliross.co.uk/museum/ibm/5160/index.php")
and
[http://aliross.co.uk/blog/?p=2]("http://aliross.co.uk/blog/?p=2")

good fun ;)

Al.

---

### Post by az on 2006-04-12
[QUOTE=Bristen Bourque]I'll be receiving an old PC in a week or two for free... it's a P166MHz, 96MB RAM and has a 1.2GB HD (not sure on disk size)...  Could that machine handle "Ubuntu Lite" perhaps?
[/QUOTE]

Breezy will install on that.  Use server mode and once you reboot and get to the command line, edit /etc/apt/sources.list and uncomment universe.  Update and then install some packages.  You are good to go.  I have a similar box. Works fine.

sudo nano /etc/apt/sources.list
sudo apt-get update

sudo apt-get install x-window-system-core xterm gdm icewm menu rox-filer synaptic

---

### Post by djsroknrol on 2006-04-12
I have it running on a AMD K-6 400 with 160RAM..video is bad...voodoo 3dfx...but it runs...

---

### Post by YuHoo on 2006-04-12
The oldest PC... Isn't this marginalizing the Mac users and those who perhaps use an alternative platform than the IBM format? It's this type of discrimination that furthers the degredation of society! Just look at how europe has become!

For the more serious note, I'd recommend slackware or damn small linux instead for the really slow/old computer. They have been reported to run on 486s and 16mb of ram. I'd definitely suggest you look to those as well as Ubuntu. If you're feeling oldschool, try RedHat 6 or an old back copy of Suse.

---

### Post by ubuntuuser on 2006-04-12
Use [Damn Small Linux]("http://damnsmalllinux.org/"). It is easy to install, and comes with a lot of programs. And you can add programs very easily. I use it on a Pentium 150 MHz with 128 MB RAM and 2 GB hard disk. It only takes around 50 Mb, so it leaves plenty of space for personal files (talking about the 1990's understanding of "plenty of space" ;-)).

---

### Post by gr0kzer0 on 2006-04-12
My laptop's pretty ancient, made when Windows98 was young! (It's got shiny "designed for Windows98" badges which i polish every morning with pride lmao!) It has 156MB of RAM, a 450MHz CPU, and sometimes runs very... slow... ly... esp OOo. But i think that's mostly down to Gnome, i'm gonna see how it goes with a lighter window manager and a less cumbersome office package

---

### Post by fng on 2006-04-12
My mom is running ubuntu on a P2 333 mhz with 512 mb sd ram.

---

### Post by IYY on 2006-04-12
If you did a server install, and then installed some lightweight window manager and apps, I think it could work... But why? The Unix philosophy (one of them, at least) is to use the right tool for the job. Ubuntu is designed for more or less modern systems. There are other distros that are made especially for old hardware.

---

### Post by az on 2006-04-12
[QUOTE=IYY]If you did a server install, and then installed some lightweight window manager and apps, I think it could work... But why? The Unix philosophy (one of them, at least) is to use the right tool for the job. Ubuntu is designed for more or less modern systems. There are other distros that are made especially for old hardware.[/QUOTE]

Yes but with all that is available in Universe, you pretty much have a general-purpose distro with Ubuntu.

---

### Post by Bristen Bourque on 2006-04-12
Well I got the older PC tonight... it's got 2GB HD (didn't check the other specs, assumed they were correct)... I tried DSL, but it does not boot from CD... since I have "some" experience with Kubuntu on my notebook, I'd like to stick with Ubuntu if possible... I probably will try the scaled down version (server install, then lightweight windows manager, etc) before going to other distro's... I'll probably go with DSL (installed on HD) if I want to go super-light...

Thanks for the information!  I've read somewheres that Ubuntu (scaled down) should run on my older PC... obviously I'll be staying away from OpenOffice :)  Mainly for web browsing and VNC client to another machine, so I should be fine.

If anybody else wants to add what klunker machine you managed to get Ubuntu running, please post away!!

ps: sorry about the PC comment... that's my world.. PC and Windows... I forget there's other hardware out there hehe! It's nothing personal ;)

Thanks,
  Bristen.

---

### Post by Javapup on 2006-04-13
The first PC I attempted to set up for my daughter was a Pentium MMX 200mghz 96megs ram with a 6gig HDD with Ubuntu 5.04.  Loaded successfully and stable as could be.  Although it took around 3 mins to launch Open office or Firefox...  Painfully slow enough that its not reasonable to expect a novice to be satisfied with the performance (although for me was a real testimony on stability as Windbloze loaded on a undersized memory gets shakey as h*ll) 
I went ahead and bite the bullet and got a P3 1.8 256meg and it runs 5.10 like a champ. 
Ubuntu has been a great choice- great support- visit often-read lots- and set up a great system for a novice user (daughter) that likes to download all kinds of crap and visit sites loaded with spyware.  With little effort on her part she's learning not only Windbloze and spreading the gospel of open source.
Its been a great learning experience for me learning a new OS without leaving me with out my windboze machines as a climb the learning curve 
Good luck

---

### Post by Bristen Bourque on 2006-04-13
> **Javapup]The first PC I attempted to set up for my daughter was a Pentium MMX 200mghz 96megs ram with a 6gig HDD with Ubuntu 5.04.  Loaded successfully and stable as could be.[/QUOTE]
 that's interesting! Machine very close to mine... when you say Ubuntu 5.04, you mean default install? Or did you go through a "light" install?

[QUOTE=Javapup]Although it took around 3 mins to launch Open office or Firefox... [/QUOTE]
 yeah, 3 minutes is too slow.. my patience is not that great heh  said:**
> [...]although for me was a real testimony on stability as Windbloze loaded on a undersized memory gets shakey [...] 
 the machine I just received has Win95 on it.. seems to work ok.. I figure if it can run Win95 (Internet Explorer, OutlookExpress, etc) it should be able to handle a light Ubuntu install without too much trouble (I hope anyways!)

Thanks for the reply!
  Bristen.

---

### Post by gr0kzer0 on 2006-04-13
IYY, ubuntu in its standard form may be designed for the more modern system. But ubuntu, and linux in general, are so modular that u can get em to fit _anything_. Just look at ubuntu lite and xubuntu. I use ubuntu on my ol' laptop cos i like the look and feel of the distro, plus its philosophy: humanity to others - is ubu thru and thru, i don't just want linux - i want ubuntu!

---

### Post by BjornHaland on 2006-04-13
[quote=gnu2tux]maybe this is cheating a little but I have it on a circa 1983 IBM PC XT which runs at approximately 8 MHz, 640K Ram and 10MB hard drive.[/quote]
Me want!!!!11 (check my avatar, remember Hero's quest?)

---

### Post by gnu2tux on 2006-04-13
I have quest for glory on my xt as well as leisure suit larry and space quest 1 & 2

it rocks.

:)

---

### Post by BjornHaland on 2006-04-13
Ah! I played the QFG, King's Quest, Police Quest, Space Quest series!

Did you make those DOS menus using basic batch programs too?

:KS

---

### Post by bodycoach2 on 2006-04-13
Installed Ubuntu on an iMac G3 (Strawberry/pink), 333mhz, 8gig, 160mg. I had Mac OSX on it, but it would freeze. It's slow bring programs up, but once up, they run just fine. Here's a link to a screenshot of it running Firefox, GIMP, and GAIM. It actually runs faster with Ubuntu, even with all the programs running.

[http://flickr.com/photos/coachdanny/107221900/](http://flickr.com/photos/coachdanny/107221900/)

---

### Post by Metz on 2006-04-13
Well....it's currently running on my laptop (Advent 7090), which is about 4 years old..ish.

My main server is an old Patriot machine....not even sure of the spec, but it's atleast a P4, I'm sure. It's about 7-8 years old.

Recently....I've installed it on my old Gateway Tower....which, if I remember correctly, is older than my kids....about 16 years old. I'm pretty sure I bought in 1990....when the 'new' (sic) pentium 120mhz was the FASTEST PROCESSOR ON THE PLANET !!! Obviously, it was defunct inside 3 months, but it still works. Only thing I had to do was swap in a normal CD drive, as it had a fancy three-disc loader in it which Ubuntu didn't particularly like :)

S'all good :):)

---

### Post by Changeling on 2006-04-13
I'm currently running  Ubuntu on a Dell Dimension 500 Celeron with 384mgs of ram. On the other drive I'm running Debian Sid.

---

### Post by moopere on 2006-04-16
I beat you all!

I've had Ubuntu Breezy running as a firewall/NAT box on a 486DX2/66 with 48MB RAM (upgrade from Debian which will install in <24MB and a floppy disk drive).  I even left xfce on it, running a 1MB cirrus logic 5428 vesa bus video (!!!!).  2 NICs, 4 serial ports, 2 parallel, 1.2GB conner disk drive

This box only just recently went down due (I think) to the VESA video card.  I'll be rebuilding it with an old trident ISA video soon and I'm sure it will keep on rocking (ha!).

Someone beat that for a low end box.

Cheers,
Craig

---

### Post by Bloch on 2006-04-16
I installed it for a friend on a PIII 800MHz with 256 ram. 

It runs fine, but the windows leave stepped track (you know what I mean) when you move them. When he had windows installed he had the transparant windows when moving/changing size.
Is there an option for this in ubuntu? Or any other options, within the gnome desktop, to improve response?

---

### Post by noalternative on 2006-04-16
[QUOTE=Bristen Bourque]Well I got the older PC tonight... it's got 2GB HD (didn't check the other specs, assumed they were correct)... I tried DSL, but it does not boot from CD... since I have "some" experience with Kubuntu on my notebook, I'd like to stick with Ubuntu if possible... I probably will try the scaled down version (server install, then lightweight windows manager, etc) before going to other distro's... I'll probably go with DSL (installed on HD) if I want to go super-light...

Thanks for the information!  I've read somewheres that Ubuntu (scaled down) should run on my older PC... obviously I'll be staying away from OpenOffice :)  Mainly for web browsing and VNC client to another machine, so I should be fine.

If anybody else wants to add what klunker machine you managed to get Ubuntu running, please post away!!

ps: sorry about the PC comment... that's my world.. PC and Windows... I forget there's other hardware out there hehe! It's nothing personal ;)

Thanks,
  Bristen.[/QUOTE]


I like f[eather]("http://featherlinux.berlios.de") better than dsl. It works on systems just as old, and is a much more complete distro in my view. Granted feather  programmers don't advertise feather nearly as well as dsl developers, but I personally like it much better.  I think it supports hardware better, and I think it is easier to install new programs in feather.  There is also luit, but it doesn't come out with new distros very frequently.  It is basically dsl with xfce.

---

### Post by Bristen Bourque on 2006-04-17
well I played around with the old PC on the weekend.. it is in fact a 166MHz, 96MB RAM and 2GB HD machine.  I basically want to use this as a "thin client" and "web browser".  I don't know if I'll have any other use for it.. perhaps I'll have a time tracking tool in there or something, but that's it...

The first thing I tried is DSL.. I figured that is the smallest and fastest Linux distro for such an old machine (I could be wrong however, I'm just a newb heh)... It did not boot from CD, so I had to create a boot floopy and a "poor man's install" (that's what they call it, but I don't know why heh).

I was unpleasantly surprised with the results.  The PC ran slower with DSL than with the Win95 that was installed on the machine.  If I ran Win95 with a VNC client, the graphics were way quicker than if I was using DSL and a VNC client (perhaps the VNC client in DSL was not as recent as the Win95 one?).  I also noticed that browsing the internet was also faster in Internet Explorer on Win95.  So I'm thinking that Ubuntu with a light-weight windows manager will be slower than DSL?  Would that be true?  I was really hoping to have Linux on that box, but I'm not sure it's worth the trouble since Win95 is in there and it appears to work faster than with Linux? 

I must of done something wrong, right?

Thanks for any input!
  Bristen.

ps: I really enjoyed hearing about all the old klunkers you people have Linux running on.. that 486 must be SOOOOME slow!! :)

---

### Post by noalternative on 2006-04-17
[QUOTE=Bristen Bourque]well I played around with the old PC on the weekend.. it is in fact a 166MHz, 96MB RAM and 2GB HD machine.  I basically want to use this as a "thin client" and "web browser".  I don't know if I'll have any other use for it.. perhaps I'll have a time tracking tool in there or something, but that's it...

The first thing I tried is DSL.. I figured that is the smallest and fastest Linux distro for such an old machine (I could be wrong however, I'm just a newb heh)... It did not boot from CD, so I had to create a boot floopy and a "poor man's install" (that's what they call it, but I don't know why heh).

I was unpleasantly surprised with the results.  The PC ran slower with DSL than with the Win95 that was installed on the machine.  If I ran Win95 with a VNC client, the graphics were way quicker than if I was using DSL and a VNC client (perhaps the VNC client in DSL was not as recent as the Win95 one?).  I also noticed that browsing the internet was also faster in Internet Explorer on Win95.  So I'm thinking that Ubuntu with a light-weight windows manager will be slower than DSL?  Would that be true?  I was really hoping to have Linux on that box, but I'm not sure it's worth the trouble since Win95 is in there and it appears to work faster than with Linux? 

I must of done something wrong, right?

Thanks for any input!
  Bristen.

ps: I really enjoyed hearing about all the old klunkers you people have Linux running on.. that 486 must be SOOOOME slow!! :)[/QUOTE]


firefox is more memory intensive than Internet Explorer.  Try Opera, which is now free.  Also you can [tweak firefox]("http://www.freerepublic.com/focus/f-bloggers/1327586/posts") to use less ram.   You can also try the epiphany browser.    

Yes, ubuntu running xfce will be slower than dsl or feather.

It is generally agreed that linux requires more memory and less processor speed than windows.  Try upgrading your memory.

---

### Post by noalternative on 2006-04-17
I use it in a Compaq 5184 with an amd k6-2 350 mhz, and 194 mb of ram.  I dual boot it with Windows XP on a 30 gb hardrive.  It has a dvd-rom. This is my main computer.  I run [xubuntu breezy badger]("https://wiki.ubuntu.com/Xubuntu").  Basically it is ubuntu with the xfce desktop.


My second computer is a Dell Latitude xpi laptop, with 16 mb of memory and a 1 gb hardrive, and a floppy with no cdrom.  I use [Tiny Linux]("http://tiny.seul.org/") on it, with jwm windows manager.  I use siag office and a patched version of dillo.  I use mutt text based email program with it.

---

### Post by rjburk on 2006-04-18
I have Kunbuntu running on a PII with 64mg of RAM.  It's an old(of course) Gateway motherboard(maybe a good one, I don't know) I think the harddrive is what made it go.  I used a good 20gig HD.  
I can log onto the internet using my DSL connection and stuff.

---

### Post by Bristen Bourque on 2006-04-18
[QUOTE=noalternative]firefox is more memory intensive than Internet Explorer.  Try Opera, which is now free.  Also you can [tweak firefox]("http://www.freerepublic.com/focus/f-bloggers/1327586/posts") to use less ram.   You can also try the epiphany browser.    

Yes, ubuntu running xfce will be slower than dsl or feather.

It is generally agreed that linux requires more memory and less processor speed than windows.  Try upgrading your memory.[/QUOTE]

as for the web browse, there was a Dillo in DSL which is apparently way lighter than FireFox... right? there was a slight (barely noticeable) improvement in speed when using Dillo... both were "usable", but just slower than IE on Win95.

as for memory, I'd love to upgrade... however, I have no idea where one could find RAM for such an old PC :-k Besides, it would have to be free because the machine is so old, it could die tomorrow :(

Thanks for the reply,
  Bristen.

---

### Post by Xzallion on 2006-04-18
I just got Ubuntu running on a Pentium 1 233Mhz with 64Mb ram.  It uses XFCE4 and runs openoffice fairly easily.  Its a little slow loading apps, but it gets the job done.

---

### Post by georgepds on 2006-04-19
For older machines you might also want to try puppy linux. My goal is to get some distribution ( not sure which) on my old IBM think pad ( memory limit ~96 mB)

It was designed in the era of w95. I do have w2k working on it, but it is way too slow. 

[http://www.puppylinux.org/](http://www.puppylinux.org/)

--G

---

### Post by Bristen Bourque on 2006-04-19
the way it is going now, I may not have an option but to install DSL if I want Linux on it.. seems to be the only one I can get running on the box... for some reason, I can't boot from CD (even with SmartBootManager)... tried instlux and that didn't work either... :(  Not that important I guess, it's just to be a VNC client and web browser, even if I have to put it with Win95, it's not that big of a deal I guess... I regret selling my P550Mhz, 256MB RAM, 30GB HP though, that would of worked!

I'll look into Puppy Linux! 

Thanks for the suggestion.
  Bristen.

---

### Post by Peter76 on 2006-04-19
I have Ubuntu running on several older machines, the slowest an IBM 200Mhz with 96 Mb RAM and the "fastest" a PIII 700 with 196 Mb of Ram. All have icewm as windowmanager and abiword and gnumeric for the office stuff. Firefox is starting quite slow on the ibm, but runs fine after starting; on the P111 it has not really a problem.

---

### Post by OBnascar on 2006-04-19
[QUOTE=Bristen Bourque]I'll be receiving an old PC in a week or two for free... it's a P166MHz, 96MB RAM and has a 1.2GB HD (not sure on disk size)...  Could that machine handle "Ubuntu Lite" perhaps?[/QUOTE]

Give VectorLinux 5.1 Live CD a try[[COLOR="DarkOrange"]**HERE**[/COLOR]]("http://www.vectorlinux.com/")

It is small, fast, light-weight and works well on older computers

---

### Post by Bristen Bourque on 2006-04-19
[QUOTE=Peter76]I have Ubuntu running on several older machines, the slowest an IBM 200Mhz with 96 Mb RAM and the "fastest" a PIII 700 with 196 Mb of Ram. All have icewm as windowmanager and abiword and gnumeric for the office stuff. Firefox is starting quite slow on the ibm, but runs fine after starting; on the P111 it has not really a problem.[/QUOTE]

that's interesting... how do you find it works out on the P1 200Mhz? I know you mention FireFox being slow to start, but what about boot time?  The window manager response time?  I'd really love to get Ubuntu on the old box, but I just can't get the stupid machine to boot from CD!!  I may have to go through the netboot stuff, which appears to be combersome (haven't really looked into yet)...  If you think it works ok, I may continue trying to get it installed...

Thanks for the reply!
  Bristen.

---

### Post by Bristen Bourque on 2006-04-19
[QUOTE=OBnascar]Give VectorLinux 5.1 Live CD a try[[COLOR="DarkOrange"]**HERE**[/COLOR]]("http://www.vectorlinux.com/")

It is small, fast, light-weight and works well on older computers[/QUOTE]

Thanks for the suggestion! I actually have the ISO downloaded.. I've got it here somewheres... It's another option.. however, I've read that for Vector 5.1, the minimum recommended specs are much higher than my machine if I remember correctly... I think I've read that for my machine, I would have to go to an older version of Vector... I'll keep Vector on the "back burner" as another option... I'd rather go Ubuntu, or some tiny Linux such as Puppy or DSL...

Thanks for the interest!
  Bristen.

---

### Post by Kurt` on 2006-04-19
A 233mhz laptop with 64mb ram. :D

Fluxbox for the win

---

### Post by noalternative on 2006-04-20
[QUOTE=Bristen Bourque]as for the web browse, there was a Dillo in DSL which is apparently way lighter than FireFox... right? there was a slight (barely noticeable) improvement in speed when using Dillo... both were "usable", but just slower than IE on Win95.

as for memory, I'd love to upgrade... however, I have no idea where one could find RAM for such an old PC :-k Besides, it would have to be free because the machine is so old, it could die tomorrow :(

Thanks for the reply,
  Bristen.[/QUOTE]

You can probably get ram off of ebay for less than $20.  There are probably system and upgrade specs for your computer available online, or from your manuals. Frankly if dsl and dillo runs slower than 95 I think there is something wrong.  You could just stick with 95 though. It is your choice.

---

### Post by picnic on 2006-04-20
I've got it running on a Celeron 466 Mhz with 160Mb RAM and a 4Gb hard drive. I did a server install and then installed fluxbox. I've tried to avoid using any heavyweight applications on it. Using dillo and lynx for web browsing.

---

### Post by Bloch on 2006-04-20
Celeron 466MHz and 160Mb of ram seem like generous specs to me. I wonder how default ubuntu would run on that?

I have a 300MHz 96Mb machine running Libranet (a distro based on debian sarge) with IceWm and rox-filer.  It works fine and I use firefox for browsing, Abiword for writing.

I'm just wondering why you would choose ubuntu with a fluxbox window manager, rather than some completely different distro? To me ubuntu is the well-laid out gnome desktop. Is it because you get all the hardware compatibility in the background?

---

### Post by Bristen Bourque on 2006-04-20
[QUOTE=Bloch]Celeron 466MHz and 160Mb of ram seem like generous specs to me. I wonder how default ubuntu would run on that?

I have a 300MHz 96Mb machine running Libranet (a distro based on debian sarge) with IceWm and rox-filer.  It works fine and I use firefox for browsing, Abiword for writing.[/QUOTE]
 as for me, I have Kubuntu purring quite smoothly on my old IBM ThinkPad (Celeron 550Mhz, 192MB RAM, 6GB HD)... I do have problems with sound currently, but I'm not overly concerned about it.. hopefully I'll figure it out at some point... OpenOffice 2 for writing serious documents, KEdit for quick notes and text files, FireFox for web browsing, krdc for VNC client... if I can get multimedia working, I'll have a perfect setup!

[QUOTE=Bloch]I'm just wondering why you would choose ubuntu with a fluxbox window manager, rather than some completely different distro? To me ubuntu is the well-laid out gnome desktop. Is it because you get all the hardware compatibility in the background?[/QUOTE]
 I actually don't use the "Ubuntu" install but the "Kubuntu" install on my notebook... hardware compatibility, the Debian packaging/installing, the community, etc... plenty of reasons to use Ubuntu!  From what I can see so far (only a few months into Linux - started with Kubuntu), it appears to be fairly solid as well...

Bristen.

---

### Post by picnic on 2006-04-20
I used ubuntu as I had the ubuntu disc as its installed on my main computer and currently don't have the facilities to burn a cd with any other distro. I was more installing it for fun on my old computer. I may get round to trying some other lightweight distros at some point but I found the ubuntu forums a very useful source of information when I came across problems.

---

### Post by malavar on 2006-04-20
i have an oldcompaq lte 5280 with 128mhz and 48mb of ram, + 1024kb graphics card 1.7gb harddrive, but its running debian. i wanted ubuntu but i didnt know where to get pcmcia net driver modules for a net install...

---

### Post by prezbedard on 2006-04-20
an old server

compaq proliant 1600

dual 600Mhz CPUs
768MB memory

6 18.2 GB SCSI drives 

ubuntu is on one of those drives.

---

