---
title: "Macbook pro 9,1"
date: 2013-10-23
forum: Apple Hardware Users
---

### Post by Yol4o on 2013-10-23
HI to all.
I have a macbook pro 9,1 (my job machine) with kubuntu 12.10 installed in.
I want upgrade this to 13.10 or make a new installation, but if I try live distribution i don't see external screen.
My question is: if I setup kubuntu 13.10 on my machine in EFI mode or not can I see extern monitor.

My external monitory is connected with display port to VGA.

Thanks for help!

---

### Post by Yol4o on 2013-10-26
Ok, I answer myself!
For install kubuntu 13.10 with esternal screen that work, than with displayport to VGA do:

1) Use rEFInd ( [http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html) )

2) Normal installation and select "device for boot loader installation" how the partition where you decide of install it! 

2.5) If the installation end with error with "not install grub-efi-amd64... there is not a loader ecc... ecc..." don't worry, if you set rEFInd for scan for linux drive (for this read all "Installing rEFInd Using install.sh under Linux or Mac OS X" at [http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html))

3) For see external monitor and use NVIDIA driver do:

3.1) If you have had error "grub-efi-amd64" resolve dependence remove grub-pc or run "sudo aptitude" (sudo apt-get install aptitude) to see for what depends on the error and fix it

3.2) Converting Ubuntu into EFI mode ( [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode) )

3.2.1) sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
3.2.2) sudo apt-get install -y boot-repair && boot-repair

3.2.3) Click on &#8220;Advanced options&#8221;, go to the &#8220;GRUB location&#8221; tab.
3.2.4) Make sure that &#8220;Separate /boot/efi partition&#8221; is checked, then click the &#8220;Apply&#8221; button, and follow the directions (you&#8217;ll be asked to remove and reinstall GRUB)
3.2.5) Reboot. You&#8217;ll probably haedit /etc/default/grub and add &#8220;i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0&#8243;  to GRUB_CMDLINE_LINUX_DEFAULT inside the double-quotes between the words &#8220;quiet splash&#8220;. ve several new options in rEFIt, select any of them to boot up

4) Install Nvidia Driver (that help to see external screen! :) )
4.1) sudo apt-get install linux-headers-`uname -r`
4.2) sudo apt-get install nvidia-current
4.3) sudo nvidia-xconfig
4.4) edit /etc/X11/xorg.conf and add to the Device section: Option "UseDPLib" "off"
4.5) edit /etc/default/grub and add "i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0"  to GRUB_CMDLINE_LINUX_DEFAULT inside the double-quotes between the words &#8220;quiet splash&#8220;, the result is:

GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0 splash"

4.6) sudo update-grub


This is all!

Thanks to and sources of information:

*) [http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/](http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/)
*) [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)

Sorry for my English

---

