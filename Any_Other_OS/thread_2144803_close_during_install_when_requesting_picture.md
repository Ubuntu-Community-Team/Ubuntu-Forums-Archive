---
title: "close during install when requesting picture"
date: 2013-05-13
forum: Any Other OS
---

### Post by ninethousand on 2013-05-13
Hello, i am new to these forums.
MY pc is a Sony Vaio VGN-FE550G
When I install Linux Mint,the installer trys to get a picture from my Camera.
After that point, my PC closes the installer.
This also is happening in Zorin 6 Core.


Thanks.
ninethousand

---

### Post by sudodus on 2013-05-13
Welcome to the Ubuntu Forums :-)

You can add a picture later on. If you have a small picture (I know png is OK, maybe also jpeg) copy it to ~/.face . This means the hidden file .face in your home directory.

So try to skip that photo adventure and let us hope the installer will continue! If you still have problems, come back here and post the specs of your computer, as much as possible, but at least

- cpu, ram, graphics chip/card

And let us know how many partitions there are and how much space there is left on the internal HDD (or SSD)!

You can check that with ***Gparted***, when booted from the install drive (running Mint, but before trying to install)

---

### Post by ninethousand on 2013-05-13
Thanks for the help,sudodus!
I don't really want a picture.
The problem is, as soon as it gets to the point to add a picture, the installer closes before i can do anything about it :(
How can this be fixed?


The RAM is the original it was since I got it. I never changed any specs,really.
I did a clean install, there should be no other partitions.

---

### Post by sudodus on 2013-05-13
Please specify your computer! It makes it much easier to help. Otherwise we can only guess. It might be the camera driver, but also something else, but it appears to be associated to the camera because it happens at that time.

Can you run a live session (booted from the CD/DVD/USB drive) before installation?

Which version of Mint (time-wise) and flavour (desktop environment) are you trying to install?

Also, the linux distros are slightly different, and may cooperate in different ways with the hardware. So it might be worth trying some other version of Mint or some other distro.

---

### Post by ninethousand on 2013-05-13
I can run a live session.

I am not using mint, encountering the same problem in Zorin Core 6.

LSUSB says my camera is a:
Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1

I can run Ubuntu fine, its just slow.

---

### Post by ninethousand on 2013-05-13
Whew,its fixed! I waited for it to copy the files, then i went next.
Thanks for the help,sudodus! Nobody else did.

---

### Post by sudodus on 2013-05-13
You still have not written anything directly about the cpu, ram and graphics, but you tell us that the hardware is not powerful enough to run Ubuntu fast enough. So I suggest that you select a flavour of Ubuntu with a lighter footprint,

- Lubuntu with the ultra lightweight desktop environment LXDE or
- Xubuntu with the lightweight desktop environment XFCE (not quite as fast, but a little more eye-candy and more advanced application programs)

After installation you can install 'any' program into 'any' distro or flavour, so you can easily add more advanced application programs to Lubuntu. The choice is about the desktop environment, the gnu linux engine under the hood is the same.

---

### Post by ninethousand on 2013-05-13
error: file not found.
grub rescue>
....
What

---

### Post by ninethousand on 2013-05-13
it can run ubuntu, unity is laggy
gnome 3 isnt as laggy
LXDE worked fine.
didnt try XFCE.
i dont know how to check my ram,graphics,etc.

---

### Post by sudodus on 2013-05-13
The computer does not boot in a correct way. So something went wrong. We need more information about your computer, now particularly about the internal drive and partitions. One way to get that information is to run YannBuntus boot-repair script. See this thread at the Ubuntu Forums

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by oldos2er on 2013-05-13
Moved to Other OS/Distro Support.

---

### Post by sudodus on 2013-05-13
> **ninethousand said:**
> it can run ubuntu, unity is laggy
gnome 3 isnt as laggy
LXDE worked fine.
didnt try XFCE.
i dont know how to check my ram,graphics,etc.

Great, you have something running. Use ***hardinfo ***to get the information in a GUI and maybe add some details with the terminal window command ***lshw***

```
sudo lshw>lshw.txt
```

and read the result with for example less

```
less lshw.txt
```

---

### Post by sudodus on 2013-05-13
> **ninethousand said:**
> 
MY pc is a Sony Vaio VGN-FE550G


[http://www.cnet.com/laptops/sony-vaio-fe550g-core/4507-3121_7-31688990.html](http://www.cnet.com/laptops/sony-vaio-fe550g-core/4507-3121_7-31688990.html)

Are these specs correct? The cpu and graphics? But the ram might be anything.
> 
Core Duo 1.66 GHz, 1 GB RAM, 100 GB HDD

Graphics Processor  Intel GMA 950 


*Edit*: If this is the case, I would still recommend Lubuntu and Xubuntu, and since you have already installed LXDE into Ubuntu, it is also a good alternative. So check out all the things you need, browsers, voip programs, multimedia players ... and ask if necessary.

But if it is something complicated, it is better to make a new thread with a descriptive title for the new problem.

Maybe you are soon ready to mark this thread as SOLVED: Edit the first post, go advanced and change the prefix to SOLVED.

---

### Post by ninethousand on 2013-05-13
nonono
i HAD ubuntu.
i dont have it anymore, because i wanted zorin.
i have no os now :(
those specs are probably right.

---

### Post by ninethousand on 2013-05-13
I think i fixed it!
the program worked. thanks.

---

### Post by sudodus on 2013-05-14
> **ninethousand said:**
> I think i fixed it!
the program worked. thanks.

Do you mean YannBuntu's Boot-Repair script?
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Congratulations :KS

I'm glad your system works now :-)

---

