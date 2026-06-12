---
title: "[SOLVED] Best virtualization: Ubuntu within Windows or Windows within Ubuntu?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-11-11
Hello,

After several attempts at running XP (and soon Vista) with VMWare and VirtualBox within Ubuntu, I'm now wondering if the reverse option could be a more appropriate solution. I would like your opinion on this. Either way, I want to virtualize an existing partition into the other (raw disk if you prefer).

**Virtual Ubuntu in Vista - Ultimate Flexibility**

Pros: all the drivers load, all the media play and I have several thousands Linux programs to choose from (Ubuntu) in a native directX friendly environment where Office 2007 runs fine (Vista).

Cons: is the security as good in Vista as it is in Ubuntu, even with programs like Norton, RegCleaner, etc. ? Will the ports be open or closed like in Ubuntu? What about permissions? 

**Virtual Vista in Ubuntu - Ultimate Security**

Pros: Compiz fest for everyone if the seamless mode works one day, best threat protection for Vista based programs thanks to Ubuntu hosting/craddling

Cons: no sound in Vista with VMWare and Vbox, no support for my webcam (MS VX-6000) for Skype, no 3D accel feature in Vista


Additional question: will I have enough memory with only 1Gb to run both systems?

---

### Post by Anzan on 2007-11-11
I ran Ubuntu in a VM in Vista. 3Gs of RAM were barely enough for Vista. Bluescreens etc etc. Ubuntu of course was fine.

I just run Ubuntu now.

---

### Post by magicman5421 on 2007-11-11
How does vista run by itself? laggy? my vista uses 800 meg of ram to run by itself, w/o any programs. Ubuntu needs relatively little ram, but not none. running it through vmware or the like increases the ram load on your comp too. Have you considered running xp instead of vista? ram problems immediately eliminated

---

### Post by veloce on 2007-11-11
Can't speak for vista, but wrt xp and ubuntu: 

I much prefer virtual xp running on ubuntu.  Key things for me:

- ubuntu manages memory better.
- ubuntu manages smp better.

My stripped down xp vm (no virus protection, nothing loaded except what I'm running) runs faster than my old xp installation.

Virtual ubuntu under xp was just too slow.  I hardly used it because it was too painful. 1gb was just not enough memory.

---

### Post by mkoehler on 2007-11-11
Quite simply, 1GB of memory will probably not allow you to do what you are suggesting.

However, in the case that you are willing to upgrade your machine in order to accommodate Vista and Ubuntu, you will want to run Ubuntu *within* Vista, hands down.  Vista and other MS operating systems are highly inflexible, and on linux, just the opposite is true.

Cheers!

---

### Post by veloce on 2007-11-11
> **mkoehler said:**
> Quite simply, 1GB of memory will probably not allow you to do what you are suggesting.

However, in the case that you are willing to upgrade your machine in order to accommodate Vista and Ubuntu, you will want to run Ubuntu *within* Vista, hands down.  Vista and other MS operating systems are highly inflexible, and on linux, just the opposite is true.

Cheers!

Well there you go, two completely opposite pieces of advice!

---

### Post by Colro on 2007-11-11
Your system doesn't have enough ram to support either, but sound works just fine in Virtualbox under Ubuntu. Just go to the settings for the machine you're booting, go to the audio section, enable it, and set the driver to "ALSA" (unless you know for a fact that you use another driver). This works just fine for me in 4 separate OS installs in Virtualbox.
Personally, I'd go with Ubuntu as the host and Windows as the virtual box, but it entirely depends what you're doing with the operating system. No one can make that choice but you.

A curious question, though: why do you absolutely need both? With a machine like that I'd either use Ubuntu (or, hell, probably a lighter weight distro like Slackware) or windows XP. Vista wouldn't even be on my list of possibilities with 1GB of ram, it's the most bloated OS I've seen yet.

---

### Post by the8thstar on 2007-11-11
Thanks guys! Another question: what if I set my flashdrive (4Gb) to use the Readyboost feature?

---

### Post by the8thstar on 2007-11-11
to **Colro**, here are my thoughts to answer your question"

1. Well, I've heard that Vista can be run with 1Gb of RAM, so I'll give it a try.
2. I just prefer Office 2007 over OpenOffice
3. I want the best of both worlds and loads of apps at my disposal

Ideally, I would prefer to run Vista within Ubuntu because of the security and the stability. But if I did that Vista would be crippled because it could not use the hardware properly. IMO hardware compatibility is THE  weakest link for Ubuntu.

So... if I want to use all the bells and whistles of Vista, I have to forget about security (ouch!) and run Ubuntu within it.

Another option could be to keep on dual booting, but I'd get bored waiting on the system.

The last option I'm thinking of is to virtualize the raw Ubuntu partition under Vista. This way I can still access Ubuntu through dual boot and I don't have to worry about the activation burden of Windows since there is none.

Problem is, I don't know how to do that! VirtualBox instructions on the matter are very puzzling. And I don't know about VMWare. 

What do you guys think?

---

### Post by He|iX on 2007-11-28
I have 4GB RAM in my Laptop and was wanting to try virtual ubuntu in vista ultimate.

has anyone tried this yet? any luck?

---

### Post by kpkeerthi on 2007-11-28
> **He|iX said:**
> I have 4GB RAM in my Laptop and was wanting to try virtual ubuntu in vista ultimate.

has anyone tried this yet? any luck?
Ubuntu ran just fine virtually on Vista Ultimate on my P-M 2.13 Ghz, 2 GB RAM.

---

### Post by Threbus5 on 2007-11-29
I tried three configurations on the same Gateway laptop:

(1) VMware server for Ubuntu 7.10 with a virtual Vista home premium, 
(2) a VMware server for Ubuntu 7.10 with a virtual Windows XP, and 
(3) a VMware server for Vista with a virtual Ubuntu 7.10.

The virtual Vista worked smoothly in Ubuntu at about normal speed.
The virtual XP on Ubuntu worked even better.
The virtual Ubuntu on Vista performed at less than half normal speed.

My choice consisted of installing a VMware server on Ubuntu and a virtual Windows XP.

Vista, Vista, go away.
Come again?
Not today!

And a very expensive piece of statistical analysis software provides the only reason that XP even exists on my machine.

---

### Post by the8thstar on 2008-03-16
It's been a few months since I opened this thread. Before I mark it as solved, I want to tell you what I decided to do with my machine and OSes (the currentconfig is written in my sig).

I upgraded from 1 to 2Gb of RAM to breathe a little better and Vista Home Premium ran like a horse.

However I was deeply bothered by the size of the Vista partition on my system, especially since it refused to shrink under 44Gb (my disk size is 74Gb). I removed it completely and reformatted some aspects of the hard drive, but I was able to save my /home partition while I installed Ubuntu 7.10 as the main OS.

Turned out I couldn't reinstall Vista afterwards. It had more than the recommended amount of space on its own partition but it wouldn't install because there was already an other OS there. Well, that did it for me... I installed it as my BitchOS in VirtualBox instead. Although I don't have the 3D support, Vista runs just fine with a 20Gb VDI disk file, 64Mb graphics and 1Gb of RAM. I keep the reins tight on and my computer is altogether running better thanks to this.

---

### Post by ghost_ryder35 on 2008-03-16
Congrats on being converted :)

---

### Post by the8thstar on 2008-04-19
lol Take a look at my signature... Looks like I can't make up my mind, now can I? The trick to reinstall Vista was to set the 'boot' flag to its partition with gparted to make it happy again.. The things you learn with Ubuntu!

---

