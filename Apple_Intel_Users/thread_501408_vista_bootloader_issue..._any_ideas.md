---
title: "vista bootloader issue... any ideas?"
date: 2007-07-15
forum: Apple Intel Users
---

### Post by thefockinfury on 2007-07-15
hi all,
so i just set up a triple boot on my macbook pro (core duo, 2.16ghz, 2gb, 100g b) with OSX, ubuntu, and vista. first i installed vista and then ubuntu as recommended. ubuntu boots normally using GRUB. but even before i installed ubuntu, and now after, vista prints a warning to the screen while booting up. it reads:

"Warning: Unrecognized partition table for drive 80. Please rebuild it using a Microsoft-compatible FDISK tool (err=4)"

it displays this message several times but eventually boots past it. this isn't a fatal problem as much as it is a huge annoyance because it basically doubles the startup time of the system. i found post on another forum where someone recommended EasyBCD as a remedy to this situation. i downloaded it and installed it, and told it to reinstall the MBR, but this hasn't fixed the problem. 

does anybody have experience with this issue that would care to shed some light on the matter for me?

thanks in advance

---

### Post by thefockinfury on 2007-07-15
bwahahahaha
problem solved. it took more than just rewriting the MBR with EasyBCD as suggested. i had to create entries for the linux and OSX partitions as well. now booting vista brings up the vista boot prompt that lets me select ubuntu or OSX as well. it cut my boot time in half! everything works like a charm now. sorry to post prematurely.

---

### Post by mjurmann on 2007-07-26
Hello. I was just curious if you could explain this to me.

"i had to create entries for the linux and OSX partitions as well. now booting vista brings up the vista boot prompt that lets me select ubuntu or OSX as well."

Thank you...I'm having the same problem you had and can't fix it.

---

### Post by Steve1961 on 2007-07-26
Sorry to jump in here but I'm using easyBCD to multiboot XP, Vista, Ubuntu and Debian.  Basically easyBCD lets you use the Vista bootloader to boot all your operating systems.  Just make sure you install Grub to the boot partition of your Ubuntu system and then use the EasyBCD gui to reinstall the VIsta bootloader to the mbr and add your Ubuntu partition to the Vista bootloader.  When you reboot the Vista bootloader appears with Ubuntu as a boot option.

---

### Post by thefockinfury on 2007-07-26
Steve nailed it. i use rEFIt to choose between OSX, Ubuntu, and Vista. choosing OSX boots directly into OSX. choosing Ubuntu loads GRUB from which i can choose which linux kernel to boot, plus vista. choosing Vista brings up another boot menu letting me choose OSX, Ubuntu, or Vista. it's kind of klunky but everything works fine. 

your question about adding OSX and Ubuntu to the vista bootloader: there's an option tab in the EasyBCD app that lets you add/remove entries for other operating systems to the vista bootloader. check it out here; this is exactly what i did to get everything working
[URL="http://neosmart.net/wiki/display/EBCD/Add+and+Remove+Entries"]
http://neosmart.net/wiki/display/EBCD/Add+and+Remove+Entries[/URL]

let me know if you're still having problems

---

### Post by Chrisj303 on 2007-07-28
I tripleboot OSX/UBUNTU/VISTA, and use LILO as my bootloader. It's a much more elegant soloution than EasyBCD & GRUB.

On the rEFIt screen, regardless of which OS i choose, it boots it straight away with no further screens/menus to navigate, and it does so quickly.

---

### Post by cyberdork33 on 2007-07-28
> **Chrisj303 said:**
> I tripleboot OSX/UBUNTU/VISTA, and use LILO as my bootloader. It's a much more elegant soloution than EasyBCD & GRUB.

On the rEFIt screen, regardless of which OS i choose, it boots it straight away with no further screens/menus to navigate, and it does so quickly.

This can be done with lilo _or_ grub if people would install grub to the ubuntu partition instead of the MBR.

---

### Post by thefockinfury on 2007-07-28
> **cyberdork33 said:**
> This can be done with lilo _or_ grub if people would install grub to the ubuntu partition instead of the MBR.

i did that and i still have to boot through GRUB after i select my OS with rEFIt. could i have done something wrong? do you have any other threads or articles to refer me to? my triple boot works fine but i suppose it would have more 'oomph' if i didn't have to wade through 2 bootloaders for 2 of my 3 OS's!

cheers

---

### Post by cyberdork33 on 2007-07-28
> **thefockinfury said:**
> i did that and i still have to boot through GRUB after i select my OS with rEFIt. could i have done something wrong? do you have any other threads or articles to refer me to? my triple boot works fine but i suppose it would have more 'oomph' if i didn't have to wade through 2 bootloaders for 2 of my 3 OS's!

cheers

You have to use a bootloader because refit is not capable of loading the kernel, but set your delay to 0 and you never see it.

---

### Post by Ptero-4 on 2007-07-28
Can you actually set refit to autohide it´s menu and it´s delay to 0? And can you actually install grub to the mbr and have it come shortly after you turn on your x86 Mac? Also can refit function after OSX have been removed from the HD?

---

### Post by cyberdork33 on 2007-07-29
> **Ptero-4 said:**
> Can you actually set refit to autohide it´s menu and it´s delay to 0? And can you actually install grub to the mbr and have it come shortly after you turn on your x86 Mac? Also can refit function after OSX have been removed from the HD?
I was referring to Grub not rEFIt...

You might be able to intall rEFIt to the EFI partition at the beginning the disk have it run fine without OSX.

---

