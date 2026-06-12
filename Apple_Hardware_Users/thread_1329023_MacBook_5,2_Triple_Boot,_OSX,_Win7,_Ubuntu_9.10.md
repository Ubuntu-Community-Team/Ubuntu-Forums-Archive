---
title: "MacBook 5,2 Triple Boot, OSX, Win7, Ubuntu 9.10"
date: 2009-11-17
forum: Apple Hardware Users
---

### Post by CellPhoneDude on 2009-11-17
So I don't know how everyone else is doing it but here's how my install went when I was running 9.04.

I had just purchased a new 500gb disk for my MacBook, pulled the drive put it in an enclosure, poped in my osx dvd booted into the setup and opened disk utility. I only partitioned the 300mb part. that I wanted for OSX at this time and left the rest of the disk blank. Reason I did that is I hate whatever boot camp does to that partition and being that I planned on using refit I figured all would be ok. Next put win7 dvd in option booted installed win7 on the next 110gb part and let the installer partition it and install it. Then option booted the ubuntu 9.04 cd and followed the guiedlines from the mactel wiki. Worked great no issues with the original grub, new grub2 doesn't yet work with refit which is why refit says its a legacy OS. Now this is where I messed up I broke my 9.04 install before I could upgrade which would have let me retain my grub boot options, so I didn't a fresh install of 9.10 and I can't for the life of me figure out how to add "acpi=off" to the boot options because thats the only things that allows my machines to boot 9.10 current with refit. Also with the drives partitioned individually by each os grub2 recognizes and boots all three for me, so maybe figure out how to use grub as the first boot loader.

Also forgot to add the no matter what while in windows > disk management the windows part. should be boot and active and the bootloader should be on the windows disk as well as in ubuntu the last step of the install step 8 click the advanced button and put the bootloader on the partition where ubuntu is.

Thats how my machine works actually posting this in ubuntu 9.10 as we speak and the nvidia 185 drivers and the wireless card detected and installed drivers for no problem.

---

