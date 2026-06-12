---
title: "MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI"
date: 2013-06-26
forum: Apple Hardware Users
---

### Post by whatsamac on 2013-06-26
Hi everyone,

I have had a very hard time getting Linux to run on a  MacBook Pro 8,2 in EFI mode. I finally managed to collect all the  snippets of information at various places and was able to set it up  properly.  This howto works at least for this specific machine:

MacBook Pro 8,2
Intel(R) Core(TM) i7-2675QM CPU @ 2.20GHz
ATI Radeon HD 6750M 8GB Ram
500 GB HDD
1680x1050 non-glare display

   Result: I can boot into MacOS (EFI), Ubuntu (EFI) with i915 chipset  enabled and radeon disabled, and Ubuntu (EFI) with radeon enabled.


[SIZE=4]**  READ THIS FIRST**[/SIZE]

This Howto is specifically addressing issues that arise when trying to install Ubuntu Linux [COLOR=#ff0000]**13.04**[/COLOR] on a [COLOR=#ff0000]**MacBook 8,2**[/COLOR], however, it has been confirmed as working also for installing Ubuntu Linux [COLOR=#ff0000]**13.10**[/COLOR], and for me the system still works after the upgrade to 13.10 (and even better).  To determine which revision of MacBook you have, click in OS X on the  Apple on the top left, then &#8220;About this Mac&#8221; -> &#8220;More Info&#8221; and see  the generation in the &#8220;Model Identifier&#8221; row. The 8,2 revision has  proven to be especially stubborn not to allow Linux to be run on it, and  the tweaks contained in the installation section may not apply to other  revisions.

    [B][SIZE=4]  
INSTALLING UBUNTU[/SIZE][/B]

[SIZE=3]Preparing the boot medium[/SIZE]

You  should only attempt this after a fresh install of MacOs. Not doing so  may result in undesired effects. After you have completed the fresh  install of MacOS, boot with the MacOS Installation CD and start the disk  utility app from the menu instead of re-installing MacOS again (who  would want to do it twice anyway). Resize the MacOS partition reasonably  to make space for the Ubuntu installation. Reboot into MacOS. Get  Ubuntu ISO image from here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop), be sure to select the 64bit version.  Convert the .iso file to .img using the convert option of hdiutil in terminal:
```
 hdiutil convert -format UDRW -o /<target directory>/target.img /ubuntu.iso
```
Note:  OS X tends to put the .dmg ending on the output file automatically, but  that doesn't hurt. Plug in an USB thumb drive - beware: the following  steps will erase all data on the USB thumb drive, so make sure you don't  have anything important on it. Run
```
diskutil list
```
and determine the device node assigned to your flash media (e.g. /dev/disk2)  To unmount the flash drive, run
```
diskutil unmountDisk /dev/disk<N>
```
(replace  <N> with the disk number from the last command; in the previous example, <N> would be 2). Execute
```
sudo dd if=/<target directory>/target.img.dmg of=/dev/rdisk<N> bs=1m
```
 whereas <N>  is the disk number identified above.  Run
 ```
diskutil eject /dev/disk<N>
```
Leave the USB stick plugged as we want to boot from it soon.

  [SIZE=3]
 Install a proper Boot Manager

 [/SIZE] Now get rEFInd from here: [http://sourceforge.net/projects/refind/files/0.6.12/refind-bin-0.6.12.zip/download](http://sourceforge.net/projects/refind/files/0.6.12/refind-bin-0.6.12.zip/download)  If MacOS does not do that automatically, then extract it. Navigate to the extracted folder in Terminal, and issue 
```
./install.sh
```
 If prompted for your password, enter it.  Then do
 ```
sudo mkdir -p /EFI/refind/drivers
cp  /refind/drivers_x64/ext4_x64.efi /EFI/refind/drivers/.
```
[SIZE=3]

Start the Installation

 [/SIZE]  Reboot your MacBook. The rEFInd boot menu should appear. Select the  Ubuntu EFI image for boot. When GRUB has loaded, make sure you highlight  &#8222;Try out Ubuntu&#8220; boot entry and hit the &#8222;e&#8220; key to edit the boot line  in order to fix broken graphical output with standard options. Add the  following lines after &#8222;load_video&#8220;:
```
outb 0x728 1
 outb 0x710 2
 outb 0x740 2
 outb 0x750 0
```
  This will turn off the radeon GPU to avoid conflicting GPUs resulting  in no output at all.
[SIZE=1]It has been reported that "load_video" is non-existant in the[/SIZE] [SIZE=1]current install medium's grub configuration. It should work if you put it after "set gfxpayload=keep" as well.
 [/SIZE]
Furthermore, in the kernel line, add after &#8222;quiet  splash&#8220;:
```
 i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0
```[SIZE=1]
[/SIZE]
 Double check you typed everything correctly! If you're done, hit F10 to  boot.  Once Ubuntu has loaded (it will take a short while), select  &#8222;Install Ubuntu&#8220; from the desktop.  Follow the installation  instructions. I created a 512 MB boot partition with ext4 starting after  128MB of free space after the MacOS partition (MacOS likes to have  128MB of free space after its partition for no apparent reason), and the  rest I used for &#8222;/&#8220;, also ext4. Assign the mount points (&#8222;/boot&#8220; for  the boot partition, &#8222;/&#8220; for the other one). You might want to add  another partition for swap, but with 4 GB of RAM you should be alright  even without, with 8 GB in any case. Do as you deem reasonable. Do not  mount the MacOS partition or the EFI partition. I recommend to encrypt  your /home folder.

    [SIZE=3]
Setting up Ubuntu to actually work[/SIZE]

  Once completed, you can reboot. The MacBook will boot directly into  GRUB. Now highlight the first line (Ubuntu) again and press &#8222;e&#8220;. Add the  same &#8222;outb&#8220; lines and kernel parameters as set forth above to the boot  menu entry. After having logged in to gnome, start a terminal. You can  also use a virtual console instead of logging in to gnome by pressing  CTRL-ALT-F1 of course, as we don't need GUI for now. First of all we'll  need to get rid of the boot menu editing, as that can become highly  tedious. We do: 
```
 sudo nano /etc/default/grub
```
  Change the line &#8222;GRUB_CMDLINE_LINUX_DEFAULT=&#8220;quiet splash&#8220; to
 ```
&#8222;GRUB_CMDLINE_LINUX_DEFAULT=&#8220;quiet splash i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0&#8220;
```
Uncomment (remove the "#" before) the line "GRUB_TERMINAL=console"[SIZE=1].
[/SIZE]
 Exit with CTRL-X and confirm saving the changes without changing the output name.  Then do: 
```
sudo nano /etc/grub.d/10_linux
``` 
 Locate the line
```
echo "    insmod gzio" | sed "s/^/$submenu_indentation/"
```
with CTRL-W (you can use  the string &#8222;gzio&#8220;). Immediately BEFORE this line, enter the following so it looks like this:
 ```
echo "    outb 0x728 1" | sed "s/^/$submenu_indentation/"
  echo "    outb 0x710 2" | sed "s/^/$submenu_indentation/"
  echo "    outb 0x740 2" | sed "s/^/$submenu_indentation/"
  echo "    outb 0x750 0" | sed "s/^/$submenu_indentation/"
echo "    insmod gzio" | sed "s/^/$submenu_indentation/"
...
``` 
[SIZE=1]Thx hyao2 for telling me how to fix no-show of grub menu![/SIZE]
 Again, double check your edits carefully. Save and close this file too with CTRL-X. Now you can do
 ```
sudo update-grub
``` 
 to make the changes show up in the grub menu. Next we should update the system by doing
 ```
sudo apt-get update 
sudo apt-get dist-upgrade
``` 
 After that, reboot the system. When the screen goes black and turns  bright again, hit and hold the &#8222;ALT&#8220; key to bring up the Apple  bootloader. It will show the option &#8222;EFI BOOT&#8220;. Select it and rEFInd is  there again. Boot into MacOS and re-run the rEFInd installation routine  again in terminal: 
```
cd <directory to which refind has been unpacked>/refind/
./install.sh
```
  If you now reboot, you will get to the rEFInd menu without having to  press &#8222;ALT&#8220;.  Note that you should see at least 6 big boot options in  rEFInd (as of June 2013). The first one is Ubuntu loading via GRUB,  followed by MacOS. Then there should be at least two (depending on how  many kernel upgrades you have made) penguin icons which may not be able  to be properly booted. To the right there should be at least two  additional Ubuntu Icons. With them, you can load the respective Ubuntu  kernel directly via EFI stub. The difference between those and the left  Ubuntu icon is, that with the left one we'll get to GRUB which we  configured to turn off the ATI GPU. This will allow Ubuntu to make use  of the integrated i915 GPU, resulting in 10 to 20 degree less  temperature and higher battery life. However, the GRUB menu is no longer  shown after re-installing rEFInd, I have yet to discover why the screen  goes blank for the duration the GRUB menu is displayed (which I assume  it is). If you wait for like 10 seconds without pressing a key, the  Ubuntu loading screen appears.  Should you need higher GPU performance  for whatever reason, you can boot the most current kernel via the  appropriate right icon. This will activate the ATI GPU, but will also  result in higher temperature.  I hope this saves some people the time I  had to spend to get this up and running! I have yet to dig into the  vgaswitcheroo configuration which I have seen reported to be working  under certain circumstances. For now the selecting at boot time already  exceeds my expectations and is absolutely sufficient for me.

NOTE: with kernel 3.13 dynamic power management got introduced into the kernel, to make use of this feature and greatly enhance battery runtime under EFIStub, edit the kernel options line from within rEFInd and append 
```
radeon.dpm=1
```
For now, this will have to be done each time you boot via EFIStub, until I have time to figure out how to add that permanently.

   [SIZE=3]Enabling External Monitor via Displayport[/SIZE] 

 So far accessing an external monitor works only when booting with  radeon enabled (as the i915 sadly does not have any access to the  MacBook&#8217;s displayport). Though it didn&#8217;t work for me at first, it  suddenly started working after I had fiddled around with the drivers for  a bit. I&#8217;m not sure what actually enabled the displayport, I would get  only a black screen before, but after this it worked: 
```
sudo apt-get install fglrx-amdcccle-updates fglrx-updates
```
(This  was executed in radeon enabled mode) I rebooted into radeon enabled  mode, and ended up with a X-error resolving routine that looked like it  was part of gnome or lightdm. I exited to the console, deinstalled the  proprietary drivers (who would want those anyway) by doing
```
sudo apt-get remove &#8211;purge fglrx-amdcccle-updates fglrx-updates
```
 and rebooted again into radeon enabled mode. I started up gnome to  check if it was a KDE related thing, plugged the monitor in, and there  you go, display is automatically extended to the external display. I  logged out, and it worked in KDE too. No idea what made it work, but it  works now!

[SIZE=3]
Enabling CD Eject Key in KDE[/SIZE]

Right-click on the Kickoff Application Launcher, select "Edit Applications". Navigate to the System group, select "New Item" from the icon bar. You can name the new item "Eject" like I did or whatever you like. A description could be "Eject CD". The command to be run is "eject /dev/sr0". Un-check the "Enable launch feedback" checkbox. Save. Go to the "Advanced" tab, and click on the shortkey button. Hit the Eject CD key on your MacBook Pro's keyboard, it should register as "eject". Save again and exit. It should work now (it does for me at least).

[SIZE=3]
Stuff that works out of the box for me:

[/SIZE] Display backlight adjustment
Sound Volume adjustment
Webcam
Microphone
 Suspend to RAM and Resume (so far no crashes)
WLAN
Bluetooth 
iPhone Tethering via Bluetooth and USB works flawlessly too if you install
 ```
sudo apt-get install ipheth-utils libimobiledevice-dev libimobiledevice-utils
```
[I]
Since upgrade to 13.10:[/I]
SD Card Reader
Keyboard Backlight hotkeys


   [SIZE=3]To be fixed:[/SIZE]
Enabling proprietary drivers for AMD GPU in EFI STUB boot mode. So far I seem to use out of the box drivers that don't really provide a benefit over using the i915 chipset performance-wise. Installing the fglrx driver via jockey-kde leads to system crash upon boot (which can be fixed by removing fglrx after booting into grub mode). I didn't have much time to spend on this issue yet, though.


[SIZE=3]To be tried:[/SIZE]
Setting up vgaswitcheroo for dynamic GPU switching.

Edit: After upgrading to 13.10 (replacing all packets with packet maintainer's version and re-applying changes to /etc/grub.d/00_header), keyboard backlight setting via function keys works, too, as does the SD Card Reader.

---

### Post by buzzingrobot on 2013-06-27
Thanks for this.  I followed a similar path to get 13.04 on my 8.2 with the Intel graphics.  Then, botched it by adding and removing Gnome.  When my patience returns, I'll follow your steps.

I also needed to do the outb bit resuming from suspend, otherwise it would try to use the Radeon.

---

### Post by whatsamac on 2013-06-27
Oh right, I have yet to test if it wakes up correctly from suspend if I booted with radeon enabled. So far I'm only using the Grub boot version with disabled radeon...  Edit: Ok I got so nervous and curious that I needed to test it right away. I tested it two times, one time even with a running virtual machine (win7 on virtualbox). Both times it worked flawlessly - of course that has no statistical relevance, but it is proof of concept that it won't fail EVERY time.  Note that I get a temperature of 50°C in i915 mode with plain desktop and no running programs, whereas the temperature is around 75°C now that I booted with radeon and don't have any programs running. The temperature drop is really significant :D   So far I have not experienced a lockup or black screen on resume either way with this installation.

---

### Post by buzzingrobot on 2013-06-27
There's code here ([http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/](http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/)) that handled suspend for me.  The rest of the article didn't pan out for me.

My temps on Intel were at 50C or just below, at idle.  I did a long compile and they spiked in the 80's. 

The Radeon is unusable on Linux.  Temps spike and the fans max out with any activity.

I also had to block updates to the default kernel installed on 13.04. It wouldn't boot with an updated kernel.

---

### Post by whatsamac on 2013-06-27
Really? Temperature goes high indeed with radeon enabled, but performance is good, too. I am running on 3.8.0-25 without any issues so far.

---

### Post by buzzingrobot on 2013-06-27
Performance with the Radeon is fine.  It's just way too hot and way too noisy.

Good to know about the 3.8.0-25 kernel.  I don't think I got that far in the upgrades.  I remember the initial apt-get upgrade bumped the 3.8.0-19 a bit, and the machine would not boot.  

I *think* Apple released two very slightly different machines under the 8,2 label. That might account for differences in behavior, as well as for howto's that work for some and not for others.

---

### Post by whatsamac on 2013-06-28
Might be there are two slightly different machines, that would explain why I couldn't get it to work with any of the tutorials out there so far.  I'm still struggling to enable an external Monitor - I've got it plugged into the displayport via a displayport->DVI adapter, which works under MacOS. But under Ubuntu the kde system settings recognize it and it gets enabled, but there is no output. The workspace is appropriately enlarged, but with no graphical output on the screen that doesn't really help. Any ideas anyone? This is the same if booting in i915 mode or with radeon enabled.

---

### Post by whatsamac on 2013-07-01
Though it didn&#8217;t work for me at first, it suddenly started working after I had fiddled around with the drivers for a bit. I&#8217;m not sure what actually enabled the displayport, I would get only a black screen before, but after this it worked:

```
sudo apt-get install fglrx-amdcccle-updates fglrx-updates
```

(This was executed in radeon enabled mode) I rebooted into radeon enabled mode, and ended up with a X-error resolving routine that looked like it was part of gnome or lightdm. I exited to the console, deinstalled the proprietary drivers by doing

```
sudo apt-get remove &#8211;purge fglrx-amdcccle-updates fglrx-updates
```

and rebooted again into radeon enabled mode. I started up gnome to check if it was a KDE related thing, plugged the monitor in, and there you go, display is automatically extended to the external display. I logged out, and it worked in KDE too. No idea what made it work, but it works now!

Last thing that remains for me now is to configure X to actually use the radeon driver, so far I get lower FPS on benchmarks that I ran when I booted with radeon than when I booted in i915 mode o.O despite setting "radeon" and forcing gallium3d in xorg.conf, this does not seem to have any effect. I don't really want to install fglrx, as for my purposes open-source drivers are probably performing sufficiently as long as dual screen works, but surely they'll perform better than the i915 chipset?

---

### Post by whatsamac on 2013-07-08
Another short update: I just updated to Kernel 3.8.0-26, both GRUB (i915) boot and EFI STUB (radeon) boot work for me with this kernel update.

---

### Post by Fizzaxe on 2013-07-13
I cannot get Ubuntu to show up in the boot loader as an option.  I've followed your instructions exactly, as well as the [last post here]("http://ubuntuforums.org/showthread.php?t=1839317").  I continue to get "legacy OS" as the other option to boot from.  It goes away after unplugging the usb stick and of course comes back as an option after plugging it in and refreshing.  After formatting the drive (per the linked post recommendation) this is what I have below.  Am I suppose to do something different with this legacy option?  If I select it, it doesn't work and says its not bootable and drops to a prompt.  I did convert the download like you said and I did download the mac desktop version.

/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *3.9 GB     disk1
   1:                        EFI                         209.7 MB   disk1s1
   2:                  Apple_HFS                         3.6 GB     disk1s2

---

### Post by whatsamac on 2013-07-16
That's weird, I used the following guide to create the bootable USB thumb drive:  [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)  The steps I described above should work if you have a MacBook Pro 8,2... do you have another model maybe?

---

### Post by whatsamac on 2013-07-31
Latest Kernel Update (3.8.0-27) is running nicely.

---

### Post by SilverOne on 2013-08-11
I didn't follow your guide but i've been doing ubuntus installations very similarly to yours, i however don't use reFind and have been compiling custom kernels for integrated graphics support: [http://ubuntuforums.org/showthread.php?t=2115317](http://ubuntuforums.org/showthread.php?t=2115317)

i've tried using your refind setup with the v3.9 kernel available from : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) but no luck with efi stub

i haven't tested the sd card reader but the keyboard backlighting works perfect, with the notable exception of it always booting with it.

---

### Post by bustamanteguevara on 2013-08-12
Do you guys know if this information is relevant to the Macbook Pro 9,2? I suppose I will have to check what is the chipset and what are the differences.

---

### Post by whatsamac on 2013-08-12
I fear that the MacBooks' hardwares are pretty different from revision to revision, there seemingly are even models of the 8,2 series around that behave differently than mine does. At least I have followed several tutorials for other distributions and none of them really worked for me despite other users reporting success.

I don't know why one would avoid using rEFInd as it works rather flawlessly as far as I'm concerned, but unmodified kernels from 3.8 upwards should boot without problems via EFISTUB - if you get them selected for loading via EFISTUB properly. At least that's what I've read.

Note that with my installation procedure you'll end up with the following bootable symbols in rEFInd:

Ubuntu (GRUB) - MacOS - some Tuxes, depending on the number of kernel upgrades (all of them not working!) - Ubuntu (latest kernel, EFISTUB, working) - Ubuntu (previous kernel, EFISTUB, working) - etc...

---

### Post by Courtney_Bodi on 2013-08-23
Thank you so much! I've been trying to dual boot my computer without having it overheat for days. This tutorial was extremely easy to follow and it worked : )

---

### Post by whatsamac on 2013-08-27
Glad to hear that, thank you!   Recent Kernel Update 3.8-29 did not cause any troubles.

---

### Post by SilverOne on 2013-09-04
Hello,

this method is working for me under arch linux with kernel 3.10.10-1.

thanks again whatsamac!

---

### Post by whatsamac on 2013-09-06
Hey SilverOne,  thanks for the feedback! I would greatly appreciate if you could document how you succeeded in installing Arch Linux on this machine, as I have been trying very hard to get Arch Linux to run on this and somehow never succeeded to make it boot into i915 mode with radeon disabled. I always struggled at the point where it comes to installing a bootloader - where should I install it to (EFI partition, or somewhere else), what needs to get into the relevant directories and such. I found this tutorial [http://rorygarand.com/blog/2013/6/6/arch-linux-on-a-macbook-pro-82-part-4-boot-loader](http://rorygarand.com/blog/2013/6/6/arch-linux-on-a-macbook-pro-82-part-4-boot-loader) but unfortunately it didn't work out for me :(

I value Ubuntu for its stability and easy installation, but I'd personally prefer Arch for various reasons. If you could take the time to document your installation process (probably on the Arch Linux forum), I would be very happy to give it another try!

Also I was just experimenting with fglrx and fglrx-updates, but both end up with not being able to get the VBIOS from the kernel. Strangely, the opensource xorg-radeon driver does not seem to provide ANY performance improvements over the i915 chipset (benchmarking with Xonotic here), not sure if I need to specifically set the driver via config but the Xorg log looks like it gets loaded.

The recent kernel update 3.8-30 ran through fine.

---

### Post by SilverOne on 2013-09-08
> **whatsamac said:**
> Hey SilverOne,  thanks for the feedback! I would greatly appreciate if you could document how you succeeded in installing Arch Linux on this machine, as I have been trying very hard to get Arch Linux to run on this and somehow never succeeded to make it boot into i915 mode with radeon disabled. I always struggled at the point where it comes to installing a bootloader - where should I install it to (EFI partition, or somewhere else), what needs to get into the relevant directories and such. I found this tutorial [http://rorygarand.com/blog/2013/6/6/arch-linux-on-a-macbook-pro-82-part-4-boot-loader](http://rorygarand.com/blog/2013/6/6/arch-linux-on-a-macbook-pro-82-part-4-boot-loader) but unfortunately it didn't work out for me :(

I value Ubuntu for its stability and easy installation, but I'd personally prefer Arch for various reasons. If you could take the time to document your installation process (probably on the Arch Linux forum), I would be very happy to give it another try!

Also I was just experimenting with fglrx and fglrx-updates, but both end up with not being able to get the VBIOS from the kernel. Strangely, the opensource xorg-radeon driver does not seem to provide ANY performance improvements over the i915 chipset (benchmarking with Xonotic here), not sure if I need to specifically set the driver via config but the Xorg log looks like it gets loaded.

The recent kernel update 3.8-30 ran through fine.

sure i'll pm you

---

### Post by SilverOne on 2013-09-08
doublepost :(

---

### Post by Quackers on 2013-09-08
I'll relate my story so far regarding installing Ubuntu 13-04 on a 15" retina MacBook Pro 10,1, which has an onboard Intel graphics chip and a Nvidia GT650M chip.
This may (or may not) clarify some of the things that whatsamac has done. It may also raise questions in some respect.

Basically I downloaded the 64 bit mac version of Ubuntu 13-04 and made a USB stick in the same way as whatsamac did (hdutil).

I installed rEFInd whilst in OS X and rebooted to make sure all was good.

I then booted from the usb drive and tested the live desktop. I was aware that wireless would not work (which is a problem as this laptop does not have an ethernet card) so I had previously downloaded the drivers et al on a separate usb stick. In the live environment I tested that installing these drivers/firmware worked ok - and they did.

I then installed Ubuntu in the normal way (having already created some free space with disk utilities in OS X). 

Before I rebooted I added ```
i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0
``` to the kernel line in /etc/default/grub and then ran ```
sudo update-grub
```
You will notice that this is not quite the same as whatsamac's line. I believe this line disables the Intel grahpics chip forcing the Nvidia chip to work, but I'm not 100% sure on that.

At this point I rebooted and in the rEFInd menu I just got entries for Windows 8 (already installed), OS X and Ubuntu.
On selecting the Ubuntu entry it booted to a black screen only. 
After several hours of trouble-shooting I ended up contacting Rod Smith (authour of Rodsbooks, who used to be a member on this site) and told him what I'd done.
He suggested I install the "drivers_x64/ext4_x64.efi" (which I had not previously done) and it should then boot. This is what I did and the system then booted normally (though not through Grub).

As I constantly mess with my system I was not happy that I could not get to a grub menu (as I appeared to be booting via EFIstub) which is handy for entering boot prompts, when necessary, so I then ran Boot-Repair tool selecting the advanced options then Grub location and selected the "separate boot/efi partition" and hit apply.
This ran ok and on reboot I then got the rEFInd menu and on selecting Ubuntu it now goes to a grub menu which I can edit at will.

I have not found any Ubuntu packaged Nvidia drivers that will work with this setup (304.88, 310.xx will not boot). However I downloaded and installed 319.49 from the Nvidia site and ran the .run file with X shutdown.
I then had to edit the /etc/X11/xorg.conf file (with nano) to include the line ```
Option         "UseDPLib" "off"
``` in the Section "device" section. I again ran sudo update-grub (not sure whether that was needed) and rebooted to see the Nvidia splash screen (just briefly) and a normally booting system with 3D acceleration.

Sound worked out of the box and after installing the wifi drivers/firmware I got connected to the internet.
The screen backlight is not adjustable via the keyboard, though the little icon appears to adjust ok on the screen it is actually adjusting the keyboard backlight.
Some of the F keys work, though I can't get things like Alt+f2, ctrl+Alt+t to work even though those shortcuts appear to be loaded.

Screen resolution was stuck at the default 2880x1800 (iirc) so things were very small. I got round this by issuing ```
xrandr --output DP-2 --scale .6666x.6666
``` in the terminal (after first running xrandr -q to find out the screen's designation - DP-2 in my case - the "connected" one in the output), giving me two thirds screen resolution (1920x1200). Once I saw this was good I included that instruction as a startup item so that this resolution is there from boot.

Before installing the Nvidia driver suspend would work but resume would give an unusable display - nothing worked.
After installing Nvidia the same happens unless I actually select "suspend" from the menu. In this case resume works fine. However, just closing the lid will suspend the machine but resume will not work. Also on resume the screen backlight defaults to what appears to be full brightness which is not how it was before suspending.

---

### Post by whatsamac on 2013-09-09
Thank you Quackers, but since you've got a different hardware I'd suggest you to open a topic dedicated to the model you have. This would then allow discussion specific around the MacBook Pro 10,1 retina, which would make it easier for people searching for the 10,1 retina to find what they are looking for. This thread is about the 8,2 - and it contains specific fixes that are required to make THIS machine run. I believe there are even different series of 8,2 MacBook Pros out there, as some tutorials I've followed for the 8,2 model didn't work out for me...

---

### Post by Quackers on 2013-09-10
I understand that whatsamac but I was thinking that some problems can cross between different machines and a resolution is good wherever it comes from :)

---

### Post by whatsamac on 2013-10-18
Today I upgraded to 13.10. Whenever prompted, I replaced existing changed configuration files with the packet maintainer's new version. Then I re-applied the changes to /etc/grub.d/00_header as in my initial post, and all went fine. Keyboard backlight can be set via function keys now, yay!

Edit: I just tested the SD Card Reader, and that one works too now o.O

---

### Post by dmitrijs2 on 2013-10-28
Repeated steps today setting up Ubuntu 13.10 from scratch. All worked flawlessly.

I discovered that these
```
i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0
```
are not needed anymore.

Also, duplicate monitor appear when booting through EFI stub with Radeon turned on, which causes mouse cursor to blink. To fix that I had to generate /boot/refind_linux.conf (just run mkrlconf.sh from rEFFInd installation files), and then edit to make the first line look like:

```
"Boot with standard options" "ro root=UUID=your-uuid-here  i915.modeset=0 radeon.modeset=1 radeon.dpm=1 quiet splash "
```

---

### Post by whatsamac on 2013-10-31
Thanks a lot for reporting this! I updated my /etc/default/grub and updated grub menu (sudo grub-mkconfig), and can confirm that these lines are no longer required. Great!

I can't confirm the blinking mouse cursor though, when does that happen? I have absolutely no problems when connecting a second monitor and booting with EFI Stub. Of course I have cloned output during boot, but as soon as I reach the login screen, all is fine.

---

### Post by whatsamac on 2013-11-12
Update: I seem to have overlooked to do "sudo update-grub". My installation apparently still needs the i915 lines, I end up with black screen otherwise.

---

### Post by jwilcox09 on 2013-12-10
I'm sorry to rehash this post but I am not sure where to put the outb code?  There is nothing in the file I am editing after pushing 'e' that says 'load_video' .  All i see is this:

[http://imgur.com/Dm4kjX2](http://imgur.com/Dm4kjX2)

Also this is what diskutil list looks like

[http://imgur.com/FQ6KyHr](http://imgur.com/FQ6KyHr)

Thanks for any help

---

### Post by whatsamac on 2013-12-11
No problem, I'm checking on this thread regularly. It seems the boot medium for 13.10 has changed the grub entry a bit then. I figure if you put it after "set gfxpayload=keep", starting with a new line, that should be fine.  You seem to have quite some partitions and disks on your machine. I followed a very simple structure but the number and position of partitions and disks should not be a problem provided rEFInd and grub are configured accordingly so they know where to look (maybe they know even without configuration?). Good luck! :)

---

### Post by hyao2 on 2014-02-02
Thanks a lot to whatsamac for such a great tutorial! 

I've got a MacBook Pro and (8,2) and installed 13.10 on it. However, the grub menu did show. I did the following to get grub menus to show up duing boot, and it's not a very elegant solution. Everytime update-grub, need to edit grub.cfg again.

1. in /etc/default/grub: uncomment "GRUB_TERMINAL=console" (This will get grub menu to show)

2. sudo update-grub

3. edit /boot/grub/grub.cfg, add the following lines in menuentry 'Ubuntu' -> recordfail -> load_video:
outb 0x728 1
outb 0x710 2
outb 0x740 2
outb 0x750 0

One needs to add the same lines to other menu entries for them to boot.

Hope there's a better solution though. :)

Thanks,

---

### Post by hyao2 on 2014-02-02
Following my previous post, I've got grub menu showing full screen! Here's what I did, bascially moving outb lines from 00_header to 10_linux, so that grub starts normally. Then when it's time to boot linux, we use the outb lines.

1. in /etc/default/grub: uncomment "GRUB_GFXMODE=1440x900"; comment out "GRUB_TERMINAL=conssole"

2. remove outb lines from /etc/grub.d/00_header

3. add the following lines before echo "    insmod gzio" | sed "s/^/$submenu_indentation/":

  echo "    outb 0x728 1" | sed "s/^/$submenu_indentation/"
  echo "    outb 0x710 2" | sed "s/^/$submenu_indentation/"
  echo "    outb 0x740 2" | sed "s/^/$submenu_indentation/"
  echo "    outb 0x750 0" | sed "s/^/$submenu_indentation/"

4. sudo update-grub

---

### Post by whatsamac on 2014-02-05
Thank you a lot hyao2, indeed, the grub menu doesn't show if you follow this tutorial, but I also didn't need it to so I didn't care (I think I reduced the time it is shown so I don't have to wait). I will yet have to test this procedure myself and will gladly incorporate it in the tutorial!   

Edit: I can confirm this works very nicely - though I was lucky you mentioned 10_linux so I found out where to put it :o) I'll update the tutorial now. Thanks again!

---

### Post by Ric_Helm on 2014-02-07
I Have a 2006 MacBook 2.1 with an Intel Dual Core 2 Duo. It is 7 years old. I just installed MacOS 10.5.8 and had planned to add Ubuntu as a Dual boot. Do all these work around apply to my particular MacBook? Also, would another Ubuntu variation make it any easier?

Thank You:confused:

---

### Post by hyao2 on 2014-02-11
Ric_Helm: guess MacBook 2,1 uses different hardware than 8,2. There are quite a few wikis on ubuntu.com for your mbp model, and I believe your MacBook will run ubuntu very well.

[https://help.ubuntu.com/community/MacBookPro2-1_2-2](https://help.ubuntu.com/community/MacBookPro2-1_2-2)
[https://help.ubuntu.com/community/MacBook2-1](https://help.ubuntu.com/community/MacBook2-1)
[https://help.ubuntu.com/community/MacBook2-1/Maverick](https://help.ubuntu.com/community/MacBook2-1/Maverick)

---

### Post by hillsidecres on 2014-03-14
Not sure if this thread's still active, but I just want to confirm that these instructions work for 14.04. Everything works out of the box, even wifi (though it took a minute to kick in on the live usb.) Still need the outb and i915 commands, as far as I can tell.

The only issue I've had is the keyboard not working when resuming. This only happens if your laptop suspends from low batt. Clicking the 'A' icon in the top right of the screen seems to get it working again. Deliberate resumes don't have this issue.

---

### Post by mpb2 on 2014-03-15
Hey there! I am completely new to that forum and might have a slightly different background. I own a MacBook Pro 8,2 with AMD Radeon GPU that is completely dead (google "MacBook Pro 2011 AMD GPU failure" for further information). I tried deleting the AMD *.kext files shown within "kextstat" what leaded to a MacBook Pro that now boots (first success) but has no real video output as it uses a fallback driver integrated into the OS without QuarzExtreme (QE) support. This is not understandable as the integrated Intel Graphics Unit (IGU) should be able to manage QE as well. I somehow gave up getting my MBP to work again until I saw your tutorial on installing Linux on it. I partly managed to get Linux to run with the IGU (yeah!) with the aid of my MacPro6,1 and to ignore my dead Radeon GPU. This is absolutely great in my opinion.

Is there a possibility to do the same with refind in order to boot OS X WITHOUT dedicated Radeon chip as well? If yes, you would be my personal hero ;-)

Thanks in advance!

Mpb

---

### Post by hillsidecres on 2014-03-19
> **mpb2 said:**
> Hey there! I am completely new to that forum and might have a slightly different background. I own a MacBook Pro 8,2 with AMD Radeon GPU that is completely dead (google "MacBook Pro 2011 AMD GPU failure" for further information). I tried deleting the AMD *.kext files shown within "kextstat" what leaded to a MacBook Pro that now boots (first success) but has no real video output as it uses a fallback driver integrated into the OS without QuarzExtreme (QE) support. This is not understandable as the integrated Intel Graphics Unit (IGU) should be able to manage QE as well. I somehow gave up getting my MBP to work again until I saw your tutorial on installing Linux on it. I partly managed to get Linux to run with the IGU (yeah!) with the aid of my MacPro6,1 and to ignore my dead Radeon GPU. This is absolutely great in my opinion.

Is there a possibility to do the same with refind in order to boot OS X WITHOUT dedicated Radeon chip as well? If yes, you would be my personal hero ;-)

Thanks in advance!

Mpb

If you read the first post, refind loads your grub file which will handle switching the GPU. There are steps in the OP to config your grub to always boot the Integrated chip. (ie. outb 0x710 1, and those i915. kernel params.)

---

### Post by whatsamac on 2014-05-12
Just a quick update: update to 14.04 runs good, I accepted overwriting all modified configuration files by packet maintainer's version but I needed to re-apply the grub "outb" lines as described in the initial post. I also found out that when loading via EFIStub, the kernel does NOT automatically enable the radeon power saving feature, contrary to all announcements that it is automatically enabled with kernel 3.13+. In any case, the fans were spinning like crazy and I had high temperature on the notebook even without load. When selecting the EFIStub entry with rEFInd, you can edit the options from within rEFInd and add "radeon.dpm=1" to the end of the kernel line. This works wonders for me. I yet have to find out how to make that a permanent change but it works for me for the time being since I don't really reboot often anyway (standby works like charm).

---

### Post by alan26 on 2014-05-13
Would this work also on a later generation Air?

---

### Post by tcstone on 2014-05-26
Hello! Thanks for your very helpful post, whatsamac! I also have a Macbook Pro 8,2 and your post helped me use the Intel HD3000 graphics instead of the discrete card which is better for me.

My installation is Mint 17 (in RC status at the moment) instead of Ubuntu and I found that 10_Linux would get overwritten and remove my edits! My solution was to create a new file I called 09_Macbook to hold the outb instructions. 

So, in /etc/grub.d/ I created my file 09_Macbook as follows:

```

#! /bin/sh
set -e

echo "Turning off MBP Discrete Graphics"
cat << EOF
outb 0x728 1
outb 0x710 2
outb 0x740 2
outb 0x750 0
EOF
```

The file must be made executable, sudo chmod +x 09_Macbook.

This seems to have worked and MAY have the advantage of surviving updates better.

---

### Post by dm-np01 on 2014-06-21
Installing Ubuntu 14.04 I found that I could get the display to work by simply changing the "quiet splash" line to:
[FONT=courier new]   GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash nomodeset"[/FONT]
[FONT=arial]
And this removed the need for all the outb lines and the i915 options

Neither way results in my external monitor being detected though... :( 
[/FONT][FONT=arial]
[/FONT]

---

### Post by whatsamac on 2014-07-11
By doing "nomodeset" you disable kernel modesetting. If I am not mistaken, the Radeon GPU requires kernel modesetting to work, so you basically turn off the radeon GPU. The intel integrated GPU is not capable of addressing the displayport, so that is likely why your external monitor does not work.  If you however follow my tutorial, you'll be able to boot Linux from via EFIStub, not Grub, which works with both GPUs (intel integrated and radeon) activated, and if you add "radeon.dpm=1" to the end of the boot line (F2 to edit) (NOT in Grub!), then the dynamic power management for the radeon GPU is activated so it only gets hot when actually used.

---

### Post by whatsamac on 2014-09-04
I have now migrated my MacBook to Arch Linux, which went surprisingly well with the current kernel. I therefore won't be able to monitor this thread anymore. Future versions of Ubuntu should, due to newer kernels that support AMD GPU and intel integrated chipset, pretty much work out of the box anyway!  Good luck and have fun!

---

### Post by radoslaw-ejsmont on 2015-02-11
Hi,

Have you (or anyone else) managed to get fglrx drivers to work? I am missing some eyecandy in games when using radeon driver.


Thanks in advance!

---

### Post by Liknus on 2015-04-01
> **whatsamac said:**
> By doing "nomodeset" you disable kernel modesetting. If I am not mistaken, the Radeon GPU requires kernel modesetting to work, so you basically turn off the radeon GPU. The intel integrated GPU is not capable of addressing the displayport, so that is likely why your external monitor does not work.  If you however follow my tutorial, you'll be able to boot Linux from via EFIStub, not Grub, which works with both GPUs (intel integrated and radeon) activated, and if you add "radeon.dpm=1" to the end of the boot line (F2 to edit) (NOT in Grub!), then the dynamic power management for the radeon GPU is activated so it only gets hot when actually used.

Hi! 
May I ask you if, by using those GRUB option modifications you pointed out in the first post, it will be possible to install Ubuntu in a clean new SSD, without install neither OSX nor Refind?
So that the boot process would be: Apple Firmware -> EFIStub -> Ubuntu?

Thanks for this awesome forum, and to the moderators that allowed me to post here ;)
Bye
L.
;)

---

