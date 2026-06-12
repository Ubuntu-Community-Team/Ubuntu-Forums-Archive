---
title: "MacBookPro8,2 EFI Boot Issue"
date: 2013-03-13
forum: Apple Hardware Users
---

### Post by jhohisel on 2013-03-13
Hi, this is my first post here (though I've used ubuntu for a couple of years now). I have never fully used ubuntu as the primary OS on my MacBook Pro because of one drawback: battery life due to the discrete card being the only one available. I recently found out that booting via EFI will make the Intel (HD3000) card visible and there may be luck with switching via switcheroo. 
So, where I'm at now is as follows: I have rEFInd installed and a fresh copy of ubuntu 12.10 x64. I installed *without* installing GRUB, and after installing copied the kernel to an ubuntu folder on the EFI partition. 
So now rEFInd boots the kernel directly, and I do not have GRUB installed. (this method was described as better by the creator of rEFInd)

I now get three different situations based on arguments (provided to rEFInd):

1: "Boot using standard options" "root=UUID=6a19dc03-c729-4dbc-bcd4-25d4794935fc ro  quiet splash $vt_handoff" (this is the default mode provided by a guide)
Boots up fine but the screen is forever black, backlight in screen and keyboard works.

2: "Boot using standard options" "root=UUID=6a19dc03-c729-4dbc-bcd4-25d4794935fc ro  quiet splash $vt_handoff nomodeset=1"
Boots to the loading ubuntu screen with the purple background and five dots, but gets stuck.

3: "Boot using standard options" "root=UUID=6a19dc03-c729-4dbc-bcd4-25d4794935fc ro   nosplash debug --verbose $vt_handoff nomodeset=1"
Boots with console output, but gets stuck at what seems like it's finished loading and the next step is "Welcome to Ubuntu!" (or whatever it says)

The problem is somewhere with the graphics cards, here is some relevant output from kern.log:

RADEON (HD 6750M)
kernel: [    3.692024] [drm] radeon defaulting to kernel modesetting.
kernel: [    3.692024] [drm] radeon kernel modesetting enabled.
kernel: [    3.692075] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver
kernel: [    3.693120] usbcore: registered new interface driver uvcvideo
kernel: [    3.695089] [drm] initializing kernel modesetting (TURKS 0x1002:0x6741 0x106B:0x00E2).
kernel: [    3.695134] [drm] register mmio base: 0xB0800000
kernel: [    3.695136] [drm] register mmio size: 131072
kernel: [    3.695182] radeon 0000:01:00.0: >Invalid ROM contents
kernel: [    3.695234] radeon 0000:01:00.0: >Invalid ROM contents
kernel: [    3.695243] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
kernel: [    3.695247] radeon 0000:01:00.0: >Fatal error during GPU init
kernel: [    3.695251] [drm] radeon: finishing device.

INTEL (HD3000)
kernel: [    2.436003] fb0: EFI VGA frame buffer device
kernel: [    2.436029] intel_idle: MWAIT substates: 0x21120
kernel: [    2.436052] intel_idle: v0.4 model 0x2A
kernel: [    2.436071] intel_idle: lapic_timer_reliable_states 0xffffffff
kernel: [    3.664139] i915 0000:00:02.0: >setting latency timer to 64
kernel: [    3.703019] i915 0000:00:02.0: >Invalid ROM contents
kernel: [    3.967149] fbcon: inteldrmfb (fb0) is primary device
kernel: [    3.969514] fb0: inteldrmfb frame buffer device
kernel: [    3.977003] i915: fixme: max PWM is zero

I know there's got to be some magical argument that I'm missing, but can't determine what it is.
* What about 13.04? Any fixes regarding my issue?
Any help would be greatly appreciated.
Thanks!

---

### Post by proycon on 2013-03-15
I haven't managed to let refind directly boot in EFI mode either, if anyone has I'd love to hear it, especially if vgaswitcheroo works too. Only through grub.efi I can boot in EFI-mode, with only the discrete card enabled which is a major improvement on battery life and fan speed. See [http://ubuntuforums.org/showthread.php?t=2061791](http://ubuntuforums.org/showthread.php?t=2061791) for details on that.

---

### Post by Garlandg on 2013-03-16
You might try hitting F2 on the ubuntu boot option in rEFInd to select a boot option and then hit F2 again to modify the selection line.  Set it to text or recovery and see if you can get past the issue.  I currently use that workaround to boot my mac, though it has nvidia graphics.

The other thing I notice, though I don't have experience with radeon cards at all, is that there seems to be a driver conflict:

kernel: [    3.692075] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver

You might try blacklisting one of those modules (if you can get in using my previous suggestion).  From what I saw in a quick google search, the radeondrmfb is the driver you want.

---

### Post by proycon on 2013-03-17
I now got vga switcheroo working (but still using Grub EFI rather than refind directly to boot), check these threads:

[http://ubuntuforums.org/showthread.php?t=2103743](http://ubuntuforums.org/showthread.php?t=2103743)
[http://ubuntuforums.org/showthread.php?t=2115317](http://ubuntuforums.org/showthread.php?t=2115317)

---

