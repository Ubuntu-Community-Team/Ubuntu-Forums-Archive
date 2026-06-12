---
title: "Help me get &quot;Suspend to RAM&quot; to work on HP notebook"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-12-26
Hi there, I have resorted to asking this question even after attempting a number of workarounds to make this work in my notebook (google search, and [here]("https://help.ubuntu.com/community/SuspendHowto"), and on this forum)

**Hardware: HP Compaq nw8240, Intel Centrino 2.13Ghz, 2G RAM, 4G SWAP, ATI fglrx V5000.**

What is happening right now is that when I select "Suspend" from the "Quit" screen, the screen goes black, the volume mute LED comes on, the power button remains on, the HDD is still spinning, and the fans conitinue to blow. Even worse is when  try to awaken it by pushing the power button, nothing happens---only way to get back to desktop, is to hard reboot (by pressing the power button hard).

In XP suspend shuts power down (blinking power light on button), and HDD is quiet (not spinning).

Could some help me out so that I have a working suspend function. I wish to have this working because, right now, the notebook remains on even when I am not doing anything on it, gets unbearingly hot (palm rests).

I do not have compiz installed. My ATI graphics works  just fine with the Ubuntu ATI restricted drivers.
**I am sure i am missing some settings in acpi settings or even trying to get Ubuntu to recognize my SWAP file for hybernation??** But, I am no expert at this. So help will be much appreciated.

Thank you,

S

---

### Post by Dakine858 on 2007-12-26
Which version of Ubuntu are you using? If you happen to be using Gutsy 7.10 then compiz comes already integrated into it and most people don't realize it until something goes wrong.

So here we go with fixing your problem. The malfunction cause: compiz (to figure out do a simple test: disable compiz before entering standby and you should be perfectly able to resume)
then install via apt-get CompizConfig
go in General Options -> Display Settings 

and disable Sync to VBlank


if resume from standby still gives you a black empty screen with only the cursor then edit the following file:

sudo gedit /etc/default/acpi-support

go to POST_VIDEO=
and set it POST_VIDEO=false

in the same file nVidia suggests to disable use of VBE to restore power states for improved stability on resume:

Some distributions use a tool called vbetool to save and restore VGA adapter state. This tool is incompatible with NVIDIA GPUs’ Video BIOSes and is likely to lead to problems restoring the GPU and its state. Disabling calls to this tool in your distribution’s init scripts may improve power management reliability.
[http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/chapter-18.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/chapter-18.html)

In order to accomplish with these suggestions make sure this line shows as follows:

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

Hope this helps

---

### Post by shuttleworthwannabe on 2007-12-26
Yes, I am in Gutsy and i have an ATI card.

I am unable to get suspend to ram working--it just hangs; suspend to disk also not working;

Strange thing is that when I try doing this, it goes to screen lock...I am not sure what made this come about.

Thanks though,
S

---

### Post by hardyn on 2007-12-26
try adding vga=791 to your grub boot parameters located in /boot/grub/menu.lst
is your swap file at least the same size as your physical ram?

---

### Post by shuttleworthwannabe on 2007-12-26
My swap is 4Gigs my RAM is 2Gigs. 
Sorry for asking, but will the vga=791 do; how it will it help?

---

### Post by hardyn on 2007-12-26
it forces the default video mode from text (80chrs) to VGA.

it was the only way i could get my ATI x700 board to suspend.

---

