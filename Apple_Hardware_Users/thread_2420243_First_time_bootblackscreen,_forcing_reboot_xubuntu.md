---
title: "First time boot:blackscreen, forcing reboot: xubuntu start"
date: 2019-06-01
forum: Apple Hardware Users
---

### Post by pocce90 on 2019-06-01
Hello everybody!
I have a problem with xubuntu 18.04 installed on an old macbook pro (2007 with intel core duo, efi x32 and os x64) I've installed everything and everything works very good, except one thing: when I start the pc, and select from grub the default option, the pc doesn't start, I can see only a black screen, but if I force the shootdown (pressing and holding the power button) andrestart, the os is launched perfectly...each time! so how I can solve this issue?I'm thinking on something like forcing boot option simulating the wrong shootdown but I don't know what the boot exactly do when it runs after a brutal reboot...somebody can help me?

EDIT: I can start from recovery and xubuntu run with low settings

---

### Post by oldfred on 2019-06-01
Moved to the Apple sub-forum where those who know Mac may be able to help.

Do not know Mac, but these may have some clues.
 Old Mac  Late 2006 iMac (iMac6,1) 18.04 with patched nVidia 304
[https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic](https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic) 
   [SOLVED] Video performance of Ubuntu 16.04 on 2007 Mac Mini 2,1 (Intel Integrated 945GM/GMS)
[https://ubuntuforums.org/showthread.php?t=2349732](https://ubuntuforums.org/showthread.php?t=2349732)
Ubuntu 15.04 on Mac Mini 2,1 with EFI boot (2007 Intel)
[https://ubuntuforums.org/showthread.php?t=2287767](https://ubuntuforums.org/showthread.php?t=2287767)

---

### Post by pocce90 on 2019-06-01
> **oldfred said:**
> Moved to the Apple sub-forum where those who know Mac may be able to help.

Do not know Mac, but these may have some clues.
 Old Mac  Late 2006 iMac (iMac6,1) 18.04 with patched nVidia 304
[https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic](https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic) 
   [SOLVED] Video performance of Ubuntu 16.04 on 2007 Mac Mini 2,1 (Intel Integrated 945GM/GMS)
[https://ubuntuforums.org/showthread.php?t=2349732](https://ubuntuforums.org/showthread.php?t=2349732)
Ubuntu 15.04 on Mac Mini 2,1 with EFI boot (2007 Intel)
[https://ubuntuforums.org/showthread.php?t=2287767](https://ubuntuforums.org/showthread.php?t=2287767)

Thank you for the quick response, I have an integrated graphic card, no nVidia and I think that there are no issues with the graphic driver because everything is working good the second time that I run the PC, I think that there is an option in GRUB that freeze something, or something in the shootingdown process that saves OS status and when it's loaded cause the freeze

---

### Post by gsahli on 2019-06-02
This is just a guess - your drive may be failing, and needs extra spin-up time before it can boot.
Look at this:
[https://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry](https://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry)
If a longer delay helps, you should be thinking of replacing the drive.

---

### Post by pocce90 on 2019-06-02
I found that if I remove ```
gfxmode $linux_gfx_mode
``` in grub option the OS is launched with no problem...

---

### Post by gsahli on 2019-06-02
Good work. Video is normal now, too?

---

### Post by pocce90 on 2019-06-05
> **gsahli said:**
> Good work. Video is normal now, too?
The resolution is perfect, but I have issue with video reproduction, for example with Netflix...I have problem with refresh rate. I cannot try reinserting the string in boot option to see if the same appens because I am away for a week...but I think that doesn't appen, I think that if i put that string in grub the video works good but the main problem would appear again.

---

### Post by vistauser2 on 2019-06-30
I'm on 18.04LTS on a toughbook that after a weird update, it began to boot up - freeze - then reboot 2nd time as fine.... see:
[https://ubuntuforums.org/showthread.php?t=2421994&p=13869948#post13869948](https://ubuntuforums.org/showthread.php?t=2421994&p=13869948#post13869948)

---

