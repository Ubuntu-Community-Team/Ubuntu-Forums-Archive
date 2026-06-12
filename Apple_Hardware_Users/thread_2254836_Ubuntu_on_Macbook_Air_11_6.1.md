---
title: "Ubuntu on Macbook Air 11 6.1"
date: 2014-11-30
forum: Apple Hardware Users
---

### Post by dondondonkaibudafl on 2014-11-30
Hi Forum,


I'd like to share my ubuntu + yosemite dual boot experience. In fact, I installed mac osx and ubuntu more than three times until I felt they're perfectly settled. But, I have to confidently say, at least, macbook air is a very ideal choice for ubuntu. Issues such as swapped key on both of my built-in and external apple keyboards are not happened, the keys are perfectly mapped. Some solutions in this post is synthesized through my random search, please forgive me not remember where I exactly found (part of) them. I do appreciate and am proud of how vital the linux community is. And I am a non-CS background ubuntu user brought up by this amazing community.

[B]Hereunder is what I have now:
[/B]
- Macbook Air 11 inch mid-2013 (6.1)
- Dual boot with Ubuntu 14.04 and OSX Yosemite
-- i7-4650u
-- SSD 256GB
-- Memory 8GB
--- Apple Magic Mouse (excellent)
--- Apple Keyboard with Numeric Keypad (excellent)
--- Wacom Intuos Creative Pen & Touch Medium (overly sensitive in touchpad mode)
---- Battery life: 5 hours of development with Wifi on, 8~12 hours of development with Wifi off.

 
**Finalized Ubuntu 14.04 Dual Boot Installation:**
1. Freshly install Yosemite and encrypt and decrypt to turn core storage back into HFS+ and enable partition resizing using FileVault
2. Get an Ubuntu compatible wifi adapter or network adapter ready at hand, follow Ubuntu MactelSupportTeam's [instruction]("https://help.ubuntu.com/community/MacBookAir6-2/Trusty") and fix reFind with this [post]("http://www.maketecheasier.com/fix-dual-boot-issue-with-yosemite-ubuntu/")
3. Fix kworker thread's high cpu consumption. I feel the simplest way is to put the script in rc.local (please see below)
4. Fix cpu capped at base-frequency (please see below. edit and update grub doesn't help in my case)
5. If you would like to encrypt home folder, please be aware of the sometime home folder unmount issue and unmounted swap due to wrong partition UUID.
6. Done, works better than installing on some of my pre-2010 PC laptops.


[B]The problem I've met whatever solved or not:

[/B][I][B]Part 1: Common issues
[/B][/I]    [solved] reFInd not detected
    [solved] triple entries of ubuntu icons in reFind menu
    Broadcom bcm4360 wifi adapter slow connection with certain wifi routers
    [solved] Backlight issues after suspend
    iSight

[I][B]Part 2: You got to fight with them for a while ....
[/B][/I]    [solved] Yosemite fresh install and HDD not resizable on core storage format
    Yosemite prefers to corrupt the shared exfat partition
    [solved] CPU capped at base-frequency 1.7GHz
    [solved] kworker thread constantly consumes 70~80% on one of my cpu core
[solved] Separate and encrypted home folder results ??? in no swap partition mounted 


[B]Special Notes:
[/B]
[I][B][solved] Yosemite fresh install and HDD not resizable with core storage format:
[/B][/I]
For those of you considering a fresh install for both of your Yosemite and Ubuntu, the Yosemite's un-resizable core storage currently has no easy solution. This is the way I feel safe to cope with: turn on FileVault encryption and turn off it to decrypt the core storage, then you'll see the disk becomes HFS+ againg and resizable for your ubuntu installation.

[B][I]Yosemite prefers to corrupt the shared exfat partition:
[/I][/B]
In the end, I choose to use non-journaled HFS+ partition and create a folder permits my ubuntu user to use.

[B][I][solved] CPU capped at base-frequency 1.7GHz:
[/I][/B]
It is due to bios sets max frequency to 1.7GHz and the cpu won't work above 1.7GHz regardless 'turbo boost turned on or not'. Interestingly, editing /etc/default/grub does not help me to turn off the bios limit. I endded up with putting the following script in /etc/rc.local:
```
echo 1 | sudo tee /sys/module/processor/parameters/ignore_ppc
for x in /sys/devices/system/cpu/cpu[0-3]/cpufreq/ ; do
        echo 2301000 > $x/scaling_max_freq;
done
```
And, one more thing, I found setting max-freq to 2300000 will not enable turbo boost, but any value equal to or above 2301000 will allow my cpu to go to 2.9~3.3GHz automatically.

[B][I][solved] kworker thread constantly consumes 70~80% on one of my cpu core:
[/I][/B]
In my case, I disabled /sys/firmware/acpi/interrupts/gpe66 with the following script in rc.local and everything works normal afterwards.
```
set +o noclobber
echo "disable" > /sys/firmware/acpi/interrupts/gpe66
```


That's all, hope my experience may help some of you. I did actually spend nearly a whole week and forgot to go shopping on Black Friday!

---

### Post by wmoore on 2015-02-11
Thank you. Very, very helpful. I have been struggling with getting the CPU to 'turbo boost' beyond the base maximum and your script did the trick for me :)

Edit: I'm actually on Macbook Air 6,2 but it works just the same.

---

### Post by dondondonkaibudafl on 2015-04-14
Thanks wmoore. By the way, these scripts are found somewhere else and modified (a bit) if problem still present. It was too rush to note down where the original scripts over that weekend! The primary reference of the base frequency issue might be in Arch linux docs. I'll update the post with the reference nexttime when I need to reinstall the system.

---

