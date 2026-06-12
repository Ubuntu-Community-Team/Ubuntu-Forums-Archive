---
title: "Ubuntu 12.04 LTS on Macbook 5,1 late 2008?"
date: 2012-05-10
forum: Apple Hardware Users
---

### Post by 9646gt on 2012-05-10
Sorry my first post has to be asking for help right off the bat! I recently installed 12.04 LTS on my old laptop and like it so well that I plan to dual boot it with mac os on my macbook. The last distro I dual booted on this machine was I think Linux Mint 10 and had some issues. But I am wanting to try again with normal Ubuntu running Unity. 
 
I searched but have really found nothing. I am curious about the compatibility of my macbook 5,1 (not a macbook pro) late 2008 unibody with Ubuntu 12.04 LTS. What things can I expect to have to fix from the get go to get them working? Below is a link to the Apple specs for my laptop. It's the 2.4ghz version and currently has 8gb of ram (apple states only 4gb is supported but this is not true). The specs doesn't tell me what brand the networking and other components are. I should also say I am planning to run the 64bit version to make use of all 8gb of ram. Which ISO do I need to download? Thanks for any help!

---

### Post by Vorktanamo Bay on 2012-05-12
I also am considering installing Ubuntu 12.04 on my late 2008 macbook aluminum. I haven't found anything as far as compatibility is concerned. I tried it when 12.04 first came out and couldn't get the screen brightness buttons working, so I switched back to Lion.

I saw that 10.04.4 is compatible, with manual configuration. So I am considering loading that on until 12.04 is fixed for the macbook. 

Another thing that is keeping me on Lion for the moment is the trackpad in Unbuntu. On 12.04 the trackpad didn't "feel" right to me if that makes any sense.

---

### Post by Vorktanamo Bay on 2012-05-14
Ok so I gave 12.04 another go in my macbook 5,1 and I got most everything working.

Touchpad works out of the box.



MACTEL
I added the Mactel repository and installed the macfanctld package. In the software center you can choose the mactel repository after you add it and see what is installed. It also shows that the mactel synaptics drive is installed but I don't remember installing it.

To add mactel ppa type the following into terminal;
```
sudo add-apt-repository ppa:mactel-support/ppa
sudo apt-get update
```



BACKLIGHT CONTROLS
After installing the current nvidia drivers I regained the ability to sleep the computer but lost backlight controls. To fix this you must edit the xorg.conf as follows:
type the following into your terminal;
```
sudo gedit /etc/X11/xorg.conf
```

replace your xorg.conf with this;
```
Section "Device"
    Identifier     "NVIDIA GeForce"
    Driver         "nvidia"
    Option         "NoLogo" "True"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

Reboot and you will have backlight control back.


LAPTOP-MODE-TOOLS
I also installed laptop-mode-tools.
Type the following into terminal;
```
sudo apt-get install laptop-mode-tools
```

I hope this helps.

---

### Post by manang on 2012-05-14
I've a problem with secondo monitor on this macbook.
I've a display port with VGA adapter, but my pc desn't detect nothing.

---

### Post by Vorktanamo Bay on 2012-05-14
Not sure about the secondary monitor, I havn't tried that yet.

Something else that I forgot to add is reverse scrolling. To add lion like scrolling run this in the terminal:

```
xinput set-button-map "bcm5974" 1 2 3 5 4 7 6 8 9 10 11 12 13 14 15 16
```

to make it work after reboot add the previous command to startup applications

---

### Post by manang on 2012-05-14
nothing, with nvidia drivers and configuration of xorg as above, i haven't the control of backlight.

---

### Post by Vorktanamo Bay on 2012-05-14
manang are you dual booting ubuntu or is ubuntu the only OS on your mac. I have Ubuntu as the only OS. Before I installed Ubuntu I created a new msdos partition map with gparted on the live cd. This will delete the entire hard drive, so be sure to backup all your stuff. That may be the reason why I have backlight control and you don't but I am not sure.

---

### Post by manang on 2012-05-14
i've ubuntu and mac os x lion.
are there problems with grub parameters?
could you write your grub parameters?
thanks

---

### Post by manang on 2012-05-14
how i can reset the xinput command?

---

### Post by Vorktanamo Bay on 2012-05-14
manang, for xinput just put all the numbers in the correct order, 4 5 are swapped and 6 7 are swapped which swaps vertical and horizontal scrolling.

also you may want to run this in terminal;

```
xinput list
```

which for me outputs the following;

 ```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; bcm5974                                 	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Apple, Inc. Apple Internal Keyboard / Trackpad	id=9	[slave  keyboard (3)]
    &#8627; Built-in iSight                         	id=11	[slave  keyboard (3)]
```

From the above code you can see that my pointing device is bcm5974 


GRUB
I suck at grub but will send you my grub config as soon as I figure it out.

From what I have read on the net, EFI booting causes you to loose backlight control. I believe that I am using BIOS emulation booting.

---

### Post by Vorktanamo Bay on 2012-05-14
here is my grub.cfg

terminal command to see file
```
cat /boot/grub/grub.cfg
```


the grub.cfg file contents
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root af31d12c-9744-44bd-a7ef-a6ea1cf12f10
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root af31d12c-9744-44bd-a7ef-a6ea1cf12f10
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root af31d12c-9744-44bd-a7ef-a6ea1cf12f10
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=af31d12c-9744-44bd-a7ef-a6ea1cf12f10 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root af31d12c-9744-44bd-a7ef-a6ea1cf12f10
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=af31d12c-9744-44bd-a7ef-a6ea1cf12f10 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root af31d12c-9744-44bd-a7ef-a6ea1cf12f10
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=af31d12c-9744-44bd-a7ef-a6ea1cf12f10 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root af31d12c-9744-44bd-a7ef-a6ea1cf12f10
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=af31d12c-9744-44bd-a7ef-a6ea1cf12f10 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root af31d12c-9744-44bd-a7ef-a6ea1cf12f10
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root af31d12c-9744-44bd-a7ef-a6ea1cf12f10
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by manang on 2012-05-14
write the file
/etc/default/grub

---

### Post by Vorktanamo Bay on 2012-05-14
Here my /etc/default/grub file


```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by manang on 2012-05-14
nothin...it's the same...
mmm very strange:)

[http://goo.gl/J5dTm](http://goo.gl/J5dTm)
I See this guide, but 3 days ago i had a backlight control.
but after i have installed lightum, to control the light with the sensor of my macbook.
and after...nothing...i saw the bar, but the control was off.

---

### Post by manang on 2012-05-14
i don't know!

---

### Post by Vorktanamo Bay on 2012-05-14
Attached is a screenshot of my partition layout in gparted.

---

### Post by manang on 2012-05-14
yes, ok, i can't erase my mac os x partition...

---

### Post by 9646gt on 2012-05-14
Got it working here as well :) Working out a wirelessissue right now then should be good to go. Have yet to mess with keyboard backlight settings and such but my screen brightness works fine with nvidia drivers after enabling it in the xorg.conf.

---

### Post by 9646gt on 2012-05-14
> **Vorktanamo Bay said:**
> Ok so I gave 12.04 another go in my macbook 5,1 and I got most everything working.
 
Touchpad works out of the box.
 
 
 
MACTEL
I added the Mactel repository and installed the macfanctld package. In the software center you can choose the mactel repository after you add it and see what is installed. It also shows that the mactel synaptics drive is installed but I don't remember installing it.
 
To add mactel ppa type the following into terminal;
```
sudo add-apt-repository ppa:mactel-support/ppa
sudo apt-get update
```
 
 
 
BACKLIGHT CONTROLS
After installing the current nvidia drivers I regained the ability to sleep the computer but lost backlight controls. To fix this you must edit the xorg.conf as follows:
type the following into your terminal;
```
sudo gedit /etc/X11/xorg.conf
```
 
replace your xorg.conf with this;
```
Section "Device"
    Identifier     "NVIDIA GeForce"
    Driver         "nvidia"
    Option         "NoLogo" "True"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```
 
Reboot and you will have backlight control back.
 
 
LAPTOP-MODE-TOOLS
I also installed laptop-mode-tools.
Type the following into terminal;
```
sudo apt-get install laptop-mode-tools
```
 
I hope this helps.
 
What exactly does the laptop mode tools do? Also a bigger question, do we even need the macfan utility anymore? It seems mine is functioning fine without it.

---

### Post by manang on 2012-05-14
9646gt do you have only ubuntu on macbook?
or lion, too?
thanks

---

### Post by 9646gt on 2012-05-15
I have 10.8 developer preview and Ubuntu.

---

### Post by manang on 2012-05-15
ok, so i had installed mac os x, after ubuntu.
what version of drivers do you have?
And do you have a macbook 5.1?
thanks
(sorry, but i want to adjust my problem)

---

### Post by duracella on 2012-05-25
Hi, I'm getting really frustrated now, I have added thread in both beginners talk and Apple Users Categories.... 
[http://ubuntuforums.org/showthread.php?t=1986038](http://ubuntuforums.org/showthread.php?t=1986038)
but no answers, then I came over this thread..

It's the right click function on trackpad and webcam in cheesy that is not working...
Is that working for anyone?
And if so... did it just work out of the box for you? Or what did you do to make the problem go away? 

Thanks in Advance!
-André

---

### Post by manang on 2012-05-25
Yes, my cam works.
right click.. do you speak about physics click?
because I use double "tap" on the trackpad to do right click.

---

### Post by duracella on 2012-05-29
Yeah, physics click... so click the right side of the trackpad got no function in ubuntu on macbooks?

Hmm, weird... cheesy does not detect any source on my mom's macbook 5.1...

---

### Post by AntonOlsen on 2012-06-01
> **duracella said:**
> Yeah, physics click... so click the right side of the trackpad got no function in ubuntu on macbook?

I think it depends on the macbook version. Clicking with two fingers is a right-click on my Macbook5,1.

---

### Post by duracella on 2012-06-05
Yeah, I figured that two finger click on the trackpad surface works as right click.

For me that is a working solution, but my mother is a different story, she wants to get right click by clicking on down-right corner, like she had on OSx.. 

Is there any way to configure this?

Oh, btw... Web-camera in Cheesy suddenly recognize the web-cam source. As well does Skype.

---

### Post by kohoutek1 on 2012-06-17
I just got 12.04 dual booting on my Macbook 5.1., today. The trackpad is a mess. Without proper trackpad function, you have rudimentary, or no, window management. As I type this, I am struggling to even tap out a sentence. The trackpad interferes even with basic typing. IT IS THAT BAD!

My first try at Linux on this computer was LMDE. I had not been able to get the Macbook to even mount the Ubuntu DVD, so I'd hoped to get LMDE going. 

LMDE installed from burned DVD fine, but the trackpad problems rendered it unusable. After three hours of working through forums, howtos, and shell commands for git, svn, and whatever, I decided to see if, on the off chance, Ubuntu DVD would boot with "C" pressed on restart from LMDE. It did... some ray of hope.

I tested Ubuntu Live first. The trackpad behaved very well. So, I went ahead and installed.

After installation, it continued to work... 

For about 10 minutes...

Then, the software updates started. 270 of them. 

Then restart...

And now, trackpad is bonkers again. And me? Serious issues with my cerebral tissues, as well.

Any number of those updates could be the culprit. There was an xorg update. A kernel update. U name it...

So, here's what I've got:

(1) Single tap = secondary click context menu

(2) Full press of bottom corner, right or left = primary click

(3) No functioning scroll = attempt to scroll brings up secondary click context menu instead, though it's hit and miss, IF both fingers just HAPPEN to touch the pad at the same time.

(4) I installed gpointer-settings. That does not contain settings that will change the first three.

(5) I'm gonna gamble a bit that KDE may have better support for settings. Installing kde-full now.

---

### Post by kohoutek1 on 2012-06-17
Got KDE 4.8 working out with trackpad fully functional. All necessary settings are there.

Glad to be back on KDE too.

---

### Post by Bergschreck on 2012-06-22
> **Vorktanamo Bay said:**
> mFrom what I have read on the net, EFI booting causes you to loose backlight control. I believe that I am using BIOS emulation booting.
What is "BIOS emulation booting" and how can I control that? I'm using Refit for booting.

---

### Post by markthekdeguy on 2012-06-23
I just installed Kubuntu 12.04 Mac iso, 3 times, and everytime it comes time to reboot, i select Linux in Refit and the screem blacks out and reboots, been trying this for days.
i might try the normal .iso
refit says discs dot need synching,
uing Lion on Macbook Pro 5,1
i'm struggling with this one..

---

