---
title: "processor not recognized correctly?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by redgilda on 2006-09-16
Hello,

I've been thinking... I recently upgraded my pc to 3000+ processor, 1 GB of Ram and installed Ubuntu thinking it will run faaast as the wind..

However it's not that fast as I'd expect it to..
and today I checked my processor with a command I found here:

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 2
**cpu MHz         : 1004.981**
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 2012.02
```

something is wrong right?
is it just a shitty processor or can I change the settings somehow?? Surely the number I bolded out should be much higher?

ANY help appreciated.
Thanks

---

### Post by petri on 2006-09-16
Have you checked your BIOS settings?

---

### Post by redgilda on 2006-09-16
mhmm no I haven't. I am not sure what to look for in Bios but I'll try to have a look around... :>

---

### Post by petri on 2006-09-16
You seek for your CPU frequency and choose the highest one.

If you upgraded the CPU but not your motherboard you should check the BIOS figures that they do match the CPUs figures (voltage, frequency, etc) I think the standard procedure is that your motherboard should automaticly regognize the new CPU...

Check with your motherboard manual.

---

### Post by RoyArne on 2006-09-16
Your cpu is fine. The reported cpu MHz: 1004.981 will increase if you start some compute intensive task. Try "cat /proc/cpuinfo" while you encode an mpeg movie or something, and test it again while no other programs are running and you'll see the difference.

---

### Post by MrHorus on 2006-09-16
> **RoyArne said:**
> Your cpu is fine. The reported cpu MHz: 1004.981 will increase if you start some compute intensive task. Try "cat /proc/cpuinfo" while you encode an mpeg movie or something, and test it again while no other programs are running and you'll see the difference.

That's only if you have CPU scaling on and that's unlikely for a desktop - it's usually applicable to laptops.

---

### Post by RoyArne on 2006-09-16
> **MrHorus said:**
> That's only if you have CPU scaling on and that's unlikely for a desktop - it's usually applicable to laptops.

I have a desktop, installed just a day ago, and as far as I know CPU scaling is on by default.

---

### Post by steve.horsley on 2006-09-16
As RoyArne says, it looks OK. The number they market athlons with is not the clock frequency. My A64-3200+ clocks at 2G max - I nkew that wehn I bought it. But I also discovered that cat /proc/cpuinfo normally shows aroung 1G. It jumps up to 2G if I give the CPU hard work to do - they reduce their clock rate to reduce heat generation if the OS is spending significant time idle.

P.S.
After playing doom3 or ut2004 for a while, the PC takes on a very different character. Both the CPU fan and the graphics card fan get faster and faster until the whole thing is rattling and shaking. Not a problem though - I just turn the game sound up.

---

### Post by redgilda on 2006-09-16
yeah I did notice that it jumps to 1808 mhz when I'm doing more things.. but well.. if this is ok - that does not explain why the pc is not fast in general :(

I think that my computer was faster before I upgraded the processor/motherboard/RAM AND it was on Windows :/ and back then I only had 386 Ram and 1000+ processor... 

so now it should be like 3 times faster (or more as I thought switching to Linux will help too ;-) ) but it's not. any idea what is wrong? Someone wants to come over and have a look? ;-)

---

### Post by redgilda on 2006-09-16
---- my bios settings are like that ---
HT Frequency ratio 4x 
CPU Clock 200 
k8 CPU Clock ratio AUTO 
Current DDR Speed 400 
---------------------------------------

any idea if I should change things there?

---

### Post by petri on 2006-09-16
**k8 CPU Clock ratio AUTO** means your processor is regognized by motherboard and if you get more MHz when you stress it then your CPU is working as it should. Did you know there is some applet for CPU scaling, right click upper panel and choose Add. Maybe that vill show you how your CPU works. I don't know what **CPU Clock 200** means because I still have an AMD 1800+ Have you checked the manual? Or maybe google it, there must be some forum where these things are discussed and you may find an answer already written.

But why isn't pc faster in general? Oh why, oh why, oh why? 
Well how fast do you type? :p :cool: 

Seriously, 3D-games, picture editing (Gimp), video editing and those kind of things will show you the increased speed of your upgrade. General surfing and other "normal" applications doesn't need any power. Well, maybe Calc needs it at startup or all the OpenOffice apps needs CPU when you start them but while you work with them there really is no rush. You do have seen difference with your old pc and present one when you start OOCalc?

If you want to burn a DVD, rip a DVD, watch a movie, download a bunch of files  at the same time simultaneously you will notice your CPU can handle it. The old one would not have.

---

### Post by redgilda on 2006-09-16
well I'm still not sure if everything is okay..

my old pc was faster even when just browsing folders, opening pictures, opening applications etc. I haven't even started doing any 'more cpu/memory consuming' tasks..

but hey, thanks for the input :-)

---

### Post by petri on 2006-09-16
64 bit Ubuntu?

---

### Post by redgilda on 2006-09-16
umm no, in fact I'm pretty sure I installed the default Ubuntu - "PC (Intel x86) desktop CD".. so that would make me 32 bits right? Sorry, but I don't even know how to check that ;-)

Should I have installed the "64-bit PC (AMD64) desktop CD" if I have the AMD 64? Hmm... I guess when I installed it, I didn't even pay attention to what hardware I have.. #-o

---

### Post by Greycloak on 2006-09-16
Try using the K7 kernel.  I have an Athlon XP 3000+, and when I switched to the K7 kernel I noticed an improvement.

---

### Post by petri on 2006-09-16
Yes try K7 kernel, I have though I don't see any improvements. Here is a link to an howto: [http://ubuntuforums.org/showthread.php?t=85917&highlight=kernel+386+686](http://ubuntuforums.org/showthread.php?t=85917&highlight=kernel+386+686)

It is really strange that opening folders etc. is slower, I hope K7 will change that.

P.S. Forget about installing 64-bits Ubuntu. Take a look first at the forum  for 64 bit users :rolleyes:

---

