---
title: "Macbook 8,2 What I did to get hybrid graphics working."
date: 2013-01-11
forum: Apple Hardware Users
---

### Post by Chav on 2013-01-11
This is going to be a very high level guide.

1. Get EFI boot going using the following guides.
[http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)
[http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011](http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011)

2. Get your kernel source of choice. I've tested this on the latest Quantal kernel, 3.7, and 3.8-rc1, and 3.8-rc3. 

3. Apply the radeon-load-bios patch that you can find in the guides above. 

4. The dentifrice.poivron.org guide explains how to grab your vbios.bin. Copy it to /lib/firmware/radeon/vbios.bin

5. (This is key) Compile the kernel with the following options.
CONFIG_DRM=Y
CONFIG_DRM_I915-Y

DRM_RADEON=m

# This was the hardest one for me to figure out. 
# Without this the system will boot to a blank screen after 
# splash

# CONFIG_FB_EFI is not set

# These options allow your kernel to load the radeon bios before 
# the filesystem is mounted. Otherwise you will have to delay 
# loading the radeon module.
CONFIG_FW_LOADER=y
CONFIG_FIRMWARE_IN_KERNEL=y
CONFIG_EXTRA_FIRMWARE="radeon/vbios.bin"
CONFIG_EXTRA_FIRMWARE_DIR="/lib/firmware/"

6. Edit your grub.cfg to look like the following:

 menuentry 'Ubuntu GNU/Linux, with Linux 3.8.0 rc3' {
    insmod gzio
    insmod part_gpt
    insmod ext2
    set gfxpayload=keep
    outb 0x728 1
    outb 0x710 2
    outb 0x740 2
    set root='(hd0,gpt5)'
    echo    'Loading Ubuntu, with Linux 3.8.0 rc3'
    search --no-floppy --fs-uuid --set=root dbebd209-a59f-4cdf-b8f8-260a37655072
    linux       /boot/vmlinuz-3.8.0-rc3-noefifb+ root=UUID=dbebd209-a59f-4cdf-b8f8-260a37655072 ro quiet splash i915.lvds_use_ssc=0 
    initrd      /boot/initrd.img-3.8.0-rc3-noefifb+
}

7. Get suspend working properly. After resuming from suspend with the IGD card active the system would freeze when powering on the discrete card. The solution was to do step 5 in the following guide.
[http://blog.lazut.in/2012/06/vgaswitcheroo-conquered.html](http://blog.lazut.in/2012/06/vgaswitcheroo-conquered.html)

After booting up with this kernel you should be able to use vgaswitcheroo. 

I've made this 'guide' really high level on purpose. I expect that the people that take this on are comfortable compiling their own kernel.

Hope this helps!

---

### Post by proycon on 2013-03-17
Thanks for the instructions, as well as your more elaborate replies in [http://ubuntuforums.org/showthread.php?t=2115317](http://ubuntuforums.org/showthread.php?t=2115317).  I now finally managed to get it switcheroo working as well.

---

### Post by pail on 2013-03-21
Thanks for your post.  I'm new to Linux and this is the first one I've read that's given me hope.  I've got a MBP 9,1, so the only important differences between mine and yours, I think, is Intel 4000 vs Intel 3000 and nvidia rather than radeon.  What I've done is to follow y'all exactly but leave out the radeon-specific bits.  I've been through this guide and SilverOne's post ([http://ubuntuforums.org/showthread.php?t=2115317](http://ubuntuforums.org/showthread.php?t=2115317)), as well as the associated links and so much more, but am still missing that secret sauce.  I can switch to IGD just fine, but it just gives me a blank display.  I can switch back with echo DIS > switch, I just have to do so with a blank screen.  When I echo IGD > switch, it tells me that it's switched nouveau off but never mentions switching i915 on.  With the custom kernel, it's telling me during boot 
i915: invalid ROM contents, and dmesg also chimes in with a bit about failing to find VBIOS tables.

I'm booting into EFI, have got

[COLOR=#000000]CONFIG_DRM=Y[/COLOR]
[COLOR=#000000]CONFIG_DRM_I915=Y

but

[/COLOR][COLOR=#000000]#CONFIG_FB_EFI is not set

gives me a kernel hang or somesuch.  With
[/COLOR]		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
                set gfxpayload=keep
                outb 0x728 1
                outb 0x710 2
                outb 0x740 2
		set root='hd0,gpt5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  d55824de-f45d-46b3-ad9f-73a8e82198a7
		else
		  search --no-floppy --fs-uuid --set=root d55824de-f45d-46b3-ad9f-73a8e82198a7
		fi
		echo	'Loading Linux 3.9.0-rc3-gmuxyes-fbefiyes ...'
		linux	/boot/vmlinuz-3.9.0-rc3-gmuxyes-fbefiyes root=UUID=d55824de-f45d-46b3-ad9f-73a8e82198a7 ro   quiet splash i915.lvds_use_ssc=0

I boot to blackness, then the backlight comes on, then a brief flash at what I assume should be lightdm starting up.  I've tried other kernel parameters, such as i915.modeset=1 and the i915.lvds_channel=2 one, though largely without knowing what they do and without effect.

This has become much longer than I expected, sorry if I should have made it a new post.  What I'm hoping is that you (or anyone) might have a guess as to why I'm failing, or what I should try next.  Thanks much.

---

