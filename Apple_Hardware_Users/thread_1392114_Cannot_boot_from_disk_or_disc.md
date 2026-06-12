---
title: "Cannot boot from disk or disc"
date: 2010-01-27
forum: Apple Hardware Users
---

### Post by Landreville on 2010-01-27
I've installed Kubuntu (9.10 I think) on my Mac Mini 3.1 . So I have an OS X partition and an Kubuntu partition.

I got the standard no bootable device message.
I cannot boot into OS X (I dont want to get into OSX anyway) or Kubuntu.

I booted a rEFIt disc and synced the GPT and partition table.

Then I booted onto a Kubuntu live cd to re-install grub into the Kubuntu partition.  I re-installed it and tried rebooting. I got the grub menu, but must have missed a setting because it was the grub prompty. 

So I reboot to try to find the values to put into the prompt (kernel location, initrd location). But when I try to boot into the Kubuntu live cd it freezes just after ISOLINUX appears (only the top line for ISOLINUX shows up).

I tried going back into rEFIt, but it tells me the GPT and MBR are synced and it won't do anything.

If I load rEFIt and select linux, it loads to saying no bootable device -- insert boot disk....
If I load rEFIt and select the partition tool it tells me they are already synced, if I select Linux after doing that it will freeze with the tux icon in the middle of the screen.

It is obvious I need to do the next step which is install Grub, but I can't boot off any live cds! 

I have tried Kubuntu, System rescue cd, gparted live cd, os x install cd, an osx corialis boot cd I made, an older Kubuntu CD. They all freeze just after ISO Linux starts up or the OS X ones give me a do not enter sign.

Any help getting a live cd to boot would be amazing!!

---

### Post by Landreville on 2010-01-27
Here is the exact sequence of events:

1. Install kubuntu normally using second half of disk
2. Boot and get "no bootable devices"
3. Boot into rEFIt CD and sync GPT and MBR tables
4. Boot into Kubuntu Live CD to re-install grub
5. Reinstall grub by executing :
```
# grub
find /boot/grub/stage1
root (hd0,2)
setup (hd0,2)

```
6. Boot and get grub prompt 
7. Boot into Kubuntu Live CD and find the location of the kernel so I can enter into the grub prompt
8. Boot and get "no bootable devices"
9. Boot into rEFIt and it tells me GPT and MBR are already synced, then select linux -- get frozen screen with tux in the middle.
10. Boot into rEFIt and select linux (without going to partition manager first) -- get "no bootable devices"
11. Boot off Kubuntu Live CD -- freezes after showing "ISOLINUX" line
12. Boot off OS X install CD -- stops with do not enter symbol
13. Post message on forum.

My partition table is such:
sda1 efi protected
sda2 HFS+ 
sda3 Linux
sda4 Linux swap

---

### Post by llawwehttam on 2010-01-27
STOP!!!! If you are using a mac did you use bootcamp?

---

### Post by Landreville on 2010-01-27
That stop sounded pretty serious.

I'm pretty sure I used boot camp assistant to partition the drive (I actually installed kubuntu months ago, but I guess didnt restart it until now).

---

### Post by linuxopjemac on 2010-01-28
a general remark:

to boot from CD's, one can press "C" during boot and then it should boot into CD, no matter what problems on the HD. If one boots with the "left Alt" key (command key?), one should get a list of bootable devices.

---

### Post by Landreville on 2010-01-28
Yes, that is (pressing C or option/alt and choosing the CD) what I'm doing and have been doing for the times I mentioned where I did startup from a CD.

Also pressing option/alt and choosing the hard disk gives me the 'no bootable device' error.

---

### Post by dham on 2010-02-04
Same thing for me man:(.  I did almost the exact same steps.

---

### Post by linuxopjemac on 2010-02-05
"no booatable devices" means that there is no boot flag to my opinion. Try to put a "boot flag" on the Ubuntu root, from the liveCD with gparted.

---

### Post by Landreville on 2010-02-12
> **linuxopjemac said:**
> "no booatable devices" means that there is no boot flag to my opinion. Try to put a "boot flag" on the Ubuntu root, from the liveCD with gparted.
It won't boot up off a CD though.

---

### Post by linuxopjemac on 2010-02-12
what happens if you boot with the option (alt) key pressed. You should get a screen with different boot options. Select the Ubuntu CD.

---

### Post by Landreville on 2010-02-14
> **linuxopjemac said:**
> what happens if you boot with the option (alt) key pressed. You should get a screen with different boot options. Select the Ubuntu CD.

Startup of (any) CD freezes as I've stated -- please read the thread before replying.

---

