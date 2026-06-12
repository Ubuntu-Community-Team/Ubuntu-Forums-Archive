---
title: "Virtual kernel: the new generation of kernels"
date: 2011-11-12
forum: Any Other OS
---

### Post by Geri_lgfx on 2011-11-12
ohai

i have invented a new kernel conception, and i would like to hear some feedbacks about it. i will insert this to communities, please tell me, what is your oppinion on this.

Read it in my blog: [http://osdevel.blogspot.com/2011/11/just-decided-today-to-create-virtual.html](http://osdevel.blogspot.com/2011/11/just-decided-today-to-create-virtual.html)

Copypasted from my blog:

I just wake up today, and i decided to create an operating system. How to do? How to start it? Should i just create a new gui and file manager for linux, or should i create a distribution? Or should i do everything?

I always wanted to try creating an operating system wich is only mine, but this would be nearly impossible, due to the complexity of the x86 hardwares. Should i do it to other platforms?

Many many questions. Until i just realized, what i want to do:

-Platforms. Who <snip> cares them? X86 is not a business any more for tiny hw-related corporations and persons, becouse its overcomplicated, and nearly impossible to develop the hardware and the software, the operating systems are overcomplicated too.

Conclusion: if i try to create some operating system releated thing, it should not depend on any platform at all. Okay. But how to create an operating system, wich is not related to platforms? I have found it out.

The solution is a crossplatform guest operating system, wich can still run the softwares on the host computer. So i have actually started to program a high-level virtual kernel.

I lurking in #minix since a month ago, so i decided to put up as a topic (they are a howtocreateanoperating system movement after all).

[15:06:19] <Tenkawa> whats new all?
[15:17:18] <Geri_lgfx> i started to write an operating system. i typed the first 40 codeline of the kernel
[15:17:29] <Geri_lgfx> and its alreday mutch flawed than windows
[15:19:15] <Saturn|VU> poor joke ruined by poor English, well done

After all, a hello world.c example on minix starts like #include ../../KERNEL.h ... well, okay, but what <snip> is this? :D

I want this system proprietary. Maybee the minix kernel will be good as a host kernel however. Or even linux, becouse the conception does not need any gpl based code to be included in the virtual kernel.

Even if it will probably (99%) never done, and its just an experiment, it should be done with a clear conception. After all, nobody did things like this, so i would be crazy to release it under gpl. Maybee, using gpl-ed opearting system as a host is okay (linux).

Okay, so i just stated to type the code into the C editor, and after the 40 codelines - as i mentioned - my design was mutch more flawed than Windows. Basically, a simple fail in the memory management can dump my kernel back to the middle age. After writing the folowing 100 codeline, i just suddenly noticed that i gona hack the graphics with the kernel itself together. Basically, windows is being laughed for doing this. But after rethinking this, hacking the graphics together with the kernel is simply the BEST solution to create an operating system. Just think on it when the useless x11 falls apart in your linux, or something really cpu eater bug occurs. On windows, you can simply close it, under windows, well. And the another thing: the console windows. Nobody uses them since 10 years ago, but everybody hails them. Asshattery. Nobody cares about some retard 40 year old obsolote unix shits. Peoples are want to use they computer. So i decided to complitely leave out the console from the operating system.

Okay, so what <snip> is a virtual kernel? I have no idea, becouse i just invented it. Maybee there is some definition what desc. properly, what i am doing, who knows. So the thing of mine:

-Is a virtual operating system (kernel), runs in user mode, and asks for the host operating system for hardware handling.

-Its platform independent, can be booted from any host operating system, or can bundled in an own host operating system implementation (from example, a giant monolithic fugly a.out)

-Kernel (yes, the kernel) can execute basic and x86 assembly directly (just like in commodore64). So the final code (.bas) can be actually shared within multiple operating systems and platforms directly, just like back in the old days. Thankfully i not remember them.

-The design is somehow can be compared to windows95, where the kernel was hosted on dos, and some hardware functionality was did through dos.

-tcp, file handling, 3d, keyboard, mouse, io ports support

-The virtual kernel also can execute applicatins on the host operating system, becouse its an application after all.

-The virtual kernel also can can execute native code directly, hacking a context switcher to the clock interrupt is possible with this design, but i think i will leave this out, even its possible, just let this handled by the host operating system. (wich can be part of this design ofc).

-The kernel contains the handling of some popular things. The kernel can play .wav or ogg files, can load png files, and a lot of other format. Basically, the kernel is built around a multimedia engine.


-I have alreday done the context switcher for the x86.asm interpreter. Suprisingly, it can do around 10 million process switch per second.
How is this possible? Becouse my kernel is a virtual kernel, it does not need to switch beethwen real mode and protected mode. Switching to kernel mode only needed when something is touches a hardware, so when the virtual operating system calls the host operating system for some reason. So then an user->real mode fallback required. This needs the processor basically to be reseted. Back then with 286, this happended through the emergency shutdown function of the cpu, caused the cpu be complitelly reseted and flushed back by the motherboard. So you move your mouse cursor, or the timer causes an interrupt (600x per second) - your <snip> cpu turns off. Really impressive design, even if this is fixed with new instructions, its very LAME. So basically the kernel cycles with 600 hz. Ofc on bigger, if some even occur, or causes some IO rw/interrupt,etc. But my context switcher does not need this. I optimised a bit the code, so it takes only x*100 clock to switch the context. Witch i think is very impressive, becouse i basically can run my kernel somewhat around 10 mhz, with 1-200.000 simultanously running process, without getting my mouse lagged. And becouse the kernel hacked together with the graphics, even moving, resizing, touching the settings, the management of the operating system is fully available without amy glitches, even if they spinning the hard drive.

-SMP compatible design.

-Can run any command on the host OS.

-Fully booting within a 1-2 second, including graphics. Quitting within a 0.1 second.

-The block diagram of the os (quick paint draw ftw)

[IMG]http://4.bp.blogspot.com/-UQvienp-ITA/Tr2MNJD-LJI/AAAAAAAAAEg/NmtW1nkuzEw/s1600/virtualkernel.png[/IMG]

-So this virtual kernel suff is a virtual machine?
Somekind a platform independent virtual machine that actually acts like a kernel, contains the graphics interface/ctx switcher/pcb, and handles the system through the kernel.
For example:

Linux kernel -> GERI virtual kernel -> programs

or


FreeDOS kernel -> GERI virtual kernel -> programs

or

GERI kernel -> GERI virtual kernel -> programs


or

YOUR kernel -> GERI virtual kernel -> programs


-So is this conception like flash/dotnet/etc?
Not really, this is an operating system, making the interaction with the user, the user programs, and the hardware. This conception actually splits the kernel to two part: the (traditional) kernel, and the virtual kernel.

-Why tihs is good?
No fuckin idea Becouse the virtual kernel is platform independent, does not depend on the hardware characteristics.

-What is the speed of this?
Not yet measured. But its fast enough i hope.

-Why is this conception has sense?

Currently, the IT world works around this conception:

unreproducable 100million transistor CPUs, working with an operating system with uncountable amout of source code, with 200 million transistor GPUs and uncountable amout of hardwares wich are compatible with nothing until you get a software that implement the operating system's api, programs with hard work to even get a window appear on the screen, angry programmers, unsatisfyed users...

this conception: Get ANY hardware, Get ANY popular kernel wich supported on your stuff, Get ANY virtual kernel (for example, mine ofc :D) with an operating system, and run generic BASIC or ASM or whatever programs.







             1: * skilled peoples doing brutal hardwares from over9000 money *   -> continues, but it can run on every hardware. Even on some random, cheap chinese one.

             2: skilled programmers doing brutal work to get them work in the popular operating systems -> not really, random chinese cheap stuff can come with a simple operating system with libraries (or special memory areas, IO) to access the sound, video, network, usb-rocket-troll-launcher, and a c compiler to compile a virtual operating system that supports the platform, and here you go, you just can forget the problem with the operating systems forever...

             3: native programs still stay accessible! Native programs are good! They are fast, etc...


-Except these things, what benefits can be get this conception used?
----------------------------------------------------------------------
- Full interop beethwen systems - on all, the same code can run.
- Applications: there is a lot basic and x86 asm applications, they can ported to this system easilly - or they alreday run at default. C/c++ applications also can compiled into asm, so basically every program can easilly ported. For example, your tetris.c: you compile a tetris.asm from it, and there you go, you can start it on every platform, where my virtual kernel is supported.
- The hardware abstraction goes through the BASIC interpreter. From x86 ASM, you can call directly BASIC commands to reach the hardware functionality.
- The virtual kernel does not affect/limit the original kernel - use the platform-specific-native programs, just like before.

**[COLOR=#FF0000]-This is just a conception, maybee i will code it, maybee not. Maybee it makes no sense, maybee its not even possible.[/COLOR]**


**EDIT:**
so here is the definition, what a Virtual Kernel is:

The operating system's kernel should split into 2 parts: a host kernel and a virtual kernel. The host kernel still can run processes, it conrtols the memory management, the swapping, the drivers, and runs the virtual kernel. The task of the virtual kernel is to create a unified platform, skip the hardware specificityes, create the graphics user interfaces. A virtual kernel should create a virtual platform that is easy to be programmed, the specialities of the modern computer systems should be embed into the programming language, in algorithmical levels. A virtual kernel should provide the environment to run a lot kind of programs written in several programming languages. The interpreter/recompiler of the virtual kernel should mask the platform-specific implementation of the common API-s, through implementing the effective parts of the common API's in the programming language itself, not distancing it from the programming language. The host kernel should have all modules and libraries to develop a native application, and native applications also should able to use every new possibility, the virtual kernel should have the ability to interpret the functionality to reach the modern abilities in the hardware, and run the applications while they using these abilities. The virtual kernel and the host kernel can be separate modules, created by different peoples, or it can arrive in the same blob. This principle simplifies the design of operating systems.

---

### Post by lightwarrior on 2011-11-12
What is the difference between using your virtual kernel and and the use of an interpreted programming language such as Java?

---

### Post by Geri_lgfx on 2011-11-12
not mutch, if you only think on the interpreting functionality. But in reality, the virtual kernel performs the folowing definition of an operating system:

-Running programs (yes)
-Making interaction with the user (yes)
-Contains the basic applications for an operating system (yes)
-Starts with the computer (yes)
-Makes direct interaction with the hardwares (no)
-Hides the hardware from the users (yes)
-Hides the hardware from the softwares (yes)
-Makes the user interfaces of an operating system (yes)

---

### Post by lightwarrior on 2011-11-12
I would be worried on the performance...
Layer of abstraction above another layer...
Perhaps current silicon power allows for this, though.

---

### Post by BillyBoa on 2011-11-12
Looks to me like a philosophical approach of the operating system problem.

In any case I suggest you to incorporate BIOS to the kernel, to absorb all the slowness caused by a separate procedure.

---

### Post by lightwarrior on 2011-11-12
Your host OS better be a glorified and much needed update of current BIOS approach, already burned into the motherboard.

---

### Post by Geri_lgfx on 2011-11-12
lightwarrior: yes, this affects performance, but there is still support for native applications

BillyBoa: yes, its a philosophical viewpoint, but i will probably code it, and i will see if it is usable or not

---

### Post by YeOK on 2011-11-13
Is this not just the same idea as Android and its Linux Kernel and [Dalvik]("http://en.wikipedia.org/wiki/Dalvik_(software)") VM ?

---

### Post by Geri_lgfx on 2011-11-13
[YeOK]("http://ubuntuforums.org/member.php?u=717852"): yes, very related.

---

### Post by lightwarrior on 2011-11-18
How's your project going?
I kept thinking it is a great excercise.

---

