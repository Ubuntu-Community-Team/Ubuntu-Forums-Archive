---
title: "Ubuntu 12.04 and 14.04 freeze issues on MacPro"
date: 2014-08-07
forum: Apple Hardware Users
---

### Post by WaltL on 2014-08-07
Pretty much at my wits end on this, so maybe someone can give me some ideas...  

Here's the skinny:

1) Hardware is 2009 MacPro, dualQ core, 32GB RAM, 4 drives (500G original Mac drive with OSX, 1 3TB Ubuntu/Mac partitioned backup drive (1yr old), 1 3TB (1yr old, w/Ubuntu12.04) 1 4TB (2 mo old w/Ubuntu 14.04) all SeaGate drives with Ext3 filesystems)
2) Used as a dual boot machine (rEFInd boot manager) 
3) Did a clean install of 12.04 over a year ago.
4) Mac OS drive/system behaves normally and runs without any issues as far as I can tell.

2 weeks ago, 12.04 began to behave poorly- every program/window was slow to open, program or terminal windows would often darken and then lighten during a computation, the screen would freeze/lock up, but I usually still had mouse control.    Usually, I had multiple programs open/running and Chrome open.  Later, it would exhibit these problems with only a terminal window open.  Systems monitor check was always normal, e.g. no excessive RAM use, CPU loads, no funny business running in the background.   Sometimes I could ssh in and reboot, most of the time required hard reset.  Towards the end I started seeing I/O errors and figured that the drive was dying... which it ultimately did, e.g. ran smartctl and drive failed with multiple errors, including I/O 

5) Did a clean install of 14.04 on the new 4TB drive. This boots fine, but even when only working in a terminal with nothing else open, it too will also occasionally lock up and require a hard restart.  Ran smartctl test and drive passed.

6)  Installed and ran memtester on all 32G RAM for 1 cycle:
Loop 1/1:
  Stuck Address       : ok
  Random Value        : ok
  Compare XOR         : ok
  Compare SUB         : ok
  Compare MUL         : ok
  Compare DIV         : ok
  Compare OR          : ok
  Compare AND         : ok
  Sequential Increment: ok
  Solid Bits          : ok
  Block Sequential    : ok
  Checkerboard        : ok
  Bit Spread          : ok
  Bit Flip            : ok
  Walking Ones        : ok
  Walking Zeroes      : ok
  8-bit Writes        : ok
  16-bit Writes       : ok

Since the Mac OS has no issues and the memory seems okay, I'm thinking that this is not a hardware issue, even though I can't really exclude something going on with the motherboard or power supply.  Also, I'd think that the chances is the brand new drive being bad is remote (it is an ENS class drive, somewhat better than Barracuda, but not an enterprise class).

Does anyone have an idea as to what I should try next?  Can it be related to the size of these drives?  Are these symptoms familiar to anyone else running the latest LTS distros?  Any suggestions would be appreciated.

Thanks!
Walt

---

