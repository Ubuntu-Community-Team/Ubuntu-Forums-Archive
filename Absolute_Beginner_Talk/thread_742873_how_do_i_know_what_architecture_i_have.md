---
title: "how do i know what architecture i have ?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by liorc666 on 2008-04-02
i got new computer with
Intel core duo 2 E6420
and i dont know whice ubuntu i should download
64bit or 32bit ?
[http://processorfinder.intel.com/details.aspx?sSpec=SLA4T](http://processorfinder.intel.com/details.aspx?sSpec=SLA4T)

ive downloaded the 64 bit one but its works pretty slow (bout 7 mins to boot up ) (live CD)

any command i can execute ?

---

### Post by Berean on 2008-04-02
If you enter (in Terminal) "sudo lshw" this should give you a readout of your system.  Other than that I'm uncertain.  The Live CD does take a while to boot up, but 7 mins seems a little extreme.  Regards.

---

### Post by Logical Dream on 2008-04-02
If U are booting from Live CD thats aprox. time U need

---

### Post by sayakb on 2008-04-02
```
uname -a
```x86 => 32-bit OS
x86_64 => 64-bit OS  
EDIT: Sorry.. that was a terrible typo :D I corrected it!

---

### Post by chewearn on 2008-04-02
> **LinuxIsInnovation said:**
> ```
sudo unsame -a
```x86 => 32-bit OS
x86_64 => 64-bit OS

```
uname -a
```
No need sudo, and typo on "unsame".

---

### Post by hyper_ch on 2008-04-02
well, if the 64bit desktop cd run then you have a 64bit architecture... you can't run 64bit on a 32bit architecture ^^

---

### Post by sayakb on 2008-04-02
> **hyper_ch said:**
> well, if the 64bit desktop cd run then you have a 64bit architecture... you can't run 64bit on a 32bit architecture ^^

+1 Absolutely..

---

### Post by felker2 on 2008-04-02
> **liorc666 said:**
> 
Intel core duo 2 E6420
and i dont know whice ubuntu i should download
64bit or 32bit ?


Core 2 is 64-bit. So you *can* use Ubuntu 64-bit. You can also use 32-bit.

---

### Post by erginemr on 2008-04-02
You can still choose to install 32-bit, as Ubuntu 64-bit has its share of problems, most prominent one being sketchy Flash video support. So, you should do some reading on Ubuntu 32-bit and 64-bit before you set out for the installation.

For starters:
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

but a search in the forums will yield more regarding the advantages and drawbacks of using Ubuntu 64 bit.

---

### Post by taavikko on 2008-04-02
> **erginemr said:**
> You can still choose to install 32-bit, as Ubuntu 64-bit has its share of problems, most prominent one being sketchy Flash video support. So, you should do some reading on Ubuntu 32-bit and 64-bit before you set out for the installation.


There isn't sketchy flash video support, it works ;)
In gutsy you just have to install nspluginwrapper along with flashplugin.

P.s In hardy it comes with flashplugin.

---

### Post by sayakb on 2008-04-02
> **erginemr said:**
> You can still choose to install 32-bit, as Ubuntu 64-bit has its share of problems, most prominent one being sketchy Flash video support. So, you should do some reading on Ubuntu 32-bit and 64-bit before you set out for the installation.

For starters:
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

but a search in the forums will yield more regarding the advantages and drawbacks of using Ubuntu 64 bit.


+1 to taavikko, there is no Flash video problem,
```
sudo apt-get install flashplugin-nonfree
```
Works for all online flash content.

---

### Post by Jarramundi on 2008-04-20
Sorry to bust in on  the thread, but I would like to know what architecture I am using... 

Linux Jarramundi 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

It sayeth i686. Is this the architecture of my system, or some other thing? please fill me in.
Oh and it's 32 bit.

---

### Post by thisiam on 2008-04-20
> **Jarramundi said:**
> Sorry to bust in on  the thread, but I would like to know what architecture I am using... 

Linux Jarramundi 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

It sayeth i686. Is this the architecture of my system, or some other thing? please fill me in.
Oh and it's 32 bit.

Thats what i get and i know my computer is 32bit, i think it would say 64 it if it was and i'm quite sure  i686 means 32bit.

---

### Post by NightwishFan on 2008-04-20
i686 is 32bit.

---

### Post by felker2 on 2008-04-20
> **Jarramundi said:**
> Sorry to bust in on  the thread, but I would like to know what architecture I am using... 

Linux Jarramundi 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

It sayeth i686. Is this the architecture of my system, or some other thing? please fill me in.
Oh and it's 32 bit.

The "uname -a" tells you what Operating System you're using. It will not tell which underlying hardware is in use. The first check to see if the hardware is 64-bit, have a look at  "cat /proc/cpuinfo". I have:

model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+

which is a 64-bit processor.

---

### Post by Jarramundi on 2008-04-20
Great can you translate this for me?

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 2793.267
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
bogomips        : 5590.73
clflush size    : 64

---

### Post by chewearn on 2008-04-20
> **Jarramundi said:**
> Great can you translate this for me?


Refer to this explanation:
[http://gentoo-wiki.com/Cpuinfo](http://gentoo-wiki.com/Cpuinfo)

The 64-bit instruction support can be found by looking for "lm" flag.  In the case of your processor, it does not support 64-bit.

---

