---
title: "today has been a good day......but......"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-06-24
ok, today i decided to go linux all the way, as in no dual booting windows etc, ive finally figured out why wine wouldnt run (it was something to do with my sound card) ive got cedega up and running (currently need for speed underground 2) and ill be trying more games soon enough, so all in all it hs been a good day.
but when i ran the set up wizard in cedega it says my cpu is only running at 1ghz ? its an athalon 3200 + which runs at 2.01ghz stock speed, so how do i sort this out ? can i just run the wizard again and tell it the cpu is running at 2ghz ? and just out of interest how much of a difference will this make in overall performance ?
also is there a utility built into ubuntu that gives out this kind of info ? eg - cpu speed, fan speeds etc etc.
cheers.

---

### Post by atria on 2007-06-24
The cpu information printed in cedega should not impact the performance in any way.

You can find information regarding your cpu in /sys or just install cpuid with aptitude/synaptic

---

### Post by Ziox on 2007-06-24
cat /proc/cpuinfo

by the way, when creating a thread next time, use a more descriptive title.  It sometimes deters people when titles are "help needed...." and such.

---

### Post by techno-mole on 2007-06-24
interesting, i ran the command you posted -  	cat /proc/cpuinfo
and this is what i got - 

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 2
cpu MHz         : 1000.000 ------ _surely for a 2ghz cpu this should read as 2000.000 mhz ?_
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips        : 2011.08
clflush size    : 64

could it be that the correct frequencies arent being detected ? my concern being that if the system is only registering half the cpu's total capacity then the overall performance of the cpu is halved ? 
ps i changed the title of the thread as it was a little dodgy.
on other thing can you use wine to install drivers and such like, so for example if you have a bluetooth dongle and it comes with a disc with the driver and some kind of application on it can you install the driver and the application and run them both through wine ?
or is it more a case of the application using the drivers available on the system ?
cheers

---

### Post by atria on 2007-06-24
Yeah the overall performance of your cpu is reduced. Check your bios settings and ensure that your CPU is not underclocked. It can also happen because of powernow which changes your cpu frequency with respect to your cpu's current load at real time.

Wine cannot be used to run windows drivers unfortunately. I haven't seen a device working with linux through wine.

---

### Post by techno-mole on 2007-06-24
i know the cpu isnt under clocked, could the same happen if its over clocked ? by that i mean you get an irregular frequency like have ?
cheers.

---

### Post by Malta paul on 2007-06-24
A great little program which details your system including cpu is 'Sysinfo' from Applications>Add/remove search sysinfo. 
Hope you find useful  ;)

---

### Post by techno-mole on 2007-06-24
a question about the sound section when you run winecfg from terminal.
i type winecfg and then i get a window that opens up, but in terminal i get this - fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
 
and if i go to the audio section in winecfg and click on test sound and control panel im getting these to windows, one says - audio test not implemented yet (i get this when i press test sound) and the other i get when i press control panel - launching audio control panel not implemented yet.
so what do i need to do to fix this ? or is it something that hasnt been added to wine yet.
sorry for the silly questions but after a couple of months trying to get it to run, now ive got it going i have no clue as to what im doing with it, i kind of focused all my attention on actually getting it to work, which as it turned out meant taking out my pci sound card and using the on board sound.
cheers

---

### Post by techno-mole on 2007-06-24
ok, im fairly sure the cpu thing is to do with power now, i get different results depending on what im doing.
so here i am, with no windows install, totally linux (well aprt from wine and cedega) so i thought id install musicmatch jukebox, just to see if i could get it to work with wine, so i download the setup.exe and start it with wine and of it goes installing until a window pops up and says, it is strongly recommended that you install internet explorer 5 or higher and with that the install shuts down !
damn you microsoft ! :D

---

