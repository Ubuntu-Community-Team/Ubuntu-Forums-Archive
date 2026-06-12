---
title: "Installation crashes on the new early 2009 White Macbooks"
date: 2009-03-05
forum: Apple Hardware Users
---

### Post by sistoviejo on 2009-03-05
When you try to boot the live CD, it crashes right after you select the option "Try ubuntu without changing your computer".
To avoid the crash instead of selecting that option, press F6 twice and mark the option "acpi=off". Then Press ESC and Enter to boot.

---

### Post by cyberdork33 on 2009-03-05
> **sistoviejo said:**
> When you try to boot the live CD, it crashes right after you select the option "Try ubuntu without changing your computer".
To avoid the crash instead of selecting that option, press F6 twice and mark the option "acpi=off". Then Press ESC and Enter to boot.
can you get the hardware version ID from your machine as indicated here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Determine%20your%20model%20and%20hardware%20revision](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Determine%20your%20model%20and%20hardware%20revision)

---

### Post by bazzwaa on 2009-03-05
I had the same issue, I corrected it by re-installing mac os(I had successfully copied ubuntu image onto drive).  I ran the firmware updates, then I used boot camp and reefit and got no errors with a freshly downloaded and burned copy of ubuntu(incase there was some sort of update that helped, this step may be completely unnecessary, but it seemed to help.)


no longer does my ubuntu boot cd crash upon loading.  The problem I believe is actually corrected under the efi update.

anyways, hope this helps you.

I have a macbook pro 5,1 aluminum uni-body.

---

### Post by sistoviejo on 2009-03-05
> **cyberdork33 said:**
> can you get the hardware version ID from your machine as indicated here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Determine%20your%20model%20and%20hardware%20revision](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Determine%20your%20model%20and%20hardware%20revision)

I get this: MacBook5,2
As I mentioned in the title, it's an early 2009 White MacBook.

A few other issues I had:
- Apparently sound doesn't work out of the box.
- When you try to shutdown it down, the computer stays On with a blank screen.

---

### Post by cyberdork33 on 2009-03-05
> **sistoviejo said:**
> As I mentioned in the title, it's an early 2009 White MacBook.that doesn't necessarily mean anything... the version number does...

> **sistoviejo said:**
> A few other issues I had:
- Apparently sound doesn't work out of the box.
- When you try to shutdown it down, the computer stays On with a blank screen.
These both sound similar to the MacBook5,1. I would check out that documentation.

---

### Post by josephdaniel on 2009-03-07
I have exactly the same problem with the macbook white. It's the one with the following specs:
Core2duo 2Ghz 3MB cache FSB 1066Mhz
2GB ram
nVidia 9400M

Hardware Version output:
hw.model: MacBook5,2

I tried the procedure listed in the original post but it doesn't work on my macbook. 

I tried ubuntu 8.10 amd64 and i386 cds and it always failed to boot neither with acpi=off


I hope I can get ubuntu running on my macbook. 

Thanks for your help.

Joseph

---

### Post by sistoviejo on 2009-03-07
> **josephdaniel said:**
> I have exactly the same problem with the macbook white. It's the one with the following specs:
Core2duo 2Ghz 3MB cache FSB 1066Mhz
2GB ram
nVidia 9400M

Hardware Version output:
hw.model: MacBook5,2

I tried the procedure listed in the original post but it doesn't work on my macbook. 

I tried ubuntu 8.10 amd64 and i386 cds and it always failed to boot neither with acpi=off


I hope I can get ubuntu running on my macbook. 

Thanks for your help.

Joseph

I was trying to write that on the boot line but it didn't work for me.
Afterwards I tried pressing F6 twice and a little menu popped up.
There I was able to tick the "acpi=off" option.

---

### Post by josephdaniel on 2009-03-08
well I tried selecting acpi=off from the menu and I finally was able to boot the live cd. As expected the live cd ran painfully slow so I restarted into OS X, resized the OS X partition and created an empty partition for ubuntu.

I installed rEFIt, sync'ed the parition table and installed ubuntu 8.10 x64. The installation finished with no problems, grub was installed on linux partition. After restarting, I could no longer boot mac os x or ubuntu. OSX would show the prohibited sign and never actually boot up and ubuntu would hang on the grub list (I have windows xp installed). 

After some fiddling, I reset the NVRAM using the method instructed on apple's website so OS X worked once again but ubuntu still hangs at the same step.

I don't know what exactly is going wrong. If someone has successfully got ubuntu running on this machine please tell me.

I've had ubuntu on my old machine and I thought a macbook is going to work well with it. I never could imaging that macbook 5,2 would be so much different from 5,1 (ubuntu was reported to work fine with 5,1).

Any advice will be appreciated. 
Thanks

---

### Post by sistoviejo on 2009-03-08
> **josephdaniel said:**
> well I tried selecting acpi=off from the menu and I finally was able to boot the live cd. ...

As posted before I have the same laptop and was able to get Ubuntu, mac os and windows triple boot working. I had many issues though. Apparently you're only supposed to partition the hard drive once before you install MACOS using it's Disk Utility. Any move/resize/delete or creation of partitions later will bring problems.

I used these tutorials:
1 - [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)
2 - [http://tripleboot.is2.byuh.edu/](http://tripleboot.is2.byuh.edu/)

I tried many times following the instructions but had problems... I think only on my 7th or 8th try could it get all the OSs working. In the end I decided to read the instructions from top to bottom and found some tips that made the task possible.

---

### Post by cyberdork33 on 2009-03-08
> **josephdaniel said:**
> well I tried selecting acpi=off from the menu and I finally was able to boot the live cd. As expected the live cd ran painfully slow so I restarted into OS X, resized the OS X partition and created an empty partition for ubuntu.

I installed rEFIt, sync'ed the parition table and installed ubuntu 8.10 x64. The installation finished with no problems, grub was installed on linux partition. After restarting, I could no longer boot mac os x or ubuntu. OSX would show the prohibited sign and never actually boot up and ubuntu would hang on the grub list (I have windows xp installed). 

After some fiddling, I reset the NVRAM using the method instructed on apple's website so OS X worked once again but ubuntu still hangs at the same step.

I don't know what exactly is going wrong. If someone has successfully got ubuntu running on this machine please tell me.

I've had ubuntu on my old machine and I thought a macbook is going to work well with it. I never could imaging that macbook 5,2 would be so much different from 5,1 (ubuntu was reported to work fine with 5,1).

Any advice will be appreciated. 
Thanks
you need to sync the partitions AFTER installing Ubuntu. You should create a rEFIt cd or USB drive.
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by sistoviejo on 2009-03-08
> **cyberdork33 said:**
> 
These both sound similar to the MacBook5,1. I would check out that documentation.

Thank you! 
I followed all the steps in this guide: [https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)
I was able to fix the sound, keyboard multimedia keys and enable some temperature and fan sensors.

What still doesn't work:
- Adjust screen brightness.
- Show battery status. I tried resetting the SMC controller btw. Apparently Ubuntu thinks there is no battery present.
- When I try to shut down or reboot, it stays On with a blank screen. 

I am still booting with the acpi=off line, otherwise it won't boot.

UPDATE: Apparently the shut down and reboot issue is fixed by installing version 180 of the Nvidia graphics drivers. Will try later.

---

### Post by cyberdork33 on 2009-03-09
> **sistoviejo said:**
> Thank you! 
I followed all the steps in this guide: [https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)
I was able to fix the sound, keyboard multimedia keys and enable some temperature and fan sensors.

What still doesn't work:
- Adjust screen brightness.
- Show battery status. I tried resetting the SMC controller btw. Apparently Ubuntu thinks there is no battery present.
- When I try to shut down or reboot, it stays On with a blank screen. 

I am still booting with the acpi=off line, otherwise it won't boot.

UPDATE: Apparently the shut down and reboot issue is fixed by installing version 180 of the Nvidia graphics drivers. Will try later.
The battery issue may be due to the fact that you boot with acpi=off. This is something that you should not be required to do. There should be a bug. Unfortunately, I don't think it will make it into Jaunty as I am pretty sure that the kernel will need patched.

---

### Post by sistoviejo on 2009-03-09
> **cyberdork33 said:**
> The battery issue may be due to the fact that you boot with acpi=off. This is something that you should not be required to do. There should be a bug. Unfortunately, I don't think it will make it into Jaunty as I am pretty sure that the kernel will need patched.

Should I file it on launchpad?

---

### Post by cyberdork33 on 2009-03-09
> **sistoviejo said:**
> Should I file it on launchpad?
you could file it upstream with the Linux kernel as an issue, but It can be tracked in the Ubuntu bugtracker as well (launchpad)

---

### Post by sistoviejo on 2009-03-11
> **cyberdork33 said:**
> you could file it upstream with the Linux kernel as an issue, but It can be tracked in the Ubuntu bugtracker as well (launchpad)

Thanks for all your help and support.
Bug reported 
[https://launchpad.net/ubuntu/+bug/341230](https://launchpad.net/ubuntu/+bug/341230)

---

### Post by sturuko on 2009-03-11
hi,
very nice thread.
i also have a macbook white 5,2 - early 2009 - and i have the same issues.

i got sound working for a while following instructions for 5,1 macbooks on the ubuntu wiki.

i also think that ubuntu does not see properly my cpu: i cannot see two cores in /proc/cpuinfo or in gnome-system-monitor... can u verify on your system please?

thanks

---

### Post by sistoviejo on 2009-03-11
> **sturuko said:**
> i also think that ubuntu does not see properly my cpu: i cannot see two cores in /proc/cpuinfo or in gnome-system-monitor... can u verify on your system please?

Mine also shows only one. This is very strange. :|

---

### Post by cyberdork33 on 2009-03-12
> **sistoviejo said:**
> Mine also shows only one. This is very strange. :|
that might also be due to disabling acpi.

---

### Post by sistoviejo on 2009-03-12
> **bazzwaa said:**
> I had the same issue, I corrected it by re-installing mac os(I had successfully copied ubuntu image onto drive).  I ran the firmware updates, then I used boot camp and reefit and got no errors with a freshly downloaded and burned copy of ubuntu(incase there was some sort of update that helped, this step may be completely unnecessary, but it seemed to help.)


no longer does my ubuntu boot cd crash upon loading.  The problem I believe is actually corrected under the efi update.

anyways, hope this helps you.

I have a macbook pro 5,1 aluminum uni-body.

Sorry, I didn't see your message before.
Just wanted to say that I updated my firmware last week, so that might not be the issue.

---

### Post by sturuko on 2009-03-13
other issuses:
-grub&lilo does not work
-grub-pc (v. 1.95, from intrepid or from jaunty debs) freezes if i try to change the boot kernel in the grub boot menù or if i hit any button on the keyboard
-instead, it works fine with the svn-compiled version

can someone confirm these things?

---

### Post by cyberdork33 on 2009-03-13
> **sturuko said:**
> other issuses:
-grub&lilo does not work
-grub-pc (v. 1.95, from intrepid or from jaunty debs) freezes if i try to change the boot kernel in the grub boot menù or if i hit any button on the keyboard
-instead, it works fine with the svn-compiled version

can someone confirm these things?
the grub2 sources were just heavily patched for Macs recently. The svn version has these fixes now. You would probably have the same problems on other Macs with v1.95

See:
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

### Post by sturuko on 2009-03-13
ACPI now works for me on my macbook 5.2!!!
-i see battery charge, ac adapter, etc..
-i see 2 cores for my cpu :)
-i can change cpu freq and governor
-sound & microphone works (only 2 speakers.. :(
-i can shutdown my macbook
-i cannot reboot :(
-i can enter sleep mode... but i can't wakeup :D

[B]but i can't use nvidia drivers :( so no 3d effects and accelerated graphics.
[/B]

here how to make things work:
0.1 you have to use REFIT, or you have to bless grub.efi in [3] - but it's safer refit - download and install it from osx.
0.2 boot into ubuntu in some way and install all the needed packages to compile theese things
1a. checkout the last svn version of grub2 and compile it for the x86_64 efi platform - i followed [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook) and [http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)..... or download the attached file. the config file is for kernel version 2.6.27-11-generic, but you can change it for your kernel versions
1b. change, if you set it, in xorg.conf from nvidia to fbdev
```
Section "Device"
    Identifier     "Device0"
    Driver         "fbdev" #"nvidia"
#    VendorName     "NVIDIA Corporation"
EndSection

```
1c. add the folling line in /etc/modprobe.d/blacklist
```
blacklist agpgart

```
2. copy the compiled-or downloaded grub2_efi to an usbpen and reboot into osx
3. paste grub2_efi into /efi/
4. reboot
5. now you should see another entry in refit: grub2_efi. boot :)


1. here there is some code:
```

mkdir grub2_efi
svn co svn://svn.savannah.gnu.org/grub/trunk/grub2 grub2
cd grub2
./configure --with-platform=efi --target=i386
make
./grub-mkimage -d . -o grub.efi gpt hfsplus fat ext2 normal chain boot configfile
sudo cp grub.efi *.mod fs.lst command.lst ../grub2_efi

```

create your own grub.cfg file, or take the mine, and put it into grub2_efi:
```
menuentry "linux-2.6.27-11-generic" {
  # Set the root device for Linux.
  root=(hd0,3)
  # Load the loader. - other options: video=vesafb noefi
  linux /boot/vmlinuz-2.6.27-11-generic root=/dev/sda3 video=efifb agp=off acpi=force
  initrd /boot/initrd.img-2.6.27-11-generic
}

menuentry "MacOSX" {
  # Search the root device for Mac OS X's loader.
  search --set /usr/standalone/i386/boot.efi
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi
}

menuentry "Boot from MBR" {
  appleloader HD
}
menuentry "Boot from CD" {
  appleloader CD
}

# this does not work for me
menuentry "Boot from USB" {
  appleloader USB
}


#keymapping: remeber these keys when you boot, they can be helpful!!!
#F1 = ctrl-x
#F2 = ctrl-a
#F3 = ctrl-e
```

---

### Post by cyberdork33 on 2009-03-13
> **sturuko said:**
> **but i can't use nvidia drivers :( so no 3d effects and accelerated graphics.**
This is a known issue when booting via EFI. There is no work around... yet.

---

### Post by sistoviejo on 2009-03-23
Here's a news article that reports the quiet change introduced in the white MacBook hardware (the new one being MacBook5,2).
[http://www.engadget.com/2009/01/21/apple-quietly-updates-999-white-macbook-with-unibody-specs/](http://www.engadget.com/2009/01/21/apple-quietly-updates-999-white-macbook-with-unibody-specs/)

---

### Post by mughal on 2009-04-05
Hi,

Thanks a lot for this thread. I have been able to install ubuntu on my new Macbook 5.2. But, there are a few nuisances. There are problems with my touchpad. Two finger gestures don't work. I can't scroll or right click with two finger taps. Moreover, the palm sensitivity on the touch pad is way too high.

---

### Post by sistoviejo on 2009-04-05
Did you install the touchpad driver?
Follow this guide [1] Almost all of it works for the MacBook5,2.

[1] [https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)

---

### Post by mughal on 2009-04-08
Yes, I had followed all the instructions from that link. I had updated the repositories and installed the apple touchpad software using apt-get.

The instructions on that link says that two touch tap works out of the box, when it doesn't (5.2 vs 5.1 macbooks?).

---

### Post by sturuko on 2009-04-29
try this:
sudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.Device" type="string">/dev/psaux</merge>
       <merge key="input.x11_options.Protocol" type="string">auto-dev</merge>
       <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
       <merge key="input.x11_options.LeftEdge" type="string">100</merge>
       <merge key="input.x11_options.RightEdge" type="string">1120</merge>
       <merge key="input.x11_options.TopEdge" type="string">50</merge>
       <merge key="input.x11_options.BottomEdge" type="string">310</merge>
       <merge key="input.x11_options.FingerLow" type="string">5</merge>
       <merge key="input.x11_options.FingerHigh" type="string">20</merge>
       <merge key="input.x11_options.MaxTapTime" type="string">100</merge>
       <merge key="input.x11_options.MaxTapMove" type="string">150</merge>
       <merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
       <merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
       <merge key="input.x11_options.HorizScrollDelta" type="string">50</merge>
       <merge key="input.x11_options.MinSpeed" type="string">0.49</merge>
       <merge key="input.x11_options.MaxSpeed" type="string">0.78</merge>
       <merge key="input.x11_options.AccelFactor" type="string">0.0010</merge>
       <merge key="input.x11_options.LockedDrags" type="string">false</merge>
       <merge key="input.x11_options.TapButton1" type="string">1</merge>
       <merge key="input.x11_options.TapButton2" type="string">3</merge>
       <merge key="input.x11_options.TapButton3" type="string">2</merge>
       <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
       <merge key="input.x11_options.HorizTwoFingerScroll" type="string">false</merge>
       <merge key="input.x11_options.FastTaps" type="string">true</merge>
       <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
       <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
       <merge key="input.x11_options.SHMConfig" type="string">true</merge>

      </match>
    </match>
  </device>
</deviceinfo>

```

save and reboot

---

### Post by sistoviejo on 2009-05-02
> **sturuko said:**
> try this:
sudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi
...  This worked for me. Thank you.

On a different note, someone said you can actually have ACPI enabled if you boot with nosmp or maxcpus=1 in the boot flags.  It was posted in the kernel bug report here: [http://bugzilla.kernel.org/show_bug.cgi?id=13170](http://bugzilla.kernel.org/show_bug.cgi?id=13170)

I still can't change display brightness though. Anyone had any luck with this?

---

### Post by silverwhalle on 2009-07-21
disabling acpi is the cause that the number of core is one? 
i noticed my macbook recognize cpu to be single core today trying to figure out what causes slow playback of mkv file, 720p video.

$grep -i core /proc/cpuinfo 
model name    : Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
core id        : 0
cpu cores    : 1

even though that result say there's one core, both cores are actually working or not?
if not, what should i do to solve this? any solution?
i want 2 cores. 
with one core, of course, it plays 720p hd video. but it eats 100% cpu usage..

---

### Post by sistoviejo on 2009-07-21
> **silverwhalle said:**
> disabling acpi is the cause that the number of core is one? 
i noticed my macbook recognize cpu to be single core today trying to figure out what causes slow playback of mkv file, 720p video.

$grep -i core /proc/cpuinfo 
model name    : Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
core id        : 0
cpu cores    : 1

even though that result say there's one core, both cores are actually working or not?
if not, what should i do to solve this? any solution?
i want 2 cores. 
with one core, of course, it plays 720p hd video. but it eats 100% cpu usage..

I think it's a bug in the kernel. I don't remember if there's a solution yet.
Here's the bug report, you might be able to find some helpful information or a workaround:
[http://bugzilla.kernel.org/show_bug.cgi?id=13170](http://bugzilla.kernel.org/show_bug.cgi?id=13170)

---

### Post by kevin098765 on 2009-07-21
I have to say that I didn't suceed in installing ubuntu in the withe macbook5,2 (early 2009 model). 

The installation in the partition seems to be ok. I have done rEFIt and acpi=off I followed you manual and ubuntu's forum official webpage.

A grub problem always appears. After Sync MBR with rEFIt, it freezes in grub loading stage2 during rebooting ubuntu.

Could someone help me?

Thanks

---

### Post by sistoviejo on 2009-07-21
> **kevin098765 said:**
> I have to say that I didn't suceed in installing ubuntu in the withe macbook5,2 (early 2009 model). 

The installation in the partition seems to be ok. I have done rEFIt and acpi=off I followed you manual and ubuntu's forum official webpage.

A grub problem always appears. After Sync MBR with rEFIt, it freezes in grub loading stage2 during rebooting ubuntu.

Could someone help me?

Thanks

Installation is a nightmare. I wish I had documented the procedure which worked for me but I didn't.

I think I used this how-to:
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

BTW I think this is offtopic to the current thread so you should start a new thread if you want help with dual booting Ubuntu on a Macbook.

---

### Post by sturuko on 2009-10-17
> **sturuko said:**
> ACPI now works for me on my macbook 5.2!!!
-i see battery charge, ac adapter, etc..
-i see 2 cores for my cpu :)
-i can change cpu freq and governor
-sound & microphone works (only 2 speakers.. :(
-i can shutdown my macbook
-i cannot reboot :(
-i can enter sleep mode... but i can't wakeup :D

[B]but i can't use nvidia drivers :( so no 3d effects and accelerated graphics.
[/B]

here how to make things work:
0.1 you have to use REFIT, or you have to bless grub.efi in [3] - but it's safer refit - download and install it from osx.
0.2 boot into ubuntu in some way and install all the needed packages to compile theese things
1a. checkout the last svn version of grub2 and compile it for the x86_64 efi platform - i followed [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook) and [http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)..... or download the attached file. the config file is for kernel version 2.6.27-11-generic, but you can change it for your kernel versions
1b. change, if you set it, in xorg.conf from nvidia to fbdev
```
Section "Device"
    Identifier     "Device0"
    Driver         "fbdev" #"nvidia"
#    VendorName     "NVIDIA Corporation"
EndSection

```
1c. add the folling line in /etc/modprobe.d/blacklist
```
blacklist agpgart

```
2. copy the compiled-or downloaded grub2_efi to an usbpen and reboot into osx
3. paste grub2_efi into /efi/
4. reboot
5. now you should see another entry in refit: grub2_efi. boot :)


1. here there is some code:
```

mkdir grub2_efi
svn co svn://svn.savannah.gnu.org/grub/trunk/grub2 grub2
cd grub2
./configure --with-platform=efi --target=i386
make
./grub-mkimage -d . -o grub.efi gpt hfsplus fat ext2 normal chain boot configfile
sudo cp grub.efi *.mod fs.lst command.lst ../grub2_efi

```

create your own grub.cfg file, or take the mine, and put it into grub2_efi:
```
menuentry "linux-2.6.27-11-generic" {
  # Set the root device for Linux.
  root=(hd0,3)
  # Load the loader. - other options: video=vesafb noefi
  linux /boot/vmlinuz-2.6.27-11-generic root=/dev/sda3 video=efifb agp=off acpi=force
  initrd /boot/initrd.img-2.6.27-11-generic
}

menuentry "MacOSX" {
  # Search the root device for Mac OS X's loader.
  search --set /usr/standalone/i386/boot.efi
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi
}

menuentry "Boot from MBR" {
  appleloader HD
}
menuentry "Boot from CD" {
  appleloader CD
}

# this does not work for me
menuentry "Boot from USB" {
  appleloader USB
}


#keymapping: remeber these keys when you boot, they can be helpful!!!
#F1 = ctrl-x
#F2 = ctrl-a
#F3 = ctrl-e
```

mmm now nvidia drivers works very well for me.. it seems that point 1b and 1c are no more useful. and i can also wake up from sleep!

---

### Post by todor_fr on 2009-10-22
Hello,

Could you please tell us how you did about enable nvidia. I have tried but it did'n work. Could you post your actual grub.cfg et xorg.conf. Do you always blacklist agp?

Thank you

---

### Post by sturuko on 2009-11-03
xorg.conf
```


Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "Unknown"
	HorizSync       28.0 - 33.0
	VertRefresh     43.0 - 72.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load           "glx"
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0"
EndSection

Section "Device"
	Identifier     "Device0"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

grub.cfg is the same i posted in previous posts-except for kernel version

nvidia works fine with driver version 180 automagically installed by ubuntu Hardware Drivers. I think that with previous versions there were some problems.

agpgart is no more blacklisted

---

### Post by todor_fr on 2009-11-05
Thank you so much. I will try this. By the way, what is your version of Ubuntu 8.10 or 9.04? And one more question, do you recompile grub2 or you use the same version that you've posted here?

---

### Post by wpdster on 2010-09-23
Is anybody still monitoring this thread?  I've stumbled across it as I have the same problem: MacBook5,2, Ubuntu 10.04, grub 1.98, 32 bit version, 64 bit version... I can't seem to get anything to work to get me running with 2 cores and ACPI.

Any tips?

--wpd

---

### Post by clemare on 2010-10-11
Ubuntu 10.10 still the same problem here.

---

### Post by oohshiny on 2010-12-13
I reinstalled from 9.04 to 10.10 (32 bit) - reusing my grub 1.97 (64 bit, loaded into my OSX partition) works with this config:

```

menuentry "linux latest" {
  root=(hd0,3)
  fakebios
  linux /vmlinuz root=/dev/sda3 video=efifb agp=off acpi=force
  initrd /initrd.img
}

```

I'll try recompiling grub 1.99 per [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook) and seeing what happens.

---

### Post by ias on 2012-05-05
> **sturuko said:**
> ACPI now works for me on my macbook 5.2!!!
-i see battery charge, ac adapter, etc..
-i see 2 cores for my cpu :)
-i can change cpu freq and governor
-sound & microphone works (only 2 speakers.. :(
-i can shutdown my macbook
-i cannot reboot :(
-i can enter sleep mode... but i can't wakeup :D

[B]but i can't use nvidia drivers :( so no 3d effects and accelerated graphics.
[/B]

here how to make things work:
0.1 you have to use REFIT, or you have to bless grub.efi in [3] - but it's safer refit - download and install it from osx.
0.2 boot into ubuntu in some way and install all the needed packages to compile theese things
1a. checkout the last svn version of grub2 and compile it for the x86_64 efi platform - i followed [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook) and [http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)..... or download the attached file. the config file is for kernel version 2.6.27-11-generic, but you can change it for your kernel versions
1b. change, if you set it, in xorg.conf from nvidia to fbdev
```
Section "Device"
    Identifier     "Device0"
    Driver         "fbdev" #"nvidia"
#    VendorName     "NVIDIA Corporation"
EndSection

```
1c. add the folling line in /etc/modprobe.d/blacklist
```
blacklist agpgart

```
2. copy the compiled-or downloaded grub2_efi to an usbpen and reboot into osx
3. paste grub2_efi into /efi/
4. reboot
5. now you should see another entry in refit: grub2_efi. boot :)


1. here there is some code:
```

mkdir grub2_efi
svn co svn://svn.savannah.gnu.org/grub/trunk/grub2 grub2
cd grub2
./configure --with-platform=efi --target=i386
make
./grub-mkimage -d . -o grub.efi gpt hfsplus fat ext2 normal chain boot configfile
sudo cp grub.efi *.mod fs.lst command.lst ../grub2_efi

```

create your own grub.cfg file, or take the mine, and put it into grub2_efi:
```
menuentry "linux-2.6.27-11-generic" {
  # Set the root device for Linux.
  root=(hd0,3)
  # Load the loader. - other options: video=vesafb noefi
  linux /boot/vmlinuz-2.6.27-11-generic root=/dev/sda3 video=efifb agp=off acpi=force
  initrd /boot/initrd.img-2.6.27-11-generic
}

menuentry "MacOSX" {
  # Search the root device for Mac OS X's loader.
  search --set /usr/standalone/i386/boot.efi
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi
}

menuentry "Boot from MBR" {
  appleloader HD
}
menuentry "Boot from CD" {
  appleloader CD
}

# this does not work for me
menuentry "Boot from USB" {
  appleloader USB
}


#keymapping: remeber these keys when you boot, they can be helpful!!!
#F1 = ctrl-x
#F2 = ctrl-a
#F3 = ctrl-e
```


Hi 

Is there any chance of getting this set of instructions working now? I tried, but the URL 
svn co svn://svn.savannah.gnu.org/grub/trunk/grub2 grub2
doesn't exist anymore. I still have a macbook 5,2 which doesn't show the battery or shutdown properly etc.
Thanks,
I

---

