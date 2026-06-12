---
title: "kernel update from 2.6.20-15 to 2.6.20-16"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by myattb on 2007-05-28
I have just downloaded a series of security updates which have updated the Kernal from 2.6.20-15 to 2.6.20-16 and it has killed my wireless networking.

It took me about a week and a half to get it all working see thread here [http://ubuntuforums.org/showthread.php?t=442261](http://ubuntuforums.org/showthread.php?t=442261)
After the update I can no longer get connected to my network and had had to resort to windows to post here for help :(

Anyone any ideas where I should start?
I have noticed I have lost my keyring key but can't seem to replace it?
The card appears to stil be correctly installed (the power light comes up and I can see a list of networks in roaming mode).

Not sure why it should be broken after a routine(I thought) update??

Any suggestions welcome.

---

### Post by trigun on 2007-05-28
did you had to setup the module of you wireless card ?

---

### Post by ferpadro on 2007-05-28
I have also problems with the new kernel. Today morning i noticed there were new updates on the update-manager and downloaded them. When i rebooted the system, i noticed there was a newer kernel version available, and selected it to see if there were major changes. Everything seemed fine, but when i wanted to enter my virtual WinXP via VirtualBox, an error popped advicing that the vboxdrv module didnt recognize my new kernel. Maybe if i reinstall Virtualbox everything will work fine, but that would mean i have to install WinXP. So ill wait to see if there is a better option rather than reinstalling

---

### Post by wormser on 2007-05-28
You can always select the older kernel until you get it resolved.  By the way, I only saw improvements with the new kernel.

---

### Post by ferpadro on 2007-05-28
Nevermind, i initiated again with the new kernel and everything runs just fine. Maybe it needed a double restart

cheers

---

### Post by blind0wl on 2007-05-28
I can confirm that the virtualbox kernel recompile needs to happen twice before it will work.  Weird.

Cheers

Blindy

---

### Post by Happy_Man on 2007-05-28
Incidentally, does anyone have a link to a changelog? I'd like to see what's been improved.... everything's the same for me..... or so it seems.

---

### Post by onero on 2007-05-29
Hi, I wanted to ask what exactly you did to make Virtualbox work ... I upgraded my (low latency) kernel and I get the vboxdrv error as well. I've restarted twice but still no go, and when I recompile vboxdrv I get this error in vbox-install.log:

Makefile:73: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again..  Stop.


Any ideas?

---

### Post by steve.horsley on 2007-05-29
For me, trying to start a VM got me an error message telling me to run **/etc/init.d/vboxdrv setup**
which I did, and it recompiled vbox, and then failed to start it. Running the same command a second time worked and now vbox works again. 

Well done to Innotek for a fairly slick solution to having the kernel version changed. That was really quite painless.

---

### Post by mikewhatever on 2007-05-29
> **Happy_Man said:**
> Incidentally, does anyone have a link to a changelog? I'd like to see what's been improved.... everything's the same for me..... or so it seems.

Here you go [http://ubuntuforums.org/showthread.php?t=454001](http://ubuntuforums.org/showthread.php?t=454001)

---

### Post by techno-mole on 2007-05-29
ive had to go back to -15 from -16 as the update killed my networking, and i cant seem to get it working again.
i have 3 pc's in the house , mine has 2 sata drives, one with xp and one with ubuntu on, the other 2 pc's run xp and i had them all networked together, file sharing was set up nicely and everything, and then i clicked the update button and now its network death.
i can see the windows network, but the other 2 pc's dont show up, and from the windows pc's i can see my pc but cant access it as it says network path not found.
ive tried un-installing samba and re-installing and then setting it all up again but it doesnt work, went back to -15 and its all there and running as it was before i updated the kernel.
:(

---

### Post by Inxsible on 2007-05-29
My update added a phantom "CD ROM - 1" drive.

Of course I just have one CD/DVD RW -- which still shows. My fstab also has just one entry which existed before the updates too.

My GRUB however showed me 4 Ubuntu entries Regular and Recovery for .16 and also for .15

I checked that everything else worked the way it should, so I just deleted the .15 entries from /boot/grub/menu.lst

Do we need to actually uninstall the .15 kernel ...or just leave it the way it is ?

---

### Post by bobbydale on 2007-05-29
I have also install the new updates, but I am having more trouble... Here is what happens when I boot up:


```

Starting up . . . 
Loading, please wait . . .
**[NOTE: Now it will sit for a few minutes before proceeding]**
     check root= bootarg cat /proc/cmdline
     or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/desk/by-uuid/d8d6faff-8452-451a-9404-c27f5e7c9ede does not exist Dr
opping to a shell!

BusyBox v1.1.3 (Devian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs) 
```


Any ideas?

---

### Post by techno-mole on 2007-05-29
i have no idea what that means im afraid (only been using linux for a short time) can you go back to the previous kernel when you boot ? - eg - press escape before grub loads and then select the previous kernel version ? thats all i can suggest really, use the previous version until some one who knows more than me comes up with something better.
cheers.

---

### Post by bobbydale on 2007-05-29
Unfortunately, I get the same error with both kernels.  :(

---

### Post by techno-mole on 2007-05-29
ok, im no expert but that may not be so good.
sorry i couldnt be of more help, my knowledge of linux can be written on the back of a postage stamp (doing my best to learn)
cheers

---

### Post by tagrace on 2007-05-29
I had to go back to  15 as 16 will not start the x server on this machine. :(

---

### Post by bobbydale on 2007-05-29
Its no problem.  I just hope that someone else will come along with the same problem and know what occurred.  I could run a live disc and rollback some updates, but I am not sure what caused the problem.  

I ran the same updates on a different laptop last night with no problems so it did not occur to me to write down what was being installed this morning so that I could manually rollback.

If I try to run the (recovery mode) option, I get this output:

```

usb3-5.5: new full speed USB device from ehci_hcd and address 1
usb3-5.5: configuration #1 chosen from 1 choice
usb3-5.5: USB disconnect, address 1
usb3-5.5: new full speed USB device from ehci_hcd and address 2
usb3-5.5: configuration #1 chosen from 1 choice
usb3-5.5: USB disconnect, address 2
usb3-5.5: new full speed USB device from ehci_hcd and address 3
usb3-5.5: configuration #1 chosen from 1 choice
usb3-5.5: USB disconnect, address 3

```

It continues for a long time and the address starts over at 1.

This is lame.

---

### Post by Inxsible on 2007-05-29
Both my kernels worked !!
 
But after looking at so many ppl having problems, I am wondering if it was a good idea to delete the 15 entries from my grub menu :-k   [-o<    #-o

---

### Post by jamesford on 2007-05-29
two reboots and a router restart and all was fine again here

---

### Post by Inxsible on 2007-05-29
> **jamesford said:**
> two reboots and a router restart and all was fine again here
 
What was the problem ?
 
Network not working...or an extra CD Rom Drive ?
 
Or any other that I havent encountered ?

---

### Post by bobbydale on 2007-05-29
I would think that if you are booting up, then everything is ok.

When deleting entries from your grub menu, it is always a good idea to make a back up of your /boot/grub/menu.lst file:

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

My laptop is a dual-booter and WinXP will boot up fine, so I know the hardware is ok...

I am going to try booting from a live CD to compare the changes of my grub files to my backup menu.lst file.

---

### Post by Inxsible on 2007-05-29
> **bobbydale said:**
> I would think that if you are booting up, then everything is ok.
 
When deleting entries from your grub menu, it is always a good idea to make a back up of your /boot/grub/menu.lst file:
 
```
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
 
My laptop is a dual-booter and WinXP will boot up fine, so I know the hardware is ok...
 
I am going to try booting from a live CD to compare the changes of my grub files to my backup menu.lst file.
 
Well the only change I made was to remove the entry for 15. I know its not the best of solutions, but I can again add those entries by copying over the 16 entries as that was the only difference between them. 
 
I haven't uninstalled the 15 kernel...is there a necessity to do that ?

---

### Post by luvr on 2007-05-29
> **Inxsible said:**
> I haven't uninstalled the 15 kernel...is there a necessity to do that ?
There's no real need to uninstall the older kernel.
If you won't ever boot into the older kernel again, then you no longer need to keep it installed, but nothing bad happens if you keep it around either.

---

### Post by bobbydale on 2007-05-29
Figured it out.

Something changed my /boot/grub/menu.lst

New Entry:
```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel         /boot/vmlinuz-2.6.20-16-generic root=UUID=d8d6faff-8452-451a-9404-c27f5e7c9ede ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

For my system, the "kernel" line should have been:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/sda2 ro quiet splash
```

I have Ubuntu installed on that partition.  I am not sure what the long string of numbers is that was added.  I think it may be the serial number of the hard drive.

I hope this helps someone in the future.

Now... If I can just figure out how to tune the parameters of my kernel...

---

### Post by Inxsible on 2007-05-29
> **bobbydale said:**
> Figured it out.
 
Something changed my /boot/grub/menu.lst
 
New Entry:
```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel         /boot/vmlinuz-2.6.20-16-generic root=UUID=d8d6faff-8452-451a-9404-c27f5e7c9ede ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```
 
For my system, the "kernel" line should have been:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/sda2 ro quiet splash
```
 
I have Ubuntu installed on that partition. I am not sure what the long string of numbers is that was added. I think it may be the serial number of the hard drive.
 
I hope this helps someone in the future.
 
Now... If I can just figure out how to tune the parameters of my kernel...
 
The UUID is just another way of identifying your drive. It should have been the same before (the UUID I mean)
 
But since you can log in using the drive name itself (/dev/sdX) ..thats gr8 !!

---

### Post by myattb on 2007-05-29
I have rebooted in 2.6.20-15 but my wireless key is missing from my keyring (from when I was trying to get wireless working under 2.6.20-16 and failed, and I need to enter each time to connect).
How can I get the key back into the keyring so I don't need to do this anymore?
Also how do I best remove 2.6.20-16 from my system/startup grub menu without breaking anything else?

Thanks.

---

### Post by techno-mole on 2007-05-29
ok, ive fixed my little networking problem.
i had to remove the linux restricted modules for the previous kernel version.
i then removed samba through apt-get, and then i did apt-get remove --purge samba.
i went through the file system and changed the shared folders back to normal, and removed any i had set up through administration - shared folders etc etc.
then i re-booted, installed samba through synaptic and set up the shared folders again - administration - shared folders and set up the folders i wanted to share.
and now it works, one thing i had to do was change the shared folder on the windows pc to allow network users to modify its files, i also changed it from read only and it all works now.
just thought id post this as it may help some one.
cheers.

---

### Post by mlentink on 2007-05-29
If it helps, i'm pretty sure that the update wrecked my wireless. I have a Sweex (=Atheros) card that worked fine yesterday, but ath0 wasn't even visible after the update. Rolling back ti 2.60.15 everything is back to normal. I have yet to find out how to remdy this

EDIT: Solved. The update did NOT also install the necessary linux-restricted-modules-2.60.16. After installing them, everything was fine again

---

### Post by -X- on 2007-05-29
This latest update killed my atheros as well but rolling back hasn't solved anything for me. Will attempt to uninstall most of the old kernel stuff and do some other hokus pokus.

---

### Post by casley on 2007-05-31
Yep. Two recompiles required worked for me too. Ta.

---

### Post by mysexybluefeet on 2007-06-01
How do you roll back to kernel 2.6.20-15 from 20-16??

I can start it by esc at reboot but i'm giving it to my sister and need it to work properly

thankyou

A
[email]myspot@mail-me.com[/email]

---

### Post by jeremy on 2007-06-01
comment out the 2.6.20-16 lines from your /boot/grub/menu.lst

---

### Post by mysexybluefeet on 2007-06-01
it tells me that i don't have the premissions. how do i get user acess to change the premissions or otherwise change this.

I found the synaptic program manager, would deleting the three ubuntu kernel 2.6.20-16 packages work? There's a header, a generic header and an image generic

---

### Post by Happy_Man on 2007-06-01
Stick this in a terminal: (Applications --> Accessories --> Terminal):

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by mysexybluefeet on 2007-06-02
Oh, you guys are so awesome, thankyou so much!!!

---

### Post by hasimir44 on 2007-06-12
kernel 2.6.20-16 changed my ath0 to ath0-??? (sorry can't remember..). I rebooted to kernel 2.6.20-15 and ath0 was back and connected - checked my restricted drivers and both were active (nvidia and atheros hal)  rebooted back to kernel 2.6.20-16 and everything is fixed.

---

