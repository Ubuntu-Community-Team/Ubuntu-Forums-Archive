---
title: "Wiki instructions about BootFromUSB"
date: 2007-05-13
forum: Apple Intel Users
---

### Post by dmitrijledkov on 2007-05-13
Hi everyone!

Like many, I am desperate to install to/boot from USB pen  drive on Intel MacBook. After searching google, forums, ubuntu forums and at last ubuntu wiki I came to following conclusions:

1) it is possible
2) it is possible on normal PC machines
3) it should be possible on intel mac, cause you can boot into mac over firewire/USB (net drive)
4) but it doesn't want to natively recognise anything unless it is APM or EFI mapped drive

and therefore nice pen drive with copied Ubuntu on it (modified and done following steps) won't be recognised for boot up by intel mac.

Next I found a ubuntu-wiki page BootFromUSB describing how to make it work. First method suggests to use grub, but I don't want to mess with my mac MBR in anyway.

Second method tells to create custom ubuntu boot disk, which will have USB boot support and nothing else, so that you choose to boot from CD which will actually boot USB drive.

Sounds really good and looks fairly staight-forward except that I don't understand the very first bit =)

"One the installation has finished using the disc you must reboot into your new USB system"..... but you need Boot CD......."To build your own boot CD you will need to mount your system from within the Live CD. Once that is done it is time to add the needed modules to your initrd........"

Hmmmmm Your system? My system? Blood system? Don't get it. I thought I should just mount regular Live CD image to modified it and create a new one, but it doesn't seem to have referred files under referred locations. Then I thought you should install ubuntu somewhere, then boot from Live CD, access freshly installed ubuntu & modified to create boot CD but my pen drive didn't handly ubuntu installation.

Please help what am I suppose to do?

ps I wish I had external hard-drive to backup current mac installation; defragment&repair hard drive; partition and do tri-boot. Sounds so much easier now =(

---

### Post by Chrisj303 on 2007-05-13
A friend of mine at work has created a USB-Ubuntu stick, out of curiosity i tried it on my Macbook and it worked fine with 'rEFIt' - (i triple Boot).

I will ask him exactly how he did it next time i see him, and post back.

At the end of your post, you mention dual/triplebooting. If you can back up your data, and have the time & patience, then i would definitley recommend it - you won't regret it!


chrisj303

---

### Post by ronocdh on 2007-05-13
Dmitri, don't fret about messing your MBR on your MBP. The Mactels use GPT instead of MBR anyway, which is related to the EFI/BIOS difference, so altering the "MBR" (which essentially would mean *adding* one, if I understand it correctly) wouldn't hurt OS X in anyway.

Flubbing up your MBR on a triple boot system can be a pain though, because it's possible to install GRUB on the same MBR and boot Ubuntu and XP from it (this is what I'm doing). Still, OS X is safe in its ivory tower!

That said, thanks for promising us hope about the USB pen drive, Chrisj303. I would be more interested in a "portable" Ubuntu or something that I could run off the USB drive after the host computer has already fully booted its OS. (Very similar to the way [Portable Apps]("http://www.portableapps.com") work.) Nawmeen?

---

### Post by dmitrijledkov on 2007-05-13
Thank you very much =))))))

---

### Post by dmitrijledkov on 2007-05-13
I have tried rEFIt. You can either install it and override Mac's EFI or burn a cd and boot into rEFIt from CD without affecting Mac's EFI.

I did second option and showed up 3 boot options: Mac from HD, Linux from HD and Legacy Os from liveusb (Ubuntu? cause this is were i install it).

Tried 2nd and 3rd option both resulted in black screen, white blinkin bash and text: "Boot error"

=( even tried redo my USB stick and try again. didn't work =(

---

### Post by ktraglin on 2007-05-21
From what web page did you get these "Wiki instructions about BootFromUSB"?

---

### Post by ronocdh on 2007-05-21
> **ktraglin said:**
> From what web page did you get these "Wiki instructions about BootFromUSB"?
I wager [this was the guide]("https://help.ubuntu.com/community/BootFromUSB") OP was referring to. I googled for **ubuntu "bootfromusb"** and it was the first hit. ;)

---

