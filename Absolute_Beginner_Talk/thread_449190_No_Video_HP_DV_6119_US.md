---
title: "No Video HP DV 6119 US"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by t1hall on 2007-05-20
I'm going to make this as simple as possible. I just bought an HP DV 6119 US Laptop with a nvidia 6150 go graphics card. I have tried to install every version of ubuntu from 5.10 through 7.04 and the  OS will not install. It seems like everytime I bootup to the live CD, the video works or it does not. I was able to hookup
an old monitor and load ubuntu, but as soon as the OS finished installing their is no video. This really sucks because if I have no video, how am I supposed to learn this OS???? I have searched and searched for a resolution over the internet, but I have yet to find an answer.

---

### Post by overdrank on 2007-05-20
> **t1hall said:**
> I'm going to make this as simple as possible. I just bought an HP DV 6119 US Laptop with a nvidia 6150 go graphics card. I have tried to install every version of ubuntu from 5.10 through 7.04 and the  OS will not install. It seems like everytime I bootup to the live CD, the video works or it does not. I was able to hookup
an old monitor and load ubuntu, but as soon as the OS finished installing their is no video. This really sucks because if I have no video, how am I supposed to learn this OS???? I have searched and searched for a resolution over the internet, but I have yet to find an answer.

Hi I did a search on the video and it seem to be working with ubuntu.
Have you tried the alternate cd located here
[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)
Scroll down to the alternate cd and remember to follow the burn iso "how to" found here
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Hopefully that will get you to install ubuntu and then you can tackle installation of the video driver. Hope this helps good luck!

---

### Post by abhishek456 on 2007-05-20
had you tried installing in Safe mode or text mode

---

### Post by t1hall on 2007-05-22
yup, I found the resolution. Not to sure what I'm doing, but here you go....
1. HP Pavilion dv6000 or dv6119us 
2. AMD 64, nvidia 6150 go

Boot, from your Feisty Fawn CD. Choose F6 then type in pci=noacpi and hit enter. I'm dual booting between XP/Ubuntu. Go through your guided install that Ubuntu offers. Install, reboot and enjoy.
My sound does not work, but thats OK. At least I can see what I'm doing and I'm able to learn this OS a little better.

---

### Post by jcaveman on 2007-05-23
pci=noacpi disables acpi and hence the sound doesn't work.  Try using "noapic irqpoll noirqdebug" instead.  The noapic option seems to leave most of acpi functional and sound works.  The bad news is that noapic seems to affect the interrupt controller and ends up allowing the usb driver to timeout and turn off disabling the usb ports.  Adding the irqpoll noirqdebug option seems to keep the usb ports from disabling.

---

### Post by t1hall on 2007-05-23
I don't want to sound stupid, but were do I make these changes once the OS is installed. Also, I'm having trouble running Beryl or Desktop effects. Both fail to run when I try to enabled.

---

### Post by jcaveman on 2007-05-24
You need to edit boot manager configuration file for grub:

  sudo gedit /boot/grub/menu.lst

Once the editor is open you need to look for a section that looks like this:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e1f886b8-e818-499b-89ba-cff2f5a22fb6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

Add the following parameters to the end of the line beginning with the word  "kernel"

      noapic irqpoll noirqdebug

Save the file then issue the following command:

   sudo update-grub

This will make sure these parameters are used by the linux kernel during boot up all the time without you having to do anything.  In addition, the update-grub command will make sure the changes stick whenever a software upgrade replaces the kernel.

---

### Post by buu700 on 2007-05-31
Text of my original post:
hi i have this laptop also and i've been having the same problem (it booted every ~10 times i turned the computer on, so i had to keep turning it on and off... really annoying...), so i gave up eventually and switched to w*ndows (a dell oem vista copy... i was eligible for the express upgrade though...). however, i found something very interesting that i think will help make the laptop fully linux-compatible (im gonna try this when i have time). [http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Pavillion_dv6119us](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Pavillion_dv6119us)
wireless: [http://www.gidforums.com/t-4390.html](http://www.gidforums.com/t-4390.html)
nvidia drivers: [http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)
the dv6119us article was made for gentoo, but the parts that matter can easily be applied to ubuntu.

they have everything other than the 56k modem working (nobody uses it of course...)

also, would anyone be willing to upload the following files (wireless drivers; preferrably in a zip file or something) to an online hosting site and post the link here: BCMWL564.SYS, bcmwl5.inf, and bcmwl5.sys? thanks (i can't seem to find them on my copy of vista. nevermind. after a bit of searching, i found the drivers here: [http://ubuntuforums.org/showthread.php?t=9593&p=40921](http://ubuntuforums.org/showthread.php?t=9593&p=40921)
[B]
EDIT: Ignore everything I typed before this. If you want to get your HP Pavillion dv6119us working perfectly with Ubuntu Feisty, read my final post here. It's on the next page, but for those of you who don't feel like going to the next page, here's the complete text of my final post (noob friendly):[/B]

"Well, I'm back, and I have everything running absolutely perfectly.

First, with a clean install, I used the boot options (F6) "ro quiet splash noapic nolapic irqfixup."
Then, the first thing I did was go to System>Administration>Restricted Drivers Manager and enable the NVIDIA Accelerated Graphics Driver. Then I restarted.
Then, to get wireless working, I simply installed bcm43xx-fwcutter from Synaptic.
I also have Beryl running perfectly. To get it working, install it from Synaptic, go to Applications>System Tools>Beryl Manager, notice that the computer is suddenly almost as slow as a 56kAOL-AeroVista-Spyware triumvirate would be on a barely "Premium Ready" PC, right-click the Beryl logo in the panel on the top, and go to Advanced Beryl Options>Rendering platform>Force AIGLX (If you choose Force NVIDIA, it's pretty much the same as Automatic; Force XGL brings Ubuntu to a complete standstill until it eventually falls back to GDM.
Finally, you would go to System>Preferences>Sessions and add beryl-manager as a startup program.

Time to use taimila.com's new guide to pimp out my Ubuntu the OS X way! (I'll post screens when I'm done...)"

Also, you might want to back up once you get everything working using "sbackup", which you can just apt-get install. I recommend making a free mediamax.com account, which gives you 25GB free storage and 1GB per month uploading limit. Then, set sbackup to do a monthly backup to ftp.mediamax.com, with the username and password both being your Mediamax username (no, that isn't a typo...).

---

### Post by buu700 on 2007-06-03
I installed Ubuntu and it works perfectly (and it automatically set itself to 1280x800 @ 60Hz, so I don't think I need to install the nVidia drivers). I just used "nolapic irqpoll noirqdebug" and I'll try and get wireless working soon. (By the way, I used the x64 version.)

---

### Post by buu700 on 2007-06-04
Ubuntu is running fine, except I can't get wireless or the nVidia driver (computer shows blank screen after I enable the driver in System>Administration>Restricted Drivers Manager) working. (By the way, I'm using x86 now because flash doesn't work in x64.) Also, can anyone help me get this working:[http://ubuntuforums.org/showthread.php?t=105761&p=587593](http://ubuntuforums.org/showthread.php?t=105761&p=587593)?

---

### Post by buu700 on 2007-06-05
Hi. Back (I'm probably the only one still going on this thread though...). I have WLAN working!!!!!!:
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

However, the GeForce Go 6150 isn't listed in nVidia's list of supported cards, and I haven't been able to get the nVidia drivers to work, so I'm lost... Anyone have better luck?

---

### Post by buu700 on 2007-06-09
Well, I'm back, and I have everything running absolutely perfectly.

First, with a clean install, I used the boot options (F6) "ro quiet splash noapic nolapic irqfixup."
Then, the first thing I did was go to System>Administration>Restricted Drivers Manager and enable the NVIDIA Accelerated Graphics Driver. Then I restarted.
Then, to get wireless working, I simply installed bcm43xx-fwcutter from Synaptic.
I also have Beryl running perfectly. To get it working, install it from Synaptic, go to Applications>System Tools>Beryl Manager, notice that the computer is suddenly almost as slow as a 56kAOL-AeroVista-Spyware triumvirate would be on a barely "Premium Ready" PC, right-click the Beryl logo in the panel on the top, and go to Advanced Beryl Options>Rendering platform>Force AIGLX (If you choose Force NVIDIA, it's pretty much the same as Automatic; Force XGL brings Ubuntu to a complete standstill until it eventually falls back to GDM.
Finally, you would go to System>Preferences>Sessions and add beryl-manager as a startup program.

Time to use taimila.com's new guide to pimp out my Ubuntu the OS X way! (I'll post screens when I'm done...)

---

### Post by DeeZeal on 2007-06-26
Hey, I also have the HP dv6119us and am having the same problem.  When I installed Ubuntu 7.04 x86 for the first time it seemed to go well.  When I ejected the CD and restarted though, the screen turned this very odd black and gray checkered screen.  I figured the video drivers were messed up but I am very new to Linux.

I did a clean install using 17gb + 3gb swap on an extended partition.  I left the Live CD in the computer and started it up again.  When I got the screen that has the 6 option (start or install Ubuntu, Start Ubuntu in safe graphics mode, etc.) I hit F6.  I erased everything and typed in "ro quiet splash noapic nolapic irqfixup" but then I got an error:

[ 0.057250] PCI: BIOS BUG #81[49435000] found
[ 0.840000] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)
[ 0.840000]

And that is all I get.  I have tried ejecting the CD and hitting F6 when GRUB asks me what OS to boot but I don't get a menu so I assume the CD must be left in.

Any thoughts?

:(

---

### Post by ron66 on 2007-07-14
> **buu700 said:**
> Well, I'm back, and I have everything running absolutely perfectly.

First, with a clean install, I used the boot options (F6) "ro quiet splash noapic nolapic irqfixup."
Then, the first thing I did was go to System>Administration>Restricted Drivers Manager and enable the NVIDIA Accelerated Graphics Driver. Then I restarted.
Then, to get wireless working, I simply installed bcm43xx-fwcutter from Synaptic.
I also have Beryl running perfectly. To get it working, install it from Synaptic, go to Applications>System Tools>Beryl Manager, notice that the computer is suddenly almost as slow as a 56kAOL-AeroVista-Spyware triumvirate would be on a barely "Premium Ready" PC, right-click the Beryl logo in the panel on the top, and go to Advanced Beryl Options>Rendering platform>Force AIGLX (If you choose Force NVIDIA, it's pretty much the same as Automatic; Force XGL brings Ubuntu to a complete standstill until it eventually falls back to GDM.
Finally, you would go to System>Preferences>Sessions and add beryl-manager as a startup program.

Time to use taimila.com's new guide to pimp out my Ubuntu the OS X way! (I'll post screens when I'm done...)

buu700,
  Glad to see you have it working. I'm a Ubuntu n00b attempting to repeat your success, and have a few questions.

I'm stil unclear about the Nvidia driver. Nvidia does not seem to support the GeForce Go 6150  GPU of the dv6119us.  How did you overcome this? Or did I overlook something?

Also,  I see from you other posts that you attempted the X86 version as well as the X64 version of Ubuntu. Which version was ultimately  successful for you?


Thanks.

---

