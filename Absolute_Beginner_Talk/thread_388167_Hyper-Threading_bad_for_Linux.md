---
title: "Hyper-Threading bad for Linux?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by rodrigo juarez on 2007-03-19
As I was looking trough messages searching for my BogoMIPS, I came across a line that reads:
> CPU: Hyper-Threading is disabled
So I googled for info on enabling it and I found an article named "National Vulnerability Database (CVE-2005-0109)" it goes way back to 2005, it says
> Hyper-Threading technology, as used in FreeBSD and other operating systems that are run on Intel Pentium and other processors, allows local users to use a malicious thread to create covert channels, monitor the execution of other threads, and obtain sensitive information such as cryptographic keys, via a timing attack on memory cache misses.
I couldn't find any new info about that.
But looking at my system monitor I can see two processor graphs so I imagine Hyper-Threading is enabled.

Linux says:
> CPU: Hyper-Threading is disabled
while initializing each processor; after the 2nd CPU has been initialized, it says
> Total of 2 processors activated (11976.97 BogoMIPS).

Now the questions. Is still there any risk with HT in Ubuntu? and Is my HT working?

While it's not really urgent, I would appreciate any help.

---

### Post by LanDan on 2007-03-19
don't worry ;) its fine

---

### Post by mcduck on 2007-03-19
It's not Linux issue, Hyper Threading has some serious security issues that do not depend on your operating system. Probably it's a bit safer in Linux than it's in Windows, but yes, it should be disabled as it's not safe.

I wonder how it's working for you, as I've understood that it's disabled in Ubuntu. But if your CPU really is a P4E and you see 2 CPU's then it's indeed using Hyper Threading. :confused:

---

### Post by LanDan on 2007-03-19
> **mcduck said:**
> It's not Linux issue, Hyper Threading has some serious security issues that do not depend on your operating system. Probably it's a bit safer in Linux than it's in Windows, but yes, it should be disabled as it's not safe.

I wonder how it's working for you, as I've understood that it's disabled in Ubuntu. But if your CPU really is a P4E and you see 2 CPU's then it's indeed using Hyper Threading. :confused:

the only reason its disabled by default is because the default kernel is 386 which can do cpu's with and without SMP . so it will work for everybody and NOT because its a security issue

so my guess is you are running the 686 kernel which is a good thing if supports your hardware, 

further i can see little reason why a hypothetic vulnerability that was bug fixed 3 years ago and applied only if you are running a server with encrypted transactions would have less impact on linux

---

### Post by Jason_25 on 2007-03-19
Hyperthreading was a half-baked attempt by Intel at making 2 "cores" in the CPU.  From what I have seen in gaming forums, performance is better with it disabled anyway.

---

### Post by LanDan on 2007-03-19
> **Jason_25 said:**
> Hyperthreading was a half-baked attempt by Intel at making 2 "cores" in the CPU.  From what I have seen in gaming forums, performance is better with it disabled anyway.

it certainly is not as good as 2 cores and i wouldn't expect more than maybe a 10% performance increase in certain cases but it definitely is not a bad thing and it will improve your performance slightly

---

### Post by mcduck on 2007-03-19
> **LanDan said:**
> the only reason its disabled by default is because the default kernel is 386 which can do cpu's with and without SMP . so it will work for everybody and NOT because its a security issue

so my guess is you are running the 686 kernel which is a good thing if supports your hardware, 

further i can see little reason why a hypothetic vulnerability that was bug fixed 3 years ago and applied only if you are running a server with encrypted transactions would have less impact on linux

Actually Edgy's default kernel supports SMP. Also, the Hyper Threading vulnerability was found in 2005, so I'm pretty sure it wasn't fixed 3 years ago :D

Anyway, it's of course possible that some fix (other than just disabling it) was found for Dapper.

Anyway, here's the original Ubuntu security notice: [http://www.ubuntu.com/usn/usn-131-1]("http://www.ubuntu.com/usn/usn-131-1")

edit: In Dapper you should still need to add 'ht=on' into your kernel options in /boot/grub/menu.lst to enable Hyper Threading, so it sure wasn't fixed for Dapper.

---

### Post by rodrigo juarez on 2007-03-19
I installed 686-smp kernel prior to installing nVidia drivers and Beryl, after the installation 'uname -u' tells me '2.6.17.11-generic' (it said before 686-smp instead of generic).
However, the computer is in my house and it's only used by me, so I can guess it's OK to have HT working then (if it is really working)

btw in windows disable HT from the BIOS made my computer fans to spin up and keep working at full speed all time, I believe it would mean the processor was working harder to have the system running. I haven't noticed anything like this here in Ubuntu.

Thanks for your help. =)

---

### Post by enharrin on 2007-03-19
As an aside, hyper-threading definitely has nice performance benefits.  It will never _hurt_ your performance to have hyperthreading enabled.

The best way I know to figure out if your hyper-threading/multi-core is working is

```
cat /proc/cpuinfo
```

The way I understand it, that will tell you how many CPUs (including virtual CPUs from hyper-threading) the kernel is actually seeing.

My system appears to be working as expected, since I see 4, which makes sense since I have a dual-core, hyper-threading processor.  =)

*EDIT:* Keep in mind that /proc/cpuinfo begins numbering your CPUs at zero.

---

### Post by rodrigo juarez on 2007-03-19
well, I just cat'ed cpuinfo and I see two processors, just like system monitor.
I would think the system may be seeing both processors as independant, instead of just one Hyper-treaded.

Thanks for your help (nice system btw =O)

---

