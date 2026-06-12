---
title: "Cannot boot from USB on iMac17,1 (27-inch 5k retina iMac running El Capitan)"
date: 2015-11-20
forum: Apple Hardware Users
---

### Post by __PG__ on 2015-11-20
Hello all.

I'm trying to install Ubuntu on an iMac17,1 (27-inch 5k retina iMac) running El Captian.

At first I created a USB installer following these instructions : [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
I downloaded ubuntu-14.04.3-desktop-amd64.img and converted it to .iso.

When selecting the USB to boot from, it brings up the Grub 2.02~beta2-9ubuntu1.3 menu 
```
*Try Ubuntu without installing
Install Unbuntu
OEM install (for manufacturers)
Check disc for defects

```
Once you select an option (either the first or second) the screen goes blank and nothing happens.

I have tried this with both a 4Gb an 8Gb drive.

I then tried this method : [http://www.howtogeek.com/213396/how-to-boot-a-linux-live-usb-drive-on-your-mac/](http://www.howtogeek.com/213396/how-to-boot-a-linux-live-usb-drive-on-your-mac/)
I used the downloaded iso file and attempted to boot from it. Here is the output:
```

SO path: (hd0,msdos1)/efi/boot/boot.iso
kernel path: /casper/vmlinuz.efi | ramdisc path: /casper/initrd.lz
boot folder : casper | boot parameters: file=/cdrom/preseed/ubuntu.seed


Loading Linux kernel..done


Loading initial RM disc... done


Attempting to boot the Linux distribution now...

```
At this point the process hangs and doesn't continue. I also tried a 4Gb and 8Gb key.

I repeated the process but I let the Mac Linux USB loader download Ubuntu 15.04 instead. This made no difference.

The third attempt used the UNetbooting process [http://unetbootin.github.io/#other](http://unetbootin.github.io/#other) with my downloaded .iso file.
This produced the same results as the first method (i.e. black screen after the grub menu).

At this point I'm wondering what else to try. Would trying to boot off an external superdrive make any difference?
Do I need to disable csrutil before attempting to boot off the USB?

I note that there isn't much discussion about dual-booting iMacs here, the majority of the forum discussed dual-booting MacBooks (I have a dual-boot MacBook 5,3 with Ubuntu 14.04).

Is installing Ubuntu on an iMac more difficult than a MacBook?

Hoping someone can help.

---

### Post by narender224 on 2015-11-20
Hello,
With Universal-USB-Installer-1.9.2.4 make USB pendrive as bootable.
and shutdown MAC, and power it on with holding OPTION button. boot with USB device

THanks
NSR

---

### Post by __PG__ on 2015-11-21
That executable only works for Windows as far as I can tell.

I repeated the official Ubuntu USB instructions with csrutil disabled. It made no difference.
I also used the the other iso file ubuntu-14.04-desktop-amd64+mac.iso. This made no difference.

I burnt the original file ubuntu-14.04.3-desktop-amd64.iso onto a DVD and tried to boot from the USB superdrive. Before the grub menu appears, I get the following message
```

error : file '/boot' not found

```
The grub menu then appears, however once again a black screen occurs when attempting to boot.

I might try and use grub commands directly. When upgrading my MacBook Pro to OS X Mavericks it broke rEFIt/Grub so I had to manually boot using the grub command line. 

I presume the following procedure will work 
```

root=(hd0,xxx)
kernel /boot/vmlinuz-**** root=/dev/*** ro
initrd /boot/initrd-****
boot

```
I just need to find out where the /boot directory lies on the USB or DVD.

---

### Post by __PG__ on 2015-11-25
Just looking at the default boot commands in Grub for *Try Ubuntu without installing when booting off cdrom
```

setparams 'Try Ubuntu without installing'

     set gfxpayload=keep
     linux            /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
     initrd           /casper/initird.iz

```
I might have to read up a bit more about GRUB2, it seems its a bit different to GRUB.

---

### Post by luciano.x on 2015-11-25
Maybe the problem is related to your video card.
Just try the kernel parameter 'nomodeset'. 

Before hit try ubuntu, press key e
Replace quiet spash with nomodeset

Press Ctrl + x when done.

---

### Post by __PG__ on 2015-11-29
I think you're right.
I think the issue is video related. I managed to get beyond the basic Grub2.0 screen by altering the gfxpayload command with a variety of screen resolutions. One of them worked however Grub failed to load as using 'Ctrl-X' didn't actually boot, rather it just passes 'x' as a Grub parameters F10 made it boot but Grub failed with a message along the lines of 'Command X' not found.

Next time I'll pass the right screen resolution to gfxpayload and only use F10. I'll also try nomodeset.

---

### Post by charlie37 on 2015-12-08
Were you able to find a solution? I am running into the exact same issue. Have tried both CentOS and Ubuntu distros (with and without rEFInd) on this new iMac but only receive the same blank black screen. Thanks.

---

### Post by __PG__ on 2015-12-08
Not yet. 

I tried replacing quiet splash with nomodeset. It didn't work. 
I added nomodeset after quiet splash. That didn't work.
I removed quiet splash.
I then tried various single screen resolutions with gfxpayload but they didn't work.
I got it working once...I'll keep at it.

---

### Post by charlie37 on 2015-12-08
Thanks for the reply. Will keep checking this thread... If I can find some time to dig further into this and come up with a solution, I will update as well.

---

### Post by __PG__ on 2015-12-09
It turns out that regardless of whatever gfxpayload options I provide, as long as enter an extraneous 'x' at the end of the grub command section, I will generate the subsequent menu 'error, command 'x' not found'.

So I had never had it working before.

I'm going to have a look at this : [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I've tried the 14.04 LTS USB and CDROM to boot on my old MacBook (which actually has Ubuntu installed) and it fails to boot there. 
I get to the Ubuntu purple splash screen with five yellow dots, they all change colour, and then it hangs.
Evidently the message [COLOR=#000000][FONT=Ubuntu Mono]error : file '/boot' not found[/FONT][/COLOR][COLOR=#000000]
means I'll have to figure out how to set it up via the GRUB2 command line.

---

### Post by toivo-arach on 2015-12-10
I just received a new 27-inch 5k retina iMac running El Capitan and immediately got a blank screen installing Ubuntu, I had no problem a couple of weeks ago installing on a new non 5k iMac.

I was able to get it work and install by adding      acpi=off nomodeset   the kernal boot line in Grub. This isn't a permanent solution though since acpi is quite important, for example I see only one CPU.

I don't know how to get any information on what's the problem with ACPI though.

---

### Post by __PG__ on 2015-12-25
Thanks for that. I'm installing Ubuntu now after successfully booting off the USB with 'acpi=off nomodeset' grub2 options.

Once Ubuntu has been installed, I'll see if I can fix the acpi issue.

---

### Post by toivo-arach on 2016-01-17
To get it working properly the kernel parameter is     nointremap     (the acpi=off nomodeset is not needed)

---

### Post by denzeljiang on 2016-02-20
Hey guys, I also installed ubuntu 15.10 successfully on my iMac 5k late 2015.

Just want to check whether you guys had any luck on the video card drivers?

I have the model with amd/ati m395, but had no luck after trying different drivers including opensource driver radeon and amdgpu , and 3rd party driver fglrx ( latest one is 15.12 at this point).

The screen is on maximum by default though, but very flaky, window effects is extremely slow.

---

### Post by Tine_Sandvold on 2016-05-25
I also have a 6k retina iMac 2015, and after i click on install ubuntu with the bootable flash drive in, the screen goes black.
Ive tried to fix it for 6 days now. 
Has anyone of you got it working?
If so, please tell me how...

---

### Post by jowan512 on 2016-06-24
I have been trying to do this all day. A new 2016 iMac 27"

I also have a 2010 27" and I am used to the "nomodset" etc etc setup.

I CAN get it installed. Both 16.04 and 14.04 will install IF you edit the Grub line when choosing to Install Ubuntu from the USB disk and remove "quiet splash" and add "nomodeset acpi=off"
However, it does not boot properly after install. Even if you edit the Grub line in the same way. it just hits the "loading initial ramdisk " error and freezes.

I don't know if this is a consequence of installing with "acpi=off".

This did not happen in the new 15" macbook pro I just bought too - 16.04 installed very fast.

I'm stumped :(

---

### Post by lucifer88 on 2016-08-08
Could you please share with me the working config?
I am struggling with the same issue.

---

### Post by ghadamyari on 2016-09-20
The workaround is to add **nointremap** kernel parameter before installing Ubuntu ([see this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1525615")). You should add the parameter when Ubuntu installation is finished as well.

You may need to install your graphic driver manually ([instructions here]("https://help.ubuntu.com/community/Intel_iMac"))

No other modifications ( acpi=off & nomodeset ) are needed. I could install Ubuntu 16.04 LTS on my iMac 17,1 (iMac 5K, Late 2015 Retina)

======= Here is some other tips to fully get Ubuntu 16.04 working on iMac 27 2015:

1- Install the latest version of kernel 4.7 on Ubuntu (4.7 introduces open source support for Radeon RX 480 GPUs which is essential to get your graphic card working). You can find the instructions for [kernel 4.7 here]("http://ubuntuhandbook.org/index.php/2016/07/install-linux-kernel-4-7-ubuntu-16-04/"), but install the latest one ([4.7.4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7.4/") is the latest one now) 

2- To add your Mac OSX in the grub see [this link]("http://askubuntu.com/questions/765254/add-grub-menu-for-os-x")

To get the audio working:

3- Install the latest version of salsa[ instructions here]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS")

4- Open Settings -> Sound, Choose "Speakers Built in Audio from the list", Select Mode : Choose "Analog Surround 4.0 Output" instead of "Analog Stereo Output". 

Audio should work fine now. To make it permanent, run the following command [(Instructions here]("https://wiki.archlinux.org/index.php/PulseAudio/Examples#Set_the_default_output_source")):

```

x pacmd list-sinks | grep -e 'name:' -e 'index'

    index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo>
  * index:** 5**
    name: <alsa_output.pci-0000_00_1f.3.**analog-surround-40**>


```

To get the sound card number run :
```

$ pactl list
Card #0
    Name: alsa_card.pci-0000_01_00.1
    Driver: module-alsa-card.c
    Owner Module: 6
    Properties:
        alsa.card = "1"
        alsa.card_name = "HDA ATI HDMI"

Card #**1**
    Name: alsa_card.pci-0000_00_1f.3
    Driver: module-alsa-card.c
    Owner Module: 7
    Properties:
        alsa.card = "0"
**        alsa.card_name = "HDA Intel PCH"**
        alsa.long_card_name = "HDA Intel PCH at 0xc1820000 irq 37"




```

Then edit /etc/pulse/default.pa and add the following lines at the end:

```

set-card-profile 1  output:**analog-surround-40**
set-default-sink **5**

```

The numbers may be different for you.

---

### Post by 666.axel on 2016-11-03
Hi all,

I had the same problem and found a quick simple solution. I followed [this ]("http://www.macworld.co.uk/how-to/mac/how-install-linux-on-mac-3637265/")guide and everything worked fine. I am pasting the steps I followed to make it work but I am not the author of this guide. 


Before these steps I created a bootable usb in Windows with win32diskimager.



[LIST=1]
[*]Power up the Mac while holding down the Option key.
[*]Choose the EFI Boot option from the startup screen and press Return.
[*]You will see a black and white screen with options to Try Ubuntu and Install Ubuntu. Don't choose either yet, press "e" to edit the boot entry.
[*]Edit the line that begins with Linux and place the word "nomodeset" after "quiet splash". The whole line should read:```
 linux /casper/vmlinuz.efi            file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash nomodeset --
```
[*]Press F10.
[*]Ubuntu boots into trial mode.
[*]Double-click the icon marked "Install Ubuntu".
[*]Select English and choose Continue.
[*]Select "Install this third-party software" option and click Continue.
[*]Click Yes to the /dev/sdb alert.
[*]Select "Erase disk and install Ubuntu" and click Continue.
[*]Ensure that Select Drive is displaying the main hard drive. Click Install Now. Click Continue in the alert window.
[*]Select your location on the map and click Continue.
[*]Choosing your keyboard layout and click Continue.
[*]Enter the name and password you want to use.
[*]Click Continue and Linux will begin installing.
[*]When the installation has finished, you can log in using the name and password you chose during installation.
[/LIST]

I hope this help.

Cheers,
Axel

---

### Post by jowan512 on 2016-11-18
I do have 16.04 working well on the new iMac 27.

Basic steps are :

Install with nomodeset as described before.
Then your system will NOT boot.
Use rescue CD, change parameters on boot to use nomodeset
Once in, drop to root shell, edit grub and use :

GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq"

---

### Post by g33zr on 2016-11-20
You might have better luck burning the ISO onto a DVD and booting that, which always worked for me when I ran Linux on Macs.

---

### Post by mfox on 2017-10-14
Trying all of the grub parameters listed in this thread, I was unable to boot a USB installation disk with either 16.04 or 17.04 on my late 2015 iMac; I would always end up with a dark purple screen. I don't know if it matters, but this iMac is the mid-level one with the 3.3 ghz i5 and a Radeon R9 M395 video card. Here is where it gets weird. In frustration, I tried several other distros as well as the Ubuntu 17.10 beta 2. The latest Fedora wouldn't boot at all; nor would Elementary. Clonezilla would boot to the first screen and then freeze. Ubuntu 17.10 beta and OpenSuse Leap would boot, but they would take 5 minutes to do so. I didn't try installing OpenSuse, but I did Ubuntu. It did install, and changing its grub boot parameter would allow it to boot up, but again taking many minutes. When it did boot up, network-manager would not connect to the internet with either ethernet or wifi. At this point I was ready to tear my hair out, but I tried one more, Linux Mint cinnamon 18.2. Changing the boot parameter to nointremap, it booted right up, installed OK, and the installation booted up normally once I permanently added noremap to the boot sequence! What is going on here? Others have been able to get Ubuntu to boot on a 5k iMac so why couldn't I? Mint 18.2 is a derivative of Ubuntu 16.04, so why should it boot so easily when 16.04 wouldn't boot at all? What is different about 17.10 that it can boot (though with a lot of stalling) when the previous version cannot? For now I'm just glad that I was able to install a Linux I can work with onto my new (new to me) iMac. But ultimately I want it working with Ubuntu, but am not experienced enough to know how to proceed from here. Might it work if I simply copied all of the grub boot parameters in Mint and use them with Ubuntu? I might try that next, but any suggestions would be welcome.

---

### Post by mfox on 2017-10-16
Turns out the PG had it right, at least with my late 2015 iMac with the Radeon R9 M395 video card. I can boot the 16.04 installer with acpi=off nomodeset, and it boots up at normal speed. And using the nointremap parameter did not work with this version. Unfortunately, window effects are noticeably slow with the acpi=off parameter; e.g. moving windows or resizing them. Is there some other acpi boot setting that would work without giving the window effects problems?

---

### Post by mfox on 2017-10-17
OK, this might help someone in the future. I can boot a Ubuntu installation (in this case on an external SSD) using either of two additional grub settings:
> noapic nomodeset
> napic nomodeset acpi_backlight=vendor

Both boot up quickly to the Ubuntu desktop (17.04 in this case). The one without the backlight parameter gives delayed window effects as noted with the acpi=off parameter. Adding the backlight command removes those delays, but you also lose the real time window effects; changing a window shows only the outline until you release the mouse. Also, using the backlight command causes the loss of brightness adjustment through the "brightness and lock" setting. Not a big deal, but it would be nice to have all functions working properly. I'll keep experimenting and post again if I find a solution.

---

### Post by mfox on 2017-11-14
I have now been able to install Ubuntu 16.04.3 and run it without any special boot parameters once I installed the proprietary amdgpu-pro video driver. However, to get it work, it has to be installed with a slight variant of the installation command recommended in the instructions given by AMD; the command is:
> ./amdgpu-pro-install --px
the --px replaces -y in the AMD instructions

Installing the amdgpu-pro driver allows one to choose alternative resolution settings, though none higher than 4K.

I tried installing this driver in Ubuntu 17.10 after I installed it, but it didn't work in 17.10. If you're interested in further details about my attempts to install Ubuntu on my 27" Late 2015 5k iMac, see [this ]("http://forums.plugintolinux.ca/index.php/topic,321.0.html")thread.

---

