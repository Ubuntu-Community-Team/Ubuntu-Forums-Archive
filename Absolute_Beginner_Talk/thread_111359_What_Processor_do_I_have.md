---
title: "What Processor do I have"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Healey on 2006-01-02
Hi

I have been reading a bit about which kernal I should be using - Problem is I am not sure what Processor I have !! So its hard to decide !!

I know its AMD and I know that Its 1.3Ghz but thats all I know !!

How do i ask Ubuntu what I have ???? 

I am new to all this - Sorry !!

Regards

Healey

---

### Post by Sef on 2006-01-02
cat /proc/cpuinfo will find your processor.  

[http://ubuntuforums.org/showthread.php?t=103379&highlight=Finding+Processor]("http://ubuntuforums.org/showthread.php?t=103379&highlight=Finding+Processor")


NB:  No need to apologize we all were new once, and your inquiry helped me to learn something new.

---

### Post by Lord Illidan on 2006-01-02
Have you any documentation which came with the system. It should tell you about your system.

---

### Post by Mathias-K on 2006-01-02
[QUOTE=Healey]Hi

I have been reading a bit about which kernal I should be using - Problem is I am not sure what Processor I have !! So its hard to decide !!

I know its AMD and I know that Its 1.3Ghz but thats all I know !!

How do i ask Ubuntu what I have ???? 

I am new to all this - Sorry !!

Regards

Healey[/QUOTE]

If you're trying to figure out which version of Ubuntu to use (Intel x86, PowerPC or AMD64), x86 is for you as the smallest 64bit-supporting processor is the (socket 754) Sempron 2500+ running 1.4GHz.

---

### Post by Healey on 2006-01-02
Hi

Thanks for the  reply - I get this !

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 7
model name      : AMD Duron(tm) Processor
stepping        : 1
cpu MHz         : 1313.397
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow
bogomips        : 2596.86

What kernal should I be using ???

Thanks

Best Regards

Healey

---

### Post by poofyhairguy on 2006-01-02
You should use the k7 kernel.

---

### Post by Healey on 2006-01-02
Hi 

Thanks for you replies

I am a little confused now !

Should I use K7 or x86 or are they the same !! (Almost perhaps )

Regards and Thanks

Healey

---

### Post by Suger on 2006-01-02
k7 is one of the x86 kernels (must be named something like linux-x86-k7 as opposed to linux-x86-generic. I'm on amd64 here, so I can't tell).

---

### Post by Healey on 2006-01-02
Hi

OK I will investigate futher - Backup some stuff

And then gice K7 a try

Thanks

Healey

---

### Post by mcduck on 2006-01-02
I just wanted to tell you that instead of installing any specific kernel version you should install a metapackage pointing to latest kernel, this way you'll get automatic updates..

So in your case, 'sudo apt-get install linux-K7' :)

---

### Post by Healey on 2006-01-02
Hi

Thanks for that - I will give it a try very soon

Regards

Healey

---

