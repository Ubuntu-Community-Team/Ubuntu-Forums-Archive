---
title: "Problems with USB Live Boot - Ubuntu 13.04 w/ MacBook Pro with Retina"
date: 2013-12-10
forum: Apple Hardware Users
---

### Post by codygraham22 on 2013-12-10
**Setup:**
[LIST]
[*]Apple MacBook Pro w/ Retina Display - 15.4"
[*]Mac OS X 10.9 Mavericks
[*]2.4GHz Intel Core i7
[*]8GB 1600 MHz DDR3
[*]Intel HD Graphics 4000 1024 MB
[/LIST]
**Goal:**
I am currently looking to boot Ubuntu 13.04 via USB Live Boot.
**Current Procedures:**
I am currently using a PNY 16GB USB Flash Drive (FD). I formatted and partitioned the FD via "Disk Utility". It is formatted as MS-DOS (FAT) and the partition map scheme is Master Boot Record. Once I completed this I used the app "Mac Linux USB Loader". I used the Download Distribution tab to download "ubuntu-13.04-desktop-amd64-+mac.iso". After this was downloaded I used the Create Live USB tab, then selected the file, open, Erase Existing EFI Boot, and Make Live USB. Beforehand, I made sure that it was directed to the USB which it was. I did not eject the FD and proceeded to reboot the MacBook. Once I heard the "chime" I held down the "opt/alt" key until I had three boot choices. Mac OSX, Mac OSX (back-up), and my EFI Boot. (Names are not exact but you get the picture). I selected the EFI boot (FD) option which had my Ubuntu file included.
**Problem:**
[LIST=1]
[*]Upon boot of Ubuntu 13.04 via FD it gave me the standard script "Fasten your seatbelt, we're loading your kernel...". Directly after this page it moves to a solid black screen with some odd colored pixels in a thin line up at the top of the screen. It then goes to a white screen with colored zig-zag blocks and proceeds to a black screen. It ceases to do anything afterwards.
[*]On occasion it works*. On occasion it moves past the Ubuntu Linux loading screen and then moves to a box that claims that it can only perform "low-graphics" and must be put in "low-graphics" mode. It freezes once I looked to move past these screens.
[/LIST]

The internet has an extreme/overwhelming amount of solutions. I'm looking to seal the deal and get Ubuntu running. Please, if you will, place the answer in lamen terms. I am not a computer-guru by any means but understand it enough to get around.

---

### Post by sudodus on 2013-12-11
Welcome to the Ubuntu Forums :-)

There is a lot of information how to do it at this link to a wiki page

[https://help.ubuntu.com/community/In...n/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

There is also a reference to a current thread at the Ubuntu Forums about doing it for Macs

[https://help.ubuntu.com/community/In...e_from_Mac_OSX]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Mac_OSX")

-o-

I should also mention that it it difficult to boot from some USB pendrives (although they work well as mass storage devices).

- The problem might be the PNY flash drive ***hardware***.

It might also be a ***software*** problem.

- Did you check with ***md5sum***, that the download was successful?
- Try some other method to make the pendrive bootable from the iso file.

So test the pendrive in another computer, for example a PC with Windows.

---

### Post by codygraham22 on 2013-12-11
I used VirtualBox to boot up Ubuntu. I installed "unetbootin" to the virtual hard drive and went through a similar process as stated above. It worked. It booted, asked if I wanted to install, the whole nine yards! I don't know exactly what was the difference, however, I was not about to question it. I'm currently working on being able to install Ubuntu on a portable hard drive which is currently put on stall until I'm able to get my hands on a 1TB I've been eyeing. I'll look to partition the external HDD and continue to work on this. Thanks for your reply I used this both of them which led me to experiment with some similar and alternate ways.

---

