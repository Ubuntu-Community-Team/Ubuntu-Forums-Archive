---
title: "Laptop won't install Ubuntu"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-11-09
This might be a tricky one.

Having found the "AgentAV" trojan on my XP laptop and removed it,with AVG. I thought I had sorted my slow running system.  Unfortunatly it didn't and days of trying to find a reason has me baffled. Spyware programs, cwshredder and spybot,to name a few did not help. Desparatly, I tried reinstalling XP by using the laptop recovery disk, but even then my system continues to run slow and I'm unable to find the reason.  I am also have the "Turn of computer" window pop up every ten minutes without me having selecting it.

I thought now would be a good time to try Ubuntu on this laptop. 

So to begin with, I tried running the live CD. It ran and got as far as the desktop but took 35 minutes or more but the CD drive continued to operate all the time, even after 45 minutes. 

If I try and open an application the drop down window takes ten minutes to drop down and when I make a selection, the application I've selected never opens. I'm wondering if the XP trogen might still be in the computer and causing this problem?

The laptop spec is Pentium 4 512meg RAM 40 Gig HD. Laptop Samaung V25.

Your help to install ubuntu would be appreciated.

---

### Post by byenary on 2006-11-09
The specs are hight enough to run smoothly,
I suggest youve got a hardware issue, probably your Ram module...

---

### Post by a.v.l on 2006-11-09
Any ideas on how to resolve this RAM module issue?

---

### Post by fatneck on 2006-11-09
Which version of Ubuntu are you trying to install/run Live CD of?

My laptop struggled desperately with 6.06 for i386 and 64 bit, but both versions of 6.10 run perfectly. You won't want to concern yourself with the 64 bit versions for your Pentium of course.

But do what the other fella suggests and download memtest or something to check your RAM in windows.

---

### Post by byenary on 2006-11-09
I think ubuntu cd includes a memtest, when you're about to install ubuntu, you'll get this menu where you can choose to install or check the cd etcetera, one of the options is a memtest if remember well...

---

### Post by a.v.l on 2006-11-09
> **fatneck said:**
> Which version of Ubuntu are you trying to install/run Live CD of?

My laptop struggled desperately with 6.06 for i386 and 64 bit, but both versions of 6.10 run perfectly. You won't want to concern yourself with the 64 bit versions for your Pentium of course.

But do what the other fella suggests and download memtest or something to check your RAM in windows.


-----------------------------------

Trying to install Ubuntu 6.06

---

### Post by Bartender on 2006-11-09
Another option for memtest - might be easier to get the download on someone else's machine - is download [memtest]("http://www.memtest86.com/") independently, burn it to a CD, then run the test overnight.

---

### Post by jkvv_1973 on 2006-11-09
try cc cleaner for winxp (free)

or advanced system optimizer $$$???...

(its winxp issue I know)

this will clean your registry...

---

### Post by marx2k on 2006-11-09
The LiveCD has memtest+86 as part of its' boot menu. I would suggest running that overnight at least to check your RAM

---

### Post by a.v.l on 2006-11-10
> **jkvv_1973 said:**
> try cc cleaner for winxp (free)

or advanced system optimizer $$$???...

(its winxp issue I know)

this will clean your registry...


Many thanks, cc cleaner seems to have done the trick. XP is working again at normal speed.  

Haven't tried to install Ubuntu again as I've realised the 512meg RAM I quoted, is infact only 256meg. Possibly the reason why the Ubunty installation struggled. As an exercise I installed "Damn small linux" ( only 49mb) and that works fine.  Is there something in between Ubuntu and DSL?  

Perhaps the real solution is to increase the RAM, How easy is this to obtain and fit to a samsung V25 laptop?

---

### Post by Velotix on 2006-11-10
> Haven't tried to install Ubuntu again as I've realised the 512meg RAM I quoted, is infact only 256meg. Possibly the reason why the Ubunty installation struggled. As an exercise I installed "Damn small linux" ( only 49mb) and that works fine. Is there something in between Ubuntu and DSL?

Linux is designed to be heavily scalable to completely different processor speeds and hardware configurations, so your options are naturally many and diverse.

Xubuntu is the typical solution for running Ubuntu on a PC with relatively low RAM, and is an official Ubuntu release, but if Xubuntu is still too slow for your liking there are faster options, such as FluxBox. You would need to acquire FluxBox manually once X/Ubuntu is installed, however. Definitely try Xubuntu first and see how you fare. Personally I find it a little too awkward, which is why I'm trying out Kubuntu as well - all the Ubuntu variants are based on the same core, so all you need to change is the desktop environment to get a change in performance. ^^

---

### Post by Bartender on 2006-11-10
I went to [Kingston's]("http://www.kingston.com/") website, typed "Samsung" into the Search box on the right, then found "V25" on the next page, but it brought up several different models.  Check it out, see what you come up with.  You'll need the exact model# from your lappy.
Once you know the exact Kingston part number, maybe you can find it on Newegg or find similar RAM modules from other vendors.  If it's not horribly expensive, you'll notice a nice performance jump if you can double that RAM.  Of course a gig would be even nicer!

---

### Post by a.v.l on 2006-11-12
> **Velotix said:**
> Linux is designed to be heavily scalable to completely different processor speeds and hardware configurations, so your options are naturally many and diverse.

Xubuntu is the typical solution for running Ubuntu on a PC with relatively low RAM, and is an official Ubuntu release, but if Xubuntu is still too slow for your liking there are faster options, such as FluxBox. You would need to acquire FluxBox manually once X/Ubuntu is installed, however. Definitely try Xubuntu first and see how you fare. Personally I find it a little too awkward, which is why I'm trying out Kubuntu as well - all the Ubuntu variants are based on the same core, so all you need to change is the desktop environment to get a change in performance. ^^

I'm begining to struggle for answers now, having tried Xubuntu today and once again failed to run the live CD on my Samsung V25 laptop.  Running the CD on my desktop machine confirmed the downloaded CD was ok.  XP works fine on this laptop as does Damn small Linux.  I'm confused why if XP works, Ubuntu, Kubuntu or Xubuntu doesn't?

---

### Post by Velotix on 2006-11-14
I've heard that internal conflicts within Intel have resulted in Intel Centrino laptops being designed in such a way as to be hostile to Linux on purpose, which is ironic because Linux was, and still is, primarily for Intel-compatible processors and there are many Intel engineers who actively contribute to Linux.

That doesn't mean it's impossible, but it'll probably be difficult. :/

You might want to try the Alternate CD as well - I hear they're better suited for installing to laptops. Unfortunately you won't be able to test the system that way until you've installed it, and the Alternate CD installer isn't anywhere near as intuitive.

---

### Post by ReaderRat on 2006-11-14
> Perhaps the real solution is to increase the RAM, How easy is this to obtain and fit to a samsung V25 laptop?
For Your Infomation (This may not be for the exact computer model - ballpark)
**[http://www.offtek.co.uk/product.php?manuname=Samsung&maincat=1&subcat=1&model=V25%20cXTD%202000&source=Kelkoo1](http://www.offtek.co.uk/product.php?manuname=Samsung&maincat=1&subcat=1&model=V25%20cXTD%202000&source=Kelkoo1)**

---

### Post by robgill on 2006-11-14
Try downloading and installing from the alternate install cd for 6.06.  It's not as pretty while installing, but it has the same output as the live cd.  The "live" cd requires a lot of RAM to install, but once it's installed, 256 Mb RAM should be enough for ubuntu.

---

### Post by JayTee on 2006-11-14
With 256MB of RAM you should be at least able to install Xubuntu. I think there are quite a few Ubuntu Dapper users out there that have 256MB of RAM on their systems also. The problem is probably in hardware detection for the chipset on your laptop's motherboard. I'd try what one of the other posters recommended, using the Alternate CD. It's all text based, not GUI so it requires a bit more work but it may get around your problem. One thing I have noticed running XP on many computers at work with 256MB of RAM and a P3 or P4 cpu between 1GHZ and 3.4GHZ is that bumping the RAM up to 512MB gives you a significant performance increase. At 256MB there's just enough to run XP with a program or two but it can become very sluggish, lots of swapping and your hard drive gets fragmented faster.

---

### Post by nickpaton on 2006-11-14
Speeding up Ubuntu Dapper required an addition to the Grub menu.
Open up Grub menu list in a Terminal ignoring error messages:

```
 gksudo gedit /boot/grub/menu.lst
```

Scroll down to the top Kernel listed and against "kernel" line add at the end  add:

```
noapic nolapic
```

My lines (for Edgy - but similar for Dapper) looks like:

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash vga=791 noapic nolapic
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

The vga791 gives a 1024x768 text splash size and is optional.

Save and quit.

---

### Post by a.v.l on 2007-06-23
Trying to install Ubuntu Dapper on a Samsung V25 laptop fitted with 256mb's of memory failed miserably for me, but I was able to install Xubuntu instead.  This worked when using the "safe graphic mode" option, but was a little slow in use.

I've since upgraded the memory in this laptop to 512mb's and now I've been able to install Dapper without a problem, although I believe it is working slower than  the XP system it dual boots with. I mention this only as an update for those who may have similar problems with this laptop in the future.

---

