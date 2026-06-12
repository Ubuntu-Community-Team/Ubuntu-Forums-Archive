---
title: "Dell Dimension 8100 GNOME is REALLY SLOW"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2007-03-08
Hey everybody,
My cousin moved to Georgia which isn't close at all to where I live.  He recently got a huge huge windows virus that completely prevented his computer from booting up.  He couldn't find the XP disk so I convinced him that he should use Ubuntu.  He has a Dell Dimension 8100 with a P4 1.4 Ghz and 384 MB RAM.  So we installed with the alternate cd because the Desktop CD was way too sluggish for us to install with.  After the install, boot-up takes 30 minutes and before X starts up this error shows up and takes 15 minutes to go away:

17179569 SMP mptable: bad signature [0x0]!
17179569 BIOS bug, MP table errors detected!
17179569 ...disabling SMP support (tell your hw vendor).

something like that shows up it's either that or

this:

[4294667.296000] SMP mptable: null local APIC address!
[4294667.296000] BIOS bug, MP table errors detected...
[4294667.296000] diasabling SMP support. (Tell your hw vendor)

(my cousin didn't explain it well)

Nevertheless,

X loaded up and so did gnome but gnome is so so sluggish that it feels that it doesn't have any RAM.  But I typed ```
free
``` into the command prompt and there was at least 100MB of RAM available.  What can I do to get this computer to work at a reasonable speed like it did when it had windows?  Also gnome is slow sluggish that it took 15 minutes to load firefox.  It is rediculous.  Should I try maybe xubuntu?  Or is the problem related to the SMP error?

---

### Post by youthforlinux on 2007-03-08
anyone????

---

### Post by the_darkside_986 on 2007-03-08
Sounds like something is wrong with the hardware. But yeah, try Xubuntu. XFCE desktop runs faster than WinXP on my old 300 Mhz celeron w/ 128 MB of RAM system.

---

### Post by K.Mandla on 2007-03-08
It probably is related to the SMP error. If it's possible, have him check dmesg or the kernel logs. I think errors at that level might be showing up there.

By the way, that *free -m* command in the live environment might be a little misleading; I believe it carves out part of the memory to run the live desktop, and so the actual amount free might be different.

The only way to tell if things are going to improve is to do a full install. If it's possible, see if he can try different versions (I don't think you said if it was 6.10 or 6.06.1). Xubuntu is generally considered to be less stressful on system requirements, but I don't know that it's necessarily true in every case.

---

### Post by youthforlinux on 2007-03-08
Yeah I got him to configure ndiswrapper via command line and just got the internet to work.
Do you think that it could be a video card or BIOS problem????

Also if xubuntu is too slow, what should I do?

Also I already installed ubuntu onto the hard drive and then used the free command.
He is running edgy currently and is it possible that dapper would work better?

---

### Post by Sefrin on 2007-03-08
> **the_darkside_986 said:**
> Sounds like something is wrong with the hardware.

Does anyone know of a diagnostic tool that can be used to check for this?  Hardware would be my first concern as well.

---

### Post by K.Mandla on 2007-03-08
> **youthforlinux said:**
> Yeah I got him to configure ndiswrapper via command line and just got the internet to work.
Do you think that it could be a video card or BIOS problem????

Also if xubuntu is too slow, what should I do?

Also I already installed ubuntu onto the hard drive and then used the free command.
He is running edgy currently and is it possible that dapper would work better?
It's always worth double-checking the BIOS settings, just to make sure things are kosher. Some BIOS settings can enable features that might interfere. I had a P4 desktop machine once that wouldn't boot until I disabled some of the legacy hardware compatibility settings in the BIOS. Every machine is going to be different, so I can't suggest what to use, but don't spend forever looking for something either. If it doesn't jump out at you, don't sweat it. (You might also try to reset them to the default and see if that improves things. Not every BIOS will do that.)

Think about doing a dual boot or a full installation before worrying about Xubuntu being too slow. Remember that everything runs off the CDROM in that live environment, so the speed of the drive and the access time and the data transfer rates all make the live environment a mind-numbing experience. If he likes what he sees and he's willing to give it a try, have him do a full installation and then worry about speed and performance after it's fully working. You have a thousand times more options then.

In general, Dapper is more reliable, although Edgy is still an improvement and has more newer features. I would probably start with Dapper in this case, and use Edgy if he has hardware that would benefit from the change. I'm guessing an 8100 wouldn't need much that Edgy offers, unless you can give some system stats that show otherwise. ;)

As an added thought, you might want to see if there's anything on that machine that needs taken off, while he's playing with the live CD. It's possible that he might be able to salvage files off his Windows installation before jumping to Ubuntu.

---

### Post by farrard on 2007-03-08
From the errors you posted, it looks like you got a virus in the BIOS.  Try downloading a BIOS upgrade from Dell on another PC, then follow Dell's instructions for installtion.

---

### Post by youthforlinux on 2007-03-08
1st: We already installed ubuntu to his computer and it is sluggish.

2nd: to install a bios update wouldn't we need windows

---

### Post by K.Mandla on 2007-03-08
I think you would need Windows to create a BIOS upgrade disk, but if it will boot from a floppy (or a USB, I guess) it should work independently of the operating system.

By the way, did you look in /var/log/kern.log? Are there any error messages in there?

---

### Post by youthforlinux on 2007-03-08
What about something like acpi=off nosmp notsc nolapic pci=noacpi,route-irq????

---

### Post by K.Mandla on 2007-03-08
:D Those could work. Did you try them yet?

---

### Post by youthforlinux on 2007-03-08
No but I flashed the BIOS and the SMP error went away.  The computer is now only a little faster.  The computer has a P4 at 1.4Ghz and 384 RAM and is running really slowly still.  My ubuntu box with feisty is a P4 1.6Ghz with 512MB RAM and runs really fast!!!!

---

### Post by youthforlinux on 2007-03-09
However, then I edited menu.lst and put in the extra parameters mentioned above.  Boot up was really fast, however, the computer is still running very slowly and it takes 15 minutes after the initial boot up in order for gdm to come up.

---

### Post by youthforlinux on 2007-03-09
I'm thinking of getting him to use xubuntu or kubuntu dapper.  Is that a good idea?

---

### Post by youthforlinux on 2007-03-13
The dapper cd wouldn't even boot properly...um
do you think that I should try another distro...I was thinking either Fedora or OpenSuse

---

### Post by theDaveTheRave on 2007-03-13
I've installed both a SuSe and a Ubuntu recently and I can only say that the SuSe install is much more time consuming.

I would recomend a very [SIZE="5"]large[/SIZE] glass of your favourite tipple.

Admitedly I was intalling it onto a rather old machine, but it still took me nearly 2 days to get everthing working in a fashion that made it fully utilisable.

I would also mention that I occasionally have go-slows on my ubuntu system, and I'm yet to figure out exactly why. When I do a < top > to see if any of the processes are using all of the memore / CPU there seems to be plenty of available resources, but the disk is being accesses in a major fashion (it is almost as noisy as my dogs snoring... which is very loud :rolleyes: ).

Anyway get your friend to keep perservering, it will be worth while.

Good luck to you both.

DaveM

---

### Post by youthforlinux on 2007-03-13
What about fedora????

of Mandriva????

I've used these a little bit.

The real problem is that it takes so rediculously long to boot into ubuntu it isn't even worth running the top command.

---

### Post by tck on 2007-03-16
I am having the EXACT same problem on my Inspiron 1300 : driving me crazy

noisey cd and GDM takes YONKS to kick in and doesn't even work

what the hell is wrong with it :(

---

### Post by jarviw on 2007-03-18
I am using a P3 with 512 MB RAM running ubuntu edgy,  it's slower than running dapper, but it's reasonably usable for just everyday stuff.

I think you have some real hardware setting issue there... in which case, I don't think Fedora or openSUSE would be any better for you.  my experience is that ubuntu 6.10 has the best out-of-the-box hardware support.  not perfect, but you have a much better bet for it.

you should try booting in verbose mode and see what steps it slows down/stops at.


good luck!

---

### Post by freebird54 on 2007-03-18
oops - missed further pages.  Ignore...

---

