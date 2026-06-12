---
title: "Dapper wont run X on &quot;Oldworld&quot; G3 Beige"
date: 2006-08-20
forum: Apple PPC Users
---

### Post by Marco Renoldi on 2006-08-20
I got an Oldworld Mac G3 Beige with 4GB Hard Disk, 512MB RAM, built-in video  Card ATI 3D RAGE and wanted to install Dapper.
The installation process went OK but at the reboot a message says X cannot run. Here is the log:
(WW) INVALID IO ALLOCATION b: 0xfe00100 e: 0xfe0010ff
correcting,,,
(EE) end of block range 0xfdffff < begin 0xfe000000
(EE) ATI(0): unable to register the following bus resources: [0]000xfe000400  - 0xfe0004ff (0x100) IS[B]
(II) UnloadModule: "ati"
(II) UnloadModule: "atimisc"
(II) Unloading /usr/lib/xorg/modules/drivers/atimisc_drv.so
(EE) Screen(s) found but none have a usable configuration
To make a long story short i tried anything i could: kernel arguments, different values for vmode and cmode, video=ofonly, disabling DRI, etc.
Then I decided to try Breeze Badger and that worked.
But I didnt give up the idea of having Dapper so i upgraded Breeze to Dapper with the update manager. Again... the upgrade was OK but after the reboot i got the same X problem with the same log.
Is there anyone who can understand why this happens?
Thanks for the help.
Marco

---

### Post by didg on 2006-08-20
Did you save /etc/X11/xorg.conf and /var/log/Xorg.0.log before upgrading?

Should have clues on what's going on.

---

### Post by Marco Renoldi on 2006-08-20
the xorg.conf is exactly the same

---

### Post by AndrewBarber on 2006-08-20
I have uploaded my xorg.conf, so back up your own and try this one.
My mac is the same spec[cept the parts you have upgraded[memory]].
My xorg.conf can be found [here](http://elitelinux.org/andrew/xorg.conf).
I run dapper dan, it is completely up to date. Make sure your xboot is set up properly too.

---

### Post by Marco Renoldi on 2006-08-20
Many thanks.. gonna try it soon, though at first glance it seems identical to my xorg.conf!
You are running Dapper on a Mac G3 Beige? At least now I know it is possible!
When you say "Make sure your xboot is set up properly too" you mean that you are passing arguments to the kernel other then root=/dev/hda6 in the BootX field? If so, which arguments? 
Marco

---

### Post by AndrewBarber on 2006-08-20
I dont have anything spectacular. I do have options for the frame buffer size, mainly cause I dont use X and like my vts nice a big!
But here is what I have; ```
 video=atyfb:vmode:14,cmode:32,mclk:89 root=/dev/hda6

```
Also hit Options and make sure **Force video settings** is ticked.

---

### Post by Marco Renoldi on 2006-08-20
Wow!
The values for vmode and cmode that you have are different from mine.. but above all my "Force Video Settings" is not checked!!!
Hope this gonna sove the prob..... I'll let you know
Many thanks
Marco

---

### Post by AndrewBarber on 2006-08-20
What are yours? I only put them modes in last night, it makes it bigger but I am interested in yours too heh.
I think the checkbox should help ;)

---

### Post by rexbinary on 2006-08-20
Hmm, well I'm running Xubuntu 6.06 currently on my PowerMac G3 Minitower (Platinum/Beige), and I use no kernel arguments in BootX other then specifying the root device, force video settings is unchecked, and my video works perfectly. This goes for Ubuntu 6.06 as well as I had it installed originally. It is the ATI RAGE Pro which was the later video card they used, I'm not sure if that makes any difference or not, or if you don't have the Pro already.

After you install and update your kernel, are you copying the new kernel and image file back to your BootX 'Kernel Files' folder before rebooting?

---

### Post by AndrewBarber on 2006-08-20
> **rexbinary said:**
> 
After you install and update your kernel, are you copying the new kernel and image file back to your BootX 'Kernel Files' folder before rebooting?

Totally forgot to do that actually..maybe I should and see it crash ](*,)

---

### Post by Marco Renoldi on 2006-08-30
> **rexbinary said:**
> Hmm, well I'm running Xubuntu 6.06 currently on my PowerMac G3 Minitower (Platinum/Beige), and I use no kernel arguments in BootX other then specifying the root device, force video settings is unchecked, and my video works perfectly. This goes for Ubuntu 6.06 as well as I had it installed originally. It is the ATI RAGE Pro which was the later video card they used, I'm not sure if that makes any difference or not, or if you don't have the Pro already.

After you install and update your kernel, are you copying the new kernel and image file back to your BootX 'Kernel Files' folder before rebooting?
sorry for the delay.....

My video Card is an ATI RAGE PRO...
Regarding copying the kernel and image file... well i do not do this.... what exactly should i copy and where?

---

### Post by abtabt on 2006-08-31
hello i am new in forum

if you do lshw what did that tell you ??? 

if you get missmatch/conflicks for adresses (mem )

i hope you understand my english

---

### Post by Marco Renoldi on 2006-08-31
I'm afraid i don't understand what you mean...
Anyway, the xorg.log says:
(WW) INVALID IO ALLOCATION b: 0xfe00100 e: 0xfe0010ff
correcting,,,
(EE) end of block range 0xfdffff < begin 0xfe000000
(EE) ATI(0): unable to register the following bus resources: [0]000xfe000400 - 0xfe0004ff (0x100) IS[b]
(II) UnloadModule: "ati"
(II) UnloadModule: "atimisc"
(II) Unloading /usr/lib/xorg/modules/drivers/atimisc_drv.so
(EE) Screen(s) found but none have a usable configuration
Do you have any idea?

---

### Post by abtabt on 2006-08-31
your output says that you have a conflict

go in to terminal 

type lshw 

and you will get something like this


        *-display
             description: VGA compatible controller
             product: 3D Rage Pro 215GP
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@00:12.0
             version: 5c
             size: 16MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master
             configuration: driver=atyfb
             resources: iomemory:82000000-82ffffff ioport:fe000400-fe0004ff iome mory:81800000-81800fff irq:22



and lot of konfigration off the computer ,like hd video card usb etc

and check if any off the card will interupt  (memory )  (the lshw list is long )

if you post the output here if you have problem to read it

---

### Post by abtabt on 2006-08-31
i have some question about installing drapper 606 on a old world
i cant use the cd ubuntu 606 LTS (those they shippning free)

i download server cd for 606 and install the desktop (ubuntu,kubuntu.ubuntulite etc)

thats away round it 


but have any one use the cd ubuntu 606 LTS on a (OLD WORLD)



:)

---

### Post by Marco Renoldi on 2006-09-01
OK... here is the output of lshw (it seems very much the same as yours):

*-display
description: VGA compatible controller
product: 3D Rage I/II 215GT [mach64 GT]
vendor: ATI Technologies Inc
physical id: 12
bus info: pci@00:12.0
version: 9a
size: 16MB
width: 32 bits
clock: 33MHz
capabilities: vga bus_master
configuration: driver=atyfb
resources: iomemory:82000000-82ffffff ioport:fe001000-0e0010ff iomemory:80000000-80000fff irq:22

The video card is different. I don't know if that is the problem. Your is ATI RAGE PRO, mine is ATI 3D RAGE I/II. Does it make any difference? do you see any conflict?

---

### Post by tseliot on 2006-09-01
Try with:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to the other questions.

then type:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```


if "vesa" doesn't work try "vga"

---

### Post by Marco Renoldi on 2006-09-01
tried already.... no luck

---

### Post by abtabt on 2006-09-01
i hope this will help you do a 
lspci 

and send a output

what i mean in last post was you have conflict i the memory

a card like usb,scsi,eternet card etc

if i see the hole lshw list not only the about the video card

then i can see all card and the configure off the computer

lspci will give you all the card in your computer



ps vesa dont work in this mac when you use ubuntu in yellowdog it works 

how did you get drapper in your mac server cd or the shipping cd ???

---

### Post by Marco Renoldi on 2006-09-01
ok ... i will send the output of lspci
I have downloaded the iso of both ubuntu and xubuntu and installed both

---

