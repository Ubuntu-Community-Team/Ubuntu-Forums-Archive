---
title: "Verifying DMI Pool Data...Update Success (Kubuntu)"
date: 2013-08-10
forum: Any Other OS
---

### Post by shane4 on 2013-08-10
Hey guys,

Im trying to install Kubuntu (The latest version) to a spare machine,Ive created a bootable ISO on USB drive...set in the BIOS to boot from USB first,HDD second.

But all i get is 
**[*Verifying* DMI *Pool Data*...*Update Success*]("http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CC8QFjAA&url=http%3A%2F%2Fanswers.microsoft.com%2Fen-us%2Fwindows%2Fforum%2Fwindows_vista-system%2Fverifying-dmi-pool-dataupdate-success-when-trying%2F76c31d46-4128-4cc2-be0c-d0d0b782953e&ei=mRIGUpboOOaT0QXGr4DABg&usg=AFQjCNGMYxwHku0T88SeRck6PhSghyjg1A&sig2=HYIU2MdJhZC_NG4UUdP_0A&bvm=bv.50500085,d.d2k")**


Then it hangs there.

System specs

Core 2 Duo E6300
H55 Motherboard (Gigabyte cant remember exact model)
2gb ram 
120Gb Sata2 Hard drive

Appreciate any help!

---

### Post by d-cosner on 2013-08-10
I had the very same problem! On my computer I was not using any IDE devices and turning off the IDE channels in the BIOS got it going. My board is a Biostar, also do not remember the exact model but it was challenging getting it to start reliably. I flashed the BIOS too, still get "verifying DMI pool data" and "AMD data change" but the machine starts every time now. When looking for solutions for this online I saw that a lot of people with various boards were having this issue.

---

### Post by shane4 on 2013-08-10
Thanks for replying.

Managed to get Ubuntu to install,for some reason it just wouldn't boot/install from USB to i burned a CD and it installed and works fine now.

---

### Post by d-cosner on 2013-08-10
Glad you got things going! :D

---

### Post by bcschmerker on 2013-08-10
Does BIOSTAR use a Phoenix® Award® BIOS?  I recognize this exact behavior at the close of my Gigabyte® GA-MA78GM-S2HP's pre-initialization, before it loads the hard drive's boot sector to RAM and hands off to the Grand Unified Bootloader.

---

### Post by d-cosner on 2013-08-10
>  					Does BIOSTAR use a Phoenix® Award® BIOS?    

Yes, I used a Phoenix utility to flash the BIOS.

---

