---
title: "Microsoft Virtual PC Display problem"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Ian505 on 2007-08-22
I want to try Ubuntu but I want to keep it in MS Virtual PC 07. I tried this with V 6.06 LTS but after the boot screen (which did not display the system checks, only the logo.) Ubuntu switched to 1600x600x8 SVGA display mode, which never happened when I once had Ubuntu installed on my machine and not on MSVPC. Does anybody have any idea why this happens? (It only happens at the login and desktop screen.)

[IMG]http://www.rsclans.net/UbuntuScreen.jpg[/IMG]
This is an actual screenshot of what the desktop looks when run in MSVPC.

Help is greatly appreciated.

-Ian

---

### Post by steve.horsley on 2007-08-22
The usual answer for problems like this is to change to a text console by pressing Ctrl-Alt-F1, logging in and issuing this command:
> sudo dpkg-reconfigure xserver-xorg
You should be able to accept the defaults until you get to the bit about which screen resolutions you want to use. When you've finished, restart X with this command:
> sudo /etc/init.d/gdm restart
I don't see that being in a virtual PC should change what you do if you have display resolution issues.

---

### Post by 3rdalbum on 2007-08-22
Being a Microsoft product, Virtual PC is not designed to run Linux distributions. This is a known bug in VPC.

You may want to try a better virtualisation solution for Windows such as Virtualbox or VMWare, as I know that these two products (Virtualbox is free) have no trouble with Linux as guest.

---

### Post by Ian505 on 2007-08-22
Okay, I just read one of the stickys and found a problem- I have a x600 card. I am going to try virtual box and see if that works and if not download the alternate version of Ubuntu and try that with the solution that steve gave me then try the sticky solution.

Thanks for helping- I will post my results.

-Ian

EDIT- I am going to download 7.04 just because. :-)

---

### Post by Ian505 on 2007-08-22
Okay, I have downloaded and installed virtual box... but when I try and create a new VM I dont know which OS type to select out of:

Other/Unknown
Linux 2.2
Linux 2.4
Linux 2.6
FreeBSD
OpenBSD

I really am a total novice at Linux so could someone please help me?

Thanks so much- If I get all my programs on linux I will be there to stay- thats for sure.

-Ian

---

### Post by Ian505 on 2007-08-22
> **Ian505 said:**
> Okay, I just read one of the stickys and found a problem- I have a x600 card. I am going to try virtual box and see if that works and if not download the alternate version of Ubuntu and try that with the solution that steve gave me then try the sticky solution.

Thanks for helping- I will post my results.

-Ian

EDIT- I am going to download 7.04 just because. :-)
> Okay, I have downloaded and installed virtual box... but when I try and create a new VM I dont know which OS type to select out of:

Other/Unknown
Linux 2.2
Linux 2.4
Linux 2.6
FreeBSD
OpenBSD

I really am a total novice at Linux so could someone please help me?

Thanks so much- If I get all my programs on linux I will be there to stay- thats for sure.

-Ian

Okay, I got everything working in VirtualBox and have 7.04 installed in a virtual hard drive using OS Type Linux 2.6

Thanks everyone for all your help.

(This thread is closeable.)

---

