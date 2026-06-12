---
title: "Problems w/ X server in Ubuntu 13.10 on MacBook Pro 4,1 (Early 2008) w/ 4GB RAM"
date: 2014-04-01
forum: Apple Hardware Users
---

### Post by maxbar on 2014-04-01
My setup:

[I have this MacBook Pro model]("http://www.everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-15-early-2008-penryn-specs.html") upgraded to a SSD and 4GB Apple approved RAM... and DVD drive doesn't work anymore though. Runs OS X up to currently newest version (10.9.2 Mavericks) fine, albeit slow (of course :rolleyes:).


What I want to do:

That's why I want to put Ubuntu on it. I made space on the SSD and created a second partition for installing to and running Ubuntu from. Once it's up'n running, I'll copy over my data and remove the OS X partition and re-size the Ubuntu partition to use the full disk (after a full partition backup via 'dd' to my memory stick... just in case).


My install media:

I dl'd and flashed ubuntu-13.10-desktop-amd64.iso (and later on read to try ubuntu-13.10-desktop-amd64+mac.iso) to a 64 GB Patriot USB stick via [the UUI utility]("www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") that is suggested on this site in Windows on my desktop PC.


What I tried:

After installing ReFind (as ReFit is outdated according to their site) I booted up the ubuntu-13.10-desktop-amd64.iso via USB stick to start installation - black screen after selecting either the LiveCD option or Install. After some googling I read to press 'e' at the purple menu screen (GRUB) at the entry "Install Ubuntu" (or something like that) and add at the end of the line "nomodeset" (w/o the double-quotes ["]) and pressed F10 to start the boot process into the installer with the change. Installer loaded into graphics mode, I didn't want to run through the software update at that point in time to speed things up and so I selected not to connect to the Internet via WiFi and to do the Ubuntu One thing, install finished and I confirmed reboot.


Problems:

After booting, command prompt, no GUI (Xserver). Logging in and 'startx' brings an error message at the end of a bunch of output, saying that no display was found and before that some other error messages about some libs being unsupported, or something like that, don't remember in detail. I've been at this for now 4 days. 

I also tried out the +mac.iso, as that was suggested somewhere, but it doesn't boot if flashed to the USB stick with a format - however, first putting on it the non-mac iso (selecting "format" in UUI) and then flashing on top of that the +mac iso (no "format" in UUI this time) makes it boot and I succeeded in the installation.

So, after Xserver not starting up, I googled some more and, because my MBP has a "NVIDIA GeForce 8600M GT", I found a link to a page with instructions to add the repository and how to install the drivers and compatibility listing - and the 8600M GT was listed there. After doing all that, running an update / upgrade again just in case, rebooting, but same result.

Googling some more it was suggested to re-install the nvidia drivers and blacklisting 'nouveau', now brought a black screen, not even the login console screen was shown anymore. I even tried adding 'nomodeset' or 'nofb' and even both together, yielded only the difference of a blinking cursor at the top-left.

Also, WiFi doesn't work, but right now less of an issue, as plugging in an Ethernet cable works out of the box - so fixing that I can try at a later time.

And that is where I'm at now, IDK anymore what else to do. Also I can't seem to be able to get to the console anymore.

I don't mind re-installing everything again, if necessary, but only if someone can provide an exact step-by-step guide for exactly my model - because I had followed all the other guides, and none worked and most were anyhow for older Ubuntu releases. I would be willing to install 12.04, if it's guaranteed to run on my model and there's a step-by-step guide for it.

I really hope someone has a final solution for me, I've been spending many hours on several days on this already, it's getting to the point where I'm ready to just give up. BTW, I also tried to install newest version of Mint, but that was even worse, I think it didn't even boot into the installer correctly, even with 'nomodeset'.

---

### Post by maxbar on 2014-04-04
After almost a week of having re-installed various versions of Ubuntu (and some Linux Mint versions too) and having followed various driver install / re-install / xserver configuration methods and who knows what else, I was about to give up... until I came across [this post]("http://askubuntu.com/questions/228592/blank-screen-at-boot-ubuntu-12-04-nvidia-current-macbook-air-3-2"), which actually explained why the issue my system had could be related to GRUB - which is a boot loader and shouldn't have anything to do with a boot loader at all, at least that's how I saw it, until, again, it was explained in there.

To make a long story short, here are from-scratch instructions on how I successfully installed Ubuntu 14.04 (though probably also works w/ other versions) on my MacBook Pro 4,1 (early 2008) via USB stick (probably works same mostly if installed from optical media):

*** Disclaimer Start ***
I'm writing this from memory a few hours after I have done most of this - there could be some errors / omissions I made by accident. Whether there are or there is not, I do not take any responsibility for any unforeseen outcome you might experience. To my best knowledge, however, this worked for me as described, for my specific hardware (MacBook Pro 4,1 Early 2008, 4GB RAM upgraded from 2GB, 60GB SSD upgraded from whatever GB mechanical HD originally the computer came with, OS/X 10.9.x). Make sure you have the necessary experience to follow each of the following steps, and, if necessary, make adjustments to these. Therefore, read all of the steps first, before attempting to follow these, because you could destroy all existing data that currently resides on the media that you put the Ubuntu installer on, or that of the computer that you use to put that installer on, or the computer that you want to install Ubuntu on (and possibly other unwanted things might happen)! Again: I'm not liable for anything in consequence to someone following these steps!!!
*** Disclaimer End ***

0. Read the disclaimer - _do not proceed if you do not fully understand the disclaimer and consent to it - and (!) you do not have any sort of experience with the following steps (in other words, if there's anything unclear for you in what I wrote, read beginner's tutorials on the topic, or get someone with the necessary experience to do this for you(!) )_ - in such a case PM me through here and I might help you with this. I might give some pointers to how to do it differently in here, but have not done so myself (such as, I only used a USB stick, I did not use a CD/DVD) and as such I might give there incorrect info.
1. Download of ISO install image (in my case: ubuntu-14.04-beta2-desktop-amd64.iso)
2. Download software to transfer ISO to USB stick (or burn it to optical media) - I used [UUI]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and when within the app, after choosing the ISO and selecting the USB stick, I selected "format".
3. On the MacBook within OS/X, download and follow install instructions for [ReFind]("http://sourceforge.net/projects/refind/") (you simply extract the downloaded file, open terminal, change to the folder - probably "~/Downloads" - and run the installer - I think something like "./install.sh").
4. Also, make sure you have an empty partition (w/ at least I think 6GB free disk space, mine had 8 or 10GB) on either that drive or an external drive / USB stick (install should work on other USB sticks but not on this one, installer will give you an error if you try and install on same USB stick), to install Ubuntu on. In my case, I booted from an OS/x recovery DVD (won't work just to go into recovery mode on your installed disk!) and used the disk editor there to shrink existing OS/X partition - because I want to keep OS/X on there for now, might delete it eventually though (most likely :P).
5. "Eject" and insert USB stick / optical media into MacBook computer.
6. (Re)boot MacBook computer - you might have to hold down the ALT button as soon as the computer restarted, to bring up the boot device selection. If the USB drive doesn't show up, I selected the first option and ReFind's menu was shown, where the USB stick (or even 2 versions of it) are shown - one might boot opposed to the other one.
7. A purple colored screen should show up with a frame and some boot options - use the down cursor key to select the "install" one but don't press enter, instead press "e" and then press the down cursor key several times and then the left cursor key a few times so you're in front of the "--" on the "linux ..." line (it's probably broken down into two lines because it's too long to fit all in one line) and add "nomodeset". You might also delete "quiet splash" just so you see any errors that might show up in the output when booting, in case it doesn't boot.
8. Press the "F10" key to confirm the changes and boot with those. Keep in mind that these changes are not written to the USB stick, thus they are only temporary and you'll have to repeat those if you want to repeat all this.
9. When it comes to choosing between the different install methods, I chose the last one (I think "custom" or "do something else") at which time a partition editor is displayed, in which I selected the empty space, added the partition to install Ubuntu on, selected "/" as the install location and EXT4 as the file system.
10. Then I selected "continue" or similar - it gave me a warning that I didn't have a swap partition, with which I was fine with, but you might want to add one.
11. I selected "connect to Internet" and "update during install" (if you connect to as hidden SSID, you'll probably need to right-click onto the WIFI icon at the top-right of the screen in the menu bar, and do it that way, then select "connect to Internet").
12. Follow rest of install procedure and install runs through, then reboot and take out the USB drive when screen turns black (might be optional but I prefer to do that).
13. You might have to follow procedures like in step 6., in my case my MacBook booted straight into the new bootloader (purple background).
14. Press cursor down and select "safe boot" or "additional options" or such version, not the first one that should just say "Ubuntu".
15. Still on the purple background bootloader screen with a new menu and go with the first boot entry (I don't remember if you have to press "e" again and make the same changes as in step 7, though I think you don't).
16. After the boot process completed, you should see a text menu again, on a black background. Select the first entry and you should be booting into "safe graphics" mode, same mode as used when booting into the graphics installer.
17. Now open a terminal and type in "sudo apt-get install grub-pc" and press enter.
18. After that's done with, reboot, and in purple menu select this time the first entry ("Ubuntu") and press enter - no editing of boot commands necessary.
20. This should bring up Ubuntu's graphical login screen at wonderful 1440x900 :D
21. I haven't tried this out after all the above but did so before and I just got a black screen after reboot: select in "system settings" under "software & updates" and "additional drivers" tab and select the Nvidia driver. I don't need 3D acceleration or possibly better 2D graphics performance, so I'm not going to risk doing this and possibly ending with a black screen again and possibly having to do the whole re-install again... so just be forewarned. It might work though, but I'm not going to risk it, just saying.

---

### Post by maxbar on 2014-04-05
BTW at step 18. the screen will go black first and after a short delay the boot menu with the purple background shows, but this time the screen resolution is changed to a lower one - this means that grub-PC is active.

---

### Post by maxbar on 2014-04-05
After a upgrade and update, I had the same display issue w/ black screen before, so I went into ubuntu again with "nomodeset" and at terminal:

sudo apt-get install --reinstall grub-pc

After a reboot the same again. Shutting down and booting up again, this time holding down "alt / option" key immediately after pressing the power button, until I was presented with boot options. I selected the first and when the ReFind menu showed up, I selected the third (I think it said "Linux boot") and the lower-resolution boot menu on purple background was shown again and selecting the first entry, "Ubuntu", booted up in proper Xserver hi-res accellerated mode again.

Maybe the re-install of grub-pc isn't necessary, but having to boot by going first into ReFind via "alt / option" key seems to be necessary from now on... unless somebody knows how to fix that - but I can live with as it is right now :)

---

