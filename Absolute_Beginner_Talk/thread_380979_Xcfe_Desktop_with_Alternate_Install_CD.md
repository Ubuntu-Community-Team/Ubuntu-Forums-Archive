---
title: "Xcfe Desktop with Alternate Install CD?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by stroke11 on 2007-03-10
I have an old Dell XPS 333 with a Pentium II (333 MHz) with 128 MB of RAM and a 40 GB 7200 rpm IDE hard drive.  I tried installing Xubuntu 6.10 (Edgy Eft) Desktop CD but it was hanging up.  I then tried the Xubuntu 6.10 PC (Intel x86) alternate install CD.  That seemed to work much better, but I was hanging up at 85% of the installation.  So, I tried installing with the noapic and nolapic options.  That worked.  I not have Xubuntu installed, but it is booting only into the command-line mode.  I cannot figure out how to get the Xfce desktop running or determine if it's even installed.  Here are my questions:
- Is Xcfe installed automatically with the alternate install?  
- If so, how do I start it?  
- If not, can I run it on such an old machine?  
- If so, do I need to download load it and make it from scratch?
Any help or suggestions would be appreciated.  Thank you.

---

### Post by pveith on 2007-03-10
No Xcfe is not installed by default. I would sugget doing a serer install without any aditional packages and then login in the installed system and do a 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xubuntu-destop
```

This should install all needed packages. 

After installation just do a 
```
sudo invoke-rc.d gdm restart

```

And log in your xubuntu Desktop.

This only works if the system has internet access, otherwise an ubuntu dvd might help.

---

### Post by stroke11 on 2007-03-11
pveith,

Thanks for the instructions.  They worked great, and I'm up and running!

                          stroke11

---

### Post by petroleumjelliffe on 2007-03-11
I also have an old Dell with 128MB ram.  I installed ubuntu alternate but GNOME was still running kind of slow, so I did the xubuntu-desktop install.

XFCE runs faster, for sure.  I was wondering if this is the same as installing xubuntu from scratch.  Is GNOME still running just in case I want to switch back?  The system monitor shows some processes with the word GNOME in them.

---

### Post by kcallison on 2007-08-23
I have an old Dell GX-1 (Pentium II 233) I tried installing Xubuntu on.  The Live CD didn't work.  I used an alternate CD, installed the command line version of Ubuntu, then added the Xubuntu desktop with your instuctions.  It is working great.  

Thanks.

---

### Post by chrome307 on 2007-08-23
Is this possible to carry out with a GNOME desktop as well?

What I wanted to do was have a minimal install of Feisty Fawn and a GNOME desktop ..... would I need just to use the Mini.ISO to do this ?

---

### Post by pveith on 2007-08-24
Hi,

i really don't know how to make Gnome that small (8MB is probably out of reach). But there is a smaller gnome version in the ubuntu repos: the default gnome desktop (Packagename: gnome-desktop-environment). But again there are a lot of packages in there, which you probably don't want.
For installation i would recommand the ubuntu server install, as this does a very minimal install. On top of it just install "gnome-desktop-environment". 

Hope that helps someone, somewhere... :)

(Just as a reminder OpenOffice alone is substancially more than 8MB. The language-pack alone is 8MB! Even the kernel-image is 80MB.)

---

### Post by TeaSwigger on 2007-08-24
> **stroke11 said:**
> pveith,

Thanks for the instructions.  They worked great, and I'm up and running!

                          stroke11

Enjoy :) Just as a note which you may know already, you may want to try fluxbox. You can install that from the repositories while you're in Xubuntu, then on reboot pick fluxbox, which will be listed as a different "session." Of course you give some things up, but is even faster than Xfce, about as light as it gets while still being a well featured window manager. It may be beneficial on the PII there. You can still keep your Xubuntu's Xfce handy for when/if you want to use it instead. A nice setup, IMH.

---

