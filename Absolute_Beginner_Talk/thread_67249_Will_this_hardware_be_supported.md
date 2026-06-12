---
title: "Will this hardware be supported?"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by raistrick on 2005-09-19
Had some problems with my current windows pc (brand bl**dy new as well) with kernel panics and god knows what

so getting a budget rig for linux, cos i really need one anyway...

anyone know if this spec will cause problems, before i buy it?

[http://www.overclock.co.uk/customer...productid=18776](http://www.overclock.co.uk/customer...productid=18776)

Processor : AMD Sempron 3000+ 1.8Ghz Socket 754 Retail Boxed
Memory : Kingmax PC3200 SuperRAM 400Mhz 512Mb DDR
Motherboard : Asus K8S-MX AMD K8 Socket 754 AGP Motherboard
Hard Drive : Maxtor DiamondMAX Plus 9 80Gb ATA/133 2Mb Cache
Graphics Card : VGA Integrated Mirage2 graphics in SiS760GX chipset supports DirectX8.1 (Onboard)
Case : Asus TA-210 Series Midi Tower Black
PSU : Asus TA-210 360W PSU
Cooler : AMD Standard
Optical Drive : Samsung SH-D162 DVD-ROM OEM (Black)
Audio : Audio ADI AD1888 SoundMAX 6-channel audio Codec support S/PDIF out interface
Network : LAN SiS 190/191 MAC + Realtek RTL8201CL 10/100 LAN PHY (Onboard)

Cheers

---

### Post by drogoh on 2005-09-19
Don't hinge your purchase on this but from what I see that hardware should handle Linux.  The only thing I'm hazy about is the Realtek (I know there used to be Realtek problems but I can't remember if it was Linux or a different Unix flavor).  Also, look at X.org's supported hardware for your graphics.

Again, don't let this reply be your deciding factor.  Do yourself a favor by searching on the Linux kernel mailing lists for any potential problems with the kernel.

---

### Post by mneptok on 2005-09-19
Swap that Asus motherboard for a Gigabyte K8-NS and an non motherboard integrated video card (yuck!) and I guarantee Ubuntu will run fine. nVidia is the Linux user's choice video card manufacturer, as they actively provide drivers for their cards.

Seriously, graphics integrated on the motherboard are a bad idea from many perspectives.

---

### Post by floppy on 2005-09-19
You've got close to the setup I have on one of mine. The only difference is the video. The video will work as-is, but will get better if you install the SiS driver. (Search the forum for threads about it).

I will say, though, that it's a lot better if you put in a video card.

---

### Post by TristanMike on 2005-09-19
[QUOTE=mneptok]Swap that Asus motherboard for a Gigabyte K8-NS and an non motherboard integrated video card (yuck!) and I guarantee Ubuntu will run fine. nVidia is the Linux user's choice video card manufacturer, as they actively provide drivers for their cards.

Seriously, graphics integrated on the motherboard are a bad idea from many perspectives.[/QUOTE]I second this, in fact, I'll go a step up and say that an on-board video motherboard is no good for any OS and they should abolish the whole "on-board" video thing. (imo)

---

### Post by xmastree on 2005-09-19
[QUOTE=raistrick]Optical Drive : Samsung SH-D162 DVD-ROM OEM (Black)[/QUOTE]
[This guy]("http://www.ubuntuforums.org/showpost.php?p=358730&postcount=20") seemed to have a problem with Samsung optical drives, although I can't understand why.

I remember there used to be a problem with LG drives, a couple of years ago. The FLUSH_CACHE command that linux sent to the drive was misinterpreted, and erased the drive's firmware. That was LG's fault, for re-assigning a standard command inthat way.

[http://lwn.net/Articles/55815/](http://lwn.net/Articles/55815/)

---

### Post by floppy on 2005-09-19
[QUOTE=xmastree]I remember there used to be a problem with LG drives, a couple of years ago.[/QUOTE]

The LG drives are working ok now; at least mine are :)

---

### Post by rajsarkar on 2005-09-20
To be on the safer side you should try the Live CD first.

-Raj

---

### Post by raistrick on 2005-09-20
thanks people... just needed to check.

cant change any of the spec i needed a super-cheap pc quick cos i start my dissertation next week... 

sod a gigabyte k8-ns.... i have a k8ns pro 754 and that wont bloody work. thats WHY i'm buying one.

---

### Post by mneptok on 2005-09-20
[QUOTE=raistrick]sod a gigabyte k8-ns.... i have a k8ns pro 754 and that wont bloody work. thats WHY i'm buying one.[/QUOTE]

I built a machine with a Gigabyte K8-NS Pro and it ran Ubuntu like a charm.

What, exactly, is not working?

---

### Post by raistrick on 2005-09-20
just wont install anything, 

see, story goes, old pc (more than happy with, dont play games so...) kind of, sort of, blew up....
so i got some reasonably good parts.

got a 1gb of ddr 400 memory that a the k8ns pro cant take (cos it has chips on both sides, apparently) so i bodged that and have 512 ddr 400 and another 700 and some ddr 333.
(bare in mind ebuyer sent the socket 939 one to me 3 times so i ended up buying it through overclock.co.uk)

1 month later and finally windows is being installed properly without errors (caused by the memory not being compatable)

so i get my old samsung hdd and try to install linux.... mandrake - crashed, ubuntu (read my other posts), fedora core 4 all shyte

so... i formatted it on my parents pc no problem, wrong processor but thought it might work after i did that... nothing (forget the error on startup)

fedora talked about some "kernel panic" 

just had so much trouble i possibly havent explored every avenue with linux since i spent so long with windows. have ubuntu running on my old compaq eve 1020v laptop so... just want another box to do my dissertation on... although it will probably end up on a research server anyway. i just dont get hardware

cheers guys,
rai

---

### Post by mneptok on 2005-09-20
You cannot mix and match RAM of varying speeds. Try using just one stick of DDR400 (PC3200) RAM and see what happens.

The board has both serial ATA and parallel ATA controllers and connectors. Pick one, set that as the boot device in the BIOS.

See how that works.

---

### Post by raistrick on 2005-09-20
[QUOTE=mneptok]You cannot mix and match RAM of varying speeds. Try using just one stick of DDR400 (PC3200) RAM and see what happens.

The board has both serial ATA and parallel ATA controllers and connectors. Pick one, set that as the boot device in the BIOS.

See how that works.[/QUOTE]
 sorry, i didnt make the timeline correct...

i wasnt mixing and matching when i was first trying to install in linux (with same error) i didnt have the 400 card in at all

as for the boot devices, its all correct... i'll have another bash to check

brb

---

### Post by raistrick on 2005-09-20
[QUOTE=raistrick]sorry, i didnt make the timeline correct...

i wasnt mixing and matching when i was first trying to install in linux (with same error) i didnt have the 400 card in at all

as for the boot devices, its all correct... i'll have another bash to check

brb[/QUOTE]
 ok stuck one ddr 333 chip in (the single 400 wasnt starting at all in any physical sense)

am on fedora now, but ubuntu not having it at all.

sod it, still gonna buy that other pc i think i need a seperate computer to go on this kvm i got lying around :P

---

### Post by mneptok on 2005-09-20
If Fedora works, Ubuntu should.

Try downloading the Ubuntu i386 Live CD and see if the machine will boot off that. If it does, there is nothing wrong with your hardware.

The GA-K8NS Pro is built for DDR400 (PC3200) RAM. That's the memory you should use, if possible. I always buy Crucial memory, as I have had nothing but stellar results with it. Corsair also gets high marks from folks I trust. You might consider getting a new PC3200 stick.

---

### Post by raistrick on 2005-09-20
[QUOTE=mneptok]If Fedora works, Ubuntu should.

Try downloading the Ubuntu i386 Live CD and see if the machine will boot off that. If it does, there is nothing wrong with your hardware.

The GA-K8NS Pro is built for DDR400 (PC3200) RAM. That's the memory you should use, if possible. I always buy Crucial memory, as I have had nothing but stellar results with it. Corsair also gets high marks from folks I trust. You might consider getting a new PC3200 stick.[/QUOTE]
 oh i know the issue with it, trust me, it took months to get it this far.

basically, the old 333 i  had from when the last mainboard died - god rest its soul - and i bought two (yes, granted, cheap) ram chips. and the 2 together dont work... basically, since i have this working with windows fine, and lets face it you always need a windows box... i'm gonna go ahead get the other one bought and shuv fedora or my mates ubuntu that he has successfully on cd (somehow when i burn them they rarely work) am sure its me

thanks for the help

btw - disabling anything with SATA next to it worked... but i may as well use the 1.25 ram that i have with windows and stick my spare 512 with the one i am buying. overall winner i think.

---

