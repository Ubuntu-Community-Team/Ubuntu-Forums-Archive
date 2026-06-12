---
title: "Dual Boot problem Ubuntu/Mac OSX (Macbook Pro)"
date: 2016-04-02
forum: Apple Hardware Users
---

### Post by silentrock on 2016-04-02
Hey guys,


Recently I decided to dual boot Ubuntu 15.10 and Mac OS X El Capitan in my Macbook Pro (Mid 2010, i5, 4gb). 
In the past I've managed to dual boot and even triple boot with a PC and I thought the process would be basically the same, which was a huge mistake. 

I decided to follow this guide:

[http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)

Everything was going quite well until the step where I got to refind again to boot from the Live USB; it showed 4 options; 

[LIST]
[*]Boot Mac
[*]Boot Linux (well it had this Tux icon)
[*]Boot from USB
[*]And another one which I can't remember saying something about Legacy.
[/LIST]

I tried the USB option as told in the guide, however, it took me to a black screen saying there was no bootable disk, after this, I simply restarted Mac and chose the Linux option (or the one with the penguin icon).  This booted the Ubuntu Live USB. 

I continued the steps and started the "Install Ubuntu etc." program.  When I got to the point to chose Instalaltion type, the "install along Mac osx" option wasn't displaying at all, even after restarting the Install program a couple times.

I decided to chose the "Something else" option that took me to the partitions screen. There I thought everything would be as simple as it would be in a PC Dual boot; I created a partition in sda5 for swap with 6gb, formated the target ubuntu partition (sda4) to Ext4 and set it to mount on /. Then chose the sda1 (efi thing) for bootloader installation.

Installation went as usual and after it finished the computer rebooted, unfortunately, it went straight to Ubuntu, no Refind or even Grub or anything of that sort. After rebooting again it went still went to ubuntu (which was logical ofc). I rebooted for a 3rd time and went to the Mac recovery thing (cmd + r) and I still could boot into that, however, everytime I reboot normally it goes to Ubuntu. 

As of the reboot process itself, it starts with the white/light blue-ish screen and after 3 seconds it goes black and then ubuntu.

I know I messed something with the partitions and the boot loader, but my very limited knowledge of Mac won't allow me to figure out. 

I would thank you a lot if you can help me get this running normally and by that I mean being able to select either OS through Refind (or grub if it's best or idk).

Thank you!

---

### Post by Bucky Ball on 2016-04-03
*Thread moved to **Apple Hardware Users**.*

You'll perhaps have better luck here.

---

### Post by ingcontiingconti. on 2016-04-04
I have yet finished to do so.

"Something else" is the right choice.
So if you do not use a bot manager (not a boot loader..) your mac will simply boot in ubuntu.
Using "ALT" key you will be carried to usual choice of disk, but you cannot see a Ubuntu disk.
So If You are in this situation, is fine.
recap:

1 to boot in OSX/windows:ALT at boot
2 to boot in Ubuntu: no key  at boot

---

### Post by Bob_Bruce on 2016-04-10
Next time you are in ubuntu type this in terminal:

sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind

Type or copy/paste one line at a time and hit enter, entering your password when prompted after entering the first line. There will be a couple other prompts so type Y for one and hit enter for the other. This will install rEFInd which will automatically come up and give you a choice to select OS X or Ubuntu every time you reboot the system.

---

### Post by Vinodh Moodley on 2016-04-13
There's no need to use refind. Just use the regular 64bit version of Ubuntu and install it on a partition. Once it's installed, disable SIP, bless Grub, enable SIP and use the option key to choose which OS you want to boot from. If you do everything correctly, it will look like this:

[https://youtu.be/w0RM3L8r4cE](https://youtu.be/w0RM3L8r4cE)

---

### Post by este.el.paz on 2016-04-14
> **silentrock said:**
> Hey guys,

I decided to chose the "Something else" option that took me to the partitions screen. There I thought everything would be as simple as it would be in a PC Dual boot; I created a partition in sda5 for swap with 6gb, formated the target ubuntu partition (sda4) to Ext4 and set it to mount on /. Then chose the sda1 (efi thing) for bootloader installation.

Installation went as usual and after it finished the computer rebooted, unfortunately, it went straight to Ubuntu, no Refind or even Grub or anything of that sort. After rebooting again it went still went to ubuntu (which was logical ofc). I rebooted for a 3rd time and went to the Mac recovery thing (cmd + r) and I still could boot into that, however, everytime I reboot normally it goes to Ubuntu. 

u!

@sr:

If you have solved your problem you should post back; but if you haven't fixed the issue, perhaps a key point on your install, or rather on my 09 MBP which I have set for triple boot, in the "something else" install method, if I don't set aside a ~10MB partition labeled as "bios_grub" for my LM install, the installer will say "installation successful" but GRUB won't mount and LM system won't boot.  Yours seems to be the opposite, but the fact that you don't see a GRUB window or rEFInd means that both have probably not been installed . . . ???  Also, after the install, rather than "reboot" it is better to "shut down" . . . then on cold boot often the GRUB and rEFInd items will show . . . possibly with "option" key which would load the OSX boot manager, should give you the option to boot OSX.

e...

---

