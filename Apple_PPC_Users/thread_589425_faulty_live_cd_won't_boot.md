---
title: "faulty live cd? won't boot"
date: 2007-10-24
forum: Apple PPC Users
---

### Post by anthonylane13 on 2007-10-24
Please forgive noob status at this - anyone  with experience who can offer me advice will be greatly appreciated.

I have just received my copy of feisty fawn for my powerbook g4 
  Machine Model:	PowerBook G4
  CPU Type:	PowerPC G4  (2.1)
  Number Of CPUs:	1
  CPU Speed:	800 MHz
  L2 Cache (per CPU):	256 KB
  L3 Cache (per CPU):	1 MB
  Memory:	1 GB
  Bus Speed:	133 MHz
  Boot ROM Version:	4.3.7f3

I cannot get my computer to recognise the disk outside of OSX environment (runnning OSX 10.3.9)

I've tried holding 'c' during startup, holding 'option' during startup (this only gives me the option to boot from hard disk) and emptying PRAM first - option+apple+p+r .

Nothing is working, so I have browsed my disk to check that it's not blank (it's not) but I wonder if I've been given the correct software.

This is what's in the parent directory

[folder] casper
[folder] dists
[folder] etc
[folder] install
md5sum.txt
[folder] pics
[folder] pool
[folder] ppc
[folder] preseed
README.diskdefines

I can't see anything executable in this directory.... but then again maybe I'm not supposed to?

Also, if it helps, I tried to boot from the original disk to see if I could get in that way, but my computer won't even recognise that disk, before or after OSX loads (no other problems with disk drive - no errors shown on hardware diagnostics).  It may be because the original disk is for OSX 10.1 but the compter has been upgraded to 10.3 before I got it (still waiting for previous owner to find and mail me OSX 10.3 disk)

Hope that's not information overkill.....
Please help! ](*,)

---

### Post by pxwpxw on 2007-10-24
**anthonylane13**

That looks like the correct cd, this is from the /install/ directory (using the Macosx terminal app)
```

ads-ibook-g4:~ admax$ ls -l /Volumes/Ubuntu_PowerPC_feisty/install/ 
total 432
-rwxr-xr-x   1 admax  admax     468 Apr 15  2007 boot.msg
-rwxr-xr-x   1 admax  admax    1855 Apr 15  2007 ofboot.b
-rwxr-xr-x   1 admax  admax    2243 Apr 15  2007 pegasos
-rwxr-xr-x   1 admax  admax    5111 Apr 15  2007 udeb.list
-rwxr-xr-x   1 admax  admax  153124 Mar 13  2007 yaboot
-rwxr-xr-x   1 admax  admax    2681 Apr 15  2007 yaboot.conf

```

If the CD won't boot directly using the C key or options key, it might still be possible to boot yaboot manually from open firmware.

You do that with the CD in the drive, by starting into open firmware with Command-Option-O-F.
Then at the open firmware prompt
```

0> boot cd:,install\yaboot

```
If it works you will see a yaboot text menu, TAB will get the options.

---

### Post by anthonylane13 on 2007-10-24
Thanks for your suggestion
Didn't work unfortunately - firmware gave me this:
bad READ-1 can't open cd:,install\yaboot

any other suggestions?

---

### Post by pxwpxw on 2007-10-24
> **anthonylane13 said:**
> Thanks for your suggestion
Didn't work unfortunately - firmware gave me this:
bad READ-1 can't open cd:,install\yaboot

any other suggestions?

Where did you get the ubuntu CD? If you burned it yourself there could be error problems. It would help to try it on another Applemac ppc, but It is looking  like a cd drive problem, since you say it also won't boot the MacosX install DVD? Booting should not be affected by the MacosX version you have installed. 

I don't know if your Powerbook G4 model should have any particular problem, I don't think so. Some earlier models had problems with CD size bigger than around 650MB.

If the cd drive really wont do it, there are other options:

You can do a network install by downloading installer files to you hard disk, and you can download an iso to the hard disk and do a "hd-media" install. But for these you would not use the Desktop install that you have , but the Alternate or Server install which are text menu based. 
Section 4 and 5 of the Install Guide mentions network and hd-media install methods,
and there are some howtos. I can confirm that it works.
However, you might need to wait until you have the MacosX install DVD so that you can re-install Macosx to leave free space for ubuntu, and in case of accidents.

[My network install outline is here]("http://ubuntuforums.org/showpost.php?p=2887410&postcount=4")

---

### Post by anthonylane13 on 2007-10-25
Thanks again for your suggestions.  I bought the disk from land of linux (landoflinux.co.uk)
I wonder if my hardware may have issues - I tried to boot from my OSX disk one last time, and it worked...
So I tried with the live CD and that worked too (sort of it booted, but couldn't get into ubuntu proper)

Got a whole new set of problems to deal with now, but that's a whole new thread!

I have an alternative disk on the way, so I have noted down your network install guidance for reference.

---

