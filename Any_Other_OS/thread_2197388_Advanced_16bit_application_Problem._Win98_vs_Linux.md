---
title: "Advanced 16bit application Problem. Win98 vs Linux"
date: 2014-01-03
forum: Any Other OS
---

### Post by davedarnold on 2014-01-03
Hi I am newer to linux and was wondering if you can help me with my huge issue i am haiving. I came to this linux forum as I feel you would be the most experienced. 

**My problem**: I have a Program called Testworks QT that I need to use to run a Tensile machine at my work. The program is currently working fine on an old windows machine but i am trying to create a backup plan and this is proving to be challange. It connects to the machine using an ADC card plugged into the ISA port on the computer. ISA ports on old machines are even getting hard to find so if the hardware fails im done. I have contected the OEM for a software/hardware upgrade but they want to chare $16 000 dollars to do so or $30 000 for a new machine. I built a new computer with ISA and need to get the software working. 

**New computer**: My new computer has a MSI MS-98A9 motherboard with an ISA slot. It only has SATA ports no PATA. 

**Software** **issue**: The program i am installing will install on any windows version fine but when attempting to run i get a security violation. This is due to the program requiring Direct access to a parallel port dongle attached to the computer. The program only works correctly on windows 95 and 98. I was succesfully able to install windows 98 on this hardware setup but it does not have the correct drivers to access the harddrive controller and cuases the opperating system to be to slow to use the program. The program does work correctly just really long and unsafe delays. If i install it on windows xp the program looses direct hardware access. I was able to used a program (userport) to give me intermittant access to allow the program to launch once it bypasses the security check but than it cant read the ISA card. I have tried running the program in a virtual machine (virtualbox) and i am able to connect to parallel port alot better but still cant fix the access to ISA. So i gave up on windows and am now trying linux.

**Linux attempt**: So far i have installed ubuntu with wine and got the program to install. I have allowed read write access to the parallel port but i get the security violation message telling me it cant access the parallel port. I have installed virtualbox with windows 98 and i was able to get it to open. same ISA issues. Not Knowing linux enough i am now stuck. 

I need everyones help to either give me ideas on things to try with linux and or windows. I NEED both access to the parallel port and to the ISA card on the machine. Any ideas?

---

### Post by lykwydchykyn on 2014-01-03
I don't know if you've read this:
[http://wine-wiki.org/index.php/Wine_Registry#Parallel_Port](http://wine-wiki.org/index.php/Wine_Registry#Parallel_Port)

But it looks like there are some registry settings you can add into the wine registry to set up direct parport access.

Some less esoteric things you might try are checking that you're running wine in win98 mode (use winecfg or winetricks to set this), and maybe try running it as root to mitigate permissions issues (usually a bad idea for security reasons, but at least you can see if messing with security would even be worth the trouble).

---

### Post by sudodus on 2014-01-03
In such a situation, I would try to find other computers or components, that are old enough to run without problems with Windows 98. Many such old computers might be in a fair condition and could serve as backup for the current one you are using.

I mean old enough computers that there are drivers for Windows 98 to be found via some old web-site if not available directly. I remember using [Driver Agent]("http://driveragent.com/") long ago. I checked, they are still around and seem to have drivers for Windows 98.

There should be thousands of such old computers stowed away in homes as well as at companies, but hard to find. Maybe you can ask at some web marketplace for used computers.

---

### Post by lykwydchykyn on 2014-01-03
Yeah, too bad I didn't see this earlier; just took 3 Windows 98-era computers to recycling last week.

---

### Post by sudodus on 2014-01-03
Maybe we can ask here for such old hardware. But first we must ask: [**[COLOR=#000000]davedarnold[/COLOR]**]("http://ubuntuforums.org/member.php?u=1895617"), where do you live? Someone not too far away, who is active at the Ubuntu Forums, might have what you need.

---

### Post by tgalati4 on 2014-01-03
How difficult is it to control a tensile machine?  Perhaps an arduino or raspberrypi and some relays and you have control and data collection.  For the time you spend cobbling old machines and old software, you could have new hardware and an open source solution.

[http://creativemachines.cornell.edu/freeloader](http://creativemachines.cornell.edu/freeloader)

For $16K, that's what I would do.

---

### Post by mips on 2014-01-04
For the MSI board you can try the Intel INF update utility but I'm not sure if it will even provide drivers for windows 98.
For the parallell port issue check the BIOS as there are 3-4 different modes these ports can be set to.
For the hard drive controller maybe look for a PCI PATA card that uses a chipset known to work with win98.

Best bet is to stock up on some older motherboards & cpus from places like ebay, craigslist, recycling centres etc that you can keep for a rainy day.

---

### Post by grahammechanical on 2014-01-04
I would like to come at this from a different direction. You might have a little more success with a Linux kernel that is contemporary with the hardware. The Linux kernel is constantly being improved and that includes removing code that is no longer of any use. I am wondering if the kernels in the latest versions of Ubuntu have modules for ISA cards.

There are still Linux distributions available that are built upon earlier kernels. For instance, Koppix is built upon the Linux kernel 2.6 and its was the 2.4 kernel that first gave ISA plug and play capabilities to Linux. What is more Koppix will run as a live session and the ISO image is 700MB. It can be burned to a CD and run from a CD drive. Just in case the BIOS on the motherboard does not work with DVD drives.

For the future where you might have a more modern motherboard you might want to research an adapter card that goes into a PCI slot or even a USB port and at the other end provides an ISA slot into which you can slot that Analog-to-Digital ISA card.

Are you sure that the ADC  is a custom card and not standard? What connector does it have going to the tensile machine? For completeness in having a replacement available you need also to think about having a replacement for that ADC. And for complete future-proofing, think about the possibility of have standard Linux software doing what the customized Windows software is doing. Future research beyond your immediate needs, I know.

Regards.

---

### Post by davedarnold on 2014-01-16
Thanks everyone for the replies. Sorry for not responding in a timely fashion i just got really caught up in work. I live in ontario canada. 

@grahammechanical I will try to look into adaptors for the computer but i am worried that they will futher complicate the matter. What do you think the chances of having a usb ISA adaptor are working with an old peice of software? will it be able to find it as it did on windows 98? I will also look into the kernel alot more these are the things i am not experienced with so thanks for pointing me in the right direction. The ADC card is made by the same company that makes the machine and is defintely not standard. I happen to have two identical machines but one does not work so i have two sets of cards and security dongles but only 1 computer. I have looked into a replacement card upgrade package with new software and its $16000 or i can buy a new machine for $32000. I am trying to avoid biting the bullet so will hold out for a little longer. 

@mips I have tried all the bois combinations and made sure everything is in legacy mode. There are no drivers availible for my board and windows 98. 

@tgalati4 I have looked into using a program called labview to control my input and output but the company does not wish to do this. For safty reasons they want and off the shelf software hardware package. (although the way i am going about it contridicts the whole idea but thats what they want.)

@sudodus I am trying to stay away from using old computers. Its bad enough i have been blacklisted by the entire IT department at my work for bringing in this custom build PC i dont want to add any more heaches. 

@lykwydchykyn Thanks i will look into this article a bit more. It was a bit hard for me to follow so far as i didnt understand where they where changing the registry and it didnt match what i had. My experience is not quite there as i dont work in IT.

---

### Post by davedarnold on 2014-01-16
To all,

Does anyone know of a simple way to the just install windows 98 with linux supporting the lack of hard drive controller support. Windows 98 worked perfectly when installed on this board with the program. The only thing it did wrong was it was extreamly slow do to Dos mode compatibility on the hard drives. 

I am going to keep researching ways to get linux to run it but looking for a fast solution.

---

### Post by davedarnold on 2014-01-20
Still havent figured out a solution too this issue. Anyone have any more ideas?

---

### Post by mastablasta on 2014-01-21
aside form wine and virtualbox no. there is no way to run partially win98 partially linux. wine is the closes thing you come to somethign liek this. emulated layer.

there is hwoever another OS that wants to be windows copy. it's called ReactOS.

but is this application windows98 based or can it work in DOS? because for DOs there is DOSsBox and FreeDOS available. FreeDOS supports old as well as new mashcines. so might be worth a look.

---

