---
title: "xubuntu on a macbook"
date: 2015-01-07
forum: Apple Hardware Users
---

### Post by maclenin on 2015-01-07
In the wake of my first A to e maclinux conversion, I thought I'd leave a few notes to aggregate googling and to, perhaps, rustle up additional discussion and learning.

Essentially, the task was to complete a linux-only install of xubuntu 14.04.1 (64 bit) onto a MacBook 6,1 (late 2009, nvidia video card, usb isight webcam).

In my case, the MacBook's cd/dvd drive was broken, so in lieu of the LiveCD, I was "compelled" into attempting a "LiveUSB" (stick) install.

The linux box I used as the "source" is a desktop running xubuntu 12.04 (32 bit).

Over the course of the install and afterwards, a few (already fairly widely-reported) issues arose:

i. EFI booting - solved by 64 bit xubuntu .iso having an EFI boot option, which was deployed / preserved during the startup disk creation process (see step 3.)
ii. purple line / blank screen at boot / nomodeset - a video driver-related issue which seems to have been temporarily managed by modifying grub (see steps 15. and 30.)
iii. unable to restart / reboot using any method, including shutdown -r +0. I am only able to shut down using shutdown -h (issue still unresolved)
iv. uneven isight webcam usablility (i.e. works in cheese and not in mugshot - issue still unresolved)

All issues are in various phases of resolution but none have proven to be show-stoppers.

Other familiar "issues" related to touchpad usability / temperature / etc  are, in my view, "wonky" fine-tuning pursuits and can be part of any linux install across all hardware platforms - so, I don't count those as Mac-specific issues worth highlighting in my intro. Of course, if folks have suggestions for fixing, please post them, but I have not been bothered during this install by this usual gaggle of difficulties.

So...without further ado:

**A. PREPARE A BOOTABLE LIVEUSB ON LINUX BOX**

1. Dowload (64 bit) xubuntu .iso

2. Insert (~2BG) USB stick

3. Open Startup Disk Creator

4. Select xubuntu .iso as Source disk image

5. Select USB stick as Disk to use

6. Erase Disk and Make Startup Disk (without adjusting any other settings)

7. Remove newly created / bootable LiveUSB

**B. INSTALL XUBUNTU ON MACBOOK**

8. Start / restart MacBook and wait for tone

9. Press and hold Alt (or Option) key (to left of space bar) to enter Startup Manager

10. Once "Macintosh HD" and "Recovery-10.x.x" appear as startup options, insert the LiveUSB. It will appear on screen as "EFI Boot"

11. Highlight "EFI Boot" and press enter to select it

12. The GNU GRUB menu will appear

13. Highlight *Try Xubuntu without installing

14. Press e to edit commands before booting

15. Replace quiet splash with nomodeset on this line - to address the video driver start-up / blank screen issue:
```
linux /casper/vmlinuz.efi file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash --
```
16. Press F10 to boot

17. "Try Xubuntu" for while, if you choose. I did so, for pre-install testing purposes; notice the MacintoshHD drive / icon on the desktop

18. Double-click the Install Xubuntu desktop icon

19. Choose standard install options (for the most part) throughout the install process

[B]CRITICAL JUNCTURE: WARNING! ASSUMING YOU WISH TO INSTALL XUBUNTU ONLY AND _NOT_ DUAL-BOOT (as I did):

20. Select Replace Mac OS X with Xubuntu at the installation type options page[/B]

21. The installation should complete without issue and when asked, choose to "continue trying xubuntu" and then execute a "halt" shutdown via the terminal, to shut down the MacBook...
```
sudo shutdown -h +0
```
...do not restart (via dialog or terminal), as this will most likely cause the MacBook to freeze.

**C. BOOT INTO NEW XUBUNTU INSTALL ON MACBOOK**

22. With reference to step 15., follow steps 7. - 16. to (re)boot into the LiveUSB environment to tweak the video driver start-up settings of your new xubuntu install - nomodeset needs to be made permanent in the new install in order for it to boot properly (i.e. without purple lines or solid black screens)

23. Once the LiveUSB environment is up, you'll notice that the "MacintoshHD" drive / icon has been replaced by a "xxx GB Volume" drive / icon - this "xxx" drive contains your new xubuntu install

24. Double-click on the xxx drive icon to mount the drive in /media/xubuntu/<uuid> - with uuid being a very long alpha-numeric "universally unique identifier" 

25. Open a terminal and cd into the directory into which the new xubuntu install has been mounted - for example:
```
cd /media/xubuntu/<uuid>/
```
26. Mount these additional directories from your new xubuntu install into the current ( /media/xubuntu/<uuid> ) directory in the following manner:
```
sudo mount -t proc proc proc/
sudo mount -t sysfs sys sys/
sudo mount -o bind /dev dev/
sudo mount -t devpts pts dev/pts/
```
27. chroot into the new xubuntu install - to permit editing of the (non-booted) new install environment
```
sudo chroot /media/xubuntu/<uuid>/
```
28. Edit the grub file (be careful **NOT** to use / before etc, as you are editing the new install, not the current LiveUSB environment, whose etc directory would take the leading /)
```
root@xubuntu:/# nano etc/default/grub
```
29. Replace quiet splash with nomodeset on the following line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
30. Enter Ctrl+x to exit the grub file and Y then enter to save any changes

31. Update grub
```
root@xubuntu:/# update-grub
```
32. Exit the chroot environment
```
root@xubuntu:/# exit
```
33. Unmount the additional directories
```
sudo umount {proc/,sys/,dev/pts,dev/}
```
34. Return to the home directory
```
cd
```
35. Halt (do not restart or reboot) the LiveUSB environment
```
sudo shutdown -h +0
```
36. Power the MacBook back up and you should boot straight (and un-splashedly) into your shiny new xubuntu install!

With all due deference (and with more to come):

[chroot nomodeset grub]("http://askubuntu.com/questions/270753/how-to-delete-nomodeset-from-my-grub-file-in-order-to-boot-normally?rq=1")
[nomodeset ]("http://askubuntu.com/questions/498267/trouble-installing-ubuntu-14-04-on-macbook?rq=1")
[macbook grub]("http://ubuntuforums.org/showthread.php?t=1931658")

Good luck to others and thanks for any comments, suggestions or criticisms!

---

### Post by bunkerdesign on 2015-01-20
Very useful thanks! did you manage to install the nvidia drivers?
I'm having a black screen after reboot (Macbookpro 6.2, geforce 330M, Ubuntu 14)

Cheers
Julien

---

### Post by maclenin on 2015-01-20
**bunkerdesign!**

Thanks for the comments.

As for the black screen: In my case, (and, perhaps, in yours) after install, I stuck with the "nomodeset" configuration I had establisehd via **C. BOOT INTO NEW XUBUNTU INSTALL ON MACBOOK** - and decided (at the get-go) NOT to install any of the nvidia drivers - as all was working well in "nomodeset" mode (i.e. no more "black screen").... The MacBook was configured for a friend, so I, unfortunately, don't have the system to hand, however, I did a fair amount of testing (with nomodeset) before I handed the machine off....

Incidentally, and with reference to sussing out issues related to system configurations (generally - not only related to video drivers), post-os-install, I would HIGHLY recommend installing the [_inxi_]("http://ubuntuforums.org/showthread.php?t=2260254&p=13205188#post13205188") system info script / utility - nimble - and easy to use (via the terminal)....

Good luck!

---

### Post by mörgæs on 2015-01-24
Thanks for the guide. 

It will benefit more users if you a) mark it 'solved' and b) write a brief post in the [compatibility list]("http://ubuntuforums.org/showthread.php?t=1543006") linking to this thread.

---

### Post by maclenin on 2015-01-24
**mörgæs!**

Takk for your comments. I will do as you suggest.

I hadn't yet "solved" the thread, as there are a few "unsolved" issues described in the guide. However - more attention (as you indicate) may bring solutions!

In general, the end-users are quite pleased with their resurrected MacBook!

---

