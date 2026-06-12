---
title: "Ibm Rs6000?"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by Sasquatch2000 on 2006-06-01
I have an old IBM RS6000 POWERPC server Model F30 type 7025 which no longer has any use.

Is it possible to install Ubuntu on this and try experimenting around with it? If so, how?

Thanks.

---

### Post by pauljwells on 2006-06-01
Looks like you might be the first to try this (by the lack of replies...)

It's fairly common knowledge that IBM's java binaries for the RS6000 procs work OK on ppc, so it _should_ be possible to install ubuntu. I'm guessing the problems will probably show up in the boot process - not sure if RS6000 use the same kind of open firmware 'BIOS' that the macs use.

Download the ppc iso, write it to cd and try to boot off it. After that it'll either work easily or throw an error.

Try it! what have you to lose? Post the error logs on the forum and there'll be plenty of help forthcoming. Good Luck!

---

### Post by Sasquatch2000 on 2006-06-02
I can't imagine I am the only one trying to run linux on an RS6000.

Maybe I am posting in the wrong place? Unfortunately, I did not see any other POWERPC forum on here than this one. 

Anyone know?

---

### Post by Sasquatch2000 on 2006-06-05
Anyone?

---

### Post by metrognome on 2006-06-05
No, you're not the only one...

We have a couple of 7025 F50s that I'm interested in trying this on as well.  Just haven't had time to get to it.

The BIOS is significanlty different than Macs I think.  It's been a while since I've been under the hood of these machines.  Can the PPC kernel hand SMP?  These machines have up to 4 processors.

Whoever gets to it first should start a thread of their progress.

Good luck!  Please link any good info you might find.

MetroGnome

---

### Post by euroford on 2006-06-06
[QUOTE=Sasquatch2000]Anyone?[/QUOTE]

I'm using IBM P520, but I install RHEL4U3.

---

### Post by Sasquatch2000 on 2006-06-06
[QUOTE=euroford]I'm using IBM P520, but I install RHEL4U3.[/QUOTE]

What is that? What does it do? Does that help this work on an RS6000?

---

### Post by warp99 on 2006-06-06
[QUOTE=Sasquatch2000]What is that? What does it do? Does that help this work on an RS6000?[/QUOTE]

Redhat Enterprise Linux Version 4 update 3. :cool:

---

### Post by avtolle on 2006-06-06
I googled your server, and it appears that Debian PPC Linux will work. Also, you might want to look at penguinppc.org.

---

### Post by Jeffrae on 2006-06-07
iSeries \ i5 (AS400)
pSeries

I am using an i5 520 with a guest partition running SUSE SLES 9.

Suse has terrible support so I  have thought about Ubuntu as they have made it nice to keep up to date.

I guess the only thing is that I don't have screen..  I would need IBM's virtual device drivers rolled into the distro.

If I remember right, I telnet into my list of guest partitions on port 2300.  From here I can get to my linux console.

I would love to switch to ubuntu!!

Jeffrae

---

### Post by GrumpySmurf on 2006-06-07
At work, I have a 7028-6C1 (p610) that I'm currently doing AIX migration testing on, but I plan to attempt an ubuntu server install using tty console.

I also have a 7043-150 (43P RS/6000) that I plan to install as a desktop system. Yesterday I attempted to boot off the Dapper PPC Desktop CD but I got a boot failed. However, the firmware is about 7 years old, so that might be an issue.

I'll post a thread with my progress on either/both of these systems; obviously there's interest.

---

### Post by GrumpySmurf on 2006-06-08
Well, it appears that its a no go for Ubuntu on this system.
```

boot: live
cd:0,/casper/powerpc/vmlinux: Unable to open file, Invalid device

```
OpenSUSE 10.1 is installing now though.

---

### Post by Jeffrae on 2006-06-08
OpenSuse..

Hmm Interesting.. Community Supported...

I use SLES 9 on my iSeries, but have found that Novell is terrible for support...

OpenSuse may be the way to go...

---

### Post by Sasquatch2000 on 2006-06-08
Isn't IBM somehow supporting RedHat or something?

edit: found my answer:

[Linux at IBM](http://www-1.ibm.com/linux/)[IMG]http://www.ibm.com/i/v14/t/ibm-logo.gif[/IMG]

---

### Post by joshuapurcell on 2006-06-12
I tried to install Ubuntu 5.10 on an RS/6000 270 without any luck around December of last year. During the troubleshooting I found some links to Debian-based installation howto's that involved replacing the kernel that came with the installation CD with one that would work on these systems. If I'm able to find the link to any of those installation instructions I'll post them later.

As for IBM supporting Red Hat, I can't say. I can say that it seems Red Hat releases versions of their distribution that will work out of the box on this hardware. At the same time, IBM does seem to be [getting more friendly with Ubuntu](http://www.ubuntu.com/news/db2cert).

---

### Post by digibrain on 2006-06-12
I have a BULL Escala E250 machine. I try harder to install over 6 linux distributions. Try with NetBSD - PReP.

Maybe you have luck, I don't have it !

Kind regards !

---

### Post by Sasquatch2000 on 2006-06-14
[QUOTE=GrumpySmurf]At work, I have a 7028-6C1 (p610) that I'm currently doing AIX migration testing on, but I plan to attempt an ubuntu server install using tty console.

I also have a 7043-150 (43P RS/6000) that I plan to install as a desktop system. Yesterday I attempted to boot off the Dapper PPC Desktop CD but I got a boot failed. However, the firmware is about 7 years old, so that might be an issue.

I'll post a thread with my progress on either/both of these systems; obviously there's interest.[/QUOTE]

Yes. Count me in as interested.

---

### Post by joshuapurcell on 2006-06-16
Here are some links to some information related to this:

Debian LiveCD for PPC64:
[http://ftp.uni-augsburg.de/pub/tuxppc/test/](http://ftp.uni-augsburg.de/pub/tuxppc/test/)

Linux on Power Wiki:
[http://oss.gonicus.de/openpower/index.php/Main_Page](http://oss.gonicus.de/openpower/index.php/Main_Page)

These aren't the links I mentioned earlier in this thread, but they are close. Maybe they will help with something.

---

### Post by Sasquatch2000 on 2006-06-19
Anybody have a chance to try this yet? 

Is there a way to ask the developers about this or open a bug to support this?

Thanks.


I also have available a 43P Model 240 with 604e 233 Mhz processor. This is officially a 7043-240. Not sure if this one is any better or worse than the other model I listed.

Thanks for any help towards this.

---

### Post by Sasquatch2000 on 2006-07-07
Please delete this post (Where is the delete post button?)

---

### Post by Sasquatch2000 on 2006-07-17
bump

---

### Post by Sasquatch2000 on 2006-08-10
bump

---

### Post by Jeffrae on 2006-11-30
Bump This Thread Up!! :)

Has anyone tried installing ubuntu on an IBM i5 system?

Thanks,
Jeff P

---

