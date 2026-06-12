---
title: "Installation: Strange"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by tbresson on 2005-07-11
I know this is far fetched, but I'll try anyway.

I recently decided to reinstall my Ubuntu box. I've changed nothing hardware-like but somehow I'm not able to install Ubuntu anymore. After install when it's setting things up somekind of infinate loop occurs and the pc locks with a kernel panic. The error is not always the same. 

I checked the harddrive for corrupt sectors and such, I did a memory test for over 4 hours and I tried powermax to check the disk. I also tried removing some hardware, like my DVD burner and one of my network interfaces. Still it won't install properly.

Here's the strange thing (besides that it worked fine 1 week ago with the same hardware); when I install Ubuntu as server, there are no problems and there are no problems when running the LIVE CD either.

I tried google on the error messages but didn't find anything useful except a post somewhere about trying to edit the boot and do acpi=off or something like that. I havn't tried that yet though.

I'm using the original CD I got in the mail ..

Any ideas what to try or where to look for error logs or anything useful?

---

### Post by brim4brim on 2005-07-11
[QUOTE=tbresson]I know this is far fetched, but I'll try anyway.

I recently decided to reinstall my Ubuntu box. I've changed nothing hardware-like but somehow I'm not able to install Ubuntu anymore. After install when it's setting things up somekind of infinate loop occurs and the pc locks with a kernel panic. The error is not always the same. 

I checked the harddrive for corrupt sectors and such, I did a memory test for over 4 hours and I tried powermax to check the disk. I also tried removing some hardware, like my DVD burner and one of my network interfaces. Still it won't install properly.

Here's the strange thing (besides that it worked fine 1 week ago with the same hardware); when I install Ubuntu as server, there are no problems and there are no problems when running the LIVE CD either.

I tried google on the error messages but didn't find anything useful except a post somewhere about trying to edit the boot and do acpi=off or something like that. I havn't tried that yet though.

I'm using the original CD I got in the mail ..

Any ideas what to try or where to look for error logs or anything useful?[/QUOTE]
 Could it just be a bad scratch or something on the CD??  Very weird that it works as Live CD but won't install and that the problem is new like this with no change else could it be a loose connection inside the laptop.   Happened on a friends Compaq with windows.  All sorts of weird as* errors when his hard drive cable was slightly loose but windows could still detect it was there just had problems using it.

---

### Post by tbresson on 2005-07-11
The boot partition is actually also an windows 2003 server aswell and there's nothing wrong in windows... of course there has been rumours about that linux is more sensitive to errors ... but I'll try and disconnect the harddrive cable and reconnect it.. it might help. Also, I did actually try a different medium. I have a copy on a CD I burned (got the ISO off the net) and that medium has worked before.

Maybe it's the heatwave that is hitting Denmark right now...

---

### Post by tbresson on 2005-07-12
I just tried installing Kubuntu instead... and there was no problem at all. It ran as it was supposed to. After installing Ubuntu more than 15 times and getting errors for unknown reason I guess I'll just stick to the KDE interface instead ..

Weird though.

I might try and install without the internet plugged in on the box.. maybe it's better to isolate the install to what's on the CD only. It used to work ...

---

### Post by UbuWu on 2005-07-12
You could try to do a server install and after that, type ' sudo apt-get install ubuntu-desktop ' to install the usual desktop from from the servers instead of the cd.

edit: you can also do this from a kubuntu install.

---

### Post by tbresson on 2005-07-15
Thanks I'll try that.

I actually had time to do some experiments aswell.

I tried to install Ubuntu with only 1 harddrive, a 20 GB Maxtor disk. The disk has been checked and has no errors, bad clusters and any problems according to the PowerMAX program. But I also tried installing on a different maxtor disk altogether, but still the same.

Also I removed both RealTek network adapters, disbaled the onboard soundcard (AC97) from the bios, removed the PCI ATA controller which I use normally, checked the ram with the Ubuntu ram tool at boot for over 4 hours as said before, tried to install with a borrowed graphics adapter (GeForce 2, I think) instead of the MSI GeForce 3 that I normally use, tried removing the DVD burner (NEC) and install from my lite-on cd burner (48x) and vice versa ...

and I still get the error at install.

Since I checked gfx, network, ram, harddrive, soundcard, cd/dvd drives etc. the only thing that could have happened would be some sort of bios change or perhaps all of my sudden my motherboard is a minor error which only Ubuntu detects ....

I installed Kubuntu yesterday after doing the final test with the new gfx card, and it worked fine..

I guess I'll try the "sudo apt-get install ubuntu-desktop" later today.

---

### Post by tbresson on 2005-07-15
Well.. I tried and I get the same error.

There must be something about the gnome desktop or something that my computer doesn't like all of a sudden.

The error this time was:
<1>Unable to handle kernel NULL pointer dereference at virtual address 00000000

---

### Post by tbresson on 2005-07-20
Well ... now it works.

I simply decided to replace the motherboard en the chip with an Intel board and a P4  CPU. And now it works. I guess it was related to the board or the CPU.

If you are curious the board was a ASUS AV7266-E with an AMD 1900+ CPU.

---

### Post by az on 2005-07-20
A shot in the dark would be to suggest that the fan on your AMD chip was not working properly.  That would result in your system running fine for a short time and then throwing random errors.  How long would you boot into windows?

It is a shot in the dark, since I cannot explain the Kubuntu thing...

---

