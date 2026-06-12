---
title: "12&quot; PowerBook G4 Overheating"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by rreusser on 2006-07-24
So I just installed Ubuntu (Dapper and Linux 2.6.15-23) yesterday and it's plenty enjoyable, but I was doing a bit of compiling yesterday and right after it finished, the computer shut down instantly.  I hadn't really been paying attention, but I checked and it was quite toasty.  It had cooled down by the time I booted OS X and downloaded TemperatureMonitor to check, but overheating seems to be the most likely cause.  I have no desire to write an infinite loop and test it again.  I've been searching the forums for similar problems, and my computer's response to the common solution is:

$ sudo modprobe therm_adt746x
Password:
FATAL: Error inserting therm_adt746x (/lib/modules/2.6.15-23-powerpc/kernel/drivers/macintosh/therm_adt746x.ko): No such device

And of course I don't have the /sys/devices/temperatures/ directory either.  FYI it's a 12" PowerBook G4 867 MHz, 384MB Ram, Ubuntu 6.06, Linux 2.6.15-23...  I'm sure I left something out.

I came across one answer that said the Linux on Aluminum Powerbooks with NVidia (circa Summer 2003) don't have support for any sort of temperature monitor.  Is this really the case?  If it is the case, then between that and no hardware graphics acceleration, no sleeping, no fan, sketchy wireless support I haven't gotten around to installing yet, and a whole iTunes library in AAC, it's hard to justify staying with Ubuntu...  Any suggestions?

Thanks in advance,
Rick

---

### Post by electricshoes on 2006-08-24
> **rreusser said:**
> 
FATAL: Error inserting therm_adt746x (/lib/modules/2.6.15-23-powerpc/kernel/drivers/macintosh/therm_adt746x.ko): No such device


 Did you get this figured out? I am having the same problem and have not found an answer to it.

---

### Post by APU on 2006-08-25
Interesting. On my PowerBook 12" 1.5 GHz ( PowerBook6,8 ) this seems to work. The fans are definitely running but i have not yet run a really demanding task on the Computer to check if it really overheats.

Modprobing the therm_adt746x module does not give an error too on this Powerbook! And it also has the NVidia Card.

By the way - I will get sleep (or better said hibernate) to work on this thing. There have been some successful attempts from a few people already. It will require patching and building an special kernel, but it is possible.

APU

---

### Post by electricshoes on 2006-08-25
Yeah, I have an 867 12" powerbook. I have heard from others that it may be a bug in the kernel. Im not sure if a recompile or update of the kernel would help.

I booted up the newest version of Gentoo for PPC and the fan kicked on after it booted but with a newer kernel. Going back to ubuntu, it dosnt. The powerbook will eventually lockup if running it for to long.

---

### Post by APU on 2006-08-25
You might be right. The 867 MHz Powerbook 12" used another NVidia card and most likely another chipset ast the later 1.3 and 1.5 GHz Versions. A kernel (oder kernel configuration) but could very likely be the case.

If you dare to, I would try to build a newer kernel (probably the latest 2.6.17.11) because it includes a lot of improvement for the hardware commonly used in powerbooks (current Broadcom drivers for example which have only been backportet into 2.6.15 by the Ubuntu team). I did not yet try this but I am planning to do so soon. And you are not afraid of building your own kernel since you are already familiar with Gentoo I guess.

APU

---

### Post by electricshoes on 2006-08-25
> **APU said:**
>  And you are not afraid of building your own kernel since you are already familiar with Gentoo I guess.


Alot of trial and error.. and more error.

---

### Post by tactus on 2006-08-26
> **APU said:**
> 
By the way - I will get sleep (or better said hibernate) to work on this thing. There have been some successful attempts from a few people already. It will require patching and building an special kernel, but it is possible.

APU

Oh, thanks for the update on the hibernate issue. There are some things that doesn't work right on the PowerBook 12"s but suspend/hibernate is something I can't live without.

Btw, Edgy Eft is using 2.6.17.x right now, wonder if we will see support for hibernate in *ubuntu 6.10 in october? (Or if it works in the knots right now? :) )

[Update]

Okey, I have nothing better to do, so I've started an upgrade to Edgy Eft and see if there is any news. And I just realized its a while since I last ran backup of my OS X partition. :shock:

---

### Post by APU on 2006-08-26
Please share your experiences with Edgy! I would really like to hear how it performs on a PowerBook.

---

### Post by mert on 2006-08-26
I was under the impression that lack of hibernation support was due to some kernel module or other needing to be unloaded prior to suspend_to_disk.  I'd like to get this working on my 1.3 Ghz 12" powerbook too.

As for overheating, mine runs hotter than it does when running OS X though the fan starts and stops under heavy loads.  When I've been running ubuntu and reboot into OSX the fan runs at top speed for a minute or two until it cools down.  

M

---

### Post by tactus on 2006-08-26
> **APU said:**
> Please share your experiences with Edgy! I would really like to hear how it performs on a PowerBook.

Yes, the upgrade went smooth as far as I can tell, but I don't have lilo in repository or on disk, so I haven't rebooted yet. The kernel 2.6.17 is there..

Do I have to download and burn the edgy knot image to add to repository or is there another way to get Lilo installed?

More later..

---

### Post by APU on 2006-08-26
Lilo wont really help much on a PowerBook because all PPC New World Macs (all machines with Open Firmware) use yaboot instead Lilo or Grub.

I also don´t really knwo how to go on with the update but i would think that there are already howtos available somewhere on the net.

---

### Post by tactus on 2006-08-26
Blah, I think I've spent to much time tinkering with my mac mini. Yaboot is there, working and everything. :p

Hibernate doesn't seem to work out of the box, but I haven't tested much either.

---

### Post by APU on 2006-08-26
> **mert said:**
> I was under the impression that lack of hibernation support was due to some kernel module or other needing to be unloaded prior to suspend_to_disk.  I'd like to get this working on my 1.3 Ghz 12" powerbook too.


Well this is an additional issue. If hibernate works then there will be problems with modules that are not (un)loaded correctly for sure. But right now at least my Powerbook does not even really try to resume. I can´t really say if this is due to problems in writing the RAM image to the harddrive or when the bootloader tries to locate/load this very image on the next boot. But this is something I really want to investigate next week.

BTW: In the changelog for the very last kernel (2.6.17.11) you can find the following information:

> Recently a patch was added for preliminary suspend/resume handling on
    !PPC_PMAC.  However, this broke both suspend and firewire on powerpc
    because it saves the pci state after the device has already been disabled.


I am not sure id this effects hibernate (suspend to disk) and not sleep (suspend to RAM) but hey....

---

### Post by Tobba25 on 2006-09-06
So how are we doing? I am thinking of installing ubuntu on my 12" pb 867, but is it worth it? I dont want any issues that I cannot work out, like shutdown because of overheating...

And how about wireless? And Automatix, can one use that?

---

### Post by thetravellor on 2006-09-19
I have already "dared" to build a 2.6.17.something kernel for ppc ubuntu, I cant recall which precise release it was now. 

I find the pb 12" runs much much hotter than Mac OSX. Eventually the fan kicks in full blast and stays on.

On the up side, my trackpad works one hell of a lot better and the startup splash screen sctually displays better.

I am trying valiantly without success to get the serialmonkey drivers for my ASUS wl167g stick to work. Thats why I dared to do this ;)

---

### Post by thetravellor on 2006-09-19
2.6.17.7

And the other issue, the sound was so loud on initial boot, I now keep it at 1/2 volume, or it breaks up.

---

### Post by thetravellor on 2006-09-19
I compiled adt746x into the kernel directly. (Tell me why I need a module if I know I need it?)

dmesg says:
adt746x: ADT7467 initializing
adt746x: Lowering max temperatures from 73, 80, 109 to 70, 50, 70

---

### Post by pauljwells on 2006-09-19
I have a 12" Powerbook 1GHz version. I do a fair bit of compiling and I did once get a fairly severe thermal shutdown - it looked like it had fried the hard drive! I took it to the Apple shop and had a bigger one fitted (wanted one anyway) but they said there was nothing wrong with the one that was in there and it had perhaps been something that took a while to reset??

Anyway, on mine the fans do run, and pretty damn fast too when compiling, so something is getting monitored.

I installed sensors-applet and it gves a nice readout of cpu and gpu temperatures and the fan speed n the gnome panel

---

