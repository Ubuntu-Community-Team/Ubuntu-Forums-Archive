---
title: "Windows XP RAM limitation"
date: 2012-02-21
forum: Any Other OS
---

### Post by tech291083 on 2012-02-21
Hi,

Does Windows XP OS does not support more than 8 GB of DDR2/DDR3 RAM as a technical limitation or there is more to it? I have read on the net that it does not show full 4 GB of DDR3 RAM despite it being installed, rather it shows less than 4 GB. Please help me clear my doubts. Thanks.

---

### Post by 3rdalbum on 2012-02-21
> **tech291083 said:**
> Hi,

Does Windows XP OS does not support more than 8 GB of DDR2/DDR3 RAM as a technical limitation or there is more to it? I have read on the net that it does not show full 4 GB of DDR3 RAM despite it being installed, rather it shows less than 4 GB. Please help me clear my doubts. Thanks.

No 32-bit operating system will be able to address more than 4 GiB of RAM, and as some of your computer's onboard devices will need to address some of their own RAM, you will be left with somewhat less than 4 GiB.

This is true for Windows XP 32-bit.

I don't know if Windows XP 64-bit will support more than 8 GiB or whether Microsoft has artificially limited it to that number to prevent server admins from using XP on big iron servers.

However, if you use Ubuntu 64-bit (or Ubuntu 32-bit with the PAE kernel installed to bring the memory space up to 36-bits) you will be able to address much more than 8 GiB of RAM.

I would wonder what you are doing that:

a. Can be done well on Windows XP, and
b. Requires more than 8 GiB of RAM.

---

### Post by tech291083 on 2012-02-21
> **3rdalbum said:**
> No 32-bit operating system will be able to address more than 4 GiB of RAM, and as some of your computer's onboard devices will need to address some of their own RAM, you will be left with somewhat less than 4 GiB.

This is true for Windows XP 32-bit.



Thanks for the reply. I got what you mean now. I was thinking of upgrading RAM from the current 2 GB DDR3 to 4 GB for Win XP Pro edition on my pc.  So even if one installs more than 4 GB or RAM , Win XP will not be able to use it, right? 4 GB should be the max limit for 32 bit version of the same. Thanks.

---

### Post by 3rdalbum on 2012-02-21
That's correct; it'll be able to use something like 3.3 GiB of RAM.

Also, Windows XP was programmed with the assumption that people would have low amounts of memory, so some of the things it does are not a good use of memory. If you have 4 GiB of RAM for instance, Windows XP will reserve everything over the 2 GiB mark for itself and probably never use most of that reserved block. Very wasteful. It's probably not worth putting in the extra 2 GiB unless you're moving to a later Windows; most of the time you won't even fill 2 GiB of RAM in Ubuntu.

---

### Post by tech291083 on 2012-02-21
Thanks again for the explaination, it was useful indeed. In order to get most of the 4 GB RAM that I have already bought, I will follow your advice and install Win 7 instead.  I hope that Win 7 with 4 GB will show visible speed changes. 

I am also going to dual boot this Win 7 with Ubuntu 11 and again I hope that Ubuntu will make the most of this 4 GB of RAM (not sure how much though) and I will be able to see my pc running smooth. 

Thanks.

---

### Post by tech291083 on 2012-02-21
> **3rdalbum said:**
> 
It's probably not worth putting in the extra 2 GiB unless you're moving to a later Windows; most of the time you won't even fill 2 GiB of RAM in Ubuntu.

Just one more query, do you mean that Ubuntu 32 bit will also does not address more than 4 GB or RAM?  If so, then what should I do to make the most of 4 GB RAM that I already have? Here is what I have just found on the net, which is written by someone in my opinion wanting to use the full of 4 GB RAM he has.

[http://barkahrezasyah.wordpress.com/2011/10/19/enabling-my-4gb-memory-in-ubuntu-11-10/](http://barkahrezasyah.wordpress.com/2011/10/19/enabling-my-4gb-memory-in-ubuntu-11-10/)

```

[I]$ sudo apt-get update
$ sudo apt-get install linux-headers-server linux-image-server linux-server[/I]

```

Thanks.

---

### Post by mips on 2012-02-21
> **3rdalbum said:**
> 
I don't know if Windows XP 64-bit will support more than 8 GiB or whether Microsoft has artificially limited it to that number to prevent server admins from using XP on big iron servers.

Windows XP x64 is **limited to 128 GB of physical memory** and **8 terabytes of virtual memory** per process. 
Driver support for this OS is pathetic though so I don't think many people will use it.

---

### Post by mips on 2012-02-21
> **tech291083 said:**
> Just one more query, do you mean that Ubuntu 32 bit will also does not address more than 4 GB or RAM?  If so, then what should I do to make the most of 4 GB RAM that I already have? Here is what I have just found on the net, which is written by someone in my opinion wanting to use the full of 4 GB RAM he has.

You can use 32-bit Ubuntu with [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") to address the full 4GB of RAM.

Ubuntu [COLOR="red"]**9.04**[/COLOR] [COLOR="Red"]and earlier[/COLOR]:
```
$ sudo apt-get update
$ sudo sudo apt-get install linux-headers-server linux-image-server linux-server
sudo reboot

```

Ubuntu **[COLOR="Red"]9.10[/COLOR]** [COLOR="red"]and later[/COLOR]:
```
$ sudo apt-get update
$ sudo apt-get install linux-generic-pae linux-headers-generic-pae
sudo reboot
```

**But why don't you just run the 64-bit version?** In this day and age there is no reason not to use the 64-bit version, I've been running 64-bit linux for years now and there are no issues.



.

---

### Post by Perkins on 2012-02-21
The "No 32 bit operating system can support more than 4 gig of memory" line is a piece of utter BS put out there by Microsoft to get you to upgrade to 64 bit.  XP supported > 4GB of ram prior to Service Pack 1, when they disabled it for "stability reasons."  (No, they never bothered to explain just how using PAE made anything unstable...)  Support for > 4GB is still a part of XP and later kernels, but it is disabled by their licensing scheme, and no, they won't sell you a license to use more.  They did, at one point, sell licenses to use > 4GB of RAM on some of their 32-bit server platforms.  I am not certain if that is still the case or not.

Any 32 bit processor which supports PAE (which happens to be virtually all of them, I have yet to find an exception still in use anywhere) will be capable of using more than 4 gig of memory.  The ability to address more memory than the bits of the processor would seem to allow has been an integral part of computer design since...  Well, since we started building the darn things...

For what it's worth though, the Intel line newer than the Pentium D (which includes all the Core 2 Duo, Trio, Quad variants) is virtually all 64 bit.  They were originally sold with 32 bit operating systems since that was what was cheaply available and not full of bugs, so everyone seems to assume that that's what they are, but you can install a 64-bit OS just fine and squeeze quite a bit more life out of them.

---

### Post by mips on 2012-02-21
> **Perkins said:**
> XP supported > 4GB of ram prior to Service Pack 1, when they disabled it for "stability reasons."  (No, they never bothered to explain just how using PAE made anything unstable...)

I don't think it was PAE making things unstable but 3rd party drivers that were hard coded to function within a certain address space. The problem was not MS from what I can tell but driver suppliers.

I think PAE can still be enabled via the boot.ini file.

Anyway, some casual reading [http://msdn.microsoft.com/en-us/windows/hardware/gg487503](http://msdn.microsoft.com/en-us/windows/hardware/gg487503)

---

### Post by Starks on 2012-02-21
The 4GB limit for 32-bit also includes VRAM of your video card

---

### Post by Perkins on 2012-02-21
[http://www.geoffchappell.com/notes/windows/license/memory.htm](http://www.geoffchappell.com/notes/windows/license/memory.htm)


PAE is already enabled by default because they use it for their DEP algorithms.  Logically any driver coded to understand PAE addressing should be good with it, regardless of how much memory is actually present, while drivers that are incompatible with it will be incompatible even if only a lesser amount of memory is being used.  Plus drivers that need to touch the memory directly are generally the kinds of drivers that both Microsoft and the hardware manufacturer test thoroughly.  Plus they support >4Gb on Windows 2000.  Which is older than XP.  Disabling use of > 4Gb by default for paranoia reasons so that the average user's system will just work out of the box I could understand.  Locking it out so that nobody can use it, even at their own risk, is fairly obviously a contrivance to sell 64-bit versions of their operating systems.  Especially when they phrase things to make it sound like a 32-bit limitation and not a Windows limitation.

---

### Post by mister_playboy on 2012-02-27
In looking at a 64-bit Windows install, you may find 98% of the programs are actually 32-bit.  Even core system stuff like IE will run as 32-bit by default.

It will be many years before they really transition over, and even then it will probably only be forced by MS releasing a 64-bit only OS.

---

### Post by leclerc65 on 2012-02-27
> I've been running 64-bit linux for years now and there are no issues.
I planned to go 64-bit with Ubuntu 12.04. Can you tell me whether a 64-bit distro can run 'virtualboxed' 32-bit XP ?
The last and only time I tried 64-bit is 9.04 (I think), Truecrypt didn't even open my truecrypt volume.:(

---

### Post by Perkins on 2012-02-27
Theoretically, as long as the processor supports the operating system you're trying to install as a guest, it should work just fine to install a 32 bit guest inside a 64 bit OS.  It doesn't work the other way around though.

---

### Post by CharlesA on 2012-02-27
> **Perkins said:**
> Theoretically, as long as the processor supports the operating system you're trying to install as a guest, it should work just fine to install a 32 bit guest inside a 64 bit OS.  It doesn't work the other way around though.
Installing a 64-bit guest on a 32-bit host only works if you have hardware virtualization enabled in the BIOS and your CPU supports it.

I've never tested it personally because I only run 64-bit OSes.

---

### Post by Perkins on 2012-02-27
I have a 64 bit processor with hardware virtualization running a 32 bit os, and virtualbox at least won't boot a 64 bit kernel in it.  Of course, I'm a few versions back on virtualbox, so that could have been updated.

Some other VM program might do it though.

---

