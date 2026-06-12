---
title: "BSD versus Linux question"
date: 2006-04-07
forum: BSD
---

### Post by awakatanka on 2006-04-07
I have tested some linux distro's now and my new project will be mepis soon to see if its better then my choose for the moment ,kubuntu.

I have learned a lot in the last months, but a while ago someone posted a link of pcbsd and it made me curious  and of course i tryed it out.

It had a good installer and everything worked out the box even network-manager with wep and wpa. Also i liked there way of installing, i understand that it was not the normal way of installing things but it felt like windows. I instaled kubuntu again because pcbsd was in beta and i had some very nasty bugs and i was to new to solve them.

Now my main question is :

1. What is the difference of linux and BSD?
2. Whats up with all those freebsd,openbsd etc.
3. Why is BSD more secure ( atleast that's the info i get )

Because I'm always curious to learn new things it gives me back the feeling of my early PC days when everthing was new.

[http://www.pcbsd.org/](http://www.pcbsd.org/) i was falling in love of it and will follow it. Maybe time to do a windows,kubuntu,BSD and test boot on my main desktop PC to feed my curiosity itch

---

### Post by endersshadow on 2006-04-07
1. Linux was developed at the University of Helsinki, with a top layer of GNU, which was developed at MIT.  BSD was created at the University of California at Berkeley.  Linux got its name from its creator, Linus Torvalds.  BSD got its name from its creator, LSD.  Okay, just joking, BSD means Berkeley Software Distribution.  The two are very similar, as they are both based on Unix/Minics.  Linux (more appropriately referred to as GNU/Linux, but I'm lazy) was released under the GPL or GNU Public License, whereas BSD was released under the BSD license (confused yet?).  Apple's OS X uses Darwin, a BSD distribution, under the hood.  Apple could not have done what it has with OS X with the use of a GPL base, as per the licenses.

2. Same thing with Linux.  Ubuntu, Mepis, Linspire, Debian, Slackware, Fedora, Arch, Gentoo, and other things from the Star Wars universe.

3. Not sure if it is more secure, but there are more attacks/viruses for Linux.  However, that may only be due to Linux's popularity over BSD.  I don't know enough about the discussion from the BSD side to make a full and accurate judgement :-D

---

### Post by KingBahamut on 2006-04-07
BSD, specifically OpenBSD spends a lot of time code auditing and so forth to protect against stack and buffer overflows. If memory serves correctly they use GCC specific extensions to defend against stack overflows ,etc. Additionally they spend an excessive amount of time integrating as much crypto as possible into the OS. If you want to have an even more rare look into the security features of BSD, look closely at Open and Net-BSD , they are , at least according to Theo (De Raadt) , very difficult to crack.

---

### Post by awakatanka on 2006-04-07
One thing made me confused because i did know they where both based on unix, but not everything is working on bsd side it has to be remade for it.


is the base that different that i can't configure sources?

Also i read bsd is closer to unix then linux.

And why do some choose linux above bsd and the otherway around.

And isn't freebsd another sort of kernel then openbsd? Because freebsd has different distro's so does openbsd.

I'm confused. hehe

Edit : kingbahamut answered the last part thxs.

---

### Post by ComplexNumber on 2006-04-07
Also, linux is written in pure C, so its portable across the different processors. BSD is partly written in assembly, so its not.

---

### Post by KingBahamut on 2006-04-07
While not making it nessecarily better than Linux as a whole, BSD and its variants have a certain place in the hearts of many. I find it hard to differentiate the differences between the two. At one time SunOS (that which would become Solaris, and the initial system that I learned on as my first computer) was based on BSD, though it had some aspects of SystemV (dev'ed by AT&T in '83 approx). Solaris would eventually become totally SystemV, and the next major embracing of BSD would come from Steve Jobs with NeXtStep(this was after Apple booted him from the company) , the precursor to darwin, and eventually OSX. While not as portable and Linux might be, its liscensing requirements are much more open, allowing for greater extensibility of it as an OS. At least that was the idea back in the 70s.....

---

### Post by awakatanka on 2006-04-07
[QUOTE=KingBahamut]While not making it nessecarily better than Linux as a whole, BSD and its variants have a certain place in the hearts of many. I find it hard to differentiate the differences between the two. At one time SunOS (that which would become Solaris, and the initial system that I learned on as my first computer) was based on BSD, though it had some aspects of SystemV (dev'ed by AT&T in '83 approx). Solaris would eventually become totally SystemV, and the next major embracing of BSD would come from Steve Jobs with NeXtStep(this was after Apple booted him from the company) , the precursor to darwin, and eventually OSX. While not as portable and Linux might be, its liscensing requirements are much more open, allowing for greater extensibility of it as an OS. At least that was the idea back in the 70s.....[/QUOTE]If this from a company perspective seen a better license system why isn't it embraced more then linux? Because some company's are afraid they have to give there spec's/codes free because of the gpl license if they use a part of a gpl code. 
Is bsd license maybe a better license to wright closed drivers for those company's? And there for make it a better base to build a desktop on?

Damn i hate my limited English, can't express and translate all my question.

---

### Post by IYY on 2006-04-07
If you're looking for an OS for a server, you may be interested in OpenBSD's security (even though it could be a dying project).

If it's for the desktop, however, you can pretty much see the BSDs as Linux distros. There really isn't much difference from a user's point of view: same commands, same programs, same file structure. I prefer GNU/Linux over BSD because of the GPL; the BSD license is nice, but it allows freedom to be lost, and lets people take things from OSS without giving anything back.

---

### Post by KingBahamut on 2006-04-07
I wouldnt say that the liscense is more or less restrictive. If I get what your asking. The BSD liscense is somewhat similiar to the GPL. Actually GPL would seem to be a lot less restrictive than the BSD liscense, as the BSD liscense (memory serving me again) requires a certain amount of recognition of the Berkeley Software Distribution , where as GPL does not.

---

### Post by KingBahamut on 2006-04-07
[QUOTE=IYY]If you're looking for an OS for a server, you may be interested in OpenBSD's security (even though it could be a dying project).[/QUOTE]

I wouldnt nessecarily call OpenBSD a dying project, just a slow one. They take such great stake in code changes and functionality that one can only assume it takes forever for them to make releases, additionally, the theme songs they release are just a riot to listen to even though they sound REALLY bad. =)

---

### Post by awakatanka on 2006-04-07
[QUOTE=IYY]If you're looking for an OS for a server, you may be interested in OpenBSD's security (even though it could be a dying project).

If it's for the desktop, however, you can pretty much see the BSDs as Linux distros. There really isn't much difference from a user's point of view: same commands, same programs, same file structure. I prefer GNU/Linux over BSD because of the GPL; the BSD license is nice, but it allows freedom to be lost, and lets people take things from OSS without giving anything back.[/QUOTE]
atm i'm not a server man, because i'm only young in the linux/bsd world and i first want to learn the basic's.

Can't you build a desktop on bsd and use gpl code for the prgs on top of that? 

Hmm maybe its better for me to read the bsd license first before i have questions ;).

---

### Post by KingBahamut on 2006-04-07
[http://www.opensource.org/licenses/bsd-license.php](http://www.opensource.org/licenses/bsd-license.php) 

[http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html)

Should do it for you.

---

### Post by Virogenesis on 2006-04-07
[QUOTE=awakatanka]atm i'm not a server man, because i'm only young in the linux/bsd world and i first want to learn the basic's.

Can't you build a desktop on bsd and use gpl code for the prgs on top of that? 

Hmm maybe its better for me to read the bsd license first before i have questions ;).[/QUOTE]
You can build a desktop on bsd and use gpl programs in the mixture thats what apple has done they used darwin and then layered gpl on top of  such as apache, php and various other stuff.

Personaly I wouldn't say BSD  anymore secure than linux due to the forks if a project forks then the other bugs might not get patched for example bugs a bug in freebsd might not get patched but in openbsd it might. 
We've seen this happening to apple they have used bsd but problem is now they have old bugs in their OS.

---

### Post by Sheinar on 2006-04-07
[QUOTE=KingBahamut]They take such great stake in code changes and functionality that one can only assume it takes forever for them to make releases[/QUOTE]
Actually, they make new releases every 6 months if I recall correctly.

---

### Post by imagine on 2006-04-07
[QUOTE=KingBahamut]BSD, specifically OpenBSD spends a lot of time code auditing[/QUOTE]No, they dont. They spend a lot of time *claiming that* they spend a lot of time with making the system more secure. And if a security hole is found they simply declare it as non-existant [1].
What gets done in the remaining time, depends on the situation: If the OpenBSD team needs money, they go around and ask everybody for some donations. Of course no donations out of sympathy, but because half of the world *owes* the developers some money, those lusers just didn't know yet. Otherwise the team is content with stating that BSD is superior to everything else, that the Linux sourcecode is full of crap and actually the only reason to use it can be stupidity [2].


[1] [http://www.securityfocus.com/columnists/380](http://www.securityfocus.com/columnists/380)
[2] [http://www.forbes.com/intelligentinfrastructure/2005/06/16/linux-bsd-unix-cz_dl_0616theo.html](http://www.forbes.com/intelligentinfrastructure/2005/06/16/linux-bsd-unix-cz_dl_0616theo.html)



...
Damn it, I suck at trolling :/

---

### Post by awakatanka on 2006-04-08
> **imagine]No, they don't. They spend a lot of time *claiming that* they spend a lot of time with making the system more secure. And if a security hole is found they simply declare it as non-existant [1].
What gets done in the remaining time, depends on the situation: If the OpenBSD team needs money, they go around and ask everybody for some donations. Of course no donations out of sympathy, but because half of the world *owes* the developers some money, those lusers just didn't know yet. Otherwise the team is content with stating that BSD is superior to everything else, that the Linux sourcecode is full of crap and actually the only reason to use it can be stupidity [2].


[1] [http://www.securityfocus.com/columnists/380](http://www.securityfocus.com/columnists/380)
[2] [http://www.forbes.com/intelligentinfrastructure/2005/06/16/linux-bsd-unix-cz_dl_0616theo.html](http://www.forbes.com/intelligentinfrastructure/2005/06/16/linux-bsd-unix-cz_dl_0616theo.html)



...
Damn it, I suck at trolling :/[/QUOTE]If i read the comments its a none issue because it only can be done by someone with root access and if someone gots the root access you got a bigger problem.

He isn't the onlyone that reacts in strange manners, linus can do it to sometimes  said:**
>  The FreeBSD bootloader can load binary drivers at boot-time. This allows third-party driver manufacturers to distribute binary-only driver modules that can be loaded into any FreeBSD system. Due to the open-source nature of FreeBSD, it is very easy to develop device drivers for new hardware. Unfortunately, most device-manufacturers will only release binaries for Microsoft operating systems. This means that it can take several months after a hardware device has hit the market until a device driver is available.


and > The Linux community intentionally makes it difficult for hardware manufacturers to release binary-only drivers. This is meant to encourage hardware manufactureres to develop open-source device drivers. Unfortunately most vendors have been unwilling to release the source for their drivers so it is very difficult for Linux users to use vendor supplied drivers at all. 

Does this difference makes bsd a better start for desktop os?

Thats my last question, i'm going to reinstall my main desktop to quartet boot to learn more about the difference's.

Thxs for answering all.

Btw [http://www.debian.org/ports/netbsd/](http://www.debian.org/ports/netbsd/) didn't read it yet butdebian is looking into it to also.

---

### Post by helpme on 2006-04-08
[QUOTE=ComplexNumber]Also, linux is written in pure C, so its portable across the different processors. BSD is partly written in assembly, so its not.[/QUOTE]
[http://www.netbsd.org/Ports/#ports-by-cpu](http://www.netbsd.org/Ports/#ports-by-cpu)

:-k

---

### Post by helpme on 2006-04-08
Well, I don't want to go into the licensing debate. These only always lead to flamewars.

Just wanted to point out that there's also DesktopBSD, which might be worth looking at, if you want to use BSD as a desktop:
[http://www.desktopbsd.net/](http://www.desktopbsd.net/)

---

### Post by awakatanka on 2006-04-08
[QUOTE=helpme]Well, I don't want to go into the licensing debate. These only always lead to flamewars.

Just wanted to point out that there's also DesktopBSD, which might be worth looking at, if you want to use BSD as a desktop:
[http://www.desktopbsd.net/](http://www.desktopbsd.net/)[/QUOTE]
hmmm cool more to try out.

License are needed but it restricting also users and company's in a way. To debate that someone can better make a new topic ;).

---

### Post by fuscia on 2006-04-08
pretty open-minded, in-depth explanation of the differences - [http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)

---

### Post by ComplexNumber on 2006-04-08
[quote=helpme][http://www.netbsd.org/Ports/#ports-by-cpu]("http://www.netbsd.org/Ports/#ports-by-cpu")

:-k[/quote] it would help you to actually read that article before showing yourself up again. they're the platforms that its been ported to. look down the page to read "Not yet integrated porting efforts". there's a difference between 'portable' and 'capable of being ported'.

---

### Post by PatrickMay16 on 2006-04-08
[QUOTE=ComplexNumber]it would help you to actually read that article before showing yourself up again. they're the platforms that its been ported to. look down the page to read "Not yet integrated porting efforts". there's a difference between 'portable' and 'capable of being ported'.[/QUOTE]
Whoa! Calm down, man!

---

### Post by ComplexNumber on 2006-04-08
[quote=PatrickMay16]Whoa! Calm down, man![/quote] i couldn't be more calm :). its just that at every single opportunity he has a go to try and prove me wrong. he never gets anywhere, though :mrgreen:

---

### Post by helpme on 2006-04-08
[QUOTE=ComplexNumber]i couldn't be more calm :). its just that at every single opportunity he has a go to try and prove me wrong. he never gets anywhere, though :mrgreen:[/QUOTE]
:roll: :roll: 

Actual ports that are available, not proposed or only worked on:
```
CPU 	Port
alpha 	alpha
arm 	acorn26  acorn32  cats  evbarm  hpcarm  iyonix  netwinder shark 
hppa 	hp700
i386 	i386  xen
m68010 	sun2 
m68k 	amiga  atari  cesfic  hp300  luna68k  mac68k  mvme68k  news68k  next68k  sun3  x68k
mipseb 	evbmips  (either eb and el) ews4800mips  mipsco  newsmips  sbmips  (either eb and el) sgimips
mipsel 	algor  arc  cobalt  evbmips  hpcmips  playstation2  pmax  sbmips 
ns32k 	pc532
powerpc 	amigappc  bebox  evbppc ibmnws macppc  mvmeppc  ofppc  pmppc  prep  sandpoint 
sh3eb 	evbsh3  (either eb and el) mmeye
sh3el 	dreamcast  evbsh3  hpcsh 
sh5 	evbsh5 
sparc 	sparc 
sparc64 	sparc64 (Can also run sparc binaries)
vax 	vax
x86_64 	amd64 (Can also run i386 binaries)
```

How about getting a clue before trolling the next time around?

---

### Post by ComplexNumber on 2006-04-08
**helpme**
for crying out loud, helpme, get a clue. its written partly in assembly. in case you didn't know, assembly is tied to a processor or familiy of processors. that means that its not naturally portable. at least some rewriting is necessary.

---

### Post by helpme on 2006-04-08
[QUOTE=ComplexNumber]**helpme**
for crying out loud, helpme, get a clue. its written partly in assembly. in case you didn't know, assembly is tied to a processor or familiy of processors. that means that its not naturally portable. at least some rewriting is necessary.[/QUOTE]
As NetBSD shows, these problems, if they exist at all (remember, once again you did provide no proof at all), can be easily overcome. To claim that BSD isn't as easily portable as Linux, when at least one well known BSD is known for running on everything but a toaster (oh wait, it [even runs on a toaster]("http://www.embeddedarm.com/news/netbsd_toaster.htm")) isn't very convincing. Wouldn't you agree old chap?

Also, you don't seem to be aware of it, but there are several different BSDs, so that a broad claim like BSD is written in assembly makes even less sense.

---

### Post by ComplexNumber on 2006-04-08
i'm not going to argue with you any further because the truth remains. i'm all too aware of the different variations of BSD. also, its hilarious that you should come out with something like  "remember, once again you did provide no proof at all" considering your previous posts (example: [this]("http://www.ubuntuforums.org/showthread.php?t=153754&page=6") thread). you must live in a world of your own.

---

### Post by helpme on 2006-04-08
[QUOTE=ComplexNumber]i'm not going to argue with you any further because the truth remains. i'm all too aware of the different variations of BSD. also, its hilarious that you should come out with something like  "remember, once again you did provide no proof at all" considering your previous posts (example: [this]("http://www.ubuntuforums.org/showthread.php?t=153754&page=6") thread). you must live in a world of your own.[/QUOTE]
Ah, good tactic, if you don't have any arguments left, resort to personal attacks and declare yourself the winner.
Impressive.

---

### Post by pitkali on 2006-04-08
I have tried different BSDs and perhaps I'll do it again in the future. For the time being I just would like BSD to support all my laptop hardware. This is actually strange requirement, becasue I don't use 3d acceleration anyway ;)

Besides, I got the impression, that Linux filesystems are better. I'm not sure why, but they felt faster (ReiserFS being my current filesystem). And I love Debian way of packaging stuff.

If only my microphone worked under linux. Chances are it doesn't also work under any BSD, so this is perhaps an irrelevant remark ;)

Regards,

---

### Post by awakatanka on 2006-04-08
[QUOTE=fuscia]pretty open-minded, in-depth explanation of the differences - [http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)[/QUOTE]
Thxs for the link, the pcbsd guys posted this link to and was reading it, it gives a better few of the differences of both. Its a good read.

---

### Post by pitkali on 2006-04-08
Interesting article. I didn't learn much new things. However I feel the need to comment it in the following way:

I like chaos :)

---

### Post by Lunixfanboy on 2006-04-09
[QUOTE=ComplexNumber]Also, linux is written in pure C, so its portable across the different processors. BSD is partly written in assembly, so its not.[/QUOTE]I am quite sure NetBSD would be glad to hear that and not have to support the 60 or so architectures it does [http://www.netbsd.org/Ports/]("http://www.netbsd.org/Ports/").

---

### Post by ComplexNumber on 2006-04-09
**LunixFanboy**
read last sentence of post 21.

---

### Post by awakatanka on 2006-04-09
[QUOTE=ComplexNumber]**LunixFanboy**
read last sentence of post 21.[/QUOTE]Please explain youre #21 post so that i person like me can understand it to. I realy don't know what you trying to say there.
> One of the primary focuses of the NetBSD project has been to make the base OS extremely portable. This has resulted in NetBSD being ported to a large number of hardware platforms. NetBSD is also highly interoperable, implementing many standard APIs and network protocols, and emulating many other systems' ABIs.

In post #5 you say it isn't possible they show you that they are porting to many hardware platforms, sure there some not yet done but that counts to for linux.

---

### Post by helpme on 2006-04-09
[QUOTE=ComplexNumber]**LunixFanboy**
read last sentence of post 21.[/QUOTE]
:rolleyes: :rolleyes: :roll: :roll: 
> Ports in the source tree (top)

This table lists details for each port, including the latest formal release or snapshot ('snap'). Complete binary and source distributions are available for ports with formal releases.

Those ports which are not yet considered stable are marked experimental ('exper').

    Port 	CPU 	Machines 	Latest Release
    acorn26 	arm 	Acorn Archimedes, A-series and R-series systems 	3.0 	stable
    acorn32 	arm 	Acorn RiscPC/A7000/NC and compatibles 	3.0 	stable
    algor 	mips 	Algorithmics MIPS evaluation boards 	3.0 	stable
    alpha 	alpha 	Digital Alpha (64-bit) 	3.0 	stable
    amd64 	x86_64 	Advanced Micro Devices AMD64(tm) 64-bit CPUs 	3.0 	stable
    amiga 	m68k 	Commodore Amiga, MacroSystem DraCo 	3.0 	stable
    amigappc 	powerpc 	PowerPC-based Amiga boards 	none 	exper
    arc 	mips 	Machines following the Advanced RISC Computing spec 	3.0 	stable
    atari 	m68k 	Atari TT030, Falcon, Hades 	3.0 	stable
    bebox 	powerpc 	Be Inc's BeBox 	snap 	exper
    cats 	arm 	Chalice Technology's Strong Arm evaluation board 	3.0 	stable
    cesfic 	m68k 	CES's FIC8234 VME processor board 	3.0 	stable
    cobalt 	mips 	Cobalt Networks' Microservers 	3.0 	stable
    dreamcast 	sh3 	Sega Dreamcast game console 	3.0 	stable
    evbarm 	arm 	ARM evaluation boards 	3.0 	stable
    ews4800mips 	mips 	NEC's MIPS based EWS4800 workstations 	snap 	exper
    evbmips 	mips 	MIPS-based evaluation boards 	3.0 	stable
    evbppc 	powerpc 	PowerPC-based evaluation boards 	3.0 	stable
    evbsh3 	sh3 	Evaluation boards with Hitachi Super-H SH3 and SH4 CPUs 	3.0 	stable
    evbsh5 	sh5 	Evaluation boards with SuperH SH5 32/64-bit CPU 	3.0 	stable
    hp300 	m68k 	Hewlett-Packard 9000/300 and 400 series 	3.0 	stable
    hp700 	hppa 	Hewlett-Packard 9000/700 series 	snap 	exper
    hpcarm 	arm 	StrongARM based Windows CE PDA machines 	3.0 	stable
    hpcmips 	mips 	MIPS based Windows CE PDA machines 	3.0 	stable
    hpcsh 	sh3 	Hitachi SH3 and SH4 based Windows CE PDA machines 	3.0 	stable
    i386 	i386 	i386 family IBM PCs and clones 	3.0 	stable
    ia64 	itanium 	Itanium family of processors 	none 	exper
    ibmnws 	powerpc 	IBM Network Station Series 1000 	3.0 	stable
    iyonix 	arm 	Iyonix ARM pc 	none 	exper
    luna68k 	m68k 	OMRON Tateisi Electric's LUNA series 	3.0 	stable
    mac68k 	m68k 	Apple Macintosh 	3.0 	stable
    macppc 	powerpc 	Apple Power Macintosh and clones 	3.0 	stable
    mipsco 	mips 	Mips family of workstations and servers 	3.0 	stable
    mmeye 	sh3 	Brains' mmEye Multi Media Server 	3.0 	stable
    mvme68k 	m68k 	Motorola MVME 68k SBCs 	3.0 	stable
    mvmeppc 	powerpc 	Motorola MVME PowerPC SBCs 	3.0 	stable
    netwinder 	arm 	StrongARM based NetWinder machines 	3.0 	stable
    news68k 	m68k 	Sony's m68k based "NET WORK STATION" series 	3.0 	stable
    newsmips 	mips 	Sony's MIPS based "NET WORK STATION" series 	3.0 	stable
    next68k 	m68k 	NeXT 68k 'black' hardware 	3.0 	stable
    ofppc 	powerpc 	Generic OpenFirmware compliant PowerPC machines 	3.0 	stable
    pc532 	ns32k 	PC532 	1.5 	stable
    playstation2 	mips 	SONY PlayStation 2 	snap 	exper
    pmax 	mips 	Digital MIPS-based DECstations and DECsystems 	3.0 	stable
    pmppc 	powerpc 	Artesyn's PM/PPC board 	3.0 	stable
    prep 	powerpc 	PReP (PowerPC Reference Platform) and CHRP machines 	3.0 	stable
    sandpoint 	powerpc 	Motorola Sandpoint reference platform 	3.0 	stable
    sbmips 	mips 	Broadcom SiByte evaluation boards 	3.0 	stable
    sgimips 	mips 	Silicon Graphics' MIPS-based workstations 	3.0 	stable
    shark 	arm 	Digital DNARD ("shark") 	3.0 	stable
    sparc 	sparc 	Sun SPARC (32-bit) 	3.0 	stable
    sparc64 	sparc 	Sun UltraSPARC (64-bit) 	3.0 	stable
    sun2 	m68k 	Sun 2 	3.0 	stable
    sun3 	m68k 	Sun 3 and 3x 	3.0 	stable
    vax 	vax 	Digital VAX 	3.0 	stable
    walnut 	powerpc 	IBM 405GP PowerPC "walnut" evaluation board 	3.0 	stable
    x68k 	m68k 	Sharp X680x0 series 	3.0 	stable
    xen 	i386 	Xen Virtual Machine Monitor 	none 	exper

So what exactly are you trying to tell us?
Nobody said NetBSD was already ported to all platforms, just that it was ported to an incredible amount of platforms.

P.S.: And you still didn't provide any proof for your claim

---

### Post by ComplexNumber on 2006-04-09
**awakatanka**
it means that BSD may need to be slightly rewritten so is not readily portable. the fact that netBSD has been rewritten for so many different architectures is neither here nor there and is not the point (and the point that helpme keeps on missing). linux just needs recompilation.

---

### Post by helpme on 2006-04-09
[QUOTE=ComplexNumber]**awakatanka**
it means that BSD may need to be slightly rewritten so is not readily portable. the fact that netBSD has been rewritten for so many different architectures is neither here nor there and is not the point (and the point that helpme keeps on missing). linux just needs recompilation.[/QUOTE]
This has got to be the dumbest, most uninformed, but still one of the funniest posts I ever read.

Sorry to be so blunt, but if you really think that you'd just need to recompile Linux to get it to run on a new platform, you are so incredibly uninformed it defies believe.

Just take a look how long it took to get the ppc stuff into the main kernel. This might give you an idea.

---

### Post by ComplexNumber on 2006-04-09
**helpme**
surely, you're not for real :rolleyes:

---

### Post by helpme on 2006-04-09
[Linux porting guide]("http://www.embedded.com/story/OEG20010221S0092")

[http://www.linux.org/projects/ports.html](http://www.linux.org/projects/ports.html)

---

### Post by awakatanka on 2006-04-09
[QUOTE=ComplexNumber]**awakatanka**
it means that BSD may need to be slightly rewritten so is not readily portable. the fact that netBSD has been rewritten for so many different architectures is neither here nor there and is not the point (and the point that helpme keeps on missing). linux just needs recompilation.[/QUOTE]So all different CPU specific calls are already in the kernel? Our does a new CPU needs new code in the kernel? Ifso then it's the same as slighty rewrite.

I'm not a coder so i realy don't know.

---

### Post by helpme on 2006-04-09
[QUOTE=awakatanka]So all different CPU specific calls are already in the kernel? Our does a new CPU needs new code in the kernel? Ifso then it's the same as slighty rewrite.

I'm not a coder so i realy don't know.[/QUOTE]
Take a look at the porting guide I linked to.
This should give you an idea about what is involved in porting Linux and shows that thinking that you merely have to recompile Linux to port it is simply hilarious.

---

### Post by baldy1324 on 2006-10-07
linux distros are based off of the linux kernel. freebsd, netbsd, and openbsd don't have the same kerenels. linux is a kernel b/c to get an os you have to get a distro (debian,ubuntu... that includes software. freebsd netbsd and openbsd are operating systems-freebsd has 1 set of software, 1 kernel, 1 set of documentation... don't like any of them.

---

### Post by Artemis3 on 2006-10-20
I have used FreeBSD and OpenBSD for some years and i can quickly recommend it for servers. For desktop it depends, you have to make sure all your hardware is supported, or prepare to solve things by hand with patience.

Basically NetBSD emphasizes portability, OpenBSD security, and FreeBSD speed. Other variants are trying to appeal Desktop users, or address SMP needs, etc.

For example, OpenBSD makes for an excellent router/firewall for your home lan in that old p100 or 486 you may have lying around; FreeBSD can be that big web and database server in your company, and NetBSD could run your pda.

The BSD license is also free software as defined by the FSF. The main difference is that authors using BSD license don't care if someone takes their work to use it in a propietary application and distribute a derived work from it. Thats why you can see their code bundled in Microsoft and Apple products.


The package system is not a mess. You have 2 methods for installing things: The "package system" means binary packages, pretty much like .debs and apt; and the "ports system" meaning source packages; which inspired the likes of Gentoo. Both will resolve dependencies and at the end look as installed package, but using ports means it downloads source code, compile (with posible user changes/speed or debug flags, etc) and then install.

FreeBSD (for example) is an entire distribution (not just a kernel), and a comitee gets to dictate policy such as where files should go (ie compiled stuff in usr/local and distro stuff in /usr) they make excellent documentation and maintain man pages updated.


I don't see any problems with the file system (UFS/UFS2). With softupdates enabled (by default in most installs) its pretty fast and safe.


You can take a look to the various livecds or try installing to an old machine and decide for yourself. I do believe it has already a place in the server though :)

---

### Post by xCM329 on 2006-10-21
Alright, now it is time to clear this whole argument up and input some real information...

First of all, Linux and *BSD's are completely different operating systems.  They have different goals and different outlooks on development, but they both are connected somehow to unix.  BSD was made as the Berkley Software Distro forking off of Unix System V Time Sharing.  However, Linux was based off the MANN files of unix to try to make a "free unix system."  In the early '90's, BSD was forked into two categories, BSD 4.4 (based on the original Bell Labs Unix code) and BSD 4.4Lite (removal of the 1% unix code).  From BSD4.4Lite came 386BSD (implementation of BSD on the i386 architecture), and then FreeBSD and NetBSD were two *SEPARATE*forks of 386BSD.  FreeBSD's focus was on performance and stability while NetBSD's focus was on portability.

To clarify on the subject of portability for a moment: NetBSD's code is not as portable as Linux's code, but it only requires a bit of change in the minute amount of assembly for it to be ported.

From NetBSD, OpenBSD branched striving to be the most secure of the BSD families.  Also (which is not well known), DragonflyBSD forked from FreeBSD, but is not a major concern in our discussion, and will further be omitted.  Most recently, NetBSD has been discontinued due to poor leadership, and OpenBSD's development has been weak and minimal.  FreeBSD remains the leader of the pack in concern of the BSD (non-UNIX) family.  In recent years, there have been two major attempts to create a desktop system based on the FreeBSD operating system: DesktopBSD and PC-BSD.  DesktopBSD has been known for faulty coding, and is supposedly just changes in the configuration files of FreeBSD and some added graphical features.  PC-BSD is a fully graphical FreeBSD based system that adds its own Windows-like installer and graphical configuration tools.  PC-BSD's only flaw is its copying of libraries during installation through its PBI system, leading to some small bugs if the libraries are corrupt.

Now, to the subject of the comparison of Linux to BSD...

Linux is a chaotic system (to put it lightly).  It's goal was to make a free, open source kernel that could use other tools to make a complete operating system.  There is no such thing as the GNU/Linux operating system.  LINUX is the kernel, the meat of the operating system while GNU provides tools to make linux usable.

Linux distros come out with drivers quicker than they should, providing flaws in code.  Developers praise BSD's for their organization, but that is also a flaw with BSD: it is slower than Linux in its growth.  Both are fine systems, but BSD can do everything linux can and more.  FreeBSD runs 90% of linux binaries, and other POSIX compliant system binaries.  It has more stability and the drivers are near flawless.  Will write more, but I have to go...

---

### Post by st00ner on 2006-10-31
I couldnt agree more. I have used DesktopBSD, PC-BSD, and finally i settled for just FreeBSD(when i was familiar enough with the unix like system). FreeBSD is easy to install. It might scare some away because of the small amounts of configuration you need to do. if you ask me, it gives you the perfect amount of flexibility. FreeBSD is more flexible than say ubuntu, but less software is ported to it. FreeBSD is also more stable, as code is not just rushed in resulting to bad drivers. FreeBSD does it right, or dosnt do it at all.if you have older hardware, i would suggest FreeBSD. Newer hardware, i would suggest a Debian GNU/Linux distro or gentoo. Also, OpenBSD and FreeBSD work together on security, OpenBSD mainly has more things disabled by default. I got stack smash protection in my FreeBSD kernel along with heap gaps which were originally for OpenBSD. I got all my hardware working after a while (it wasnt easy lol). When someone updates the linux compatibility layer to 2.6, i will go back to FreeBSD. but until then, i will use ubuntu.

---

### Post by Chayak on 2006-11-01
I see FreeBSD as more of a performance BSD and I've used and seen it used with good result on many servers.

OpenBSD I like for the pf it makes an excellent firewall system or anything that you need to be reasonably secure

PCBSD is a more userfriendly FreeBSD I don't have a lot of experience with it but in the time I've spent playing around it actually makes a nice desktop BSD.

Linux is controlled chaos ;) it advances rapidly in comparison to other OSs and that is both a fault and advantage depending on how you look at it. It's an exciting place to be and I think Ubuntu had the right idea going with a LTS varient to help soothe the commercial side of things.  They would be scared by six month release cycles.

---

### Post by SunnyRabbiera on 2006-11-01
Linux and BSD are arguemental cousins, both sharing the same family line but have different approaches.
I actually dont get the hate between the two, both have thier flaws and merits and both have a common enemy: Microsoft.
Both are pretty good though in some ways I find BSD lacking in some areas but it has the same potential that linux does.

---

### Post by raqball on 2006-11-01
> **SunnyRabbiera said:**
> Linux and BSD are arguemental cousins, both sharing the same family line but have different approaches.
I actually dont get the hate between the two, both have thier flaws and merits and both have a common enemy: Microsoft.
Both are pretty good though in some ways I find BSD lacking in some areas but it has the same potential that linux does.

I think the hate amongst linux and bsd is from the bsd side. They (bsd) all think Linux is inferior and that they are computer gods! Take a look at a few BSD forums and you shall see what I mean... They are very unhelpful and are pretty much stuck on themself.. My .o2 worth :)

---

### Post by raqball on 2006-11-01
Double post.. Sorry :)

---

### Post by SunnyRabbiera on 2006-11-01
Well the BSD'ers need to be co operative, they say they know the flaws in linux and they could help the project.
Both are respectable OS's and very reliable, BSD is wonderful on the servers I have at work.

---

### Post by ebozzz on 2006-11-12
> **KingBahamut said:**
> While not making it nessecarily better than Linux as a whole, BSD and its variants have a certain place in the hearts of many. I find it hard to differentiate the differences between the two.

A FreeBSD user that I have been in communication with described the difference with the following quote.....

> Unlike linux, every BSD in itself is a complete OS, not just a userland on top of a kernel.

---

### Post by jan on 2006-11-29
The question is - will BSD survive??? ;) after Linux...

---

### Post by ebozzz on 2006-11-29
> **jan said:**
> The question is - will BSD survive??? ;) after Linux...

I am pretty sure that FreeBSD will.

---

### Post by Tobster on 2006-12-05
The Apple OS is based on a version of BSD

---

### Post by mips on 2006-12-07
> **SunnyRabbiera said:**
> 
I actually dont get the hate between the two, both have thier flaws and merits and both have a common enemy: Microsoft.


Linux considers MS an enemy and want to dispose it. BSD just want to build a good OS.

---

