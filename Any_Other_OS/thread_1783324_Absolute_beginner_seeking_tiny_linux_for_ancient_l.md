---
title: "Absolute beginner seeking tiny linux for ancient laptop."
date: 2011-06-15
forum: Any Other OS
---

### Post by 27ace27 on 2011-06-15
Hello all, I am in need of an itty bitty linux version for an ancient laptop that I am trying to turn into an emulator for SNES, NES, GBA, what have you. 

I also have absolutely no experience whatsoever with linux, so it will also need to be pretty simple to install. 

The specs for the dinosaur (as I call it) are (brace yourself):

50MHz Processor
20MB RAM (total)
1GB HDD

and the only way to get anything on or off of it is via a floppy disk. 

Hopefully there is a linux distro (or something suitable)out there that fits the bill!

Thanks in advance,
Paul

---

### Post by pqwoerituytrueiwoq on 2011-06-15
Holy F that is old only thing i know of is dsl (dam small linux) i would not expect to be able to run the gui on it though

---

### Post by crispy_420 on 2011-06-15
All I have to say is good luck getting anything to run on those specs.

Maybe Minix if you want to go old school: [http://www.minix3.org/](http://www.minix3.org/)

The minimum requirements say maybe possible but that CPU may not work: [http://wiki.minix3.org/en/UsersGuide/HardwareRequirements](http://wiki.minix3.org/en/UsersGuide/HardwareRequirements)

As far as no CD-ROM, they appear to have a solution at the bottom of their download page: [http://www.minix3.org/download/](http://www.minix3.org/download/)

---

### Post by 27ace27 on 2011-06-17
Thanks for the replies guys, unfortunately now there is no easy way to get anything on to the computer now. I accidentally hit the floppy drive whilst reaching for something and tore the Flexible flat cable connecting it to the laptop.

The next solution I thought of was interfacing directly with the HDD, it is a PATA interface after all. However yet again lady luck refused to smile and no computers I have can interface with it. It spins up, the heads move, windows makes the detected new hardware sound, but then the whir of the drive wavers, and the process begins again and continues to infinity and the drive is never actually detected. Any Ideas? I suspect it may be so old that it is a power hog and when power demand spikes for a read/write operation, it cannot be supplied and the startup sequence is reset.

This was not the only obvious way, no I am not to be beaten. The next solution was to use a newer HDD with the same interface and install linux on that using a different computer since I can interface with this one. things looked up when the BIOS of the ancient computer detected 8GB of the drive, but it wouldn't boot from it (obviously, it has win XP on it).

Again, however, technology refused to cooperate. Minix does not support 64 bit systems, so I cannot use my main laptop, and it does not support core duo processors, so I could not use my secondary laptop, and it does not support AMD processors so I cannot use the computer the hard drive belongs to. However I do have an old desktop sitting in the closet with a pentium III processor, win 2000, a CD drive USB ports, and a floppy drive. This is the computer I used to put things on the ancient laptop via USB drives from my primary laptop.

Today is not my day, as again the system refused to work. There seems to be a problem with the CD drive going into idle and refusing to come back. This causes the minix setup to lock up. I did manage to get it as far as the drive detection, but it didn't show the alternate PATA drive I was using as an option for installation. On another note, I figured I could install it into the desktop's HDD, then transfer it to the alternate PATA drive, but setup had locked up again before I could do anything.

The next logical step was to try USB drive installation, but it didn't detect either of my flash drives. Wonderful.

So, I'm officially out of ideas. I'm thinking I could maybe use one of the ports to interface with a modern computer or the Hard Drive, but I don't have any of the hardware on hand and I don't really want to order it on the account that I don't know if windows 95 will recognize any of it. The ports on the computer are as follows;

2 PCMCIA slots
1 Parallel Port
1 RS232 Port
1 PS/2 Port
1 VGA port

I'm also trying harder to interface directly with the hard drive, but I don't know what I can do as I don't think it is a software issue. In the manufacturers specs for the drive, it mentioned that the combined length of cabling and circuitry between the drive and the computer was not to exceed 18 inches.

Regards,
Paul

---

### Post by Laforge129 on 2011-06-17
> **27ace27 said:**
> Thanks for the replies guys, unfortunately now there is no easy way to get anything on to the computer now. I accidentally hit the floppy drive whilst reaching for something and tore the Flexible flat cable connecting it to the laptop.

The next solution I thought of was interfacing directly with the HDD, it is a PATA interface after all. However yet again lady luck refused to smile and no computers I have can interface with it. It spins up, the heads move, windows makes the detected new hardware sound, but then the whir of the drive wavers, and the process begins again and continues to infinity and the drive is never actually detected. Any Ideas? I suspect it may be so old that it is a power hog and when power demand spikes for a read/write operation, it cannot be supplied and the startup sequence is reset.

This was not the only obvious way, no I am not to be beaten. The next solution was to use a newer HDD with the same interface and install linux on that using a different computer since I can interface with this one. things looked up when the BIOS of the ancient computer detected 8GB of the drive, but it wouldn't boot from it (obviously, it has win XP on it).

Again, however, technology refused to cooperate. Minix does not support 64 bit systems, so I cannot use my main laptop, and it does not support core duo processors, so I could not use my secondary laptop, and it does not support AMD processors so I cannot use the computer the hard drive belongs to. However I do have an old desktop sitting in the closet with a pentium III processor, win 2000, a CD drive USB ports, and a floppy drive. This is the computer I used to put things on the ancient laptop via USB drives from my primary laptop.

Today is not my day, as again the system refused to work. There seems to be a problem with the CD drive going into idle and refusing to come back. This causes the minix setup to lock up. I did manage to get it as far as the drive detection, but it didn't show the alternate PATA drive I was using as an option for installation. On another note, I figured I could install it into the desktop's HDD, then transfer it to the alternate PATA drive, but setup had locked up again before I could do anything.

The next logical step was to try USB drive installation, but it didn't detect either of my flash drives. Wonderful.

So, I'm officially out of ideas. I'm thinking I could maybe use one of the ports to interface with a modern computer or the Hard Drive, but I don't have any of the hardware on hand and I don't really want to order it on the account that I don't know if windows 95 will recognize any of it. The ports on the computer are as follows;

2 PCMCIA slots
1 Parallel Port
1 RS232 Port
1 PS/2 Port
1 VGA port

I'm also trying harder to interface directly with the hard drive, but I don't know what I can do as I don't think it is a software issue. In the manufacturers specs for the drive, it mentioned that the combined length of cabling and circuitry between the drive and the computer was not to exceed 18 inches.

Regards,
Paul


I might be off but If it is that old of a  computer you might need to have what they used to call a IDE Flip cable.   The newer motherboards doesn't need to do that.   I'd also think the Motherboard couldn't handle a 1gb hard drive.  If I remember correctly they could only do 500 megs or so.   So that might be the problem!

---

### Post by kerry_s on 2011-06-18
Tiny core linux, it's like 10mb, easily fit that hd.

---

### Post by 27ace27 on 2011-06-18
LaForge, I think you are mixed up, the 1GB drive is the one that originally came with the old laptop.

Kerry, I'll try that, but the problem is getting it on to the hard drive.

---

### Post by crispy_420 on 2011-06-18
Tiny Core may be too much for that system:

[http://distro.ibiblio.org/tinycorelinux/faq.html#req](http://distro.ibiblio.org/tinycorelinux/faq.html#req)

Looks like you need a minimum of 48MB of RAM to boot according to their FAQ.

---

### Post by Rex Bouwense on 2011-06-18
You can try Puppy Lynux.

---

### Post by kerry_s on 2011-06-18
chuck that old beast. :lolflag:

---

### Post by snowpine on 2011-06-18
You might have better luck with an early Windows version (95 or possibly 98) than with Linux.

---

### Post by conbot on 2011-06-18
It requires a bit of experience to install, but I personally reccomend CRUX.:)

---

### Post by jim Kane on 2011-06-18
> **27ace27 said:**
> Hello all, I am in need of an itty bitty linux version for an ancient laptop that I am trying to turn into an emulator for SNES, NES, GBA, what have you. 

I also have absolutely no experience whatsoever with linux, so it will also need to be pretty simple to install. 

The specs for the dinosaur (as I call it) are (brace yourself):

50MHz Processor
20MB RAM (total)
1GB HDD

and the only way to get anything on or off of it is via a floppy disk. 

Hopefully there is a linux distro (or something suitable)out there that fits the bill!

Thanks in advance,
Paul

 [FONT=Arial]I use Puppy Linux on (what i thought was) an ancient laptop[/FONT]
    [FONT=Arial]400Mhz cpu and 192Mb ram this is about the minimum spec if you want a CLI with things like Flash and Java working  properly. [/FONT]
    [FONT=Arial]Quite honestly i think the only OS that will work on your laptop is Windows 95, or even just plan old DOS :(     [/FONT]

---

### Post by JC Cheloven on 2011-06-18
I love to put back to life old pc's, but I have to admit I never did with only 20Mb ram. Nevertheless, these should be viable, currently supported, alternatives:

- [Freedos]("http://www.freedos.org/") runs in as little as 640Kb memory. It's a very realistic possibility. No gui, though.
- With [SliTaz]("http://www.slitaz.org") there is the "loram-slitaz-cdrom" possibility. It's a simple text-based installer which requires only 16 MB ram. You'll have a nice gui and all.
- Please read [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems"). Installing even a sparse ubuntu system having only 20 Mb ram may be unfeasible, but you may try. Of course only a comand-line system from an alternate cd, and setting some swap space on disk (~128Mb? with this, if you succeded, you could try afterwards even a very light gui).

My best wishes

---

### Post by kk0sse54 on 2011-06-19
> **conbot said:**
> It requires a bit of experience to install, but I personally reccomend CRUX.:)

Zero linux experience and Crux don't exactly go together ;)

---

### Post by Ichtyandr on 2011-06-19
there is also microcore linux but even that requires 26 mb ram

---

### Post by Spice Weasel on 2011-06-19
OS/2, Windows 95 or DOS are the best choices here. You probably won't be able to get a Linux GUI running with that much memory.

Alpine Linux boots to CLI with 10mb of memory, perhaps you could try a framebuffer-based emulator?

> **Rex Bouwense said:**
> You can try Puppy Lynux.

Oh my. Puppy struggles to run on my machine, which has three times as much memory.

---

### Post by crispy_420 on 2011-06-19
FreeDOS as mentioned may be a decent option since classic gaming would be within reach...

---

### Post by silex89 on 2011-06-19
Even CrunchBang is too much for that machine though O.o

---

