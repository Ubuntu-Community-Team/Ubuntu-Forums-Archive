---
title: "ASUS X205TA hardware support for any other OS"
date: 2017-12-07
forum: Any Other OS
---

### Post by Yochanan on 2017-12-07
This is a fork of the original thread [Asus X205TA hardware support in Ubuntu]("https://ubuntuforums.org/showthread.php?t=2254322"). The forum moderators requested we not discuss other distros not based on Ubuntu and suggested we create a thread here.

[QUOTE=jmills81]This thread is the best resource available for getting Linux to work properly on the X205TA. The hard work of several people spanning 3 years and 180+ pages has resulted in a device that is capable of running Ubuntu and other distros. 

@harryharryharry, et al;
Wanted to say thanks so much for the hard work. I started off as a complete Linux noob and thanks to your hard work, I'm now running Ubuntu on my X205TA and have learned a ton along the way. Couldn't have done it without you guys![/QUOTE]

With @harryharryharry's updated script attached [here]("https://ubuntuforums.org/showthread.php?t=2254322&p=13983970#post13983970"), that's all there is to it!

On Arch based distros, use my meta PKGBUILD or install the dependencies in the depends() array: 

```

pkgname=x205ta-create-iso
pkgver=1.0
pkgrel=1
pkgdesc="Meta package for x205ta-create-iso.sh"
arch=('x86_64')
url="https://ubuntuforums.org/showthread.php?t=2254322&p=13983970#post13983970"
license=('none')
depends=('grub' 'syslinux' 'cdrtools' 'dosfstools' 'rsync' 'coreutils' 'xorriso')

package() {
	return 0
}

```

Then run:
```
sudo ./x205ta-create-iso.sh myiso.iso
```


The [x205ta ArchWiki page]("https://wiki.archlinux.org/index.php/ASUS_x205ta") is another good resource.

If anyone would like me to add anything else to this post, PM me.

---

### Post by harryharryharry on 2017-12-08
_[SIZE=4]**[B]Distro-agnostic installation guide:**[/B][/SIZE]_

I thought I might use the occasion of this shiny new thread to try and shed some light on the installation-quirks of the X205TA and how to address them in this general distro-agnostic installation guide. 
(If you want a more straight-forward approach to installing ubuntu; check the last link posted above by Yochanan.)

 **Quick summary of the issues:**
 The main issue with installing linux on the X205TA stems from the fact that the laptop has a 32bit uefi-system in combination with a 64bit CPU.  
 
 This results in 2 problems:
 -    64bit isos won't boot from a usbstick because they mostly carry a 64bit bootloader (while     32bit isos generally only do legacy boot, not uefi).
 -    If you do manage to boot a usbstick and install linux to the ssd, the distro&#8217;s installer will     most likely try - and fail - to install a 64bit uefi bootloader, which will end in a pristine but unbootable     linux installation (or for some distros it will crash the installer, which is harder to     recover from. If the installer crashes you are probably better off reinstalling the OS and if     possible disabling installing grub completely)
 
 Next to these boot problems are a couple of hardware quirks (enabling audio, wifi & bluetooth, stop random freezes) that need to be addressed to get the best linux experience. Some hardware functionalities as of yet do not (and might never) work:
 - microphone
 - headphone jack detection
 (Asking for these functionalities means you didn&#8217;t read this guide)
 
_The boot issues are addressed by step 1 & 5_
_The hardware quirks by step 2,3 & 4_

 **How to address these issues:**
  _1. How to boot a usbstick:_
 So the iso needs to boot in 32bit efi mode. This can be done by placing a file called bootia32.efi in a specific location on the usbstick. Because files can&#8217;t be added if you use tools like dd & imagewriters (they create read-only usbsticks), you&#8217;ll have to extract the iso to a fat32 formatted usbstick instead:
 ```

# The next 3 commands will destroy all data on a device. Be **_extremely_** careful when you change **y** to your usbstick&#8217;s device letter.
# If you are not comfortable with the command line, I suggest you format the usb stick to FAT32 using a GUI tool like gparted or the format option in windows.
sudo parted -s /dev/sd**y** mklabel msdos #create new mbr partition table
sudo parted -s /dev/sd**y** mkpart primary 1M 100% #create 1 partition that takes up 100% of the usbstick
sudo mkfs.vfat -n X205TA /dev/sd**y**1 #format that partition FAT32 and label it X205TA

# mount the usbstick somewhere and extract the iso to it
sudo mount /dev/sd**y**1 /path/to/usbmountpoint
sudo 7z x linux.iso -o/path/to/usbmountpoint/ #notice: no space after the -o flag, x in this command means extract.
sudo mkdir -p /path/to/usbmountpoint/EFI/BOOT #if missing, this command creates a directory and its parent directories
sudo wget https://raw.githubusercontent.com/harryharryharry/x205ta-iso2usb-files/master/efi_bootia32.efi -O /path/to/usbmountpoint/EFI/BOOT/bootia32.efi
sync; sudo umount /path/to/usbmountpoint #writes any data buffered in memory out to disk and unmounts usbstick

```
 Now the usbstick will show up when pressing ESC during the X205TA boot process, and the bootia32.efi file will try to load /path/to/usbmountpoint/boot/grub/grub.cfg
 If this file/directory does not exist, a grub rescue prompt will appear. If this happens you will need to create it (/path/to/usbmountpoint/boot/grub/grub.cfg) yourself and add to the file something like this:
 > 
 menuentry 'Pretty LinuxOSname' {
                 linux /isolinux/vmlinuz intel_idle.max_cstate=1 button.lid_init_state=open
                 initrd /isolinux/initrd.img
 }
 
 The linux line should point to the kernel (usually called vmlinuz or something similar in nature)
 The initrd line should point to the initramfs  (usually called initrd.img or something similar in nature)
 The extracted iso will contain config files that reveal which boot parameters are required, it&#8217;s a bit of a trial-and-error detective game :). Pressing &#8216;e&#8217; in the grub menu lets you edit boot commands on-the-fly and try them out.  
 In the example above I&#8217;ve added 2 parameters already because it makes sense to add them when using the X205TA (so if a grub.cfg already exists you benefit from adding these parameters):
 **intel_idle.max_cstate=1** prevents freezing
 **button.lid_init_state=open** prevents suspend/resume loop when closing the lid
 
 
 
 Once booted into the live environment, my advice would be to install linux straight away. 
**Skip to step 5** for an explanation on how to install the grub bootloader to the ssd after finishing the installation (because as said, the linux installer will fail to do so properly).
 Otherwise, you can perform the following steps to get more functionality for the duration of the live boot; however they will need to be repeated after (re)booting (into either live usb or the installed linux).
 
 _2. How to gain internet connectivity_
 The internal wireless card&#8217;s module (brcmfmac) needs a file called /lib/firmware/brcm/brcmfmac43340-sdio.txt to get the card up and running, but it&#8217;s missing (well it&#8217;s not in the right location). You can copy it by running the following commands:
 ```

# probably not necessary, but to be sure the EFI variables are properly exposed to userspace
sudo modprobe efivarfs
sudo mount -t efivarfs efivarfs /sys/firmware/efi/efivars

# then copy the file that starts with nvram to /lib/firmware/brcm
sudo cp -a /sys/firmware/efi/efivars/nvram* /lib/firmware/brcm/brcmfmac43340-sdio.txt

# and reload the brcmfmac module
sudo rmmod brcmfmac
sudo modprobe brcmfmac

```
 You can also opt to use a slightly different version I host on github:
 [https://raw.githubusercontent.com/harryharryharry/x205ta-iso2usb-files/master/brcmfmac43340-sdio.txt](https://raw.githubusercontent.com/harryharryharry/x205ta-iso2usb-files/master/brcmfmac43340-sdio.txt)
 which has the added benefit of supporting 5GHz networks (pretty weird the version in the EFI variables doesn&#8217;t...)
 
 _3. How to gain bluetooth connectivity_
 The internal bluetooth chip needs a file called /lib/firmware/brcm/BCM43341B0.hcd and a running bluetooth service and a running btattach command (for which you can also create a service).
 ```

# Download the firmware file to the right location
sudo wget https://raw.githubusercontent.com/harryharryharry/x205ta-iso2usb-files/master/BCM43341B0.hcd -O /lib/firmware/brcm/BCM43341B0.hcd

```
 Create a file called /etc/systemd/system/btattach.service with the following contents:
 > 
 [Unit]
 Description=Btattach
 
 [Service]
 Type=simple
 ExecStart=/usr/bin/btattach --bredr /dev/ttyS1 -P bcm
 ExecStop=/usr/bin/killall btattach
 
 [Install]
 WantedBy=multi-user.target
 
And then:
 ```

# (re)start the services with
sudo systemctl restart btattach
sudo systemctl restart bluetooth

# check the services
sudo systemctl status btattach
sudo systemctl restart bluetooth
# (if the btattach service failed, check if the binary 'btattach' is installed)
# (if the service btattach failed but btattach is installed, try changing /dev/ttyS1 to /dev/ttyS4 and reload and restart the service)

# when you&#8217;re booted into linux on the ssd you can repeat step 3. and enable the services at boot with:
sudo systemctl enable btattach
sudo systemctl enable bluetooth

```
 
  

 The tweaks in step 4. will only take effect during boot so they cannot be applied during a running live session.
 
 _4. Further tweaks_
 To add headphone support (>=4.13 kernels only) and blacklist 2 modules that will cause problems, add the following contents to a file called /etc/modprobe.d/50-x205ta.conf
 > 
 # this quirk is needed to get headphones support in kernels >=4.13
 options snd_soc_rt5645 quirk=0x31
 
 # module snd_hdmi_lpe_audio breaks sound
 blacklist snd_hdmi_lpe_audio
 
 # module btsdio breaks wifi on suspend/resume
 blacklist btsdio
 
 
 Download a UCM-file from Pierre Bossart&#8217;s github, required for audio to work
 ```

sudo wget https://raw.githubusercontent.com/harryharryharry/x205ta-iso2usb-files/master/HiFi.conf -O /usr/share/alsa/ucm/chtrt5645/HiFi.conf
# (this file is prone to be overwritten during distro updates of alsa-libs, check your package manager on how to prevent this from happening or backup the file so you can easily restore it.)
# original file source: (which doesn't support headphones, and has headphones output as default instead of speakers)
# https://raw.githubusercontent.com/plbossart/UCM/master/chtrt5645/HiFi.conf

```

 

 And last but not least...
 
 _5. Properly install grub bootloader (make linux on the ssd bootable)_
 I began by telling linux will try to install a 64bit uefi bootloader. This last step will explain how to chroot in to the linux installation from a liveusb stick and do what the installer failed to do.  
 
 I&#8217;ve found this step to be a very handy tool for all future linux rescue situations. If you&#8217;re ever in a situation where linux won&#8217;t boot at all, this is a very rudimentary tool to help fix that. From within chroot you can remove/install/reconfigure/backup packages to your heart&#8217;s content just as if you were regularly booted into the distro. (This step also exemplifies why encrypting your rootfs is important, since all the passwords in the world won&#8217;t protect you if someone can simply be a root user by chrooting into your OS from a live usb.)
 
 In this case we will be reconfiguring grub (and in some cases installing extra grub packages).
 
 The most important part for this step to work is to find the right block device where the rootfs of your linux installation is located. Tools like **blkid** and **lsblk** will help you find the right block device. (hint; it&#8217;s probably ext4, taking up 95% of your ssd, and called root)
 
 ```

# mount the rootfs partition (change X and Y) on /mnt
sudo mount /dev/mmcblkXpY /mnt
cd /mnt #(or, sweet bonus trick:   cd $_  )
sudo mount --bind /proc proc
sudo mount --bind /sys sys
sudo mount --bind /dev dev
sudo mount --bind /dev/pts dev/pts
sudo mount --bind /run run
sudo chroot .

# you are now chrooted into the linux installation that is on the ssd, ready to perform miracles
mount -a #firstly, attempt to mount all filesystems listed in /etc/fstab, because the efi partition should be mounted

# probably not necessary, but to be sure the EFI variables are properly exposed to userspace run:
modprobe efivarfs
mount -t efivarfs efivarfs /sys/firmware/efi/efivars

# this is the main command: it installs 32bit efi grub to the efi partition
grub-install --target=i386-efi --bootloader-id=Linux --efi-directory=/boot/efi --recheck
# (this command will fail if the necessary grub libraries are not installed, they should be in /usr/lib/grub/i386-efi/)
# (some distros use grub2-install instead of grub-install)

# now it's a good idea to add the intel_idle.max_cstate=1 button.lid_init_state=open parameters (explained in step 1) to /etc/default/grub (between the quotes after GRUB_CMDLINE_LINUX_DEFAULT) before generating grub.cfg
# and then generate grub.cfg
grub-mkconfig -o /boot/grub/grub.cfg
# (some distros use grub2-mkconfig)
# (likewise, on some distros you should install grub.cfg to /boot/grub2/ instead of /boot/grub/ &#8211; check which directory already exists)

# exit the chroot environment
exit

# reboot the laptop
sudo reboot

# and cross your fingers
sudo cross-fingers

```
 Please note that mainline kernels need intel_idle.max_cstate=1 as a boot parameter to stop random freezes. However this parameter prevents the laptop from going to deeper sleep states, which will make the device less power-efficient. If you want to prevent freezes, but still have the laptop be as power-efficient as possible, please refer to my [patched kernel compilation guide]("https://ubuntuforums.org/showthread.php?t=2254322&page=158&p=13625163#post13625163") or install one of my [prebuilt patched kernels]("https://ubuntuforums.org/showthread.php?t=2254322&page=132&p=13595504#post13595504") (if you are successful in booting a patched kernel, remember to remove the intel_idle.max_cstate=1 parameter from /etc/default/grub and update grub.cfg).

[SIZE=1]Valuable sources:
bugtracker sound issue X205TA: [https://bugzilla.kernel.org/show_bug.cgi?id=95681](https://bugzilla.kernel.org/show_bug.cgi?id=95681)
bugtracker freezing issue baytrail: [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)[/SIZE]

---

### Post by zetarancio on 2018-01-21
Hi Harry,
I understood I should post here instead of the other thread in order not to mess up the other one.
Would you mind sharing the patch you used to get the mic working in the rev27 kernel, is something like the following one?
[https://github.com/jwrdegoede/linux-sunxi/commits/master](https://github.com/jwrdegoede/linux-sunxi/commits/master)
Or is it a modified version of that one?
Thanks again

---

### Post by harryharryharry on 2018-01-21
The patch I used on my kernel was submitted to the upstream kernel recently (by Hans de Goede - I guess the github page you linked to is Hans' github account):
[https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/?h=next-20180119&id=b70b309950418437bbd2a30afd169c4f09dee3e5](https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/?h=next-20180119&id=b70b309950418437bbd2a30afd169c4f09dee3e5)

Besides this patch (which will not be needed for very long as it will be in mainline kernel sources soon), you wil need to replace /usr/share/alsa/ucm/chtrt5645/HiFi.conf with a modified one I shared on my github:
[https://github.com/harryharryharry/x205ta-iso2usb-files/blob/master/HiFi.conf](https://github.com/harryharryharry/x205ta-iso2usb-files/blob/master/HiFi.conf)

It is a copy of HiFi.conf Pierre Bossart had on his github (he modified something 2 months ago that breaks audio on the X205TA - which is already [reported back to him by plennaerts]("https://github.com/plbossart/UCM/commit/7815960261a935391d4103b240712e782a4b6fcb#comments")). My modifications are to set speakers output as default (instead of headphones) and changing the RECMIX channels for the Analog Microphone to BST2 instead of BST1.

---

### Post by datgrey on 2018-01-23
Hi guys,
first of all thanks a lot for all your work getting Linux to a usable state on the X205!
I have successfully installed Debian 9 (dual booting with Windows 10) on my machine just yesterday using Harry's last prebuilt image, everything seemes to work OK but I'm facing a strange issue: I can't modify the screen brightness anymore on Windows (FN+F5 and FN+F6 don't do anything; FN+F7 correctly shuts the screen off though).
Has anyone faced a similar issue before? Any idea on how to test the brightness key on Debian with Xfce to rule out a possible hardware problem? Thanks!

---

### Post by harryharryharry on 2018-01-23
Which kernel (version) are you using?  Brightness keys didn't get support until (I think) around march 2017. If you are running the stock kernel debian ships with, the kernel might be rather old and not yet have brightness fn keys support.

---

### Post by datgrey on 2018-01-23
Ignore this post... I've found out that the root of the problem had nothing to do with me installing Debian, it was a generic PnP-Monitor driver installed by TeamViewer disabling all the brightness functions.
Sorry for the confusion and thanks a lot!
---
Thanks for the quick response :) I was using the stock kernel, now I've updated it with your version (revision 27) and can confirm the fn keys work while using Debian; the problem still persists with Windows though, I've even tried resetting the installation and reinstalling the ATK package drivers but it didn't fix the issue.
I'm starting to think the problem isn't with the keys though, since I can't turn on "Night light" either nor change the brightness level from "Power Options" -> "Edit Plan Settings" (there's no brightness bar at all); can someone with a dual-boot setup confirm these functions should work?

---

### Post by harryharryharry on 2018-01-24
Hehe, good you found out the cause and posted it here anyway. Some other people that are dual booting might be able to help address the brightness issue under windows. If you haven't found it already, there seems to be a thread for this issue on the teamviewer forum (not really a big help since apparently the issue has been around for some time, and there doesn't seem to be much progress):
[https://community.teamviewer.com/t5/TeamViewer-General/Display-brightness-function-lost-after-install-of-monitor-driver/td-p/9036](https://community.teamviewer.com/t5/TeamViewer-General/Display-brightness-function-lost-after-install-of-monitor-driver/td-p/9036)

---

### Post by onetefo2 on 2018-03-31
Hi!

After several time (years?) I have been using the harry^3 and kemyland custom kernels and patches for my x205ta with Arch. Currently, I am using the custom kernel for x205ta from the AUR.

But since the bluetooth is working, I've experienced a strange behaviour: when it's working, the Wifi speed connection suddenly drop down (i.e. from 1-2MB/s to 10-100KB/s).
Anyone else have this issue?

Thank you all of you again!

---

### Post by Yochanan on 2018-03-31
Whoops, nevermind.

---

### Post by mastertorch on 2018-04-13
Dear Harry³, I just created an manjoro deepin usb live stick with your great tool. I was not able to finish the install procedure of manjoro due to a grub error. I then followed your steps above and tried to reinstall grub via chroot. It failed due that no i386-efi files are installed. I was not able to install these. Somewhere I found the advise to install grub-i386-efi via AUR, but I was not able to find any package like that. Installing Grub via AUR faile, also.
Do you have any idea how to get the system to boot from ssd?

Best regards 
mastertorch

---

### Post by Yochanan on 2018-04-13
@mastertorch

Did you run the /root/install-grub.sh right after installation finished?

FYI, harry has current prebuilt ISO's of Manjaro Deepin, Cinnamon and Budgie on his website.

---

### Post by mastertorch on 2018-04-13
@Yochanan
Yes, I ran the bash script while in chroot. It tries to install grub via the i368-efi folder, which didn't worked, because there is no i368-efi folder in usr/lib/grub/.
Do you know if Harry applied any additional tweak for his iso's of Manjaro? As I know, Manjaro 17.0.3 was the last release to have a 32-bit ISO. Therefore there is no i368-efi support anymore. Which version of Manjaro do you use on your x205ta?

---

### Post by Yochanan on 2018-04-13
Why are you trying to install 32-bit? Remember, this device supports 64-bit but has a 32-bit UEFI bootloader. Both the script and the prebuilt ISO's are meant for 64-bit and will install 32-bit grub.

I'm running Manjaro Xfce 64-bit 17.1.7.

If you really want to install 32-bit, there is a community project that's been releasing 32-bit Manjaro builds for months now: [https://manjaro32.org/](https://manjaro32.org/)

---

### Post by mastertorch on 2018-04-13
Oh, don't get me wrong. I installed 64bit but there is no 32bit grub available. So the install is not bootable. How did you manage to install 32bit grub?

---

### Post by Yochanan on 2018-04-14
I ran the install-grub.sh after installation was finished. I forgot to do that once, so I just wiped the USB stick and reinstalled.

---

### Post by mastertorch on 2018-04-14
@Yochanan

I PM'ed Harry³ about my problems and he pointed out that grub version in the arch repo contains all needed files for filling /usr/lib/grub with the needed I386-efi files. I just checked the version of grub in  the Manjaro repo, it is 2.03.0-5 and the A.L.A version with the I386-efi  files is 2:2.02-5.
So I installed downgrade via pacman while in chroot:

pacman -Syu downgrade

and downgraded to 2:2.02-5 via:

DOWNGRADE_FROM_ALA=1 downgrade grub

and then selected grub version 2:2.02-5.
This filled the chroot/usr/lib/grub/I386-efi and I installed grub via Harry's script /root/install-grub.sh.

Worked like a charm. After this I just needed to add the headphone support and the UCM-File from Pierre Bossart&#8217;s github.

--
Just for information: 

I also had the problem to use pacman with chroot. I followed Harry's instructions for neccessary mounts, but following link was missing:

sudo ln -s /proc/self/mounts /etc/mtab

Also in Manjaro you can access chroot via 

sudo manjaro-chroot /mnt/ /bin/bash

without mounting proc, sys, dev.
--

Now I have some issues with hibernation. Sometimes after wake up, sound is broken. Also after a few hours of hibernation the system wont wake up at all. What are your experiences regarding hibernation?

---

### Post by Yochanan on 2018-04-15
Don't use hibernation, it's never worked well. I use suspend instead. Sometimes it'll still freeze during suspend even with the patches harry added, but it's much better than it used to be.

---

### Post by Yochanan on 2018-06-24
@harryharryharry:

I just tried building a Manjaro 17.1.10 ISO and received the following error. I built Manjaro 17.1.8 at the beginning of June just fine.

```
+ create_install_grub_executable
+ cat
./x205ta-custom-liveusb.sh: line 465: /home/yochanan/ISO/X205TA/tmp.s9R6nwG8Yc.x205ta-custom-liveusb.sh/squashfs-root/root/install-grub.sh: No such file or directory
```

[verbose log]("https://pastebin.com/9Xc7ZzsC")
[URL="https://pastebin.com/Kk2YLfnz"]tree of working directory
[/URL]

---

### Post by jul1en on 2018-06-27
Hi all,
I had a working x205ta with xubuntu -thanks to harry's and others hard work- and want to switch to Manjaro. 
I tried harry's iso and was not able to make it boot.
I used the custom script to prepare my usb drive and am able to boot the live session but the installation fail for reasons apparently similar to mastertorch (i386-efi files missing). I tried to follow the post from mastertorch but I am struggling after dozens of trials and fails :confused: maybe I need a bit more detailed guidance... I am not a very advanced user...

I confirm that the script does not work with last manjaro iso 17.1.10 but is OK with older ones

---

### Post by harryharryharry on 2018-07-03
It seems manjaro have altered their iso labels a little, so the script wasn't recognizing the isos as being manjaro isos anymore. I've updated the [script]("https://ubuntuforums.org/showthread.php?t=2254322&page=176&p=13660509#post13660509") (needed to remove literally 1 character ;)). Thanks for the feedback. Other feedback is always welcome via PM.

---

### Post by Yochanan on 2018-07-05
Thanks! Not a big deal, but for some strange reason, the ISO is owned by root instead of me:

```
-rw-r--r-- 1 root     root     2387427328 Jul  5 08:51 x205ta-harryskernel-manjaro-xfce-17.1.10-stable-x86_64.iso
-rw-r--r-- 1 yochanan yochanan 2282766336 Apr 19 13:08 x205ta-harryskernel-manjaro-xfce-17.1.8-stable-x86_64.iso
```

---

### Post by harryharryharry on 2018-08-12
Ah yes, because there are several actions (tweak files inside iso, mounting, formatting usb) that need root permissions, I've lazily added a root-check so the whole [script]("https://ubuntuforums.org/showthread.php?t=2254322&page=176&p=13660509#post13660509") can only to be run as root, that's why it also outputs a file with root ownership. I've added a chown command at the end of the script that changes ownership of the file to the sudo user that runs the script (and also some improvements to the usb formatting, sometimes the script created a usb stick that didn't boot because the stick wasn't properly formatted, I think I solved that now).

---

### Post by bazzle2 on 2018-09-18
Hey guys I have a major problem I cannot install another distro on my X205ta because it won't pass (initramfs) screen. Did anyone encounter this and found a fix please?

---

### Post by Yochanan on 2018-12-02
> **harryharryharry said:**
> ...

I just tried creating a Manjaro Xfce 18 USB on my other laptop running Manjaro Cinnamon and noticed this error during the build:

```
==> Starting build: 4.19.2-sound-39
  -> Running build hook: [base]
  -> Running build hook: [udev]
  -> Running build hook: [block]
==> ERROR: Hook 'miso_shutdown' cannot be found
==> ERROR: Hook 'miso' cannot be found
==> ERROR: Hook 'miso_loop_mnt' cannot be found
==> ERROR: Hook 'miso_kms' cannot be found
  -> Running build hook: [filesystems]
  -> Running build hook: [keyboard]
==> Generating module dependencies
==> Creating gzip-compressed initcpio image: /boot/initramfs-4.19.2-sound-39.img
==> WARNING: errors were encountered during the build. The image may not be complete.

```

[Verbose log]("https://pastebin.com/4C92tThx")
I changed this line so it would build in RAM: 
```
WORK=$(mktemp -d --suffix=.${0##*/} -p /tmp)

```
I haven't tested the USB yet as my X205TA is in storage at the the moment.

---

### Post by harryharryharry on 2018-12-06
I looked into the error and it seems a new pacman version deprecated the  use of --force as a flag. This option is used in the script to install  some needed packages - in this case manjaro-tools-iso - to be able to  create a bootable new kernel/initramfs. There doesn't seem to be a  replacing option to overwrite all existing files and directories pacman  encounters.

[S]This means making a manjaro iso with an updated kernel using the script  isn't possible anymore (at least it isn't a simple rewrite). However,  you can still boot the resulting iso with the original kernel by  choosing it in the grub menu. If you succeed in installing manjaro you  can then install my kernel.[/S]See my next post

---

### Post by freemedia2018 on 2018-12-06
> **harryharryharry said:**
> This means making a manjaro iso with an updated kernel using the script  isn't possible anymore (at least it isn't a simple rewrite).

Hi, automated remastering fan here. 

Forgive my lack of familiarity with manjaro, if you can't --force couldn't you delete the files or folders that you wanted it to overwrite?

---

### Post by harryharryharry on 2018-12-06
[S]Yes that's possible, but quite honestly it isn't worth the hassle.[/S]Last time I tried installing manjaro, the live-installer didn't work properly (crashed) with my kernel. So to install you have to use the original kernel anyway.

edit: I made another attempt and seems like it was easier than I initially thought. I've updated the script and made an image of manjaro minimal xfce (as stated before, installation might still fail (with my kernel), this is X205TA we are talking about after all ;) )

---

### Post by Yochanan on 2018-12-11
That did the trick, I successfully created the image. Thanks! Yeah, the --force flag is depreciated and there's now --overwrite, but neither are recommended to use at all.

---

### Post by harryharryharry on 2018-12-14
Nice! Yeah you're right, it was a hacky way to get around certain Manjaro-quirks (rootfs is divided between 4 different squashfs-files) that led to errors when building a custom iso &#8212; which (to my surprise) isn't needed anymore. If you are on the installed version of Manjaro (or any linux really) you should (almost) never have to use the --overwrite/--force option of the package manager in question, as the package manager isn't aware what it might end up breaking.

---

### Post by lordenzo on 2019-04-12
I have an Asus x205ta and i am trying to install linux(Mint) onto it and i have had no luck and i believe the problem discussed here is the reason. I'm wondering if this method is the best method to install linux and does it still work? I'm currently running windows 10 and it looks like many of the commands in OP are linux commands so im wondering how will i be able to install a single installation of linux over windows? A good starting point for me would be greatly appreciated.  Thanks.

---

### Post by michael348 on 2019-04-20
FWIW Arch Linux kernel 5.07 has wifi support OOB.

---

### Post by constantin- on 2019-07-07
Hello, all!
There are 2 good news for X205TA users:
1) ASUS has released new BIOS (203 for X205TAW & 213 for X205TA) after ~4 years [https://www.asus.com/us/Laptops/ASUS_EeeBook_X205TA/HelpDesk_BIOS/](https://www.asus.com/us/Laptops/ASUS_EeeBook_X205TA/HelpDesk_BIOS/)
2) New Debian 10 'buster' runs out-of-box with stock kernel at X205TA (wi-fi, bluetooth, sound+mic), only brcmfmac43340.txt is needed
cp /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113 /lib/firmware/brcm/brcmfmac43340-sdio.txt

---

### Post by datgrey on 2019-08-14
@[**[COLOR=#000000]constantin-[/COLOR]**]("https://ubuntuforums.org/member.php?u=2077489") Hi, what kernel version are you using? I tried a clean install and with Buster default 4.19 kernel I have no sound.

Edit - I got it working doing the following:
1) install kernel 5.2.8
2) download HiFi.conf and chtrt5645.conf from harryharryharry's and PierreBossart's GitHubs
3) install firmware-intel-sound from Buster non-free packages

Edit 2
I realized that headphones weren't working, I had to add the line "options snd_soc_rt5645 quirk=0x31" to /etc/modprobe.d/50-x205ta.conf

---

### Post by akashp21 on 2019-10-16
Hi everyone, i have managed to make almost everything work on my laptop, except bluetooth. I have attempted to follow Harry's guide to enable it, also from Arch wiki, etc, nothing seems to quite work.
This is my output while trying to query for the status of btattach.


```
btattach.service - Btattach
   Loaded: loaded (/etc/systemd/system/btattach.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2019-10-16 15:06:50 IST; 4s ago
 Main PID: 1823 (code=exited, status=1/FAILURE)

Oct 16 15:06:50 akash-debian systemd[1]: Started Btattach.
Oct 16 15:06:50 akash-debian btattach[1823]: Failed to open serial port: No such file or directory
Oct 16 15:06:50 akash-debian btattach[1823]: No controller attached
Oct 16 15:06:50 akash-debian btattach[1823]: Attaching Primary controller to /dev/ttyS4
Oct 16 15:06:50 akash-debian systemd[1]: btattach.service: Main process exited, code=exited, status=1/
Oct 16 15:06:50 akash-debian systemd[1]: btattach.service: Failed with result 'exit-code'.
```

Also it shows that controller is not attached..

any ideas guys? i have been trying to do it for 2 days without any avail...

---

### Post by camero2734 on 2020-01-31
Hello all,

I recently installed Linux Mint (the one from [http://x205ta.myftp.org:1337/isos/](http://x205ta.myftp.org:1337/isos/)). Everything works perfectly fine!

Except that the microphone didn't work. I noticed that my kernel was sound-40, while the latest was 43 (here [http://x205ta.myftp.org:1337/kernel/](http://x205ta.myftp.org:1337/kernel/)). So I installed it... and now my sound is completely broken.

pavucontrol simply says "Connection to PulseAudio failed". I tried using the remove-harry-kernels.sh script to see if that would help (and then I reinstalled the 43 kernel afterwards), but PulseAudio is still broken. I also tried using following [https://askubuntu.com/questions/426648/how-to-reinstall-pulseaudio-ubuntu-12-04](https://askubuntu.com/questions/426648/how-to-reinstall-pulseaudio-ubuntu-12-04) to reinstall pulseaudio, but the problem still exists.

What do I do?

---

### Post by coffeecat on 2020-01-31
Moved post #36 to the any other OS Asus X205TA thread.

---

### Post by Yochanan on 2020-09-14
First post edited with updated install instructions.

---

### Post by sverx on 2023-01-08
> **joshua123456 said:**
> You are referring to an old and obsolete guide. Which distro did you install?

Ubuntu and his flavors have now out of the box support for the X205TA. You can build your own iso with Harry's script.
 
[https://ubuntuforums.org/showthread.php?t=2254322&page=214&p=13983970#post13983970](https://ubuntuforums.org/showthread.php?t=2254322&page=214&p=13983970#post13983970)

Once you have build your own custom iso you can live-boot it and start the installation. Bluetooth/Wifi/Etc will work without any tweaking.

I build my custom Ubuntu iso a year ago for Ubuntu 20.04.2, all worked fine although with today's knowledge I would probably have switched to Lubuntu as it uses less resources. Unfortunately my X205 has died.

I still didn't install anything, I was simply checking a few live Linux distros...

But even on latest Bodhi, that is based on Ubuntu 20.04, the Bluetooth doesn't seem to work. Same on WattOS, which is Debian based but has a very very recent kernel. Bluetooth is working on Windows 8.1 so it's definitely something on the Linux side.

---

### Post by joshua123456 on 2023-01-09
> **sverx said:**
> I still didn't install anything, I was simply checking a few live Linux distros...

But even on latest Bodhi, that is based on Ubuntu 20.04, the Bluetooth doesn't seem to work. Same on WattOS, which is Debian based but has a very very recent kernel. Bluetooth is working on Windows 8.1 so it's definitely something on the Linux side.

I don't know neither Bodhi nor WattOS. They are also not official Ubuntu flavours. You might want to try to get some help somewhere else for those distro's?

If you want Bluetooth to work I suggest to build your own iso (with the script I was referring to in my previous post) and try Lubuntu, Xubuntu or Ubuntu first. Those will work as I know from my own experience.

---

### Post by sverx on 2023-01-09
Sure, I'm getting help already both from the Bodhi Linux and the WattOS communities, I just was referring to the "distro agnostic" instructions to make sure I'm getting everything right.

In any case, the pointed script to build your own ISO doesn't address Bluetooth at all, it just makes sure that the ISO contains the needed files for the EFI boot at 32 bit.

Soon I'll hopefully have some more time to look into this, so I'll chime back again if I need (more) help.

---

### Post by sverx on 2023-01-10
Installing WattOS and of course ran into the uefi32 issue (Calamarin crashed). Fixed that.

But I can't make Bluetooth work. I seem to remember reading somewhere that with Kernel 5.10 you needed some different approach than the btattach one in the guide. I'm failing to find where I read that unfortunately.

Any hint?

EDIT: found, it was [this]("https://ubuntuforums.org/showthread.php?t=2254322&page=217&p=14022861#post14022861")

now Bluetooth seems to work!

 :guitar:

---

### Post by howefield on 2023-01-10
Posts moved to appropriate thread.

---

