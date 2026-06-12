---
title: "Installed Ubuntu 14.10 on MacBook Pro (5,5) without rEFIt or rEFInd, hangs on purple"
date: 2014-12-23
forum: Apple Hardware Users
---

### Post by vitale232 on 2014-12-23
Hey all,


I recently inherited a mid 2009 13" MacBook Pro. I wanted to install Ubuntu 14.10 on the machine rather than OS X. I've previously had success with Ubuntu 13.10 on a 2006 MacBook by booting to live USB and installing over the current OS, so I tried this method again with admittedly limited research.


While installing 64-bit Ubuntu 14.10 on the MacBook Pro 2009, everything seemed to go fine. However, when I rebooted the machine in an attempt to launch Ubuntu for the first time, I was greeted by GRUB, selected Ubuntu, and then dropped to a purple screen. Nothing changed after 30 minutes -- still a purple screen. Repeated attempts to boot into Ubuntu 14.10 produce the same results.


In hindsight, it looks like I probably should have installed rEFIt or rEFInd on the machine prior to installing Ubuntu, as the 2009 MacBook uses EFI rather than BIOS. Is this required even when you're not setting up a dual boot?


Thus far, I have tried two routes to solve the issue. First, I tried to boot back to Ubuntu live USB, but to no avail. The GRUB menu appears as usual, but when I select either "Try Ubuntu" or "Install Ubuntu", the screen goes black and hangs there.
My second attempt was to create a bootable USB of OS X Yosemite. This too is getting hung up. When I select the option to load from USB, the Apple symbol appears on the screen with a progress bar. The progress bar has been hung at ~25% for the last 45 minutes or so. I have yet to have the option of installing the OS.


What is the best way to get my machine running again? I would be happy to have either OS X or Ubuntu installed at this point.


Thanks for any tips, tricks, or flames.

---

### Post by vitale232 on 2014-12-24
UPDATE:

I followed the [advice]("http://askubuntu.com/questions/470492/ubuntu-14-04-black-screen-when-installing") of infostacker on AskUbuntu. I plugged in my live USB (Ubuntu 14.10, created on Windows 7 with Unetbootin), hit 'e' on the GRUB menu while the 'Try Ubuntu without installing' text was highlighted, and added to the 'linux' line of the boot command: 'quiet splash acpi=off nolapic nomodeset'.  This got me the purple screen that you typically see upon booting Ubuntu with the moving dots (the splash screen?). Once it got past the moving dots stage where you'd expect the Unity desktop to pop up, I was greeted with some text.  The final line of text where the system appears to get hung reads:

'(initramfs) Unable to find a medium containing a live file system'.

Here's a picture of the entire screen:

[IMG]https://lh4.googleusercontent.com/-Me6FQu7ZwO0/VJsKpYXQVmI/AAAAAAAAbuQ/uSaRvfPwJhA/w863-h647-no/14%2B-%2B1[/IMG]




When I try to run Ubuntu off of the hard drive (i.e. without the live USB) using the same command, I get different results.  I get a purple screen that reads like this:

  Booting a command list

Loading Linux 3.16.0-28-generic ...
Loading initial ramdisk ...

It hangs on the last step to infinity and beyond.

Does this new insight help at all?  Thanks.

---

### Post by vitale232 on 2014-12-24
[COLOR=#000000][FONT=Arial]**UPDATE 2:**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am able to boot into Ubuntu if I edit the GRUB script. When I append quiet splash with nolapic I am able to boot without issue.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]My first move upon booting was to install the proprietary NVIDIA 331 driver, which is the tested driver and claims to be suggested for my system. I then removed the open source driver using sudo apt-get --purge remove xserver-xorg-video-nouveau.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Upon normal reboot, I get stuck at the purple screen again. It seems the only way to boot the system is with the nolapic parameter. What could be the underlying cause of this?[/FONT][/COLOR]

---

### Post by Jon_Terrell on 2014-12-26
I installed the 32 bit version but opted for the security/LVM(?) on my first try and had to start through the GRUB screen, which later froze up.  I then reinstalled without selecting those options (and not connected to the internet, which probably doesn't matter) and everything worked and updated without starting through the GRUB screen now.  I tried the 64 bit version and got 1.2.CD Type? which would not load, but if you have a DVD you can select it by holding the alt button on powerup, some people seem to think they need USB drive.  Too bad a novice luser (me?) can't kill the macbook startup sound!

---

### Post by slickymaster on 2014-12-26
*Moved to the ***Apple Hardware Users*** sub-forum*

---

