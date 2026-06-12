---
title: "Dual Boot with Vista and ubuntu 7.04 x64 bit possible on DV6325?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by dacookiemonn on 2007-06-03
I like the Feisty that I installed on the desktop on a seperate harddrive, so I downloaded the 64 bit version and want to install it on a 15-20 Gb partition in my HP pavilion dv6325 (dv6000).
First thing I think I need is a boot manager so I can boot to vista when I want right?
Also am I going to need to hook it up to external lcd becasue of the black screen issue, or should I wait to see if it will detect it and use ext lcd as backup?
Id hate to not be able to get back into vista, for now at least.
Does any one have a link for intructions to set grub to allow me to boot to vista and ubuntu?
I searched, but did not find any info on the 64 bit version on a laptop.  If recommended, I would put the x86 version on if I am going to have too many issues, but I got a turn X2 64 bit 1.6 Ghz cpu adn Nvidia 6150 go, which im not too sure about if there are sutable drivers.
Ill wait for a reponce, so I dont dive into something that is not recommended, but Im ready when I get a confirmation.

thanks

---

### Post by dacookiemonn on 2007-06-03
Anyone?  I dont wanna mess it up more than vista has promised. lol

---

### Post by jonward0690 on 2007-06-03
Well you can dual boot easy because it installs grub by default and.You can use the 64bit verson as long as you have a 64bit processer even though i recomend just using the 32bit verson cause it is more stable.Your nvidia graphics should have linux drivers.And if you want to hook up a external hard drive to Ubuntu you will have to reformat it to Fat 32 because you can't read write in Ntfs in Ubuntu.

---

### Post by freebird54 on 2007-06-03
Well - the first thing is - YES you can.

The second thing is - DO ALL PARTITION RESIZING FOR VISTA WITH VISTA!  Apparently it hates to be  resized externally by anything - even Windows tools.  Just leave blank space for the Ubuntu installer to work with....  BTW - the NTFS writing issue appears to be a thing of the past - ntfs-3g will work fine for seeing partitions across systems.

As to 64 bit - for itself it works great, but apparently there are other issues restricting which software you can run - and possible more driver issues than with 32 bit.  Depends on your purposes for running it I guess!

Enjoy - and hope this helps.

---

### Post by dacookiemonn on 2007-06-03
Well I just hit the install button.  I shrunk the Vista partition to give me 14Gb free FAT space in Vista.  I then had to use the noapic nolapic option to boot liveCD and went through installer and selected guided largest free space.  I notice it is way faster than the single core 1.6 Ghz AMD 64 in the desktop with the 32 bit version.  This laptop has a 1.6 Ghz AMD Turion X2 64 bit :) 
It took me about an hour to install on desktop the other day, its already at 67% as of writing this less than 10 minutes in.

Give me a link to the proper place to post the results in detail for others to see, I will post it tonight or tomorrow.

WOW 78% installed.  Thats super fast

---

