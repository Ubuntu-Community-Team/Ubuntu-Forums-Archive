---
title: "Question: How can I turn a PII laptop into a net admin tool?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by thecgmguy on 2007-03-27
Hi Folks, 

I need your help with a general linux question.  

I need to find a linux distribution for my old old laptop.  Here's the specs: 
- PII 333 MHz Processor
- 96 MB RAM
- 3.3 GB Hard Drive
- No integrated NIC
- USB Ethernet Dongle (Linksys USB200M)
- 24X CDROM
- USB Port

I'm wanting to convert the laptop into a network admin tool.  I'd like to use it to accomplish the following tasks: 
- Monitor network nodes (PING, SNMP, Latency Tests)
- Network Connectivity and Routing Tests (Telnet, Dig, NSLOOKUP, etc)
- Packet Captures and packet analysis
- Web browsing
- Linux command practices
- GUI interface

So I'm looking for a distribution that will work with my specs and provide as much network tools and functionality as possible. 

But wait, there's more =P

I plan to leave the laptop up and running for long periods of time so I don't want to use a "live cd" distribution... or rather, I need it to run off of the hard drive. 

BONUS POINTS - I'd like the desktop to look nice (yea, I know... I'm shallow like that).  Any ideas?

Thanks for your time....

-MB

---

### Post by halitech on 2007-03-27
most of the tools will run from any distro but with only 96 meg of ram, very limited what will run.

check here

[http://distrowatch.com/search.php]("http://distrowatch.com/search.php")

and do a search for old computer in the distrobution categories

---

### Post by kerry_s on 2007-03-27
-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by thecgmguy on 2007-03-27
Thanks for the prompt feedback halitech but that link didn't work... :(

---

### Post by thecgmguy on 2007-03-27
Kerry_S, 

Thanks for the prompt feedback.  Silly question but does DamnSmallLinux support support all of the standard software?  Would I have to do anything special to get the apps to work on a small distribution? Is DSL based on a specific distribution?

---

### Post by halitech on 2007-03-27
> **thecgmguy said:**
> Thanks for the prompt feedback halitech but that link didn't work... :(

wierd, works for me.

here is the list I get

1. AUSTRUMI
AUSTRUMI is a business card size (50MB) bootable live CD Linux distribution. It is based on Slackware Linux with initialisation scripts borrowed from the Blin project.

2. Damn Small Linux
Damn Small Linux is a business card size (50MB) Live CD Linux distribution. Despite its minuscule size it strives to have a functional and easy to use desktop. Damn Small Linux has a nearly complete desktop, including XMMS (MP3, and MPEG), FTP client, links-hacked web browser, spreadsheet, email, spellcheck (US English), a word-processor, three editors (Nedit, nVi, Zile [emacs clone]), Xpdf, Worker (file manager), Naim (AIM, ICQ, IRC), VNCviwer, SSH/SCP server and client, DHCP client, PPP, PPPoE, a web server, calculator, Fluxbox window manager, system monitoring apps, USB support, and soon it will have PCMCIA support as well. If you like Damn Small Linux you can install it on your hard drive. Because all the applications are small and light it makes a very good choice for older hardware.

3. DeLi Linux
DeLi Linux is a Linux distribution for old computers, from 486 to Pentium MMX 166 or so. It's focused on desktop usage. It includes email clients, a graphical Web browser, an office package with word processor and spreadsheet, etc. A full install, including XFree86 and development tools, needs no more than 300 MB of harddisk space.

4. Feather Linux
Feather Linux is a Linux distribution which runs completely off a CD or a USB pendrive and takes up under 128MB of space. It is a Knoppix remaster (based on Debian), and tries to include software which most people would use every day on their desktop.

5. Fluxbuntu Linux
Fluxbuntu is a light-weight, standards-compliant, Ubuntu-based Linux distribution featuring the Fluxbox window manager. The project's primary goal is to develop an operating system that would run on a wide range of mobile devices and computers, both low-end and high-end.

6. PapugLinux
PapugLinux is a minimal GNU/Linux live CD based on the Gentoo Linux distribution for x86 computers. The goal of PapugLinux is to provide a minimal but functional free operating system which can be run on most computers, from old systems with as little as 64 MB of memory to the latest powerful configurations.

7. Puppy Linux
Yes, Puppy Linux is yet another Linux distribution. What's different here is that Puppy is extraordinarily small, yet quite full featured. Puppy boots into a 64MB ramdisk, and that's it, the whole caboodle runs in RAM. Unlike live CD distributions that have to keep pulling stuff off the CD, Puppy in its entirety loads into RAM. This means that all applications start in the blink of an eye and respond to user input instantly. Puppy Linux has the ability to boot off a flash card or any USB memory device, CDROM, Zip disk or LS/120/240 Superdisk, floppy disks, internal hard drive. It can even use a multisession formatted CD-R/DVD-R to save everything back to the CD/DVD with no hard drive required at all!

8. SaxenOS
SaxenOS is a lightweight Slackware and Zenwalk-based distribution with the Xfce desktop. It is designed for older, low-specification computers.

9. TA-Linux
TA-Linux is a free Linux distribution that targets Linux power users. Its main goal is to have a small base installation that the end-users can expand to include the software they need. The secondary goal is to support as many different architectures as possible, at this time x86 is fully supported with Alpha, Sparc, PPC and PA-RISC around the corner. Extra software not included in the base is handled using a system resembling the *BSD ports system, called Collection, which handles installation, upgrading and dependencies. The primary way of installing new software is to download the source, compile and install it (totaly automatic). The user can also choose to install already built binary packages, also automaticaly using the Collection system.

10. VectorLinux
Vector Linux is a small, fast, Intel based Linux operating system for PC style computers. The creators of Vector Linux had a single credo: keep it simple, keep it small and let the end user decide what their operating system is going to be. What has evolved from this concept is perhaps the best little Linux operating system available anywhere. For the casual computer user you have a lightening fast desktop with graphical programs to handle your daily activities from web surfing, sending and receiving email, chatting on ICQ or IRC to running an ftp server. The power user will be pleased because all the tools are there to compile their own programs, use the system as a server or perhaps the gateway for their home or office computer network. Administrators will be equally as pleased because the small size and memory requirements of the operating system can be deployed on older machines maybe long forgotten.

---

### Post by mikegpc on 2007-03-27
I have ideas. You might not like them. First of all, for most Graphical installations of linux that i know of, you should have a minimum of 10 gigs of space on your hard drive.
Normally your swap would be double the size of the memory, in MB. However, in this case, you might want two gigs. 
If you laptop can handle the upgrade, get a 20 or 30 gig.
I don't recommend DSL. It's great if your starting out, but when your out in the field, stick with the latest issues of Native Installation Linux you can get.
I don't recommend overclocking your CPU, but you might just want to look for a second hand one with higher specs. Just so you get optimal operation.

---

### Post by lamalex on 2007-03-27
i can recommend both vector and fluxbuntu. fluxbuntu is easier depending how much linux skill you have. both are good choices. any distro will allow you to install all of the tools you need no problem

---

### Post by thecgmguy on 2007-03-27
> **Iamalex said:**
> i can recommend both vector and fluxbuntu. fluxbuntu is easier depending how much linux skill you have. both are good choices. any distro will allow you to install all of the tools you need no problem


Thanks Iamalex!

I'm really tempted to try fluxbuntu (I loved Ubuntu) but was a little concerned when I saw that it's just a "developmental release" right now.  Is it stable?

---

### Post by kerry_s on 2007-03-27
> **thecgmguy said:**
> Kerry_S, 

Thanks for the prompt feedback.  Silly question but does DamnSmallLinux support support all of the standard software?  Would I have to do anything special to get the apps to work on a small distribution? Is DSL based on a specific distribution?

It's live cd you can try it. DSL is based on debian.

---

### Post by tgalati4 on 2007-03-27
I believe DSL is based on Knoppix.  It works well on older hardware (for instance my HP Omnibook, 64MB, Pentium MMX 166MHz.  You can dress it up nicely.  It's fast on any hardware that it runs on.  Will run completely in RAM with 128 MB or more (which is really fast).  Uptime:  Months without a problem.  

Limited network tools, but you can always compile your favorite toolkit.

I remember seeing a Live CD of just Network tools, but I can't remember the distro.  

Definitely increase the RAM to 128 MB or more for decent firefox performance, otherwise you have to go with a slimmer browser without Java and flash support.

Also, get yourself a decent pcmcia network card.  I think you will find that USB (1.1) ethernet dongles will limit your throughput.  Afterall you want to measure network performance.  Also get a decent WiFi card (if you have two pcmcia slots).  That way you can sniff your wireless with Kismet at the same you are pinging your wired servers.

Good luck and let us know what you settled with.

---

### Post by houstonbofh on 2007-03-27
There is a better source than me for this.
[http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/](http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/)
That crazy man did this! [http://www.ubuntuforums.org/showthread.php?t=294292](http://www.ubuntuforums.org/showthread.php?t=294292)

I have used his tweaks on a 256 meg 650 and used full Ubuntu, and it is very usable.  Slow as death to install, but fine now!

---

