---
title: "Several questions about linux"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by idontknow9999 on 2006-04-23
I have never used unix/linux ever. I downloaded the ubuntu 5.10 64 bit live and it looks good. I have been thinking of making a partition for it in 1 week. I got a couple questions:

note: Comp specs are at bottom.

1. Is getting the ubuntu 64 bit a good idea? Should I get the 32 bit? Speed wise and compatibility wise. Also, will I notice a speed difference?

2. I program in Visual Basic. I was told I could use a program called <wine> to continue using it. What exactly does wine do? Will I lose performance in doing this? Also, what are linux natural coding languages in? Can I code in any language (as long as there is a compiler for it?)

3. I have been thinking of getting the opterton 165 1.8GHZ (and OCing to 2.4-2.6GH). How is the support on ubunto (ex: can I give a core to a specific ap) and how is the software support for dual cores on ubuntu? Is it better then win xp pro?

4. As I said, I am new to linux. Will I need to read anything before I install it?

My computer specs:
_MotherBoard:_ DFI LANPARTY UT nF4 Ultra-D (BIOS: 2005/06/23, on board's optimal settings)
_Ram:_ OCZ EL PC3200 400MHZ DDR 1024MB Dual Channel
_CPU:_ AMD Athlon 64 3200+ Processor S939 WINCHESTER 2.0GHZ 512K L2 Cache 90NM
_Video Card:_ XFX GEFORCE 6600 GT PCI-E (Video Bios: 5.43.02.23.04, forceware version: 81.98)

---

### Post by catlett on 2006-04-23
I don't have specific answers but you have the live cd use it. Although it won't be a perfect example of Ubuntu installed on your computer it will be a good barometer for how Ubuntu will interact with your system.
If the live cd sets up and runs well then the install should set up well. If the live cd has problems configuring and running then chances are the install will have trouble as well.
I don't know much about wine except that it is a type of "emulator". I don't even know if that is the right word but it "emulates" a windows environment so you can run window's programs.I haven't heard many great things about it. There is a commercial product Crossover that allows window's proograms on Linux, I believe.
Your best bet may be VMware player. This allows you to run multiple OSs on virtual desktops. VMware can run on windows and linux. I know linux virtual machines run well in windows but I don't know about the reverse.

---

### Post by ComplexNumber on 2006-04-23
> 2. I program in Visual Basic. I was told I could use a program called <wine> to continue using it. What exactly does wine do? Will I lose performance in doing this? Also, what are linux natural coding languages in? Can I code in any language (as long as there is a compiler for it?)
you can also use mono that has a vb.net compiler.
linux is written in C, so you will find most programs written for linux ton be in C/C++. there are also many python, C#, java, and perl programs. if you want to program in it on linux, there is a compiler/interpreter available.

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=idontknow9999]I have never used unix/linux ever. I downloaded the ubuntu 5.10 64 bit live and it looks good. I have been thinking of making a partition for it in 1 week. I got a couple questions:

note: Comp specs are at bottom.

1. Is getting the ubuntu 64 bit a good idea? Should I get the 32 bit? Speed wise and compatibility wise. Also, will I notice a speed difference?

A: Well, not really. 64 bit ubuntu doesn't have many applications and it is much harder to get mp3 and other audio/video codecs working while with 32 bit you can just use automatix and it installs them for you. If you are new to Linux and want to save yourself some headaches, use 32 bit.

2. I program in Visual Basic. I was told I could use a program called <wine> to continue using it. What exactly does wine do? Will I lose performance in doing this? Also, what are linux natural coding languages in? Can I code in any language (as long as there is a compiler for it?)

A: Wine runs windows applications. I believe it has support for VBS and tests show that wine actually runs applications better then windows.

3. I have been thinking of getting the opterton 165 1.8GHZ (and OCing to 2.4-2.6GH). How is the support on ubunto (ex: can I give a core to a specific ap) and how is the software support for dual cores on ubuntu? Is it better then win xp pro?

A: It is ok. There is a kernel in the repositories for it to make it work.

4. As I said, I am new to linux. Will I need to read anything before I install it?


My computer specs:
_MotherBoard:_ DFI LANPARTY UT nF4 Ultra-D (BIOS: 2005/06/23, on board's optimal settings)
_Ram:_ OCZ EL PC3200 400MHZ DDR 1024MB Dual Channel
_CPU:_ AMD Athlon 64 3200+ Processor S939 WINCHESTER 2.0GHZ 512K L2 Cache 90NM
_Video Card:_ XFX GEFORCE 6600 GT PCI-E (Video Bios: 5.43.02.23.04, forceware version: 81.98)[/QUOTE]
Hope that helps. :)

---

### Post by uzi09 on 2006-04-23
[QUOTE=catlett]I don't have specific answers but you have the live cd use it. Although it won't be a perfect example of Ubuntu installed on your computer it will be a good barometer for how Ubuntu will interact with your system.
If the live cd sets up and runs well then the install should set up well. If the live cd has problems configuring and running then chances are the install will have trouble as well.
I don't know much about wine except that it is a type of "emulator". I don't even know if that is the right word but it "emulates" a windows environment so you can run window's programs.I haven't heard many great things about it. There is a commercial product Crossover that allows window's proograms on Linux, I believe.
Your best bet may be VMware player. This allows you to run multiple OSs on virtual desktops. VMware can run on windows and linux. I know linux virtual machines run well in windows but I don't know about the reverse.[/QUOTE]


i agree with the live-cd suggestion. i did that on my new comp and saved me a ton of hassle cuz it actually didn't work for various reasons.

anyway- as far as WINE goes, wine is actually not an 'emulator' -- no kidding, it actually stands for Wine Is Not an Emulator ;D. u can learn more about how it works on their site at [www.winehq.com](www.winehq.com)
I've used it to try to run games. I've read a bit about it as well. There seems to be quite a bit of support on it, but every time i ran it - i was never able to get it to work right (then again, i wasn't doing what u're planning on doing) and ended up giving up.

there is also a program called Cedega. It's a commercial program, but from what i've read, it seems to work far better. if it were me, i'd probably find a compiler like mono that ComplexNumber mentioned.

otherwise most programming i've seen done on Linux is either C/C++ or python (along with others, but these seem to be the main 2).

good luck
uzi

---

### Post by nalmeth on 2006-04-23
I run the 32-bit kernel on my EM64T intel processor, just because the 64-bit has less apps readily available for it (same deal in windows). You can work around this by creating a 32-bit environment inside your 64-bit. It's easy to do (follow a howto, copy/pasting commands), and works quite seamlessly, but being new to linux, you might just save the hassle and use the 32-bit. Pick up automatix, and you'll be all set. (automatix does not support 64-bit yet)
I didn't notice much speed difference in either direction.
I don't know anything about your visual basic. There might be an equivalent app available, this should be used ahead of wine.
Wine is a windows compatibility layer for linux, and is very impressive, but doesn't always give perfect results. Some apps can run faster than in windows, some much slower, and some not at all.
As far as I understand, the linux kernel can support dual-cores very well, but I can't give you many/any details about how it works.
You don't HAVE to read anything to get going, but it always helps.
Check out the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page"), and wiki.ubuntu.
There is excellent documentation for Ubuntu, and it's getting better. There are great howto's in the forums here too. Use the search function and you'll find a lot of great info.

---

### Post by Sef on 2006-04-23
> 4. As I said, I am new to linux. Will I need to read anything before I install it?

Read Herman's excellent tutorial on dual booting.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by idontknow9999 on 2006-04-23
catlett: I already tried the live cd. It why I said I am interested in this OS. Also, I want a partition, so virtual desktop kind of defeat the point.

ComplexNumber: I never coded in vb.net. 

MasterChief1234: 1. Ok, good, ill go for the 32 bit. 2. Interesting. 

uzi09: Yeah the person who is talking to me about linux talked about wine and cedega. Apparently it can play the games I want it to play.

nalmeth: Interesting.

Sef: tnx for the link.

---

### Post by ComplexNumber on 2006-04-23
>  ComplexNumber: I never coded in vb.net. if you've coded in VB 6, then you can benefit from knowing that its more difficult than vb.net. vb.net is vb 6 with all the crap taken out.

---

### Post by arundel on 2006-04-23
Thanks for the tutorial link Sef

---

