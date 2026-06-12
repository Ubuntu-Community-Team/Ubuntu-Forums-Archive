---
title: "Why 32bit Feisty was installed on a AMD 64 system?"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by maria-n on 2007-11-16
My PC has an AMD 64 dual core processor (confirmed by the system monitor). However when I installed Feisty from the CD which was shipped to me and I opted for the AMD64 mode, the installer refused and said it's a 32 bit system.

Since then it has worked without problems, upgraded to Gutsy, no probs either.
But now I'm installing extra software and reading about APT etc, I'm again faced with the choice for 32 - or 64 bit packages. 

Can anyone tell me, why that may have happened at the installation?
Should I leave it as it is (after all it works) or try to install 64 bit?
How can I verify, that when I upgraded to Gutsy, it remained the 32 bit version? (I guess so though).
And with software installation: I think I should use the 32-bit versions, but am I right? (The software should fit with the OS i guess, rather than the processor)

Looking forward to your answer,
Maria

---

### Post by shad0w_walker on 2007-11-16
If everything is working there is relatively little point to bother changing over to 64bit. It's alot easier now to run 64bit with out the hassles but if your system works why bother? I run 32bit on my 64bit machine, though mostly it is to avoid downloading 2 different isos (Slow connection)

---

### Post by Inxsible on 2007-11-16
If you are running a 32 bit OS, you will not be able to install or use 64 bit packages or applications.

You can easily use 32 bit OS and apps on 64 bit machines, but not the other way around.

---

### Post by stchman on 2007-11-16
> **maria-n said:**
> My PC has an AMD 64 dual core processor (confirmed by the system monitor). However when I installed Feisty from the CD which was shipped to me and I opted for the AMD64 mode, the installer refused and said it's a 32 bit system.

Since then it has worked without problems, upgraded to Gutsy, no probs either.
But now I'm installing extra software and reading about APT etc, I'm again faced with the choice for 32 - or 64 bit packages. 

Can anyone tell me, why that may have happened at the installation?
Should I leave it as it is (after all it works) or try to install 64 bit?
How can I verify, that when I upgraded to Gutsy, it remained the 32 bit version? (I guess so though).
And with software installation: I think I should use the 32-bit versions, but am I right? (The software should fit with the OS i guess, rather than the processor)

Looking forward to your answer,
Maria

For a lot of apps that you download there is no 64 bit version.  Until 64 bit becomes more mainstream use the 32 bit version of your OS.

---

### Post by mellowd on 2007-11-16
I would just stick with 32bit for now. Unless you are planning on running a huge sql database or something.

---

### Post by rsambuca on 2007-11-16
> **stchman said:**
> For a lot of apps that you download there is no 64 bit version.  Until 64 bit becomes more mainstream use the 32 bit version of your OS.

That statement is not really true anymore, although it used to be the case.  If you actually take the time to check, the repos for the 32bit and 64bit are almost identical.

---

### Post by insane_alien on 2007-11-16
can you post the outputs of 
 ```
cat /proc/cpuinfo
```

and

```
uname -a
```

---

### Post by maria-n on 2007-11-16
Thanks for all the replies :-)

This is the output of the first command:

:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping        : 1
cpu MHz         : 1000.000
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips        : 2011.14
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping        : 1
cpu MHz         : 1000.000
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips        : 2011.14
clflush size    : 64

I'll copy the other in a new reply...

---

### Post by maria-n on 2007-11-16
Output of the uname-command:

:~$ uname -a
Linux maria-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux


"i686" doesn't that mean it's the 64-bit version of Gutsy?

Now I'm really puzzled: would Feisty have been installed as 64-version, in spite of the message about 32 bit-version? Or has Gutsy automatically chosen the proper version, when I upgraded to it?

Note: since everything works fine, I'll in any case not try to install an other version of Gutsy. But it's good to know which software-version I should use, when given the choice...

---

### Post by Inxsible on 2007-11-16
> **maria-n said:**
> Output of the uname-command:

:~$ uname -a
Linux maria-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux


"i686" doesn't that mean it's the 64-bit version of Gutsy?

Now I'm really puzzled: would Feisty have been installed as 64-version, in spite of the message about 32 bit-version? Or has Gutsy automatically chosen the proper version, when I upgraded to it?

Note: since everything works fine, I'll in any case not try to install an other version of Gutsy. But it's good to know which software-version I should use, when given the choice...No i686 means its the 32 bit version. x86_64 usually means 64 bit

---

### Post by Sims2789 on 2007-11-16
> **maria-n said:**
> My PC has an AMD 64 dual core processor (confirmed by the system monitor). However when I installed Feisty from the CD which was shipped to me and I opted for the AMD64 mode, the installer refused and said it's a 32 bit system.

Since then it has worked without problems, upgraded to Gutsy, no probs either.
But now I'm installing extra software and reading about APT etc, I'm again faced with the choice for 32 - or 64 bit packages. 

Can anyone tell me, why that may have happened at the installation?
Should I leave it as it is (after all it works) or try to install 64 bit?
How can I verify, that when I upgraded to Gutsy, it remained the 32 bit version? (I guess so though).
And with software installation: I think I should use the 32-bit versions, but am I right? (The software should fit with the OS i guess, rather than the processor)

Looking forward to your answer,
Maria

Installing the 32-bit version on a system with a 64-bit processor won't cause any problems.

The 64-bit version is ridiculously fast. I estimate that it boots in under 30 seconds on my ThinkPad T61.  However, a few things are missing, like a proprietary Adobe Flash plug-in (though I think the Gnash plug-in supports AMD64). Other programs won't run either, like Rockbox. So, I'm stuck with the 32-bit version.

All the key Ubuntu programs run on AMD64 architecture. If you definitely don't need the programs that don't, use it, but if you're unsure stick with the 32-bit version.

---

### Post by rsambuca on 2007-11-16
> **Sims2789 said:**
> Installing the 32-bit version on a system with a 64-bit processor won't cause any problems.

The 64-bit version is ridiculously fast. I estimate that it boots in under 30 seconds on my ThinkPad T61.  However, a few things are missing, like a proprietary Adobe Flash plug-in (though I think the Gnash plug-in supports AMD64). Other programs won't run either, like Rockbox. So, I'm stuck with the 32-bit version.

All the key Ubuntu programs run on AMD64 architecture. If you definitely don't need the programs that don't, use it, but if you're unsure stick with the 32-bit version.

Where are you getting your info?  The adobe Flash plugin works perfectly in Gutsy 64-bit.

---

### Post by maria-n on 2007-11-19
Thanks to everyone who took the trouble to reply! :-)

Sadly no answer to the question why Feisty couldn't be installed as a 64bit system, but all related questions are nicely answered. I'll stick to the 32bit version and use software for that one.

---

### Post by hyper_ch on 2007-11-19
Interesting, the cpuinfo says it's 64bit...

Instead of running feisty, why not trying the Gutsy 64bit version?

---

### Post by rsambuca on 2007-11-19
> **maria-n said:**
> Thanks to everyone who took the trouble to reply! :-)

Sadly no answer to the question why Feisty couldn't be installed as a 64bit system, but all related questions are nicely answered. I'll stick to the 32bit version and use software for that one.

What are you talking about?  Feisty **could** be installed as a 64bit OS on your system, but you used the incorrect installation disc (you used the 32bit installation disc).  Each disc only comes with only one flavor for installation, either 32bit or 64bit.  You used the 32bit version.

---

### Post by dptxp on 2007-11-19
> **maria-n said:**
> My PC has an AMD 64 dual core processor (confirmed by the system monitor). However when I installed Feisty from the CD which was shipped to me and I opted for the AMD64 mode, the installer refused and said it's a 32 bit system.

Maria

Either you have a 32 bit CD or a 64 bit CD, there is no option for 32 bit OR 64 bit on any Ubuntu CD.
How did you select 64 bit mode ?
The 64 bit CD has 64 bit written on it.

---

### Post by markyb86 on 2007-11-19
> **dptxp said:**
> Either you have a 32 bit CD or a 64 bit CD, there is no option for 32 bit OR 64 bit on any Ubuntu CD.
How did you select 64 bit mode ?
The 64 bit CD has 64 bit written on it.

The cd sleeve says it too!

---

### Post by stchman on 2007-11-19
> **rsambuca said:**
> That statement is not really true anymore, although it used to be the case.  If you actually take the time to check, the repos for the 32bit and 64bit are almost identical.

Yes, the repos are almost identical.  I was speaking of going to [www.getdeb.net](www.getdeb.net) or other websites.  I know that it is not that common but sometime you want a more specialized app.

For instance, if you go to Openoffice.org website I don't see anywhere where you can get the 64bit .deb installer.  I am aware that Ubuntu has OO installed already.

---

### Post by sgtbug on 2007-11-19
@author of the topic
is ur machine a laptop? because many laptops are not working in 64-bit mode.. i had a similar issue with a Vaio..

---

### Post by rsambuca on 2007-11-19
> **stchman said:**
> Yes, the repos are almost identical.  I was speaking of going to [www.getdeb.net](www.getdeb.net) or other websites.  I know that it is not that common but sometime you want a more specialized app.

For instance, if you go to Openoffice.org website I don't see anywhere where you can get the 64bit .deb installer.  I am aware that Ubuntu has OO installed already.

On getdeb, all you have to do is click the "other version" link at the top to get the 64bit versions.  Even if they didn't exisit, you could always just compile from source, like someone has done for all the getdeb packages.

---

### Post by aqchat300 on 2007-11-19
quote from the common person:32bit is the most mainstream compiled code around these here parts... going 64bit means sure u will get 32 and 64bit crap but technology slugs and lags today with 64bit 32bit uses less memory less processor and is the most used os around the forums so for best support 32bit is your best bet and most supported the speed boost from 64bit will be noticeable in the future or even to the easily tricked mind in the future coders will probably just be in the middle of development barely anyone has full drivers so a word of mine now 32bit dude it is functional nice and mainstream with linux support.. plus i have a mid-end laptop and 64bit chews the processor for me i think it is a bit slower... wine is going to make u drunk if u try to use it with 64bit.. :lolflag::popcorn::KS thus my end of my post is finished. BTW if u want 64bit that bad i think u should of just downloaded the ISO yourself so it doesn't opt anyways when it comes to 64bit u do it all
yourself... well the 32 bit crowd gets front row seats to see *STRUGGLING PEOPLE AND THE 64BIT HALF MADE PENGUIN WITH SOME SKIN MISSING*:popcorn: lol dumb long title.

---

### Post by mivo on 2007-11-19
> **stchman said:**
> For a lot of apps that you download there is no 64 bit version.

Can you name five commonly used applications for which there are no 64-bit versions?

---

