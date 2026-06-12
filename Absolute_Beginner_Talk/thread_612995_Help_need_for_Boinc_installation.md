---
title: "Help need for Boinc installation"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by gzone on 2007-11-14
Can anyone tell me where "libcurl3 (> = 7.16.2-1)" is located? I need this file to install the Boinc Manager...it is one of the dependencies for Boinc.

---

### Post by celticbhoy on 2007-11-14
Get this from debian website :-

You have searched for packages that names contain libcurl3 in all suites, all sections, and all architectures. Found 7 matching packages.
Exact hits
Package libcurl3
    *  sarge (oldstable) (libs): Multi-protocol file transfer library, now with SSL support!
      7.13.2-2sarge5: alpha amd64 arm hppa i386 ia64 m68k mips mipsel powerpc s390 sparc
    * etch (stable) (libs): Multi-protocol file transfer library
      7.15.5-1etch1 [security]: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc
    * etch-m68k (libs): Multi-protocol file transfer library
      7.15.5-1: m68k
    * lenny (testing) (libs): Multi-protocol file transfer library (OpenSSL)
      7.17.0-1: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc
    * sid (unstable) (libs): Multi-protocol file transfer library (OpenSSL)
      7.17.1-1+b1 [gnuab]: kfreebsd-amd64
      7.17.1-1: alpha amd64 arm armel hppa hurd-i386 i386 ia64 kfreebsd-i386 m68k mips mipsel powerpc s390
      7.17.0-1: sparc

Other hits
Package libcurl3-dbg

    * sarge (oldstable) (libdevel): libcurl compiled with debug symbols
      7.13.2-2sarge5: alpha amd64 arm hppa i386 ia64 m68k mips mipsel powerpc s390 sparc
    * etch (stable) (libdevel): libcurl compiled with debug symbols
      7.15.5-1etch1 [security]: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc
    * etch-m68k (libdevel): libcurl compiled with debug symbols
      7.15.5-1: m68k
    * lenny (testing) (libdevel): libcurl compiled with debug symbols
      7.17.0-1: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc
    * sid (unstable) (libdevel): libcurl compiled with debug symbols
      7.17.1-1+b1 [gnuab]: kfreebsd-amd64
      7.17.1-1: alpha amd64 arm armel hppa hurd-i386 i386 ia64 kfreebsd-i386 m68k mips mipsel powerpc s390
      7.17.0-1: sparc

Package libcurl3-dev

    * sarge (oldstable) (libdevel): Development files and documentation for libcurl
      7.13.2-2sarge5: alpha amd64 arm hppa i386 ia64 m68k mips mipsel powerpc s390 sparc
    * etch (stable) (libdevel): Transitional package to libcurl3-openssl-dev
      7.15.5-1etch1 [security]: all
    * etch-m68k (libdevel): Transitional package to libcurl3-openssl-dev
      7.15.5-1: all
    * lenny (testing): Virtual package
      provided by: libcurl4-openssl-dev
    * sid (unstable): Virtual package
      provided by: libcurl4-openssl-dev

Package libcurl3-gnutls

    * etch (stable) (libs): Multi-protocol file transfer library
      7.15.5-1etch1 [security]: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc
    * etch-m68k (libs): Multi-protocol file transfer library
      7.15.5-1: m68k
    * lenny (testing) (libs): Multi-protocol file transfer library (GnuTLS)
      7.17.0-1: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc
    * sid (unstable) (libs): Multi-protocol file transfer library (GnuTLS)
      7.17.1-1+b1 [gnuab]: kfreebsd-amd64
      7.17.1-1: alpha amd64 arm armel hppa hurd-i386 i386 ia64 kfreebsd-i386 m68k mips mipsel powerpc s390
      7.17.0-1: sparc

Package libcurl3-gnutls-dev

    * etch (stable) (libdevel): Development files and documentation for libcurl
      7.15.5-1etch1 [security]: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc
    * etch-m68k (libdevel): Development files and documentation for libcurl
      7.15.5-1: m68k
    * lenny (testing): Virtual package
      provided by: libcurl4-gnutls-dev
    * sid (unstable): Virtual package
      provided by: libcurl4-gnutls-dev

Package libcurl3-gssapi

    * sarge (oldstable) (libs): libcurl compiled with GSSAPI support
      7.13.2-2sarge5: alpha amd64 arm hppa i386 ia64 m68k mips mipsel powerpc s390 sparc

Package libcurl3-openssl-dev

    * etch (stable) (libdevel): Development files and documentation for libcurl
      7.15.5-1etch1 [security]: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc
    * etch-m68k (libdevel): Development files and documentation for libcurl
      7.15.5-1: m68k
    * lenny (testing): Virtual package
      provided by: libcurl4-openssl-dev
    * sid (unstable): Virtual package
      provided by: libcurl4-openssl-dev

---

### Post by celticbhoy on 2007-11-14
I know version no's are different, but it was the Debian site not Ubuntu.

---

### Post by Skip Da Shu on 2007-11-14
> **gzone said:**
> Can anyone tell me where "libcurl3 (> = 7.16.2-1)" is located? I need this file to install the Boinc Manager...it is one of the dependencies for Boinc.

I'm curious why you need to find this and I didn't when I installed boinc-client and boinc-manager with apt-get??

I'm using 7.10 64bit

---

### Post by gzone on 2007-11-14
Thank you celticbhoy, I will take a look. Skip Da Shu..I don't know why but the 32 bit version does. Do you think the command line version from Boinc will work? If you have any thoughts I am looking forward to hearing them.

Thanks for all your help.

---

### Post by Skip Da Shu on 2007-11-14
> **gzone said:**
> Thank you celticbhoy, I will take a look. Skip Da Shu..I don't know why but the 32 bit version does. Do you think the command line version from Boinc will work? If you have any thoughts I am looking forward to hearing them.

Thanks for all your help.

Ya'll are already over my head.  I'm still trying to figure out how I can overlay BOINC v5.10.21 x86_64 over my BOINC v5.10.8 that apt-get installed... but the good news is the apt-get of boinc-client and boinc-manager was fairly painless and must be idiot proof since I got it working :)

FYI, if you run E@H their app is requiring stdc++ v5 and my fresh install of Gutsy uses stdc++ v6.  I'm seeing this problem in 64bit but am told it's also true in 32bit also.  I don't understand the problem though I read them to say (6 months ago) v6 was too new... but also saw some  talk about curl and graphics libs used... all way over my head and the thread was old.  I left a post asking them when the 1.5 year old v6 libs would be rolled in.  I guess some versions of Linux will let you have both sets of libs there but perhaps not Debian/Ubuntu... like I said... I'm really stretching it to even try and repeat what I'd read on this... not a C programmer.  It's out on the E@H number crunching forum if you're interested.

---

### Post by gzone on 2007-11-14
> **Skip Da Shu said:**
> Ya'll are already over my head.  I'm still trying to figure out how I can overlay BOINC v5.10.21 x86_64 over my BOINC v5.10.8 that apt-get installed... but the good news is the apt-get of boinc-client and boinc-manager was fairly painless and must be idiot proof since I got it working :)

FYI, if you run E@H their app is requiring stdc++ v5 and my fresh install of Gutsy uses stdc++ v6.  I'm seeing this problem in 64bit but am told it's also true in 32bit also.  I don't understand the problem though I read them to say (6 months ago) v6 was too new... but also saw some  talk about curl and graphics libs used... all way over my head and the thread was old.  I left a post asking them when the 1.5 year old v6 libs would be rolled in.  I guess some versions of Linux will let you have both sets of libs there but perhaps not Debian/Ubuntu... like I said... I'm really stretching it to even try and repeat what I'd read on this... not a C programmer.  It's out on the E@H number crunching forum if you're interested.

Hey Skip Da Shu, I ended up rebuilding the computer, but this time connected to the internet. Got Boinc to install and run signed up on some new projects with no problem. The reason I built a ubuntu machine is for Orbit@Home. The work units is currently only in linux.

E@H I have on a WinBlows XP so I'm not going to use linux for anything that has a Winblows App. I'll try to see if E@H will blow up in my face with this new 7.10 Ubuntu. I'll keep you informed.

---

### Post by Skip Da Shu on 2007-11-14
Man I was all wrong... it's not E@H but Lieden... sorry.

Here's what I've got running under 64 bit Ubuntu 7.10 w/ 64bit BOINC:

ABC@home	attached	
APS@Home	attached	
Climate Prediction -0.0%	(needs some 32bit lib to run 32bit app)			 
Einstein@Home	   -0.0%	(needs some 32bit lib to run 32bit app)			 
Leiden Classical   attached	(doesn't work w/ Debian or Ubuntu due to old stdc++ lib)
LHC@Home	 attached	
Malaria Control	   attached
Orbit@Home	 attached
Pirates@Home    attached
Predictor@Home attached
QMC@Home	 -0.0%		(needs some 32bit lib to run 32bit app)			 
Rectilinear Crossing No. attached
RieselSieve	    attached
Rosetta@Home  attached
SETI@Home	 attached
SIMAP	              attached
Spinhenge@home	-0.0%	no linux app
SZTAKI Desktop Grid   -0.0%					 
World Community Grid -0.0%	(needs some 32bit lib to run 32bit app)			
uFluids          -0.0%  no linux app, dropping project anyway

The ones listed as "**attached**" are on this machine all run fine with 64bit Gutsy except Lieden (doesn't work in 32bit either, seemingly to me because they will not upgrade a stdc++ lib to current version).  The ones with 0% I havent' got working 64 bit yet and are on my WinXP boxes along with all the ones attached here (except Orbit).

This Xubuntu install is/was an experiment to see if I can dump windows on the dedicated crunchers.  I'd like to go the 64 bit route (**ABC & AFS run in 1/2 the time per WU** with same credits in 64bit due to being 64bit integer based applications) but so far the list is a bit short.  Seriously thinking about writing a blanket letter to all the project "owners" asking if it isn't time for 64 bit support to be a bit higher priority.  While I read posts claiming 1 project that had a -1.8% drop in thru-put in 64bit all the others saw a 3~9% improvement.

There are a bunch of reasons but it really all boils down to... legitimate alternatives to Win/Vista are now available that semi-normal people (like me) can actually install and operate for an attractive price and without that ridiculous Vista ULA. 

For my dedicated crunchers Xubuntu, or a server install or Gentoo might be the best solution (Xubuntu was my choice as it seemed the least painful) but having now seen this OS and having read that Gnome or KDE base Ubunutu is even more user friendly I'm thinking about installing one of those versions now just for the experience and as a dry run for...

I started out thinking I'd never replace XP on the desktop machines but now I'm even questioning that.  I'm toying with the idea of putting Ubuntu (KDE or Gnome desktop) 32bit on my wife's machine... she's not so ingrained into the innards of Windows and OpenOffice apps do more than she uses with MSOffice now.  Other than that she she already uses T-bird and Firefox... I don't think she knows that the CD drive is really also a burner and she has yet to figure out that you can create a document and send it to the printer/fax w/o printing the page first and then running it thru the fax machine. :confused:  I'd already dumped the wireless and put her back on a wire.  Her little speakers that came with her keyboard seem to do anything she wants them to do (play sound from web pages and "party poker")... I think all that will either work or I can make it work with a Ubuntu install.

I will just have to tell her the MS police are coming unless she can show me her legal XP and Office papers (or $350 in small unmarked bills).  

I can smbfs out to her storage that's currently on a WinXP machine (but even this may a Xubuntu machine before long).  Just gotta get "sudo mount -a" to work at user logon.  I'm on the verge of getting remote access working at boot (I can get the server running once I'm logged in... just not starting at boot like I want it to).

OK, 'nuff ramblin' on and on by me.

l8r, Skip

---

### Post by gzone on 2007-11-15
Hi Skip Well you are alot further ahead with linux then I'am. For me it is still Orbit@Home that got me to load linux. I did run linux before but didn't notice any great jump in the numbers. So to keep the house happy I keep it on Winblows. I did pick up a used P-4 for the linux an old Dell Optiplex GL260.

On a day to day basis Ubuntu is all that one needs for email and surfing. It is when you get into things like Boinc is where the fun begins. All in all it's all good will slowly load more and more projects on to the linux.

That brings me to the question what kind of system can make use of 64 bit OS and App's?

Greg

---

### Post by Skip Da Shu on 2007-11-15
> **gzone said:**
> 
That brings me to the question what kind of system can make use of 64 bit OS and App's?
Greg

Depends on the CPU.

On the AMD side most of the later Semprons (the ones called Sempon64s) all the Athlon 64s and all the X2 series.  Basically anything AMD introduced after around 12/2003.

I'm less certain on the Intel side... I know all the current Core2 Duo based CPUs (including quads and Xeon's based on same) support 64bit.  The Core 2 Extremes (not duos but the ones that have two CPUs in one tin can) also do.  Some of the Centrino chips and Pentium Ds in the 520 and above series.  I don't know if Pentium 4s ever had what they called "EM64T" actually released or not... it was a point of debate back around 4/2004.  As Intel release some "prescott" P4s to system integrators that supported 64 bit but the early retail ones did not.

So... P4 or older... probably not unless it was very late P4... Probably most Pentium D and all later Intel chips do.  AMD, just about everything except old socket A "Athlon XP"s and early Semprons.

If you see 'EM64T', 'AMD64' or 'x86_64' supported on CPU specs, it does 64 bit.

If you have one in mind email or PM me and I can look it up.

Skip

---

### Post by gzone on 2007-11-15
Would that mean that my new Intel Dual Core Mac could be 64 bit?

---

### Post by Skip Da Shu on 2007-11-15
Highly likely.

EDIT: 2nd thought ... w/o a doubt.

---

### Post by Skip Da Shu on 2007-12-01
BTW... someplace on this site I found and updated to reflect the steps I took to install the v5 stdc++ libs and that made the leiden project happy on 64bit and some others (QMC, E@H, CPDN) happy on the 32bit install.

Then later I figured tripped over the Synaptic Package Manager and used it to add the v5 stdc++ libs on this machine... even easier.

I left the first cruncher running 32bit Xubuntu and it's off doing it's thing.  I've got the 2nd one on the bench now running 64bit Xubuntu.  BOINC is up and running as a daemon (service) just fine but I have some project specific issues.  QMC, CPDN and E@H give me a new error.  WCG does also but only on one of there applications, other one works fine.

```
Sat 01 Dec 2007 06:24:50 PM CST|QMC@HOME|Reason: Unrecoverable error for result three_ad_anthracene.3996_0 (process exited with code 22 (0x16, -234))
```

I haven't gotten any work from Orbit yet but they say by year end they'll be up and running.  Well back to searching for an answer to this "code 22" error.

---

### Post by gzone on 2007-12-02
Hi Skip,
I'm still waiting for Orbit too. Took a look at the pictures, really nice setup.

---

### Post by Skip Da Shu on 2007-12-02
Hey, I found the error code 22 problem with QMC and E@H running under 64bit Ubuntu.

These projects send 32 bit applications to the 64 bit client (and OS) and need some additional libraries installed.  I used System>Synaptic Package Manager and did a search for "IA32" and found a set of shared 32bit libs for AMD64 systems.  Installed these and QMC and E@H are both crunching now.  :)

I am assuming at this point that my code 22 error on CPDN will also be solved but I have to wait 3 more hours before I can get another WU from CPDN as I already crashed my limit of 2 WUs in a 24hour period.  I'll edit this later if CPDN error also resolved.

The guys on the CPDN and BOINCSTATS forums pointed me to this so I'm off to thank them now.

My remote access via x11vnc also works on this fresh install of 64bit Xubuntu with the changes I made on the 32bit Xubuntu machine literally copied and pasted into this one.  SO I must have mangled something in my multiple attempts to get a VNC server running at boot time on that machine.  I think I may go back and start over on that machine and install 64 bit on it since I now have these projects all working on 64 bit:
[B]
Proven to work now:[/B]
ABC (64bit integer math based, will run substantially faster with 64 bit OS/BOINC/APP)
QMC
SETI
Rsieve	
WCG
E@H
Malaria Control
SIMAP
Leiden
Rosetta
RCN
LHC
CPDN 

**Assume to be working, need new WU to test:**
Pirates
Predictor
APS (64bit integer math based, will run substantially faster with 64 bit OS/BOINC/APP)
ORBIT

**Not expected to work (either only Windows or Linux in beta testing):**
uFluids
Spinhenge
NanoHive
SZTAKI (32bit Linux only, confirmed)

---

### Post by Skip Da Shu on 2008-03-23
> **gzone said:**
> Hi Skip,
I'm still waiting for Orbit too. Took a look at the pictures, really nice setup.


Orbit@home is up and they let out a small batch of linux WUs a day or two ago!

---

### Post by Skip Da Shu on 2008-03-23
Updated list of projects that are running on my Xubuntu 64b machines w/ libia32 and libstdc++5 packages installed below.

**Native 64b apps running under Ubuntu/Xubuntu:**[LIST=1]
[*]ABC (large output boost using 64b on this one)
[*]Rsieve
[*]POEM
[*]Rosetta
[*]RCN
[*]Skeeter (Malaria Control)
[*]SIMAP (confirmed before they ran outa work)
[*]SETI
[*]LHC
[*]Leiden (some problems on some of there apps, Classical OK, unresolved at this point)
[*]Predictor (no WUs to confirm this one)
[/LIST]

**32b apps running under 64b Xubuntu/Ubuntu:**
[LIST=1]
[*]CPDN (Hadsm only)
[*]QMC
[*]E@H
[*]SpinH
[*]WCG
[*]Orbit
[/LIST]

Sure would like to know how to package install the boinc version in the Hardy libs... hint hint.  I'm running a v5.10.8 package install with executables overlaid from v5.10.45 off of Berkeley.  Surprised I haven't broken the whole mess.

---

