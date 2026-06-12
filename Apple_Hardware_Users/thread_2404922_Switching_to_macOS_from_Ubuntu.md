---
title: "Switching to macOS from Ubuntu"
date: 2018-10-30
forum: Apple Hardware Users
---

### Post by reegz on 2018-10-30
Hi folks,

I have been an Ubuntu user for quite some time now. My usage is probably more along the lines of a moderate user rather than a full-on power user; though I do enjoy writing bash scripts whenever I run into a something that requires me doing a task more than once e.g.: fetching data and sanitising it; pinging services; searching through files and filtering results etc. Actually, I just enjoy looking for excuses to write scripts. Gives me the chance to better understand awk, sed and tee *fear*.

My department at work has started clamping down on non-Windows machines and have advised that I need to switch from Ubuntu to Windows *spit* asap. They have offered me an alternative of switching to a Macbook instead.

I have never used any Apple products and have over the years built up an irrational hatred of the Cult of Apple. However, I do think they build good quality hardware and have UX's (?) that the Linux world can only dream of. No, I'm not becoming an acolyte!

So my question to the members of this forum is whether I - as a Linuxy type user - be able to live with macOS? Is this a switch that is easy enough to make? Will I still have command line access as I do today with the ability to script at my leisure? Are there any pitfalls that await me? And what about the things I haven't even thought about yet?

Appreciate any insightful comments in this matter.

---

### Post by TheFu on 2018-10-30
Awk, sed, tee can be replaced by any of the more used scripting languages like perl, ruby or python.  If I were starting today, I'd learn python. Georgia Tech has 4 free python courses on [https://www.edx.org/](https://www.edx.org/)  which should get anyone to intermediate-advanced level.

Ok, my OSX story ... 

In 2012, I was working for a company that wanted to port their android apps to iOS - the Apple iOS, not the Cisco IOS which has been around 20+ yrs.  Anyway, to write apps for iOS, a Mac is mandatory.  They shipped me a nice Core i5 Mac and told me to get started. 

Then I was a Unix/Linux guy for 20+ yrs.  Got the Mac on the network, connected to my KVM and started learning. Here's my impressions over 2-3 weeks with the system.
* I'd played with MacOS in college - long, long, ago.  We used it with MS-Word to write our senior projects which required heavy mathematical formulas. At the time, no other commonly used tools could handle the equation.
* Apple renames common things to proprietary names.  ssh isn't ssh.  NFS isn't NFS.  CIFS isn't CIFS.  All these things meant I needed a translator to get the "apple-speak" understanding.  At the time, their CIFS implementation was terribly broken and not working.  It think that lasted a few months - it was just my bad luck it happened be when I was new to Apple.
* I was able to migrate my Firefox and Thunderbird configurations over to the Mac. They worked perfectly.
* Generating and using ssh keys was the same. Can't remember the details. Might have needed to install some tools.
* The shell tools shipped with the system are BSD style, not system-V.  That may or may not matter to you.  I had to try to remember commands from my SunOS days.
* Many of the shell tools have flaws and bugs that were fixed 2-5 yrs ago, but haven't been patched by apple.
* There is brilliance in the Mac GUI, but if you are used to Windows or Linux GUIs, then all the "be different, just to be different" choices are maddening. At least for me.
* I use X/Windows and the x-buffer as a key part of my workflow.  This uses a select/paste technique, not copy/paste.  Copy/paste adds 2 extra steps and it is wasteful IMHO.
* I'm addicted to having window focus controlled by mouse location inside a window, not by clicking.  This is commonly known as X-Mouse on Windows. Few people know about it and only people with a Unix X/Windows background are usually aware of this capability.  I routinely leave the active window "behind" other windows as data/commands are entered.
* I often run programs on a remote system and display the output or GUI on the system I sit behind, This is not a remote desktop. It is the normal X/Windows client/server DISPLAY method.
* Sometimes I like to use different window managers, the GUI for my Linux systems.  Generally, I go with a lite-WM and usually strip it down further.  These days my system doesn't have menus. Access to about 10 commonly used programs is through keyboard commands.  It is my system and customized for my needs.  I don't care if 5B other people cannot use it. 

The real issue I had with the Mac was that the default GUI wasn't what I wanted and didn't support things I'd been using for decades.  I wasn't going to get over it.  I missed X/Windows and the flexibility it provides.  

A few times the frustration was so great I wanted to throw the machine against the wall, hard.  I assigned someone else to perform the porting (Android to iOS) and never looked back. Handed over the Mac to that guy and got back to setting up and maintaining our enterprise systems using F/LOSS following standards and avoiding proprietary solutions.

I was the problem.  Like many new users, I wanted to keep using my old methods on a new OS.  I expected unix to be unix, when clearly it wasn't.  This is the same problem that Windows users moving to Linux have.  They want Linux to work just like Windows, which is impossible.  I was too inflexible.  That was 100% my flaw, not a flaw with OSX.  I found the OSX GUI cumbersome. The consistency in the interfaces was nice, but I already had 30+ yrs of muscle memory with other key combinations.

As a work machine, if I didn't have to buy the software it needed, then OSX would be my choice over Windows as the lessor of evil choices. The "Apple Tax" is real. Some online sales charge Apple users just a little more. To my knowledge, OSX doesn't send "telemetry data" back to Apple with no way to disabled it.  Win10 does.  OSX doesn't reboot your machine without your approval after updates.  I'd have a Linux VM for most uses, but OSX under it given the choice you have.

OTOH, current knowledge about Windows is probably more valuable to an IT career if you might need to change jobs in the future. Knowledge of OSX probably isn't as useful in the business world, except in select industries. If you work or plan to work in one of those, then OSX skills are highly valuable.

Anyways, that's my story of trying OSX. Hopefully others with great experiences will share them too.

---

### Post by gsahli on 2018-11-02
Once you get used to it, you'll like MacOS just as much as linux (but not more than).
I've been using both since the late 90s. I was a Unix user before that, and also a Mac user during the OS7-8-9 period. Understanding Linux is a big help for Mac users.
I don't understand the IT crackdown on Linux - but I've heard recent horror stories about this in Europe. Is it a lack of understanding? Some integration that doesn't work?

---

### Post by gnwiii on 2018-11-24
I have years of experience with unix (mostly SGI Irix), linux, and macOS (dating from when it was called NeXTStep), and recently retired from a workplace where Windows was the "corporate standard".  Until recently, users who rely mainly on bash shell scripts, emacs, and terminals had little problem moving between linux and macOS.   The main issue has been the differences between the (elderly) BSD utilities on macOS and the more current GNU versions used on linux.   Some factors consider:

1.  some linux distros started using dash instead of bash for /bin/sh, creating problems with applications that use bashisms in scripts.

2.  macOS recently got "System Integrity Protection" (SIP) which blocks some common (but questionable from a security standpoint) practices such as using LD_LIBRARY_PATH to force an application to use a specific library version.   Some developers are finding SIP makes it difficult to maintain cross-platform applications, but others seem to be learnign how to work with SIP.

3.  macOS moving to a new graphics system, which has impacted OpenGL

4.  The macOS community has ported many linux tools, including X11 (XQuartz) and a very complete collection of linux/GNU utilities thru the macports project.  Macports has a  rolling development model so usually provides newer linux/GNU utilities than Ubuntu LTS versions.   

5.  macOS uses the clang compilers which don't yet have robust Fortran.  You can, however, get gfortran from macports or other sources.

6.  Windows 10 has WSL which currently provides several linux distros (Debian, Ubunto, SUSE).  WSL provides a terminal with bash -- for X11 graphics you have to add a 3rd party Windows Xserver.  Some network tools are not available in WSL and disk I/O is much slower than for a native linux install.  From your description, WSL might be adequate unless you have large data sets where I/O performance is important.

When switching platforms, you need to think about where you can go for help when things break.   Microsoft as a company appears to have lost the historical antagonism towards linux and FOSS, but lower level support in large enterprises doesn't get those memos.  Large enterprises often have groups doing high-end graphics and video that rely on macOS, but those groups probably can't help with bash scripts.  That leaves the internet, where there are a few people using WSL for bash scripts and a larger community of macOS users working with bash scripts.

---

### Post by reegz on 2018-11-24
> **gnwiii said:**
> I have years of experience with unix (mostly SGI Irix), linux, and macOS (dating from when it was called NeXTStep), and recently retired from a workplace where Windows was the "corporate standard".  Until recently, users who rely mainly on bash shell scripts, emacs, and terminals had little problem moving between linux and macOS.   The main issue has been the differences between the (elderly) BSD utilities on macOS and the more current GNU versions used on linux.   Some factors consider:

1.  some linux distros started using dash instead of bash for /bin/sh, creating problems with applications that use bashisms in scripts.

2.  macOS recently got "System Integrity Protection" (SIP) which blocks some common (but questionable from a security standpoint) practices such as using LD_LIBRARY_PATH to force an application to use a specific library version.   Some developers are finding SIP makes it difficult to maintain cross-platform applications, but others seem to be learnign how to work with SIP.

3.  macOS moving to a new graphics system, which has impacted OpenGL

4.  The macOS community has ported many linux tools, including X11 (XQuartz) and a very complete collection of linux/GNU utilities thru the macports project.  Macports has a  rolling development model so usually provides newer linux/GNU utilities than Ubuntu LTS versions.   

5.  macOS uses the clang compilers which don't yet have robust Fortran.  You can, however, get gfortran from macports or other sources.

6.  Windows 10 has WSL which currently provides several linux distros (Debian, Ubunto, SUSE).  WSL provides a terminal with bash -- for X11 graphics you have to add a 3rd party Windows Xserver.  Some network tools are not available in WSL and disk I/O is much slower than for a native linux install.  From your description, WSL might be adequate unless you have large data sets where I/O performance is important.

When switching platforms, you need to think about where you can go for help when things break.   Microsoft as a company appears to have lost the historical antagonism towards linux and FOSS, but lower level support in large enterprises doesn't get those memos.  Large enterprises often have groups doing high-end graphics and video that rely on macOS, but those groups probably can't help with bash scripts.  That leaves the internet, where there are a few people using WSL for bash scripts and a larger community of macOS users working with bash scripts.

Thank you for the detailed feedback.

---

