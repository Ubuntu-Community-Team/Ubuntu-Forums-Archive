---
title: "[SOLVED] CPU frequency scaling unsupported"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by A Pragmaticist on 2008-01-20
When I startup into the desktop, I get an error message: 

"CPU frequency scaling unsupported

You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling."

After I first installed Ubuntu, I had changed from powernowd to cpufreqd, but then decided to change back.  However, after I went back to powernowd I started to get this message every time I start up the desktop, and my panel says the same thing, i.e. cpu frequency scaling unsupported.

I have been unable to figure out to fix this after several hours looking around, and instructions I found either did not work, I could not figure out how to do them, or I was not sure if they were appropriate for my problem.

I went back and forth between powernowd and cpufreqd, hoping that one of them would work eventually.

When I try to reinstall powernowd, the details say this:

"(Reading database . . . 117595 files and directories currently installed.)
Preparing to replace powernowd 0.97-lubuntu7 (using . . ./powernowd_0.97-lubuntu7_i386.deb)  . . .
 * Stopping powernowd:
    . . . done.
Unpacking replacement powernowd . . .
Setting up powernowd (0.97-lubuntu7) . . .
 * Starting powernowd . . .
/etc/init.d/powernowd:  156:  cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling governor: Directory nonexistent
 * CPU frequency scaling not supported
    . . . done."

When I try to install cpufreqd:

"(Reading database . . . 117595 files and directories currently installed.)
 Removing powernowd . . .
 * Stopping powernowd:
    . . . done.
 Selecting previously deselected package cpufreqd.
 (Reading database . . . 117595 files and directories currently installed.)
 Unpacking cpufreqd (from . . ./cpufreqd_2.2.1-2_i386.deb) . . .
Setting up cpufreqd (2.2.1-2) . . .
No cpufreq interface found, not starting cpufreqd."

When I go into /sys/devices/system/cpu/cpu0, there is no cpufreq.

Here is my cpu info:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 104
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-56
stepping        : 1
cpu MHz         : 1808.311
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc [6]
bogomips        : 3619.82
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 104
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-56
stepping        : 1
cpu MHz         : 1808.311
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc [6]
bogomips        : 3616.50
clflush size    : 64

I did download the AMD driver, but I can't figure out how to do anything with it or even if I need it.  I also tried to modprobe powernow k8, but "no such device".

Can anyone help me with this?

---

### Post by A4006 on 2008-01-20
You need to enable CPU frequency scaling in the BIOS.

---

### Post by A Pragmaticist on 2008-01-21
I went into the BIOS and through the menus, but could not find cpu frequency scaling.  Could you help me figure out how to change it in the BIOS?

---

### Post by A4006 on 2008-01-21
What is the motherboard model number and manufacturer? It could be that it is not supported by your processor/motherboard in the first place.

---

### Post by A Pragmaticist on 2008-01-21
Well, the BIOS says the system id is 30b7, and I believe the manufacturer is Quanta.  If this is not the right info, could you help me figure it out?  I have had a really difficult time figuring it out; HP does not seem to list the motherboard.

---

### Post by p_quarles on 2008-01-21
You can get the make and model of the motherboard by running the following in a terminal:
```
sudo lshw
```
That will list all your hardware. The mobo is near the top of the list.

---

### Post by A Pragmaticist on 2008-01-22
When I did lshw, this is what showed up.  I am not sure what qualifies as the make and model here, unless it is the AMD Turion entry.

"description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 1962MB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-56
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.1
          size: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc _6_
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB"

There was more, but it went on about memory1 (unclaimed) and so forth; I did not see anything about a motherboard other than the beginning I posted here.  If you would like to post it all, let me know; I thought it was quite a bit for a post, that's why I did not just post the whole thing..

---

### Post by p_quarles on 2008-01-22
> **A Pragmaticist said:**
> *-core
       description: Motherboard
       physical id: 0
Is there no information between the "description" and the "physical id"? On mine, it gives a vendor and product name. That will tell you exactly what the mobo is.

---

### Post by A Pragmaticist on 2008-01-22
Nope, no such info between "description" and "physical id".

---

### Post by p_quarles on 2008-01-22
Did you run lshw with sudo? If you run it without root privileges, you'll get what you're currently seeing.

---

### Post by A4006 on 2008-01-22
Seeing as your motherboard is a generic one from the manufacturer, I doubt you have support for CPU frequency scaling.  Besides, why do you even want to use CPU frequency scaling?  If you want to monitor the CPU usage just use a desklet like this one [http://www.gnome-look.org/content/show.php/WaterMark+system+information?content=71960]("http://www.gnome-look.org/content/show.php/WaterMark+system+information?content=71960")

---

### Post by A Pragmaticist on 2008-01-23
When I do sudo, it does not even come up with "core", it just starts with cache 0:

"   *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KB
             capacity: 1MB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GB
          capacity: 2GB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: HYMP512S64CP8-Y5
             vendor: DA00000000000000
             physical id: 0
             serial: 40001837
             slot: DIMM 1
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             product: HYMP512S64CP8-Y5
             vendor: DA00000000000000
             physical id: 1
             serial: 40003842
             slot: DIMM 2
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)"

And after that goes into memory 1(UNCLAIMED) and so forth.

I guess I am not sure why I want cpu frequency scaling, I just thought it would be good to have since I have a laptop and I thought it was normal to have some sort of setting running, at least by default.  I thought it also curious that powernowd had already been installed and everything was fine, until I tried to change back from cpufreq to powernowd.  Really, I had no idea it would cause me this much trouble, and I am upset now to find out that figuring out what my motherboard is has been this difficult.

Well, I suppose I'll check out the applet you suggested.

If anybody can help me figure out the motherboard though, that would be awesome; I'd still like to figure that one out.

---

### Post by ajgreeny on 2008-01-24
Perhaps you need more lines to scroll in the terminal profile.  Edit the profile of the terminal to 1000 lines instead of 500 default and it may help.
PS, I assume you **did** scroll the terminal output to see all the info.

---

### Post by stchman on 2008-01-24
When you got your laptop did the Windows install support frequency scaling.  Maybe the mobo in that laptop does not support that function.

---

### Post by A Pragmaticist on 2008-01-24
ajgreeny, your assumption was correct.  And thank you, the 1000 lines did help.  (Is there a command to see whatever is cut off at the top?)

I believe this is the pertinent part:

*-core
       description: Motherboard
       product: 30B7
       vendor: Quanta
       physical id: 0
       version: 65.28
       serial: None
       slot: @
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.3A (07/19/2007)
          size: 101KB
          capacity: 960KB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification

I am guessing that the model is 30B7 and the maker is Quanta?  Hopefully I am reading this correctly.  Not too sure what to do with this info.  Should frequency scaling show up on the capabilities list if I were able to do it?

I really don't know if the Windows install supported frequency scaling, but I can check; I have a dual boot.  I'll go take a look, but if someone could point out how to find it on Windows Vista in case I don't post again, that would be great.

P.S. - If there is any info about my comp I should never post, it would be cool if someone could let me know.

---

### Post by A Pragmaticist on 2008-01-24
Oh yeah, A4006, I have no idea how to run the desklet.  I downloaded Watermark, but now I don't know how to get it to work.  Any tips?

---

### Post by A Pragmaticist on 2008-01-24
stchman, 

I checked into Vista, but I am not sure if I understood how to look for it.  I could not find anything that said "frequency scaling", and there was not much to find when I googled to see what to look for.  I did find some instructions, and it did seem that I was able to find what someone online had indicated at [http://www.neowin.net/forum/lofiversion/index.php/t496361.html](http://www.neowin.net/forum/lofiversion/index.php/t496361.html) (which was: "open power options, select a plan to edit, click advanced settings and there is an option for max and min CPU freq"; although nothing said CPU freq, I did see the 5% and 100% that the other person responded in that forum's thread in an option to configure power settings in the advanced settings.  I am not sure what to make of this though.

---

### Post by mc4man on 2008-01-24
in vista type perfmon in start search box and press enter
see if blue box for cpu is anything but 100% max frequency (indicates scaling)
if 100% check power plans for something like balanced or power saver and then recheck in performance monitor

---

### Post by A4006 on 2008-01-24
> **A Pragmaticist said:**
> Oh yeah, A4006, I have no idea how to run the desklet.  I downloaded Zoom, but now I don't know how to get it to work.  Any tips?

You need to install screenlets in the first place.  Follow the instructions here [http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_users_.28Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon.29]("http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_users_.28Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon.29") and then download and install this screenlet [http://www.gnome-look.org/content/show.php/CPU+Meter+Screenlet+vista%27ish+look?content=64599]("http://www.gnome-look.org/content/show.php/CPU+Meter+Screenlet+vista%27ish+look?content=64599").
  I have had some issues with them but it probably has something to do with me continually screwing up my system.

---

### Post by A Pragmaticist on 2008-01-26
mc4man, thx

I checked the blue box, it is indeed scaling, never seems to be at 100 but shifts between lower numbers.

So what do I do now that I know I should be able to use scaling?  I'd still like to use powernowd instead of cpufreqd, but I guess anything at this point would be alright.

---

### Post by A Pragmaticist on 2008-01-26
A4006, thx

I was able to set up the screenlet manager, and downloaded the screenlets you suggested.  But I am not using the second one you suggested, the first one seems to have everything I need.

I could not figure out how to configure the watermark screenlet to start-up when I login, but that's okay because I just added it as a custom application to my panel, and it starts up the screenlet, just as I configured it with all the extra opened and pre-configured windows for it.

However, I am still wondering about the frequency scaling...

---

### Post by A4006 on 2008-01-26
Yeah, I had the same problem with the screenlets not loading on startup.  I solved it by writing a .sh script that runs upon startup, that goes like this:

python /home/a4006/.screenlets/Sidebar/SidebarScreenlet.py&
python /usr/local/share/screenlets/Calendar/CalendarScreenlet.py&
python /home/a4006/.screenlets/CPU_Meter/CPU_MeterScreenlet.py&

and so on.  You can make it executable by typing this "sudo chmod a+x /path/to/script" into terminal.  As for frequency scaling, I _can_ use it, I just never do.  I don't think it's that useful, although it might be for you.

---

### Post by A Pragmaticist on 2008-01-26
A4006,

I had already done all that, but then I got the error that there was no such path.  It does not really matter anyway though, I am happy with my solution.

---

### Post by A Pragmaticist on 2008-01-28
Is there anyone who can help me with the cpu frequency scaling problem?

---

### Post by A Pragmaticist on 2008-01-30
bump

---

### Post by A4006 on 2008-01-31
It would appear not.

---

### Post by A Pragmaticist on 2008-02-08
Well, I'll try again here...

bump

(Anyone think it'll help if I just start a new thread about this problem?  I'm not sure if this is okay to do, I'm just asking)

---

### Post by mc4man on 2008-02-08
some reading, whether helpful who knows
[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

---

### Post by A Pragmaticist on 2008-02-10
Well, in case anyone cares, I upgraded to Gutsy despite the official advice against doing so for HP laptops of my series.

Consequently, CPU Frequency Scaling is working again for me...so I'm just going to make this "Solved", even though my "solution" was to upgrade to a version of Ubuntu which is supposed to be a major regress overall for my comp.  It does run painfully slow now and I am having problems with acpi, but oh well, at least I feel like I made progress.

Thanks to everyone who tried to help.

---

