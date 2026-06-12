---
title: "Spent some time in FreeBSD this weekend"
date: 2008-04-20
forum: BSD
---

### Post by jdong on 2008-04-20
It's a long weekend at MIT so I finally had some free time to screw around. And this time, it was FreeBSD testing day! I've been excited about the FreeBSD 7 release but not had a chance to give it a spin yet.

I set up a quick and dirty VirtualBox VM with 10GB disk space  and 48MB RAM to give FreeBSD an extreme test on  the server side. That's not a typo... I'm going for the extreme low-resource setup, and plus I had very little RAM to spare thanks to our good friend fglrx and its gracious RAM usage...

The install was pretty uneventful, unchanged from earlier  releases -- I'm fairly familiar with sysinstall and found it generally usable, though of course it's not all that user friendly and benefits greatly from familiarity or a manual read beforehands.

Post-install, I tried the freebsd-update tool for managing system updates -- it worked just fine. Since the release there has only been an update to like 3 system files, which fetched and applied without any issue. 
I noticed portsnap (for managing the ports tree securely without the need for configuring a supfile either) was in the default system, which is quite nice.

I then bit the bullet and updated the base system to RELENG_7, which is the FreeBSD 7.x development branch. This upgrade also went smoothly without any hitches, and while I was at it I recompiled the kernel with SCHED_ULE, the new scheduler.


I then set up a quick proof-of-concept test of a real-world task: setting up a mailserver. My goal was simply a IMAPS server via dovecot that mirrors my primary (2GB) maildir. I tested Hardy Heron and FreeBSD7 both inside identical-specs virtual machines.

Setup time was strongly in favor of Ubuntu -- I got the server up and running in 1/4th of the time that it took me to get dovecot out of ports and configured to run on bootup, with SSL, etc. However, 1 hour or 4 hours really isn't that big of a deal for me.

Performance was subjectively in favor of FreeBSD. I tested using mutt on both VMs connecting via localhost to IMAP. On 48MiB RAM, both systems suffered greatly in terms of swapping on large tasks such as opening up huge servers. As a measure of interactivity, during the middle of opening a folder with 48,000 messages, I used a 2nd SSH shell that was open to execute "find
~/Mail -name new". FreeBSD won by a **definitive margin**, while Ubuntu took a long time to respond interactively to the new command, even the sshd lagged while I was typing. It's clear that FreeBSD handled a mixed CPU+IO+swapping load better. In general, as a subjective note (I have no numbers to back this up), I found FreeBSD's performance to be extremely predictable. While it wasn't on top for everything, it did fare very consistently with no obvious weak spots. I don't think I can say the same about Linux 2.6.x though. While it is unbeatable
in some aspects of performance, at times you can really find a workload that brings Linux to its knees unexpectedly.

So overall in terms of FreeBSD 7:

**I liked...**

(1) freebsd-update and portsnap in the default setup. Makes it simpler to apply security updates and manage ports.

(2) **Astounding** performance and interactivity on severely limited hardware. In this aspect I found it really surpassed Linux.

(3) BSD "coreutils" felt faster. Everything from ls to top felt like they responded faster for some reason.

**I disliked...**
(1) Very barebones base install. I'm not a csh fan and I would've liked bash either by default or available. I also found it disappointing portupgrade wasn't a part of the base system. Managing ports via the makefiles in /usr/ports is pretty cumbersome.

(2) Requires a good deal of configuration out-of-the-box to get it up and running intuitively... I feel ubuntu is closer to what I need out of the box.
(3) Ports and /usr/src in general seemed like it required more maintenance than Ubuntu/Debian APT. There's no clear separation in the Ports tree between stable/security updates and new releases of stuff, and even during my brief time in the OS I did experience a config file migration necessary after a Port upgrade.
(4) Hardware support is lackluster at best. Out of the box both of my laptops' "real" hardware handled FreeBSD very poorly, neither networked (even wired!) out of the box, and one I was able to get networking after a RELENG_7 update bootstrapped by USB drive. This is definitely a work-in-progress area for this OS. With that said, **if there's a driver, it generally is rock solid**, unlike Linux where there's many in-tree drivers that IMO are alpha quality at best.


Overall, I think FreeBSD is a great, solid OS that has its merits, but I don't think I'll be seriously using it for personal tastes. I'm really familiar with Ubuntu/Debian and feel competent administering it, but I feel like a complete idiot when it comes to the BSDs. Of course, I would use a FreeBSD box administered by someone else without hesitation! I have the utmost respect for this hardcore UNIX.

---

### Post by DahVid on 2008-04-20
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/introduction.html#CURRENT](http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/introduction.html#CURRENT)
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/introduction.html#STABLE](http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/introduction.html#STABLE)

---

### Post by SuperSon!c on 2008-04-20
now THAT'S what i call some insight! i've never tried freebsd being a noob and probably won't for awhile, but that was an excellent read, thanks!

---

### Post by cardinals_fan on 2008-04-20
FreeBSD converted me.  It is great and NetBSD might even be more fun...

---

### Post by thisllub on 2008-04-20
I agree with most of what you say. 
I always have 2 distros on a machine at any time. Currently I have Arch and FreeBSD 7 on my laptop.
ACPI works beautifully on my ACER laptop with FreeBSD and causes  hanging on every Linux I have tried.

Wireless networking and the lack of a viable virtualisation product are the only things holding me back.

I find FreeBSD to be very smooth and efficient.

The biggest advantage Ubuntu has over ANY open source offering is the quality of these forums. The BSD forums are littered with spam and porn with a lack of useful information.
However Hardy is pretty big. My experience with the beta makes me suspect that HAL , DBUS and all the other "modern" daemons will be introduce more bugs and make it slower than Gutsy. 

I certainly wouldn't use Hardy on a server. I would use FreeBSD.

---

### Post by jdong on 2008-04-20
> **DahVid said:**
> [http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/introduction.html#CURRENT](http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/introduction.html#CURRENT)
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/introduction.html#STABLE](http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/introduction.html#STABLE)

I believe I stated that correctly, right? RELENG_7 is the 7-STABLE branch which represents the development effort going into the 7.x point releases. That is, a mix of conservative new features and bugfix updates.

---

### Post by samb0057 on 2008-04-20
FreeBSD is much more stripped down than linux, not intended for the home users, but someone who is going to do major customization to the system. It's not going to include a bunch of helpful stuff by default, its meant to be very minimal. I like this in a way, for my servers atleast.

---

### Post by jdong on 2008-04-20
> **samb0057 said:**
> FreeBSD is much more stripped down than linux, not intended for the home users, but someone who is going to do major customization to the system. It's not going to include a bunch of helpful stuff by default, its meant to be very minimal. I like this in a way, for my servers atleast.

No, don't get me wrong, I totally see the merit in the minimalist install and as a geek it doesn't bother me greatly to put those things on myself. I'm just remarking in general it seems to take more effort to set up a FreeBSD server than an equivalent Linux one. though IMO that's a very rewarding experience/investment.

I have nothing but the utmost respect for the BSDs -- they are very solid, very meritable OSes.

---

### Post by cardinals_fan on 2008-04-20
> **thisllub said:**
> 
The biggest advantage Ubuntu has over ANY open source offering is the quality of these forums. The BSD forums are littered with spam and porn with a lack of useful information.
However Hardy is pretty big. My experience with the beta makes me suspect that HAL , DBUS and all the other "modern" daemons will be introduce more bugs and make it slower than Gutsy. 

The BSD forums are a mixed bag.  They have a massive amount of trash and spam, but a few of the users are exceedingly helpful.  The Ubuntu forums are the best, of course.

---

### Post by jdong on 2008-04-20
> **cardinals_fan said:**
> The BSD forums are a mixed bag.  They have a massive amount of trash and spam, but a few of the users are exceedingly helpful.  The Ubuntu forums are the best, of course.

I am no BSD community expert but it seems like majority of the good-quality help is concentrated on mailing lists. Also, things haven't really changed much in BSD-land for a longer period of time and googling tends to yield very relevant info. The FreeBSD handbook, which I forgot to mention in my review, is definitely ON TOP of my likes list!

---

### Post by cardinals_fan on 2008-04-20
> **jdong said:**
> I am no BSD community expert but it seems like majority of the good-quality help is concentrated on mailing lists. Also, things haven't really changed much in BSD-land for a longer period of time and googling tends to yield very relevant info. The FreeBSD handbook, which I forgot to mention in my review, is definitely ON TOP of my likes list!
The mailing lists are the location of most support action.  Both FreeBSD and NetBSD have fabulous manuals.

---

### Post by jdong on 2008-04-22
Ok, a quick example of the differences I'm seeing in an everyday task: At dinner a silly question came up of how many times the word "nazi" shows up in my e-mails. So, instead of approaching it hypothetically, I whipped out a terminal on my Hardy box and typed **grep -Ri nazi Mail | wc -l**.

Then I remembered I still have a BSD VM set up on the same box, so why not give that a try too? So I SSH'ed into the FreeBSD VM and typed the same thing. Given virtualization overhead, I expected certainly that Ubuntu would respond first with my answer. To my surprise, **FreeBSD finished first**, by a considerable margin! Shocked at this result, I attempted to time both of them with the time command, taking 5 samples and reporting the minimum. Here's the best runs:

```


# FreeBSD 7-STABLE

[jdong@wormhole ~]$  time grep -Ri nazi Mail | wc -l 
grep: warning: Mail/.Inbox: recursive directory loop
     315

real	1m17.137s
user	0m3.779s
sys	0m14.692s

# Hardy
[jdong@jdong:~]$ time grep -Ri nazi Mail | wc -l                  (04-22 20:55)
grep: warning: Mail/.Inbox: recursive directory loop

315
grep -Ri nazi Mail  184.98s user 7.61s system 81% cpu 3:57.66 total
wc -l  0.00s user 0.00s system 0% cpu 3:57.66 tota

```

Ubuntu took **over two times longer** and yielded the same result. Now I understand that FreeBSD has a different grep implementation than Linux, but frankly I don't care for this purpose -- I wanted to know how many times a word shows up in my e-mail and FreeBSD answered that question first. Even inside a VM with only 128MB RAM while Ubuntu had the rest of the 2GB RAM native.


Now this is a very limited example microbenchmark, but it definitely contributes to the general gut feeling I have that FreeBSD is "snappier"

**UPDATE:**

If that's not sick enough, I decided to test multitasking: In simultaneous SSH sessions I issued a grep command each against the same directory but for different words, simulating multitasking workloads on similar datasets (which I expect the CPU and IO schedulers to have some leeway in optimizing). Pasted are the results one after another, but understand that they ran in parallel on the actual test:

```

#FreeBSD

[jdong@wormhole ~]$  time grep -Ri nazi Mail | wc -l 
grep: warning: Mail/.Inbox: recursive directory loop
     315

real	1m22.114s
user	0m4.693s
sys	0m10.446s
[jdong@wormhole ~]$ time grep -Ri jdong Mail | wc -l
grep: warning: Mail/.Inbox: recursive directory loop
   58094

real	1m21.615s
user	0m2.879s
sys	0m9.935s


#Linux
[jdong@jdong:~]$ time grep -Ri nazi Mail | wc -l                  (04-22 21:03)
grep: warning: Mail/.Inbox: recursive directory loop

315
grep -Ri nazi Mail  173.90s user 4.47s system 70% cpu 4:11.32 total
wc -l  0.00s user 0.00s system 0% cpu 4:11.32 total
[jdong@jdong:~]$ time grep -Ri jdong Mail | wc -l                 (04-22 20:59)
grep: warning: Mail/.Inbox: recursive directory loop

58191
grep -Ri jdong Mail  171.29s user 6.02s system 70% cpu 4:10.44 total
wc -l  0.01s user 0.02s system 0% cpu 4:10.44 total

```


Even though FreeBSD only had **one virtualized core** while Ubuntu was allowed both CPU cores (and used both cores fully throughout the test), FreeBSD was able to service the requests faster than Ubuntu.

Note also that the average grep time from single to multi threaded for FreeBSD increased from 1:17->1:22 while for Linux increased from 3:57 to 4:11... The latter result doesn't make sense to me because FreeBSD barely suffered a hit even though it was limited to one core while Ubuntu used both cores but suffered a bigger proportional hit!

---

### Post by cardinals_fan on 2008-04-22
Doesn't really surprise me; FreeBSD has felt faster than any Linux distro to me, and Ubuntu isn't an especially fast distro anyway.

---

### Post by stream303 on 2008-04-22
Wow - great posts!  I hate to admit this, but when I was first learning *nix, I didn't know vi and was struggling with Yggdrasil. :)

I switched to FreeBSD, and when I found the EE editor, (or was it AE included by default for mere mortals, I was hooked.)

Of course I now know enough vi to be comfortable, but even then I was amazed at how fast the userland utils seemed to be compared to Linux, or for that matter open or netbsd.

I don't have the guts yet to put it on my PPC box, now that freebsd has that port available..  Why did you have to post this - freebsd is calling me again... :)

---

### Post by thisllub on 2008-04-23
> **jdong said:**
> 
Even though FreeBSD only had **one virtualized core** while Ubuntu was allowed both CPU cores (and used both cores fully throughout the test), FreeBSD was able to service the requests faster than Ubuntu.



I don't really think that is a good test for a number of reasons.
The host had to run both processes so it was much busier. Whenever the VM had  CPU cycles they would mostly have been used for the task at hand.

I have FreeBSD and ARCH on this machine so I will try some tests and report back.

---

### Post by klange on 2008-04-23
If your graphics drivers are working, go compile Compiz-Fusion, it should run fine on FreeBSD.

---

### Post by jdong on 2008-04-23
> **thisllub said:**
> I don't really think that is a good test for a number of reasons.
The host had to run both processes so it was much busier. Whenever the VM had  CPU cycles they would mostly have been used for the task at hand.

I have FreeBSD and ARCH on this machine so I will try some tests and report back.

Well, while testing the host I intentionally left the virtual machine idle. Definitely in a 1-thread test it would have been strongly in favor of FreeBSD because KVM virtualization (the last available benchmarks) shows around 10% overhead on a "make world" test.

---

### Post by Sporkman on 2008-04-23
I tried running DesktopBSD in virtualbox last night - it installed fine, but afterwords kept crashing when starting it up... Maybe it's because I installed the 32 bit version but my hardware is 64 bit (AMD turion64)...

Meh. I'll try Nexenta next...

---

### Post by jdong on 2008-04-23
> **Sporkman said:**
> I tried running DesktopBSD in virtualbox last night - it installed fine, but afterwords kept crashing when starting it up... Maybe it's because I installed the 32 bit version but my hardware is 64 bit (AMD turion64)...

Meh. I'll try Nexenta next...

It's probably, actually, VirtualBox. I had a lot of trouble running VirtualBox and FreeBSD together, getting unexplained guest soft-locks (CPU spins but whole userland is frozen while compiling packages), network not working (must downgrade to 10MBit NIC emulation), and even one host kernel panic.

---

### Post by Sporkman on 2008-04-23
> **jdong said:**
> It's probably, actually, VirtualBox. I had a lot of trouble running VirtualBox and FreeBSD together, getting unexplained guest soft-locks (CPU spins but whole userland is frozen while compiling packages), network not working (must downgrade to 10MBit NIC emulation), and even one host kernel panic.

I figured as much, unfortunately I don't have a spare machine kicking around to do a real install.

---

### Post by jdong on 2008-04-23
Try using KVM (libvirt/virt-manager, see Ubuntu Server manual) or VMWare Server, both of which work well at virtualizing FreeBSD.

---

### Post by Sorivenul on 2008-04-26
I've been quietly using FreeBSD for a while now and absolutely adore it.  Gave NetBSD a test run recently and liked it as well.  Best of both worlds?  DragonflyBSD.  Surprised there's not much mentioned about it in the BSD subforum here.  Dragonfly will have a place on my new box when summer begins.  My tests of it as a server are outstanding, though I have yet to test desktop capabilities.  Just my two cents.

---

### Post by WitchCraft on 2009-01-10
This comparison is probably not objective.

First, grep is not representative for the performance of an entire operating system - I guess everybody knows that.

Second: It doesn't matter how much memory you give to a program. If the program doesn't use it, then you can give it 100 GB RAM and you won't see a difference. If you read and write from disk, it's probably more important how good data is compressed on read/write.

Third: Even if you have exactly the same sourcecode on the same operating system, you can get different results. 

For example, Arch Linux compiles everything as 686, while Ubuntu compiles everything as i386. Now Pentium 4 with Direct 3d Now, MMX, SSE1,2,3,4 should be faster on heavily processor-dependant tasks (such as string comparison) than a 386 DX/SX processor...

Now, I don't know what your FreeBSD was compiled for, but it's most likely not i386.

4th: You don't know what impact the VM has on scheduling.
If the time for the VM OS and Ubuntu is split in two "equal time" parts, then Ubuntu will of course be slower, because the time for managing the VM must be taken from Ubuntu's scheduling time share...

---

