---
title: "What linux to use?."
date: 2012-08-05
forum: Any Other OS
---

### Post by confrontation on 2012-08-05
I downloaded a copy of BackTrack5R2-KDE-64.iso , I then went to but it from my USB stick only to get a message saying...

"This kernel requires an x86-64 CPU but only detected an i686 CPU.
unable to boot - please use a kernel approriate for your CPU."

Is there a linux like backtrack that will suit the i686 CPU?
and why isnt linux x86-64 backwards capable?

Regards
Greg

---

### Post by QIII on 2012-08-05
i686 hardware architecture is 32 bit.  You will have to use a 32 bit OS.

While a 32 bit OS will run on a 64 bit machine (generally -- some libraries may present issues), the reverse is not true. 

It is not a matter of "backwards compatibility".  The 32 bit machine architecture of the i686 simply will not allow the use of a 64 bit OS.  (In some cases one can virtualize a 64 bit machine on a 32 bit hardware system.)

---

### Post by confrontation on 2012-08-05
I am running windows 7 64bit on the computer I want to install linux on.

Everest results

CPU Type	DualCore Intel Core i5 540M, 2400 MHz (18 x 133)
CPU Alias	Arrandale-3M
	
Instruction Set	
64-bit x86 Extension (AMD64, Intel64)	Supported
AMD 3DNow!	Not Supported
AMD 3DNow! Professional	Not Supported
AMD 3DNowPrefetch	Not Supported
AMD Enhanced 3DNow!	Not Supported
AMD Extended MMX	Not Supported
AMD MisAligned SSE	Not Supported
AMD SSE4A	Not Supported
AMD SSE5	Not Supported
Cyrix Extended MMX	Not Supported
IA-64	Not Supported
IA MMX	Supported
IA SSE	Supported
IA SSE 2	Supported
IA SSE 3	Supported
IA Supplemental SSE 3	Supported
IA SSE 4.1	Supported
IA SSE 4.2	Supported
IA AVX	Not Supported
IA FMA	Not Supported
IA AES Extensions	Not Supported
VIA Alternate Instruction Set	Not Supported
CLFLUSH Instruction	Supported
CMPXCHG8B Instruction	Supported
CMPXCHG16B Instruction	Supported
Conditional Move Instruction	Supported
LZCNT Instruction	Not Supported
MONITOR / MWAIT Instruction	Supported
MOVBE Instruction	Not Supported
PCLMULQDQ Instruction	Not Supported
POPCNT Instruction	Supported
RDTSCP Instruction	Supported
SYSCALL / SYSRET Instruction	Not Supported
SYSENTER / SYSEXIT Instruction	Supported
VIA FEMMS Instruction	Not Supported

---

### Post by ratcheer on 2012-08-05
That system is certainly capable of running 64-bit Linux. There are any number of distros you could try. I enjoy using Ubuntu, Arch Linux, and Sabayon Linux. Each can be configured with a wide choice of desktops. The possibilities are virtually endless.

You will find something that works.

Tim

---

### Post by Sarcastic Cows on 2012-08-05
If no 64-bit OS work on your computer, try a 32-bit version

But for distributions, it's really your choice. The current distros that share most the Linux market are Arch, Mint, Ubuntu and some others, too

If you want to go away from mainstream distros, look at distrowatch.com, they have a list of the top 100 distros.

---

### Post by tartalo on 2012-08-05
> **Sarcastic Cows said:**
> The current distros that share most the Linux market are Arch, Mint, Ubuntu and some others, too

Errr, 

In the Desktop the ranking would be:
Ubuntu, Fedora, SUSE, Debian, Mint, Mandriva, CentOS, Kubuntu, RedHat, Epiphany, Gentoo, Mips, PCLinuxOS, Arch, others

[http://stats.wikimedia.org/archive/squid_reports/2012-06/SquidReportOperatingSystems.htm](http://stats.wikimedia.org/archive/squid_reports/2012-06/SquidReportOperatingSystems.htm)

In the Server:
Debian, CentOS, Ubuntu, RedHat, Fedora, Suse, Gentoo

[http://w3techs.com/technologies/history_details/os-linux](http://w3techs.com/technologies/history_details/os-linux)

---

### Post by Sarcastic Cows on 2012-08-05
> **tartalo said:**
> Errr, 

In the Desktop the ranking would be:
Ubuntu, Fedora, SUSE, Debian, Mint, Mandriva, CentOS, Kubuntu, RedHat, Epiphany, Gentoo, Mips, PCLinuxOS, Arch, others

[http://stats.wikimedia.org/archive/squid_reports/2012-06/SquidReportOperatingSystems.htm](http://stats.wikimedia.org/archive/squid_reports/2012-06/SquidReportOperatingSystems.htm)

In the Server:
Debian, CentOS, Ubuntu, RedHat, Fedora, Suse, Gentoo

[http://w3techs.com/technologies/history_details/os-linux](http://w3techs.com/technologies/history_details/os-linux)

Yeah, the ones most people use

---

### Post by QIII on 2012-08-05
i686 is a 32 bit architecture.  It was "revived" initially for the  original Core brand of dual core processors and reworked to allow a 64  bit instruction set. But that was a kludge.

I don't understand why an i3, i5 or i7 would be identified as as i686 by your installer.

---

### Post by blackwolf92 on 2012-08-05
You can download a 32bit version of Backtrack if you want..

---

### Post by QIII on 2012-08-05
> **blackwolf92 said:**
> You can download a 32bit version of Backtrack if you want..

That doesn't solve the issue of why his 64 bit version is incorrectly saying the hardware won't support it, however.

This might be a question best asked on a dedicated BackTrack forum.

---

### Post by confrontation on 2012-08-06
Thanks everybody for your input.
Ill take QIII advice and ask on a backtrack forum.
I will post my findings so all you are up to speed on my issue if anybody else has the same problem.

---

