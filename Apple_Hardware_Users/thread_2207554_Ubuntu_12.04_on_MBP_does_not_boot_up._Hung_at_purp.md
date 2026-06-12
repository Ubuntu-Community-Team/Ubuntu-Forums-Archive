---
title: "Ubuntu 12.04 on MBP does not boot up. Hung at purple screen five dots."
date: 2014-02-24
forum: Apple Hardware Users
---

### Post by morningsunshine on 2014-02-24
Hi folks,

I am using Ubuntu 12.04 on MACbook Pro 5.3. It was working all  fine but then the screen suddenly turned black and I waited and it wont turn back  on. So I hard shut it down and started it again. Now it started the  boot and purple screen with five dots came up. And it has been sitting  there for a long time now.

I haven't installed any new software and OS updates either. There should be more than enough disk space available too.

I had installed ubuntu on mbp few months back. Since then it has been running fine. Now, meanwhile since it went down, I tried a few things.

I tried setting nomodeset at boot time - pressing 'e'. No change
Tried previous Linux versions - No change

Now, I also put in Live CD and this time it showed LiveCD splash screen at the start. And then the screen turned black. I hear the LiveCD is running but there is nothing shown on screen.

Can someone please give pointers? help!

---

### Post by morningsunshine on 2014-02-24
Additional info:

I just did a hard shutdown and started it again, pressing Alt key. It is showing the Internal HDD (the one that has Ubuntu 12.04), 1 CD icon named Windows (this is LiveCD ubuntu), and 1 CD icon named EFI boot.

---

### Post by morningsunshine on 2014-02-24
Update1:

I tried EFI boot option. It again went in to blank screen. Second time, EFI boot, press 'e' removed 'quiet splash' and added 'nomodeset'.
This started showing the boot messages on a terminal. In the final message, it shows error related to udevd, repeating over and over:

udevd[146]: timeout killing '/sbin/modprobe -bv pci:<large name here>, [214]

This keeps on repeating.

Then I see message about 'mounting filesystem' and this same udevd error message.

Finally, it throws a busybox shell
(initrramfs) 

And this udevd message clobbers the screen...

I killed this udev process and now have initramfs shell.

---

### Post by morningsunshine on 2014-02-24
Update2:

I booted in to LiveCD. I choose 'Boot from first hard disk' and F6 -> set 'nomodeset' and boot. 
Also set 'noacpi' second time.
Still does not complete boot. Stuck at purple screen with five dots all lit up.

---

### Post by morningsunshine on 2014-02-24
Update3:

It is back up again! After trying as I mentioned above, I decided to let LiveCD boot up once, bcos it wasn't getting up and just showing the black screen. I am not sure very sure if I had set the noacpi / nomodeset option(s) when I tried this LiveCD run. Anyhow, LiveCD booted up all fine & gave the GUI / desktop access. This is the first instance when LiveCD run was successful **ON** the MBP.

After this I shut it down & tried again. It did not come back up.

I did a few checks again & still no change. After around 10 mins, I decided to let HDD boot once more, without any changes in the boot options. And viola, it did wait for a min will all 5 dots lit up, and turned to black screen but then the mouse arrow appeared finally, and then the wallpaper, and then the login screen. I logged in and writing this update from the MBP. I still have to put the screws on MBP insides and cover. Just don't want to shut this baby down again.

So, if someone has taken a look at this scenario, I intend to ask about **_what should I check now to get more information as to what got screwed up. Logs? Configuration files?_** Any ideas are much welcome. Please lemme know.

---

### Post by morningsunshine on 2014-02-24
Okay it is hit again. This is definitely a problem with video drivers / graphic card. It was working fine and suddenly the screen turned blank. I pressed Ctrl Alt Fn6 and now I see the distorted view, linings on the screen. Uggghhh. Please share any pointers about fixing this video / graphic problem..

---

### Post by morningsunshine on 2014-02-24
Update:
I restarted the box and it did boot up fine. I logged in and have changed the following:

*sudo gedit ****/etc/default/grub*** [B]-
[/B]
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
- changed to
 GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash"

I found it here -> [http://www.howtoeverything.net/linux/ubuntu/nvidia-and-ati-graphics-card-problems-ubuntu-1004-1204](http://www.howtoeverything.net/linux/ubuntu/nvidia-and-ati-graphics-card-problems-ubuntu-1004-1204).

Hopefully it will be fine now.

---

### Post by morningsunshine on 2014-02-24
screen still going blank after every 10 15 mins. have removed all nvidia drivers already.

---

### Post by morningsunshine on 2014-02-26
Bump! Noone?

---

### Post by jorgeblasio on 2014-02-26
Maybe your hardware (video card) is failing.

---

