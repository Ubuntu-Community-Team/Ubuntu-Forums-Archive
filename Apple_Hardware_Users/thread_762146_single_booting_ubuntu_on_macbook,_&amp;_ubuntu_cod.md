---
title: "single booting ubuntu on macbook, &amp; ubuntu code?"
date: 2008-04-21
forum: Apple Hardware Users
---

### Post by turcott on 2008-04-21
Hi , I have a few questions, and hoping I can get the answers from some of the other members here in the forum.


a)	I recently ended up purchasing a macbook with the intel core 2 duo cpu, 1gb of ram, it came formatted with no OSX disc,  Anyways I installed ubuntu 7.10, but everytime it boots up I get a white screen for about 30 sec before ubuntu loads, how do I prevent this from happening?

b)	 Should I install the amd64bit version of ubuntu since i'm running a core 2 duo which is also a 64bit cpu or stick with the x86 32bit version?

c)	If open source means the source code is available to alter or change, is that the same as kernel compiling…would compiling a kenral be making use of the source code?  Not sure how that really works, maybe examples of how the source code would be used would help me understand better?

d)      I thought the instructions to tell the cpu what to do were more efficient in a mac but maybe that was when they used the IBM cpu's...i would assume with mine having an Intel core 2 duo that really my mac is like a namebrand laptop such as HP, Compaq, with the use of Intel cpu's I can't see how Mac has any type of advantage, and if anything a disadvantage cause now Mac owners have to buy Mac/Apple parts, where as with a PC you usually have more oem or aftermarket hardware or accessories to purchase.  So far i'm really enjoying my Mac, i just would like some feedback to help me understand a few things, thanks in advanc!

---

### Post by plasmatonic on 2008-04-21
a) That is normal, since Intel Macs use EFI motherboard, a BIOS compatibility must load and find a suitable boot device. The only way around is to natively boot EFI.

b) That is a personal choice, with 1GB of ram, you will see no real world performance increase, but possibly a loss.

c) Compiling any code requires just that... the source code. So yes, compiling the kernel is making use of open source code. An example of editing code could mean a variety of things, like modifying the kernel source to fix an issue with ALSA (sound) on your particular hardware.

d) The transition to intel hardware means that Apple products allow total choice for what you run on your computer... may it be Windows, OS X, Solaris, or *nix. In terms of advantages vs other manufacturers, Apple makes some of the sleekest looking, best performance manufactured computers available... the "apple tax" is a thing of the past in most cases. Sure, as a product line is getting close to upgrade, its price vs performance ratio may not be that of competitors, but its still a pretty economical option. Look at the mac pro... just try to build your own for that cost ;P

---

### Post by cyberdork33 on 2008-04-21
> **turcott said:**
> Should I install the amd64bit version of ubuntu since i'm running a core 2 duo which is also a 64bit cpu or stick with the x86 32bit version?
See this post. There are advantages and disadvantages.
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

> **turcott said:**
> If open source means the source code is available to alter or change, is that the same as kernel compiling&#8230;would compiling a kenral be making use of the source code?  Not sure how that really works, maybe examples of how the source code would be used would help me understand better?Compiling is the process of taking a source code and making an executable binary from it. The base Linux kernel (AKA 'vanilla') source code can be found at [http://kernel.org/](http://kernel.org/). You can view the source of the kernel and make changes if needed and submit the changes to be included in the kernel. The same goes for pretty much all software in Ubuntu. Example: As new Macs come out, there are often issues with the newer hardware not working properly. One of these things recently has been keyboards. In order to add support for these newwer keyboards, someone had to alter the source code for the kernel, and then posted patches to the Ubuntu kernel so that the normal Ubuntu kernel could benefit from the new hardware support.

> **turcott said:**
> I thought the instructions to tell the cpu what to do were more efficient in a mac but maybe that was when they used the IBM cpu's...i would assume with mine having an Intel core 2 duo that really my mac is like a namebrand laptop such as HP, Compaq, with the use of Intel cpu's I can't see how Mac has any type of advantage, and if anything a disadvantage cause now Mac owners have to buy Mac/Apple parts, where as with a PC you usually have more oem or aftermarket hardware or accessories to purchase.  So far i'm really enjoying my Mac, i just would like some feedback to help me understand a few things, thanks in advanc!Well, you are stating a lot of things that many would debate, but the bottom line is that Macs were always just another computer, they just had some unique hardware that most 'PCs' didn't use (such as the use of the IBM PPC). Macs have always been a unique breed of computer and that will probably not change. That is what makes them attractive to people to a certain degree.

---

### Post by 3rdalbum on 2008-04-21
a. No idea.

b. If you've got more than 3 gigabytes of RAM that you desperately need to use, then install the 64-bit edition. Otherwise, stick with the 32-bit edition. Ubuntu tends to use less RAM than Mac OS X, so you can have a speedy computer with 1 gig of RAM.

c. If you recompiled the kernel, then yes that is a use of the source code. But it's easier and more useful to study and modify applications on the system. Ubuntu has the ability to retrieve the source code for all software available in the main and universe repositories, so you can take a look at what makes up your favourite program (or a system service). If you make modifications to fix bugs or add new features, and then submit those back to the main developer, that is a very powerful element of open source.

Some people also take the source code of one project, and incorporate it into a completely new project. This is called "forking". 

d. True, the PowerPC processors were more efficient than the x86  processors, but now essentially your Mac is just like a brand-name PC.

---

### Post by turcott on 2008-04-22
wow, i would not know where to begin on fixing a hardware issue using the source code of ubuntu.  

So the kernal is what, the programming language being used?  too many things to remember, program language, source code, kernel, shell, then knowing the commands so you can add or change the OS, or application, that's lots to remember, lol.

---

### Post by cyberdork33 on 2008-04-22
the kernel is the base software layer. It determines how the software can interact with hardware. 
[http://en.wikipedia.org/wiki/Computer_kernel](http://en.wikipedia.org/wiki/Computer_kernel)
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

The code language you use can be whatever you want as long as it can be compiled to a binary.

---

### Post by oskarloko on 2008-04-22
I'm wondering how the hell you got a MacBook without OsX... 

Well, you can compile the kernel, and this is My2Cents:
[LIST]
[*]Benefit: The computer will be more efficent and quick
[*]Loose: you have to maintain the compiled kernel and avoid official upgardes.
[*]Benefit: Some hardware options will work
[*]Loose: You can have some hardware behave strage
[*]Benefit: You'll be pride of your build kernel - as an artesanal work.
[*]Loose: You can be desesperate when something doesn't work
[/LIST]

The kernel is the central component of Ubuntu, it's a complex but fine piece of software. 
As I see, if its the first time you deal with Ubuntu just explore the system/applications and see if it fit your needs and you're comfortable with it. 

Then you can try to compile the kernel, play with system daemons, etc.

Ah, for the 32/64 bits question: as above, 32 bits is widely used and you'll find a lot of software without problem ( Flash Player, Skype )
64 bits is more powerfull, but not all software -specially non-free one is ported ( Flash Player, Skype ) and you can run it but it will be harder to you.

You can make 2 ( or three ) partitions: one with a stable Ubuntu system and other with a beta-test one, just to try 64 bits/ kernel/ Gentoo / etc.

Good luck!

---

### Post by turcott on 2008-04-22
i ended up picking it up at the pawn shop (all legit and stuff), which is why the price was lowered on it.  I didn't care anyways, cause i could always borrow a copy of os 10.5 from one of the many studends at the university and dorms.  I wanted to use ubuntu instead, so unfortunately i never had osx on there to use the bootcamp option, ect.  Ubuntu interests me cause i would like to learn how to use the source code and alter it, but all the remembering you have to do with understanding how to type the commands and knowing what they'll do, as well as other languages seems a like a crap load of stuff to take it!  i'm understanding what's been posted so far, not lost in la,la, land yet, anyways anymore info random or relevent would be weclomed.


So using the ubuntu terminal and typing in commands would be the same as going into Win XP and using cmd or command prompt?  From what i'm understanding, you need to download the kernal and basically type or add new code in whatever language like C, C++ ect, then somehow save it as a binary file, then save or attatch it to the kernel?  Would you use the terminal in the ubuntu OS to do all this?

---

### Post by khalil123 on 2011-10-12
[SIZE=2][FONT=Arial]Earn Extra money from your home by doing ad posting jobs with Virtual online Jobs. 101% guarantee of income of your work. Earn per ad post you did.     For More info and advertise your website visit: [COLOR=#0000ff]_[http://adf.ly/2yWrC](http://adf.ly/2yWrC)_[/COLOR][/FONT][/SIZE]

---

