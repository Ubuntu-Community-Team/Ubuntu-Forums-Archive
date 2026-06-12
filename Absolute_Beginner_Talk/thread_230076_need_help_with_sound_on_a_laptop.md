---
title: "need help with sound on a laptop"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Thaid on 2006-08-05
I have a ibm thinkpad 380 xd. i have no sound. it saying i have no sound controler setup. how do i do this?
thanks

---

### Post by neilp85 on 2006-08-05
Check out this [thread]("http://ubuntuforums.org/showthread.php?t=205449"). Hopefully that can get you going

---

### Post by Thaid on 2006-08-05
thanks muchly but still none the wiser

---

### Post by szabigalambosi on 2006-08-17
I own a TP 770E and it has the same sound chipset as your 380xd. I'm running Xubuntu (dapper) and finally managed to get the sound to work as follows:

1. Install **pnpbios-tools**. 
2. Use **lspnp -v** to identify the sound card device numbers.

For me the the relevant parts were:
[SIZE="1"]
...
0e CSC0000 Crystal PnP audio system CODEC
...
0f CSC0010 Crystal PnP audio system control registers
...
10 CSC0001 Crystal PnP audio system joystick
...
11 CSC0003 Crystal PnP audio system MPU-401 compatible[/SIZE]


3. Turn the pnp devices on using **sudo setpnp 0e on**. Do this also for 0f and 11. 

4. Check again with **lspnp -v** the reported ports for the devices. For me 0e reported 0x530, 0f was 0x538. Check also the dma numbers and the irq.

5. Do **sudo modprobe snd-pcm**
6. Do **sudo modprobe snd-cs4236 index=0 port=0x530 cport=0x538 dma1=1 dma2=0 irq=5 isapnp=0**. Change the port addresses and stuff as needed. 

Thats it. 

To do this automatically on boot, I wrote those commands (except sudo) to a file *ibm_sound*, which I placed in */etc/init.d/*. Then created a symbolic link as **sudo ln -s /etc/init.d/ibm_sound /etc/rc2.d/S99ibm_sound**.

I'm sure there is a more elegant way to do this, but this works. If someone nows a better way, please reply. 

Cheers, Szabi

---

### Post by goldenaches on 2006-09-02
Had the exact problem; actually couldn't get the old 770E sound to work with any Linux distro - followed Szabi's info and now the thing is functioning! Wish I had found his post last year!

---

### Post by szabigalambosi on 2006-09-15
An important update:

Apparently ACPI wasn't activated on my 770e at all. Luckily the CPU never overheated! Using **acpi=force pci=noacpi** kernel flags at boot enables ACPI but sadly the sound gets broken, again. Enabling ACPI renders PNP inoperable. Hmm.. There is no free lunch.

-Szabi

---

### Post by AndrewS on 2006-11-08
Szabi

I was pleased to see your post about getting sound to work on my old Thinkpad (although I couldn't get the symbolic link thingy to work yet) but then I got worried about whether I've got ACPI activated or not.  I guess since I got the sound to work, I haven't - how important is this?  The laptop won't auto-power down, I think this might be related?

Thanks

Andrew

---

### Post by Nopposan on 2006-12-17
Are you sure that your laptop uses acpi anyway?  Mine uses the older apmd to control thermals and fan emergency shutdown etc.  If it's a really old laptop then probably it uses apmd.  Check with the manufacturer's documentation or on their website.

---

### Post by glug101 on 2007-01-13
> **szabigalambosi said:**
> An important update:

Apparently ACPI wasn't activated on my 770e at all. Luckily the CPU never overheated! Using **acpi=force pci=noacpi** kernel flags at boot enables ACPI but sadly the sound gets broken, again. Enabling ACPI renders PNP inoperable. Hmm.. There is no free lunch.

-Szabi

I realize that this post is stone cold by now (being months old and all), but I just had to give props to this.  Kudos to Szabi!!  

I have an IBM Thinkpad 380z that was ruggedized back in the 90's with thick metal shell 8)   I love this old clunker, and the cardbus port allows me to put in a wireless network card cheaply.  I have installed linux on this beast many times and always had trouble with sound, but my recent install of Xubuntu has been the most difficult so far.  From my experience with Ubuntu in general, it doesn't look like it even attempts to install isa cards.  This is not just an issue with my 8 year old laptop, but with my brand new Athlon XP Mobile motherboard that I use as a desktop, since it seems that the nicer system status bits on the motherboard use an outdated isa interface!  

So, in recap, thanks very much to Szabi for this sound fix, and a passing suggestion that Ubuntu should have at least mediocre isa/pnp support.

Cheers

---

