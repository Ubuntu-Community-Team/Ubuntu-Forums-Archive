---
title: "When trying to write .iso file my USB drive will not recognize?"
date: 2013-12-07
forum: Any Other OS
---

### Post by savagetackle66 on 2013-12-07
I was using Unetbootin on Windows 7 to write the .iso for BackTrack5 r3 GNOME (debian based) onto a SD Cruzer 4 GB usb drive. This worked fine and the bootloader worked flawlessly I just ran out of memory after downloading one or two things.. obviously. Now that I have a good feel on how to use it I decided I wanted to upgrade to just a 16GB USB drive (SanDisk Cruzer Glide also) so that I could have a few applications. My PC recognizes the usb on drive E: and even brings up auto play. The USB drive came with two files that were both security files which I didnt open. I simply formatted the drive to FAT32 and did a quick format. When I enter Unetbootin everything is fine until I reach the section to specify the install location. you have two options (USB Drive & HDD) if you choose usb from the drop down menu you should see your drive E: in the drop down menu adjacent to it. Mine does not register any USB device. I have unplugged, replugged, reopened, reformatted and cant get Unetbootin to identify the flash drive although my PC does.
NEXT I download YUMI to make an ISO. YUMI does not recognize it as a USB drive either but YUMI allows you to see all drives, not just the rocognized. I choose drive e: which is simply titled "16GB" and I write the ISO file to the USB. Everything goes fine and I try to boot the USB. YUMI bootloader has one option upon starting "Continue to HDD" which skips the ISO and starts good ole windows again! :mad: Please help~! sorry about the length but I havent found a post to answer this specific question and I know you guys will want specifics on what actually happened

---

### Post by mips on 2013-12-09
What you could do is download dd for windows

1. Use dd to zero the usb stick
2. Write the image to the stick using dd.

**[COLOR=#ff0000]WARNING![/COLOR]: Incorrect usage of dd can lead to severe data loss if you specify wrong source & destination devices!**

---

