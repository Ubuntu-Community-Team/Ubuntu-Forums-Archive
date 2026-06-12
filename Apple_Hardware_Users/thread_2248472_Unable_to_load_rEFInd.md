---
title: "Unable to load rEFInd"
date: 2014-10-15
forum: Apple Hardware Users
---

### Post by yousufinternet on 2014-10-15
Hello every one, 

I have recently installed ubuntu 14.04 on my MacBook Pro 9,2 , I installed it side by side with Mac OS X, and used rEFInd to boot into ubuntu, then I have decided to use the Mac OS X partition as my home folder, so I formatted it and moved my home folder into the new formatted partition, to discover after restarting the computer that the rEFInd loader was formatted with the partition, I was able to boot again into ubuntu by installing rEFInd on a flash drive and booting from it, I have tried to install rEFInd again through ubuntu using the install.sh file but was unsuccessful too, it gives me the following message: 

> Installing rEFInd on Linux....
ESP was found at /boot/efi using vfat
Found rEFInd installation in /boot/efi/EFI/refind; upgrading it.
Installing driver for ext4 (ext4_x64.efi)
Copied rEFInd binary files

Notice: Backed up existing icons directory as icons-backup.
Existing refind.conf file found; copying sample file as refind.conf-sample
to avoid overwriting your customizations.

An existing rEFInd boot entry exists, but isn't set as the default boot
manager. The boot order is being adjusted to make rEFInd the default boot
manager. If this is NOT what you want, you should use efibootmgr to
manually adjust your EFI's boot order.
Installing it!

ALERT: There were problems running the efibootmgr program! You may need to
rename the refind_x64.efi binary to the default name (EFI/boot/bootx64.efi
on x86-64 systems or EFI/boot/bootia32.efi on x86 systems) to have it run!

Existing //boot/refind_linux.conf found; not overwriting.

ALERT:
Installation has completed, but problems were detected. Review the output for
error messages and take corrective measures as necessary. You may need to
re-run this script or install manually before rEFInd will work.





and now all I have when normally booting my mac is the recovery system, and when I press alt I get the windows option but not successful in booting into it.. 
please help! and sorry for my english :)

---

### Post by este.el.paz on 2014-10-15
> **yousufinternet said:**
> Hello every one, 

I have recently installed ubuntu 14.04 on my MacBook Pro 9,2 , I installed it side by side with Mac OS X, and used rEFInd to boot into ubuntu, ***then I have decided to use the Mac OS X partition as my home folder****, so I formatted it and moved my home folder into the new formatted partition, to discover after restarting the computer that the rEFInd loader was formatted with the partition,

and now all I have when normally booting my mac is the recovery system, and when I press alt I get the windows option but not successful in booting into it.. 
please help! and sorry for my english :)

@yousuf:

It's not clear what exactly you've done . . . if you "installed side by side" did the installer set up separate partitions for OSX set as "HFS+" and the linux partitions set as "ext4" for the "/" . . . and "swap"???  And then, after the install you decided to delete the OSX partition and use it for linux?  OSX doesn't play well with others, so if you make any modifications to your OSX side it will "influence" the linux side, and in particular the rEFInd install would have to be "blessed" again.

But, if you erased OSX you probably erased rEFInd.  It sounds like the situation is "very complicated" . . . the general wisdom for apple computers is to set up a dual boot . . . OSX in its own partition, install rEFInd in OSX, and then set up separate partitions for linux . . . and install linux.  I've seen some guides on the web for running apple computers just using Ubuntu, but it is more complicated than just installing rEFInd.  

And, if you are just now running ubuntu the rEFInd install is different . . . so if you installed it in OSX then deleted OSX, you 'd have to install it for linux, etc.  You probably should do it over . . . or, you could try to use "Super Grub 2" disk to try to boot whatever system you have installed . . . and then if you can open GParted . . . and get the partition data posted here . . . that might explain what you are doing.

On another note, I also did an OSX upgrade, I reblessed rEFInd . . . but it still isn't letting me boot xubuntu without SG2 . . . .

e.e.p.

---

### Post by yousufinternet on 2014-10-16
> **este.el.paz said:**
> @yousuf:

It's not clear what exactly you've done . . . if you "installed side by side" did the installer set up separate partitions for OSX set as "HFS+" and the linux partitions set as "ext4" for the "/" . . . and "swap"???  And then, after the install you decided to delete the OSX partition and use it for linux?  OSX doesn't play well with others, so if you make any modifications to your OSX side it will "influence" the linux side, and in particular the rEFInd install would have to be "blessed" again.

But, if you erased OSX you probably erased rEFInd.  It sounds like the situation is "very complicated" . . . the general wisdom for apple computers is to set up a dual boot . . . OSX in its own partition, install rEFInd in OSX, and then set up separate partitions for linux . . . and install linux.  I've seen some guides on the web for running apple computers just using Ubuntu, but it is more complicated than just installing rEFInd.  

And, if you are just now running ubuntu the rEFInd install is different . . . so if you installed it in OSX then deleted OSX, you 'd have to install it for linux, etc.  You probably should do it over . . . or, you could try to use "Super Grub 2" disk to try to boot whatever system you have installed . . . and then if you can open GParted . . . and get the partition data posted here . . . that might explain what you are doing.

On another note, I also did an OSX upgrade, I reblessed rEFInd . . . but it still isn't letting me boot xubuntu without SG2 . . . .

e.e.p.

Yes, what you said is correct, you understood me well, I created first a partition for linux using disk utility, and installed rEFInd in OS X, then installed ubuntu on that partition, after using ubuntu and liking it, I decided to delete the OS X partition, so I erased OS X, and rEFInd too unfortunatly, now I am just running ubuntu but I need rEFInd to boot into it, and I can't figure out how to install it.. here is how my partitions look like currently: 

[https://www.dropbox.com/s/fx37s4p0a27oeez/Screenshot%20from%202014-10-16%2008%3A40%3A00.png?dl=0](https://www.dropbox.com/s/fx37s4p0a27oeez/Screenshot%20from%202014-10-16%2008%3A40%3A00.png?dl=0)

also I don't know how to bless rEFInd again..

---

### Post by d4m1r on 2014-10-16
```
ALERT:
Installation has completed, but problems were detected. Review the output for
error messages and take corrective measures as necessary. You may need to
re-run this script or install manually before rEFInd will work.
```

I don't see any output ;) Most likely, rEFInd has additional error logs somewhere you could find and post here that might be more indicative of the problem...I don't know where they are but Google is your friend. You also can most likely access the reFInd sliver under Ubuntu if you are still able to boot into Ubuntu somehow....

Having gone through similar issues myself, I would just say it might be easier to just redo everything...If you don't have a lot of time/customizations already invested in your Ubuntu install. reFInd is very picky and little documentation exists on troubleshooting it. When I say redo everything, I mean put in your 64 bit Ubuntu xx.xx install DVD, hold the right button while booting your Macbook Pro to access the OS X recovery menu, and select the BIOS installation option for Ubuntu. During the installation, select the advanced option and delete all partitions except for the ~200MB OS X recovery menu one. Then complete the installation and from now on, when you power on your MBP, it will directly go to Ubuntu :)

---

### Post by yousufinternet on 2014-10-16
Actually I am not sure that reinstalling ubuntu all over again will change anything, unless it will remove the original EFI of the MacBook Pro and replace it with GRUB, I guess that it will be just setting there and I will have the same situation, being unable to boot into it.. 

and for the error messege you quoted, I think it is reffering to these paragraphes: 
> 
An existing rEFInd boot entry exists, but isn't set as the default boot
manager. The boot order is being adjusted to make rEFInd the default boot
manager. If this is NOT what you want, you should use efibootmgr to
manually adjust your EFI's boot order.
Installing it!

ALERT: There were problems running the efibootmgr program! You may need to
rename the refind_x64.efi binary to the default name (EFI/boot/bootx64.efi
on x86-64 systems or EFI/boot/bootia32.efi on x86 systems) to have it run! 

and I have tried renaming the refind_x64.efi binary to the default name bootx64.efi but it never worked. any other ideas? :(

---

### Post by este.el.paz on 2014-10-16
> **este.el.paz said:**
> @yousuf:
But, if you erased OSX you probably erased rEFInd.  It sounds like the situation is "very complicated" . . . the general wisdom for apple computers is to set up a dual boot . . . OSX in its own partition, install rEFInd in OSX, and then set up separate partitions for linux . . . and install linux.  I've seen some guides on the web for running apple computers just using Ubuntu, but it is more complicated than just installing rEFInd.  

And, if you are just now running ubuntu the rEFInd install is different . . . so if you installed it in OSX then deleted OSX, you 'd have to install it for linux, etc.  You probably should do it over . . . 
e.e.p.

> **d4m1r said:**
> 
I don't see any output ;) Most likely, rEFInd has additional error logs somewhere you could find and post here that might be more indicative of the problem...I don't know where they are but Google is your friend. You also can most likely access the reFInd sliver under Ubuntu if you are still able to boot into Ubuntu somehow....

Having gone through similar issues myself, I would just say it might be easier to just redo everything...If you don't have a lot of time/customizations already invested in your Ubuntu install. reFInd is very picky and little documentation exists on troubleshooting it. When I say redo everything, I mean put in your 64 bit Ubuntu xx.xx install DVD, hold the right button while booting your Macbook Pro to access the OS X recovery menu, and select the BIOS installation option for Ubuntu. During the installation, select the advanced option and delete all partitions except for the ~200MB OS X recovery menu one. Then complete the installation and from now on, when you power on your MBP, it will directly go to Ubuntu :)

@yousuf:

You ***could*** try a fresh install of rEFInd . . . which may or may not work . . . the "blessing" instructions are on "rodbooks" wiki for it . . . in this case now you would follow the "Install rEFInd using linux" section . . . .

But, there are now two people saying, "Do it again" . . . and over a couple of years of playing with linux I have found that if something goes wrong on a new install . . . doing it again is the best way.  How to do that is up to you d4m1r has offered his way of getting to a ubuntu only system . . . from what I've seen using the MBR way was not recommended for Mac, so I use the rEFInd install to the (freshly reinstalled) OSX partition . . . dragging the "install.sh" file to the admin account Terminal window, after some other command is entered (instructions in the rodbooks wiki) . . . and using DU to set up a "free space" . . . at the end of the disk . . . and then in ubuntu install phase select "manual" . . . creating a small (10MB) partition labed as "bios_grub" . . . the "/" partition labeled "ext4" . . . and 1 - 1.5 RAM labeled as swap.  Then run the install, after which . . . shut down, on reboot the rEFInd window should open . . . selecting "windows" or the penguin will take you to GRUB and then on to the splash . . . .

Either way you go, indeed you don't need two "Recovery Disks" . . . but, at this point, best to "nuke and pave" . . . .

e.e.p.

---

### Post by yousufinternet on 2014-10-16
Thanks a lot guys for your help, but I have figured out my way to solve this by doing the following, this will help any one need to have ubuntu as the only operating system on a mac, and wants to do that by deleting OS X: 

1- You will need to boot into your ubuntu install, this can be done by creating a live usb ubuntu, and running it, then creating a bootable refind usb drive, and using that to boot into ubuntu. 

2- Inside ubuntu, download rEFInd and install it as usual using the install.sh file.

3- If you get the same error message as I do Copy all the contents of the refind folder into a new created boot folder, this command will do it:
> Sudo cp -a /boot/efi/EFI/refind/. /boot/efi/EFI/boot/

4- Rename the refind_x64.efi binary into the default name as suggested in the output, this will do it too:
sudo cp /boot/efi/EFI/boot/refind_x64.efi /boot/efi/EFI/boot/bootx64.efi

5- The last thing to do is to make the refind boot option the startup disc for the mac, this could be done by pressing alt at the computer start to show the different options available, and then pressing ctrl while selecting the refind disc.. 

So it just seems that I haven't followed the instructions in a proper way.. :)

---

### Post by este.el.paz on 2014-10-16
@yousuf:

Very good, hope it works out.  But, it looks like you are following someone's instructions . . . it would be better to enclose that material in "Quotes" and/or even offer a link to that quoted material that you are posting . . . to help others discern the applicability of it for them . . . .  You should credit the person who is helping you directly or indirectly from a wiki . . . what wiki???

e.e.p.

---

### Post by yousufinternet on 2014-10-16
it's just copy and paste instructions sir, I wrote them my self :?

---

### Post by este.el.paz on 2014-10-16
> **yousufinternet said:**
> 

So it just seems that I haven't followed the instructions in a proper way.. :)

> **yousufinternet said:**
> it's just copy and paste instructions sir, I wrote them my self :?

Ah, so you just mean that you didn't follow your *own* instructions???  That's OK, I do that all the time . . . .

e.e.p.

---

### Post by yousufinternet on 2014-10-17
Sorry that my sentence wasn't clear.. I meant that I didn't follow the correction procedure that was shown in the output in a proper way, because what I was doing is just renaming the file whithout creating the boot folder.. :) 

this is the correction procedure: 
> 
ALERT: There were problems running the efibootmgr program! You may need to
rename the refind_x64.efi binary to the default name (EFI/boot/bootx64.efi
on x86-64 systems or EFI/boot/bootia32.efi on x86 systems) to have it run!

---

