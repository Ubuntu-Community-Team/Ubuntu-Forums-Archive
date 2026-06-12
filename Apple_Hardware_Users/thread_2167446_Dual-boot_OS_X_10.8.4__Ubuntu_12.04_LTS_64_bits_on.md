---
title: "Dual-boot OS X 10.8.4 / Ubuntu 12.04 LTS 64 bits on MacBookPro9,1"
date: 2013-08-13
forum: Apple Hardware Users
---

### Post by Q7YspEs on 2013-08-13
Hi everybody,

I'm trying to install Ubuntu 12.04 LTS 64 bits along with OS X 10.8.4 (dual-boot) on my MacBookPro9,1.
I've spent almost 2 days on it so far and I've not succeeded yet.
I knew it wouldn't be child's play so I had googled quite a few times before doing anything. I noticed that the most part of the articles were referring to 3 major steps:
1) install rEFIt;
2) create a new partition for Linux with Boot Camp or Disk utility;
3) reboot on Ubuntu LiveDVD and install Ubuntu on the aforementioned partition with the appropriate partitioning scheme (swap, data and system at least).

As amazing as it sounds, I'm stuck with step 3, the easiest one I would have said! Indeed, I cannot boot on my LiveDVD from rEFIt (rEFInd actually as rEFIt doesn't seem to be supported anymore): when I click on my DVD during the boot process, 2 things may occur:
- the screen goes in text mode and freezes eventually (likely after the usb initialization) ;
- or Ubuntu is ready for installation but freezes just after the network configuration step (I get the waiting icon next to the mouse pointer).
I've tried many many things (install rEFInd on ESP, install rEFIt instead, download the 32 bit version, download 13.04 instead, reboot multiple times), with no avail.

Does anybody have a suggestion?
Thank you in advance,
Jean-Laurent

---

### Post by Earle_Kirkley on 2013-08-14
Jean-Laurent,

I had a similar problem not long ago with my late 2008 pro.  The solution seems to be opting for the nomodeset function before continuing with the install.  This change can be made at the main boot menu of the ubuntu disc.  Before you choose to Install or Try, press the F6 key and select nomodeset, hit enter to check the selection, and then esc to go close the popup.  Then select your option from the main menu.

Good luck,

Earle

---

### Post by Q7YspEs on 2013-08-14
Hi Earle/everybody,

Thank you for your answer, your feedback is really appreciated! :)

I did what you suggested (reboot with "C" key, press F6 and select option nomodeset, then try and finally install), and it worked!!
However, I'm still having the issue at another stage now :/ Indeed, I cannot boot on my new fresh Linux partition...
When I start my computer, I have the rEFInd boot manager as expected which mainly proposes : booting on my OSX partition and "boot Linux from EFI". However, the only thing I get when I choose the latter is...a blinking cursor on a black screen! And it doesn't help to wait... I think there is a problem with my boot manager or boot loader but I don't know where exactly... (drive encryption is not enabled for your information).

Could you/someone help me again?
Thank you in advance!!
Jean-Laurent

---

### Post by Q7YspEs on 2013-08-17
Considering the fact that the "nomodeset" option helped me to get the following screens and then install Ubuntu, I think I should need to boot with that option everytime I restart my computer. The problem is that there is no such option in rEFInd prompt screen, isn't it? Indeed, the only option I have is by pressing F2 which offers the choice to boot with my Linux or to go back to the menu, that's all!

Please help me as I'm somewhat hopeless...
Thank you!

---

### Post by Quackers on 2013-08-21
Yes, you need to get to the grub menu but I'm not sure how to do that on a Mac.
Once the grub screen appears you can add the nomodeset boot option to the end of the kernel line (after pressing the e key whilst the grub menu item you want to boot is highlighted). Once you are booted into Ubuntu you can either edit the grub file or maybe install the appropriate video driver for your card whiwh will mean that the system can boot without the boot option.
Once you've selected the Ubuntu logo in rEFInd try tapping the shift key and see if a grub menu appears.

---

### Post by Tinka on 2013-08-21
I was able to get Ubuntu 13.04 installed with relatively little hassle. If you aren't dead set on using a LTS version I would go wtih the newest possible version as the hardware is better supported

---

### Post by Q7YspEs on 2013-08-25
Hi everybody,

Thanks for all your advices. It works now! :)
For your information, I followed this excellent tutorial: [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/) (I used a bootable usb stick created with Unetbootin).

Thanks again.

---

### Post by Quackers on 2013-08-25
Glad to see you're up and running.
I recently installed 13-04 to my MBPr 10,1 and did not follow that guide. I ended up with no rEFInd menu entry for Ubuntu so could not boot it.
I contacted Rod as he used to be a member here and he gave me a simple enough fix so that now I'm booting off an EFI stub loader (I think) which means no grub menu, which is ok so long as I don't have a booting problem.
Saldy I can't remember the fix he gave me :-( I'll look into it and post back.

EDIT  I've remembered! I installed the ext4fs EFI driver and then rEFInd detected the Ubuntu install and loaded an icon for it in the boot menu.

---

