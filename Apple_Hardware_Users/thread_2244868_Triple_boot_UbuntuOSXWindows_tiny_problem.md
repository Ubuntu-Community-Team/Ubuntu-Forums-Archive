---
title: "Triple boot Ubuntu/OSX/Windows tiny problem"
date: 2014-09-19
forum: Apple Hardware Users
---

### Post by Sam_seldeeno on 2014-09-19
Hello all,

I have the new macbook pro which already has OSX Mavericks installed. I used it to do three more partitions: one extra for Windows 8.1, another for Ubuntu and the last one for Swap.

All went great until and I installed Ubuntu together with OSX which can be started via Refind manager. Now when I used gdisk to create the hybrid (that will contain my Windows and Ubuntu) and restarted to install Windows, installation went fine but now I cannot see Refind nor I can choose my OS. My laptop only restarts and I hear the apple chime repeated in broken tones! Any clues what I am doing wrong here?

Thanks

---

### Post by coffeecat on 2014-09-19
Welcome to the forum.

I've moved this to ***Apple Hardware Users*** where you are more likely to find people with experience of this.

---

### Post by este.el.paz on 2014-09-19
> **Sam_seldeeno said:**
> Hello all,

I have the new macbook pro which already has OSX Mavericks installed. I used it to do three more partitions: one extra for Windows 8.1, another for Ubuntu and the last one for Swap.

All went great until and I installed Ubuntu together with OSX which can be started via Refind manager. Now when I used gdisk to create the hybrid (that will contain my Windows and Ubuntu) and restarted to install Windows, installation went fine but now I cannot see Refind nor I can choose my OS. My laptop only restarts and I hear the apple chime repeated in broken tones! Any clues what I am doing wrong here?

Thanks

@Sam:

You messed something up man . . . .  : - ))  Of course it's hard to know exactly what that is, but, from my own experience of messing up . . . possibly you just need to again "bless" rEFInd, or re-install it . . . after doing your windows install??  In my own triple boot set up, when I have done an upgrade on OSX it "breaks" the rEFInd "blessing" . . . .  

Couple other questions, are you restarting with the "option" key at this point?  That would/should get you the OSX log in manager window and you should be able to select OSX or "windows" . . . which is also how OSX "sees" linux.  Technically the rEFInd window is supposed to "come up first" but I found that after a couple reboots that stopped working and I have to use the option key, then if I want rEFInd I select the second disk (installed in front of 2nd disk) . . . and then if I want ubuntu, it goes to the GRUB window and then the buntu splash . . . a little bit time consuming but it works.

And, you **might** need to make a partition for GRUB . . . and flag it as so . . . although it seems like some folks are not needing GRUB with the perhaps newer "mac" iso . . . . 

e.e.p.

---

### Post by Sam_seldeeno on 2014-09-19
Actually if I leave it start without pressing the option key then it starts giving me the apple chime sound and then broken tones of that chime sound! Weird! And if I press the option key, it give me the option to go to Windows or EFI drive which is the manager, but when I choose that EFI drive labeled one it freezes on this screen!

---

### Post by este.el.paz on 2014-09-19
> **Sam_seldeeno said:**
> Actually if I leave it start without pressing the option key then it starts giving me the apple chime sound and then broken tones of that chime sound! Weird! And if I press the option key, it give me the option to go to Windows or EFI drive which is the manager, but when I choose that EFI drive labeled one it freezes on this screen!

???  "EFI" drive??  Nothing showing "OSX"???  W/O reading back through yr post, but, let's say there is an "EFI" partition on the HD, you should put OSX **next*** on the drive, next to EFI, then perhaps wiindows, and then the multiple partitons for linux . . . .  If you have the order in some other way, i.e., EFI, then ubuntu, then windows, then OSX . . . that **might*** cause an issue for the boot sequence . . . .

e.e.p.

---

### Post by Sam_seldeeno on 2014-09-19
WHEN I partitioned using utility disk, I made OSX first (of course) then Windows and then Ubuntu partitions. The installation order is OSX, then Ubuntu, and used Ubuntu to create the Hybrid MBR (that contains in sequence my Windows and my Ubuntu: 3 and 4) and then the attempt at Windows got things bad. Maybe Hybrid is what got them mixed up?

---

### Post by este.el.paz on 2014-09-19
> **Sam_seldeeno said:**
> WHEN I partitioned using utility disk, I made OSX first (of course) then Windows and then Ubuntu partitions. The installation order is OSX, then Ubuntu, and used Ubuntu to create the Hybrid MBR (that contains in sequence my Windows and my Ubuntu: 3 and 4) and then the attempt at Windows got things bad. Maybe Hybrid is what got them mixed up?

OK, although perhaps the windows install after ubuntu also "messed" things up; probably ubuntu stuff should go in last.  

Possibly "hybrid MBR" is a problem, there was a poster on the forum who was vehement about "not wanting a hybrid MBR" . . . can't say I know exactly what that is . . . but, I used the OSX Terminal to "drag n drop" the "install.sh" file to install rEFInd . . . you have to read "rodbooks" instructions for rEFInd . . . but, it's a simple install, and it creates a folder "EFI" on your OSX user . . . rather than inside the "EFI" partition???  Then, shut down the computer, and then restart and see if that fixes the issue . . . .  But both OSX & windows appear to be "unfriendly" to other systems, including possibly the rEFInd install . . . .

e.e.p.

---

### Post by d4m1r on 2014-09-29
Had a similar problem when setting up my own triple boot....Had to start from scratch and I suggest you do as well, in this order;

1) Wipe the drive completely.

2) Using the Macbook Pros native recover menu (press and hold a specific button, forget which) you can install OS X again using your connection. I recommend you doing this via a wired connection and even then, this alone with take a few hours because I has to download the whole OS and then install it. No keys/serials required, it will install the full legitimate version.

3) Once you have OS X installed and configured, install Windows 7/8 via the Macbook Pros native recover menu. I would highly recommend the MBR install instead of UEFI. It is just easier to deal with and having Windows plus Linux later on both using MBR is a lot simpler.

4) Once you have OS X + Windows successfully installed, install reFITwhich will replace the need for Boot Camp.

5) Once you have reFIT successfully configuired to boot into either OS X or Windows, you can add Linux to the mix :)

6) Simply put in a bootable disc of Ubuntu, and access the boot menu via the Macbook Pros native recover menu. Select the Linux MBR install and complete the installation.

7) Reboot and now all 3 OS' should be visible from reFIT :)

---

### Post by este.el.paz on 2014-09-29
> **Sam_seldeeno said:**
>  but when I choose that EFI drive labeled one it freezes on this screen!

> **d4m1r said:**
> Had a similar problem when setting up my own triple boot....Had to start from scratch and I suggest you do as well, in this order;
1) Wipe the drive completely.
4) Once you have OS X + Windows successfully installed, install reFITwhich will replace the need for Boot Camp.
7) Reboot and now all 3 OS' should be visible from reFIT :)

@sam:  Hopefully you found a solution to your problem . . . in terms of this comment about "EFI drive freezing on screen" . . . that might point to an issue with the rEFInd installation, you could post to their forum on sourceforge for those kind of issues . . . OR, as I mentioned, it could be that GRUB was not properly installed.

@d4:  Thanks for stopping by, right, possibly a nuke and pave is needed, but it seemed like Sam got OSX installed first and so shouldn't need to do a re-install of it, just the Windows and Linux parts . . . but, either way, for post 10.6.8 OSX it shouldn't be "rEFIt" any more, but now it is "rEFInd" that is needed . . . right?  I thnk I pointed that distinction out earlier in the thread; I 've mentioned it so many times on this forum I've lost track, but rEFIt doesn't "support" or "recognize" OSX after 10.6.8 . . . or 10.7.

e.e.p.

---

