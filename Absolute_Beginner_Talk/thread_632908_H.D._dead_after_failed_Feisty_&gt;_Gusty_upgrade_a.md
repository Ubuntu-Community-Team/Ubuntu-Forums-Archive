---
title: "H.D. dead after failed Feisty &gt; Gusty upgrade attempt"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by dsiddens on 2007-12-06
This is a second attempt on Ubuntu Forums  to get help on recovering the use of a hard disk from a laptop with a amd64 chip.  The computer was running with Feisty 64.  I followed the Synaptic Package Manager lead to upgrade. Had a tough time getting the .iso over a poor connection, then burned the CD. 

After the files were obtained it began replacing to the Gutsy versions. As the files were being written, I noticed quite a few depencencies errors with their messages that a given file (program) would not be installed or might not work properly. This message suggested that I file a bug report. A bit further on into this upgrade process I noticed that there were messages giving me the option to "compare the differences" between the file I had and the new file. So on one of these messages, I don't know which one, I selected "D" and was given a command line screen that described stuff I did not know about and then sat there saying "end".

I figured that hitting enter would return me to the install process. Not so. The machine was sitting at the command prompt waiting for, I don't know what. Eventually I thought if I did a power down/up that the install process would pick up from where it left off. Again, not so. I tried booting from the regular kernal choice and from the recovery mode, neither of which yeilded a working computer.

From the screens that stopped on the boot attempts I wrote do  wn the last screen of each attempt. The significant lines are:

For the kernel 2.6.22-14 (recovery mode)
[10.960197]/build/buildd/linux-source-2.6.22-2.6.22/drivers/ftc/hc.tosys.c: unable to open rtc device(rtc0)
[10.973499] input: AT Translated Set 2 keyboard as /class/input/input1
[11.063970] VFS: Cannot open root device "UUID =adc16267-58e2-4882-9850-9da2e35d482" or unknown-block (0,0)
[11.064022] Please append a correct "root=" boot option; here are the available partitions:
[11.064075] Kernel panic - not sysncing: VFS: Unable to mount root fs on unknown-block (0,0)

For the kernel 2.6.22.14-generic
[16.798468] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[17.014051] Kernal panic-not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

at the bottom of the screen:
Kernel alive
kernel direct mapping tables up to 100000000@8000-d000

I had other boot choices which I went through and tried them all with the result that I was brought to a light blue screen with a cursor that I could move around but no text or sign-in boxes.

The machine in question is a laptop AMD64. It was running fine with the Feisty software.
I'm on our secod laptop hoping that some one can give me a newbie's, detailed instruction to get Gutsy up and running.

Since I made the original request for help I bought another laptop h.d. and loaded Gutsy onto that. However, the inoperable disk hold stuff I need.

Thank you, Doug

---

### Post by Sef on 2007-12-06
> However, the inoperable disk hold stuff I need.


I would download Knoppix and use that Live CD to copy the files to a usb key and then move the folders to the new computer.

As for the original problem, how well does Ubuntu 7.10 (Gutsy Gibbon) Live CD work?

---

### Post by dsiddens on 2007-12-06
Sef,

Thank you for your reply.  The 7.10 Live CD seems to work better than the installed 7.10.  I have about a 3 minute wait during boot time when booting from the H.D.!  Additionally I have problems with sleep/wake/hibernate when booted from the H.D. that I don't when from the Live CD.

I'll put the "dead" H.D. into position #2 in this HP dv8000 and see what happens.  I'll probably take notes by hand of any messages that come up and then post back here. 

Thank you, Doug

---

### Post by dsiddens on 2007-12-06
Here is some more information: I tried to boot with both h.d.'s inside their drive bays.  I put the trashed h.d. into position #2 of the laptop's drive compartment.  The working install of Gutsy is on the #1 drive.  When I attempted to boot the screens ended with this:

[14.065759] PCI: Cannot allocate region 7 of bridge 0000:00:04.0
[14.065802] PCI: Cannot allocate region 8 of bridge 0000:00:04.0
[14.285332] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

In addition to the above, the caps light was flashing.

I'd like to get the mess of a half (?) install of Gutsy cleaned off, get my personal data, then format and start over.

---

### Post by dsiddens on 2007-12-27
I placed a jumper on the slave pins of the trashed h.d., installed it into the #2 position and booted normally from the #1 h.d. 

I am able to see all the files.

Now it is a question of trying clean off the Gutsy stuff or complete the Gutsy install (with corrections) or moving the files to another h.d. and formatting the trashed disk and doing something fresh from that.

Any comments and or pointers?

Thanks, Doug

---

