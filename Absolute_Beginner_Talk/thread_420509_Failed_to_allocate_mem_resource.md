---
title: "Failed to allocate mem resource"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-04-23
During the startup of Ubuntu on my laptop, I notice this message on my screen for a sec, before the Ubuntu logo comes up with the status bar and I can see it if I switch to the console window with Ctrl-Alt-F1 while on the Gnome login window:



[     0.518800] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0

This makes no sense to me but it might to someone else.

---

### Post by Selage on 2007-05-21
Same thing here!

The numbers are different, but it end up doing nothing!

Any fixes for that?

Greetz

---

### Post by noorez on 2007-05-23
I havn't found any....could this be a problem with hardware incomatibility?

---

### Post by Selage on 2007-05-24
All i found out is when i replaced my Nvidia 7800 (PXI Express) with a Old PCi card, the problem is gone.

Maybe its a Bios thing, MSI-Express option or something like that...
Greetz

---

### Post by kiasanth on 2007-08-16
> **noorez said:**
> 
[     0.518800] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0

This makes no sense to me but it might to someone else.

It is failing to map the memory to a piece of your hardware, most likely a graphics card since it is at 0000:01:00.0 on your bus, not to mention it's trying to allocate 128Megs (20000 Hex)wich is a lot for most non-video card hardware

My guess is that you have an nVidia Graphics card, they are known for failing the first attempt at memory allocation during startup... this message is 99% of the time completely harmless as the OS tries again and if you don't get the message again then it succeeds. If you can use all the screenmodes and hardware acceleration then this message is not a problem at all.

---

### Post by [woodstock] on 2007-09-10
I would like to rivive this thread.
I have bought a new Laptop (Samsung X65 if it matters) and I get the same error message. The problem is that it doesn't go away and the Lattop freezes after this message occurs. This happens with all CD I have testet so far (Feity-Alternate, Gutsy-Dekstop, Gutsy-Alternate, both daily build and Tribe 5). The only Live-CD that will work is Knoppix. Unfortunately the system itself is rather old and I would like to use Ubuntu.

Even if I want to check for CD integrity this message appears and the system halts. I have tried various boot-parameters in literally any combination without success. The parameters I used were
> noapic
nolapic
pci=noacpi
acpi=off
pnpbios=false


I would appreciate any help on this, because I can't even install Ubuntu.

The hardware specs:
Core 2 Duo T7500
nvidia 9800 GS, 256 MB RAM
2 Gig RAM

(The rest should not matter)




One strange thing worth mentioning: I have a external HDD which I carry around with me to boot from various copmuters at my workplace. I can boot from that HDD and I can see that message form above blinking up for an instant. After that the boot process resumes as expected. (There are some other issues concering the laptops hardware, but it works in principle). I know that I could work around that i-will-not-boot-from-CD-problem using this external HDD, however I would like to have a clean installation of Gutsy on that laptop and I do not like to mess up my system that I use for my daily work (which is on that external HDD).

---

### Post by showe1966 on 2007-11-20
hi vis a vis the latest post, im writing this from my samsung x65.
I achieved this very simply by installing version 6.06 LTS from the cd on the website.

I tried to install v 7.10 , and see that memory allocation problem as described.

Interestingly enough, when i did "apt-get upgrade" the network card dissapeared.
i then had to re-install.
so so far, i did not manage to use "apt" to do anything !!!
i will post you more info. when i find out whaT HAPPENED.
best of luck,

steve

---

### Post by showe1966 on 2007-11-24
i am making a small amount of progress here on getting some of the problems sorted out in installing ubuntu on a samsung x65 laptop.

To summarize here are the problems:-

1. 7.10 will not install. The kernel panics during boot with a message "failed to allocate memory resource"
2. 6.06 installs ok.
If I update my system with apt, the network card dissappears.
The screen resolution is poor, and the wireless card is not detected.


The first problem I have been able to fix is the display resolution.

I just editted my "xorg.conf" file and changed the screen resolutions by adding the models 1680x1050 and 1280x1024 to those available, and the screen then works ok after a reload of x that is:-

sudo gedit /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24

	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

OK ! PARTY ON!
onto the next problem.
BTW how do i pass arguments to the kernel before boot like some of the following:-
pci=nommconf ?
can anyone tell me ??

---

### Post by overdrank on 2007-11-24
```
> **showe1966 said:**
> i am making a small amount of progress here on getting some of the problems sorted out in installing ubuntu on a samsung x65 laptop.

To summarize here are the problems:-

1. 7.10 will not install. The kernel panics during boot with a message "failed to allocate memory resource"
2. 6.06 installs ok.
If I update my system with apt, the network card dissappears.
The screen resolution is poor, and the wireless card is not detected.


The first problem I have been able to fix is the display resolution.

I just editted my "xorg.conf" file and changed the screen resolutions by adding the models 1680x1050 and 1280x1024 to those available, and the screen then works ok after a reload of x that is:-

sudo gedit /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24

	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

OK ! PARTY ON!
onto the next problem.
BTW how do i pass arguments to the kernel before boot like some of the following:-
pci=nommconf ?
can anyone tell me ??
```

Hi if you want to amend the kernel during boot you can press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and add pci=nommconf  and then hit enter and then  b to boot.  That will be temporary, if you want to do it permanent then you will have to edit your grub. ```
gksudo gedit /boot/grub/menu.lst
```
and add to the kernel there. This link may help with the grub
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
 Hope this helps. Good luck!

---

### Post by showe1966 on 2007-11-26
thanks a lot for that.
i will try if i get stuck.

anyway, i am making slow progress on these problems.
here is what i have discovered so far:-

1. I installed v6.06LTS from the desktop CD.
I have had a lot of luck with this version, and so far have not been able to upgrade to anything else.
I noticed that when i do a dmesg|more
I was getting a message about the number of processors being limited to one, not good considering it is an intel dual core processor (or some similar guff).
well i got to looking at the kernel-source dpkgs and noticed that the 386 kernel i had automatically been installed from the desktop cd does not include SMP support.

so, I downloaded the latest version of 2.6.15 kernel for 686, which does apparently support SMP, and low and behold the dual process was detected ! Yippeeeee !!

Oh ****, however, i soon noticed that the network card was not detected any more.
Well i havea work around for this in the form of a pcmcia network card that i plugged into the darn computer and that one worked.

by that time, i had f""ked up the install so badly i decied just to resinstall everything again for the 10,00000,00000 time.
The really incredible thing was this time, when i upgraded to the 686 kernel for version 2.6.15-29, both network cards were now detected.
I assume this must occur because i had my extra pcmcia network card installed which was in some what allowing the kernel to "see" the original internal network card.

So, now i have the screen resolution problem sorted out AND the network problem sorted out.

Remainging problems to fix are:-

1. If I upgrade to a more recent kernel, the system won't boot up - probably down to a problem of compatibility with the nvidiageforce 8600mGS.
Would probably need to compile a custom kernel to fix this problem 

2. The wireless card is not detected. I am going to try installing ndiswrapper to fix this one.
I will post any sucessful outcome here.

later !!!!!!

---

### Post by showe1966 on 2008-02-08
you can get round all these problems as follows:

install gutsy 7.10 from the alternate cd at the command line.

the command line install is a bit "old-school" but who cares as long as it works !!

---

### Post by jsaturno on 2008-03-06
Hi,

I have the same problem (PCI: Failed to allocate mem resource...)

But it gave me some other problems: Seconds later my computer freezes and i can't initiate ubuntu.
If i remove my graphics card there is no problem and ubuntu works perfectly.
I have ubuntu 7.10 installed on a Pentium D 2.8 GHz with nvidia 7300 graphics card. Dual boot: ubuntu + XP

---

### Post by jsaturno on 2008-03-31
Can anybody help me?

---

