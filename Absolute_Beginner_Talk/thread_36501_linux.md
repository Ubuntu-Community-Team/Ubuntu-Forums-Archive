---
title: "linux?"
date: 2005-05-23
forum: Absolute Beginner Talk
---

### Post by Delirious on 2005-05-23
what exactly is:

/
/boot
swap

Im having a hard time understanding  why u need 3 partitions for linux?

---

### Post by StacyWebb on 2005-05-23
/ is the root of your drive
/boot is where the kernel commands boot from (ie which kerenel you want to use and with what parameters)
swap is like a temp section for running apps

---

### Post by bigbadblo on 2005-05-23
Delirius...

Ok, this might be the blind leading the blind ... but this is how it was explained to me:

"/" is otherwise known as "root."  Kinda link the C:\ drive in that everything starts here, whether its a directory, etc.  In addition, certain commands can only be performed from the root.

"/boot" is just what you'd think -- the boot partition where Linux keeps all of its boot-up info.  Its seperate, like much of the linux directories, so that things can't become corrupted as easily as if they were all lumped together.

"swap" is the equivalent of the Windows pagefile.  This is empty space that linux will utilize as a virtual pagefile on the fly, in order to carry out system processes and the sort quickly and easily.

The above may not be 100% accurate, but that's how it was presented to me...

Hope it helps,

bigbadblo

---

### Post by Delirious on 2005-05-23
I just tried to install it but i dont think i configured the drives correctly and i hosed my windows install, didnt loose anything importand just windows. 

I have 2 partitions one a 5 gb and a 20gb. When i was istalling there wasnt an option for boot and one for the root that i noticed, i configured the drives manually. Im sure its just me. im reinstalling windows now then im goin to have another go.

---

### Post by bigbadblo on 2005-05-23
Delirious...

I don't know if this helps, but I managed to get a dual boot system up and running today -- without hosing the XP partition and installation!

Here's what I did:

Installed Windows XP FIRST.  I had it partition my 30gb drive as follows:  Windows XP formatted the first 10gb as NTFS, created an unformatted partition of 11gb next, and then concluded with a 8.5gb (whatever was left) partition that was formatted as FAT32.

After XP was installed and operating, I tossed in the Ubuntu installation CD and did this:  when prompted to change the partitions, I opted to do so manually.  I then selected the "guided partitioning" and selected "largest available partition."  Ubuntu picked up on the 11gb unformatted area of the hdd and created all necessary partitions like "/" and "/boot", etc.  After all of that good stuff, I just installed Ubuntu, and then towards the end of the installation process I opted for using the GRUB boot loader:  it identified XP, and walla!  Dual boot system!

Should be relatively simple if you follow the above.  If not, ask and I'll see if I can offer more advice. Its nice to be able to go through this process with others at the same place!

Take care,

blo

---

### Post by davide_bruzzone on 2005-05-24
[QUOTE=bigbadblo]Delirius...

Ok, this might be the blind leading the blind ... but this is how it was explained to me:

"/" is otherwise known as "root."  Kinda link the C:\ drive in that everything starts here, whether its a directory, etc.  In addition, certain commands can only be performed from the root.

"/boot" is just what you'd think -- the boot partition where Linux keeps all of its boot-up info.  Its seperate, like much of the linux directories, so that things can't become corrupted as easily as if they were all lumped together.

"swap" is the equivalent of the Windows pagefile.  This is empty space that linux will utilize as a virtual pagefile on the fly, in order to carry out system processes and the sort quickly and easily.

The above may not be 100% accurate, but that's how it was presented to me...

Hope it helps,

bigbadblo[/QUOTE]

bigbadblo,

What you said is accurate... I just wanted to clarify a couple of things...

- /boot is also where your linux kernel images live. If/when you compile a new kernel, you'd put it in /boot and would add it to your boot loader configuration to boot it. The boot loader is what allows you to boot Windows, different Linux distributions, different kernels, etc.
- swap is Linux's virtual memory area/file/whatever on your disk. Like Windows, Linux supports the notion of virtual memory which allows the operationg system to think that it has, say 512 MB of memory in a machine that only has 256 MB of physical RAM. When something that's in physical RAM isn't needed (or isn't being used and something in swap is needed in physical RAM), the operating system moves it into the swap file (BTW, my knowledge of the details of exactly how this happens are completely foggy since I'm no kernel hacker... :-)). A lot of swapping between physical RAM and the swap file is bad and means that you would benefit from more physical RAM...

Cheers...

Dave

---

### Post by thoms on 2005-05-24
I've installed it dual boot on a few machines and never had a problem with the automatic partitioning, saved me a lot of faffing of the sort that had occoured when I installed other distro's.

I believe that the swap partition is moving towards obsoletion as faster memory becomes cheaper and technology advances.

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=thoms]
I believe that the swap partition is moving towards obsoletion as faster memory becomes cheaper and technology advances.[/QUOTE]


Yep. More RAM makes it uneeded. I never swap on my 512mb machine.

---

### Post by Sionide on 2005-05-24
But surely, having 512mb of ram and a 250mb /swap then is the same as having 700mb odd of ram. no?

---

### Post by ola on 2005-05-24
> But surely, having 512mb of ram and a 250mb /swap then is the same as having 700mb odd of ram. no? 

Yes except for that the last 250mb (the swap drive) is much slower than your real RAM.

---

### Post by aysiu on 2005-05-24
Also, you may just not need the 768 MB RAM, honestly. I have 512 MB RAM and set aside 512 for swap. I've never had to use swap, even with four or five programs open.

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=Sionide]But surely, having 512mb of ram and a 250mb /swap then is the same as having 700mb odd of ram. no?[/QUOTE]

No. Real RAM is fast. Swapping is slow.

---

### Post by Delirious on 2005-05-24
I have 1gb of good memory so i guess ill do without the swap.

Yup its nice to walk through this with others :D

So all i have to do is have one partition aside from windows(thats on the same drive). then:
1. create one partition for linux
2. boot into ubuntu and do the manual partition
3. direct it to the partition i want it in.
4. then there should be an option to let it setup the partitions it needs automatically within my one partition?

Does this sound right?

I just got windows setup and running again so im dont really want to hassle reinstalling it even if it only takes 30min  :?

---

