---
title: "Can I run Arch Linux??"
date: 2011-05-08
forum: Any Other OS
---

### Post by ClientAlive on 2011-05-08
Sorry guys. I know this is Ubuntu forums but I can't get registered on Arch Linux forums. They ask you this ludicrous question at the bottom of the registration page that there's no way I can give the right answer.

So here's what I would have posted there if I could have gotten on the forum:


So, what's the bottom line? Can I run Arch Linux on my machine? If so, which release do I get? (Which architecture?). I'm pretty new to Linux and just don't understand all the technical mumbo jumbo yet. 

;)

Can somone please take a look at my system info and let me know?

By the way, sorry if the following info is overkill. I had to make a call and I'm just not sure. Thanks.

MODEL INFORMATION FROM DMIDECODE:

```
System Information
        Manufacturer: Hewlett-Packard
        Product Name: HP Pavilion ze2000 (PV336AV#ABA)  
        Version: Rev 1
        #
        #
        Wake-up Type: Power Switch

```


LSPCI INFO:

```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```


CPU INFO:

```

cpu family	: 15
model		: 36
model name	: AMD Turion(tm) 64 Mobile Technology ML-34
stepping	: 2
cpu MHz		: 800.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips	: 1595.27
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```


One last, little, teensie weensie little thing . . . if I might ask . . .

How about that bcm 4318 wireless card when it comes to Arch Linux? Same deal as any other distro? Do the whole b43fwcutter thing? Or ndls wrapper if that doesn't work?

Thanks a bunch.

---

### Post by Paqman on 2011-05-08
That's a pretty old machine, how much RAM does it have? Whether it will run Arch really depends on how you wanted to set it up. What will you be using the machine for?

---

### Post by ClientAlive on 2011-05-08
> **Paqman said:**
> That's a pretty old machine, how much RAM does it have? Whether it will run Arch really depends on how you wanted to set it up. What will you be using the machine for?


Oh. Well, just that I'm fairly new to Linux, got my hands on Oracle VM Virtual Box, and wanted to play around with a few different distros just to see what they're like. Arch was just one of the half a dozen or so I picked out to play with.

I have one gig of ram (or so I was sold). Free seems to show something less than that. Here's the current results of free. Got a lot resource hungry stuff going on on the machine right this min so I'm sure it will reflect that as well.


FOR "FREE"

```

~$ free
             total       used       free     shared    buffers     cached
Mem:        896060     745232     150828          0       6776     280936
-/+ buffers/cache:     457520     438540
Swap:      1648632     169616    1479016

```


FOR "FREE -M"

```

~$ free -m
             total       used       free     shared    buffers     cached
Mem:           875        784         90          0          1        336
-/+ buffers/cache:        446        428
Swap:         1609        165       1444

```


***Basically my real confusion lies with this business about the architecture of the CPU. I don't understand what i386, i486, i686 mean. More importantly I don't understand what mine is and how to compare or know what is compatible. That's the biggie for me.***

Thanks for the help.

---

### Post by wildmanne39 on 2011-05-08
Hi, you have an amd64 cpu chip so you can run the amd64 bit version of arch, but I use virtualbox also and it takes more resources because you will actually be running 2 operating systems at once, what ever you normally run and then the one in virtualbox. That computer problem will not run well using a virtual machine. For example whatever amount of memory you give to the system running inside virtualbox will be subtracted from the memory you have left to run the primary operating system. I hope this helps.

---

### Post by Perfect Storm on 2011-05-08
Moved to Other OS/Distro Talk.

---

### Post by wildmanne39 on 2011-05-09
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Talk.

Hi, looks like a nice distributionm do you also run ubuntu?

---

### Post by ClientAlive on 2011-05-09
> **wildmanne39 said:**
> Hi, looks like a nice distributionm do you also run ubuntu?


My host o/s is Ubuntu 10.04 LTS. Yes. Love it. This raises another thing I've been thinking about too but I don't want to hijack my own thread. lol.

Well, I'll mention it I guess - but I still hope to find an answer to my initial question. Don't really want to run 64 bit, so I need to figure out this i386, i486, i686 stuff.

My other thought though; was if I can run some really really lite Linux distro for my host and then just run everything else on top of that in Virtual Box. This seems like a good idea to me for a number of reasons. If I did that though then I would want the host o/s to be an extremely stripped down Linux without even any gui, and strip down the window manager and whatnot to just the bare minimum. Wouldn't know what to look for for that though.

But the i386, i486, i686 thing. That was the orig point of confusion for me.

Thanks guys.
:D

---

### Post by manzdagratiano on 2011-05-09
You should be easily able to run Arch as a dual boot with as much as Gnome or KDE; in a VM, of course, Blackbox/Fluxbox/Openbox will be faster.

I personally use Blackbox, but people seem to like Fluxbox more. If you follow the Arch Linux Beginner's Guide (first link on Googling), you **will** have Arch running in no time.

The qualifiers i386, i486, etc refer to the different avatars of the Pentium processor, and processors derived from it, and are not very relevant any more. The 32-bit architecture nowadays is called i686. Your AMD Turion processor would be considered 'i686'.

---

### Post by krapp on 2011-05-09
> **ClientAlive said:**
> Sorry guys. I know this is Ubuntu forums but I can't get registered on Arch Linux forums. They ask you this ludicrous question at the bottom of the registration page that there's no way I can give the right answer.

lol. Yeah I wtf'd too when I registered.

You have run the text (copy+paste) in your Terminal and paste the output. It's their way of keeping their forums 133t so to speak. They moderate their forums as if having forum users were an inconvenience. I'm no fan of their way of doing things.

---

### Post by ClientAlive on 2011-05-09
> **manzdagratiano said:**
> You should be easily able to run Arch as a dual boot with as much as Gnome or KDE; in a VM, of course, Blackbox/Fluxbox/Openbox will be faster.

I personally use Blackbox, but people seem to like Fluxbox more. If you follow the Arch Linux Beginner's Guide (first li
nk on Googling), you **will** have Arch running in no time.

The qualifiers 1386, i486, etc refer to the different avatars of the Pentium processor, and processors derived from it, and are not very relevant any more. The 32-bit architecture nowadays is called i686. Your AMD Turion processor would be considered 'i686'.


Bam! There it is!!  :D

Thanks bud!


> **krapp said:**
> lol. Yeah I wtf'd too when I registered.

You have run the text (copy+paste) in your Terminal and paste the output. It's their way of keeping their forums 133t so to speak. They moderate their forums as if having forum users were an inconvenience. I'm no fan of their way of doing things.


Yeah, after about half a dozen tries (and a few prayers that what I was putting in there wasn't gonna destroy my machine) I finally got it right and got an answer from the terminal. It was this long #$$ string of numbers and letters (I mean like 20 or 25 characters). Problem is, when I pasted that in the field at the forum it didn't like that answers - I was no closer.

Ahh well, you guys are much nicer I'm sure. Better that that happened anyway.

:D

---

### Post by wojox on 2011-05-09
Definitely i686. Here's a good post on installing Openbox [WiLL X TrEmE]("http://willensky.blogspot.com/")

---

### Post by manzdagratiano on 2011-05-09
> **ClientAlive said:**
> Bam! There it is!!  :D

Thanks bud!





Yeah, after about half a dozen tries (and a few prayers that what I was putting in there wasn't gonna destroy my machine) I finally got it right and got an answer from the terminal. It was this long #$$ string of numbers and letters (I mean like 20 or 25 characters). Problem is, when I pasted that in the field at the forum it didn't like that answers - I was no closer.

Ahh well, you guys are much nicer I'm sure. Better that that happened anyway.

:D

That question is just to ascertain if you are running Linux, possibly Arch (I think the output may be different in Ubuntu and Arch - I am in Ubuntu at the moment) - because of the 'uname' thrown in there - as you can check with 'uname -a' in a terminal. This is piped to sha256sum, which is like a signature generator for an expression, like md5sum does for a file - the idea is that different strings will generate very different signatures, and it is unlikely you will get the right signature starting from a wrong string. The 'sed' in the end is just to cut off unwanted dashes and spaces. Thus, this is actually an effective method to keep spammers away. If you run this command in your Arch VM, I think it would easily let you register.

EDIT: The output is indeed the same in Ubuntu and Arch - it is a signature of the string '19Linux'. You cannot get the right sha256sum starting from another string.

---

### Post by mips on 2011-05-09
> **ClientAlive said:**
> My host o/s is Ubuntu 10.04 LTS.

If you are running the 32-bit version you will only be able to run a 32-bit guest in a VM if I'm not mistaken.


> **manzdagratiano said:**
> Your AMD Turion processor would be considered 'i686'.

No, it would be be considered AMD64 as it's a 64-bit processor. So he can run either the i686 or AMD64 version, up to him.

[http://en.wikipedia.org/wiki/AMD_Turion#Lancaster_.2890_nm_SOI.29](http://en.wikipedia.org/wiki/AMD_Turion#Lancaster_.2890_nm_SOI.29)
> **Lancaster (90 nm SOI)**

Stepping E5
L1 cache: 64 + 64 KiB (data + instructions)
L2 cache: 512 or 1024 KiB, fullspeed
MMX, Enhanced 3DNow!, SSE, SSE2, SSE3, **[COLOR="Red"]AMD64[/COLOR]**, PowerNow!, NX Bit
Socket 754, HyperTransport (800 MHz, HT800)
VCore: 1.00 V - 1.45 V
Power consumption (TDP): 25/35 watt max
First release: March 10, 2005
Clock rate: 1600, 1800, 2000, 2200, 2400 MHz
25W TDP:
MT-28: 1600 MHz (512 KiB L2-Cache)
MT-30: 1600 MHz (1024 KiB L2-Cache)
MT-32: 1800 MHz (512 KiB L2-Cache)
MT-34: 1800 MHz (1024 KiB L2-Cache)
MT-37: 2000 MHz (1024 KiB L2-Cache)
MT-40: 2200 MHz (1024 KiB L2-Cache)
35W TDP:
ML-28: 1600 MHz (512 KiB L2-Cache)
ML-30: 1600 MHz (1024 KiB L2-Cache)
ML-32: 1800 MHz (512 KiB L2-Cache)
**ML-34: 1800 MHz (1024 KiB L2-Cache)**
ML-37: 2000 MHz (1024 KiB L2-Cache)
ML-40: 2200 MHz (1024 KiB L2-Cache)
ML-42: 2400 MHz (512 KiB L2-Cache)
ML-44: 2400 MHz (1024 KiB L2-Cache)


@ClientAlive

If budget allows I would slap another 1GB of RAM into that machine. RAM is cheap and makes a big improvement to your experience (with other distros & operating systems as well).

I would run the 64-bit version.

---

### Post by ClientAlive on 2011-05-09
> **mips said:**
> If you are running the 32-bit version you will only be able to run a 32-bit guest in a VM if I'm not mistaken.




No, it would be be considered AMD64 as it's a 64-bit processor. So he can run either the i686 or AMD64 version, up to him.

[http://en.wikipedia.org/wiki/AMD_Turion#Lancaster_.2890_nm_SOI.29](http://en.wikipedia.org/wiki/AMD_Turion#Lancaster_.2890_nm_SOI.29)



@ClientAlive

If budget allows I would slap another 1GB of RAM into that machine. RAM is cheap and makes a big improvement to your experience (with other distros & operating systems as well).

I would run the 64-bit version.

I saw somewhere that I can get up to 4 gig on thie mother. I got to thinking about it earlier and for a couple hundred I can prob upgrade ram and hd on this thing. Being, what, 5 yrs old, I worry about that hd. Plus it's only 40 gig anyway - isn't it aweful!  :D

---

### Post by mips on 2011-05-09
2GB should be more than enough (which also looks like the max ram for that model) and no need to spend that much money on a old computer. Just double check whether it can be upgraded first.
[http://www.laptopmemoryupgrade.com/result.asp?MsClsID=101&MsClsName=Laptops&ModelID=55057&ModelName=Pavilion%20ze2000z](http://www.laptopmemoryupgrade.com/result.asp?MsClsID=101&MsClsName=Laptops&ModelID=55057&ModelName=Pavilion%20ze2000z)
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007609%20600006173%20600000407&IsNodeId=1&name=1GB](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007609%20600006173%20600000407&IsNodeId=1&name=1GB)
Faster  PC3200 (400MHz) ram *should* also work although clocked at 333MHz

Your hard drive is most likely a 4200rpm PATA (verify first) unit than can be replaced with a 7200rpm unit which is faster.

---

### Post by manzdagratiano on 2011-05-09
> **mips said:**
> 
No, it would be be considered AMD64 as it's a 64-bit processor. So he can run either the i686 or AMD64 version, up to him.

My bad! :) I never looked at the 64-bit parts. Indeed, I just wanted to state that all modern Intel/AMD processors are to be considered i686 (x86) or amd64 depending on their address size, regardless of which brand they belond to. Cheers! (or, as the Norsemen say, 'Skol!').

---

### Post by ClientAlive on 2011-05-09
> **mips said:**
> 2GB should be more than enough (which also looks like the max ram for that model) and no need to spend that much money on a old computer. Just double check whether it can be upgraded first.
[http://www.laptopmemoryupgrade.com/result.asp?MsClsID=101&MsClsName=Laptops&ModelID=55057&ModelName=Pavilion%20ze2000z](http://www.laptopmemoryupgrade.com/result.asp?MsClsID=101&MsClsName=Laptops&ModelID=55057&ModelName=Pavilion%20ze2000z)
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007609%20600006173%20600000407&IsNodeId=1&name=1GB](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007609%20600006173%20600000407&IsNodeId=1&name=1GB)
Faster  PC3200 (400MHz) ram *should* also work although clocked at 333MHz

Your hard drive is most likely a 4200rpm PATA (verify first) unit than can be replaced with a 7200rpm unit which is faster.


Thanks for the links. So, now I'm a little confused about something. I see that it says 2 gig max at that first link, but then what is this I see in dmidecode? It says 4 gig. Can the dmidecode information be wrong?

```

Handle 0x0009, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

```

---

### Post by mips on 2011-05-09
> **ClientAlive said:**
> So, now I'm a little confused about something. I see that it says 2 gig max at that first link, but then what is this I see in dmidecode? It says 4 gig. Can the dmidecode information be wrong?


No idea. From personal experience though laptops that are about 6yrs old only take 2GB. Your situation might differ.

---

### Post by ClientAlive on 2011-05-09
> **mips said:**
> No idea. From personal experience though laptops that are about 6yrs old only take 2GB. Your situation might differ.


Right on. I guess I'll be sure to contact HP before spending any money. I wonder what that "number of devices" listing means in the system information above. It lists 2. I think that means 2 slots for dimms right?

---

### Post by mips on 2011-05-10
> **ClientAlive said:**
> Right on. I guess I'll be sure to contact HP before spending any money. I wonder what that "number of devices" listing means in the system information above. It lists 2. I think that means 2 slots for dimms right?

Try HP but they would probably just look at the spec sheet and say 1GB max as that is what it says, memory manufacturers say 2GB.

You're laptop has 2x 200 pin SODIMM slots that accept DDR1 ram clocked at 333MHz (PC2700) although 400MHz (PC3200) should also work but there are sometimes exceptions to this I have found.

You can get a service manual for your laptop (and other documentation) from here [http://h20000.www2.hp.com/bizsupport/TechSupport/Product.jsp?lang=en&cc=us&taskId=101&prodClassId=-1&contentType=SupportManual&docIndexId=64179&prodTypeId=321957&prodCatId=82710&prodSubCatId=18703](http://h20000.www2.hp.com/bizsupport/TechSupport/Product.jsp?lang=en&cc=us&taskId=101&prodClassId=-1&contentType=SupportManual&docIndexId=64179&prodTypeId=321957&prodCatId=82710&prodSubCatId=18703)

Product Number :	PV336AV	
Description :	HP PAVILION ZE2200Z CTO NOTEBOOK PC
[http://partsurfer.hp.com/Search.aspx?searchText=PV336AV#ABA](http://partsurfer.hp.com/Search.aspx?searchText=PV336AV#ABA)

---

### Post by ClientAlive on 2011-05-10
> **mips said:**
> Try HP but they would probably just look at the spec sheet and say 1GB max as that is what it says, memory manufacturers say 2GB.

You're laptop has 2x 200 pin SODIMM slots that accept DDR1 ram clocked at 333MHz (PC2700) although 400MHz (PC3200) should also work but there are sometimes exceptions to this I have found.

You can get a service manual for your laptop (and other documentation) from here [http://h20000.www2.hp.com/bizsupport/TechSupport/Product.jsp?lang=en&cc=us&taskId=101&prodClassId=-1&contentType=SupportManual&docIndexId=64179&prodTypeId=321957&prodCatId=82710&prodSubCatId=18703](http://h20000.www2.hp.com/bizsupport/TechSupport/Product.jsp?lang=en&cc=us&taskId=101&prodClassId=-1&contentType=SupportManual&docIndexId=64179&prodTypeId=321957&prodCatId=82710&prodSubCatId=18703)

Product Number :	PV336AV	
Description :	HP PAVILION ZE2200Z CTO NOTEBOOK PC
[http://partsurfer.hp.com/Search.aspx?searchText=PV336AV#ABA](http://partsurfer.hp.com/Search.aspx?searchText=PV336AV#ABA)


Sweet! Think I got things pretty squared away in my mind about this stuff now. Thanks guys.

:)

---

