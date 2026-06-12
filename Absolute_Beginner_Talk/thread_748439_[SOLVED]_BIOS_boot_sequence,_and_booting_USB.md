---
title: "[SOLVED] BIOS boot sequence, and booting USB"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-04-07
Hi,

I wasn't aware that I could boot from a USB.  Does the following mean that I can?

Boot device Priority
1st boot device [Removable Dev.]
2nd boot device [CD/DVD]
3rd boot device [Hard Drive]
4th boot device [Network: On board]

Thanks for your help.  Regards,

---

### Post by Sand Lee on 2008-04-07
most likely it does. Plug in a usb drive and look around the bios to see if its label appears anywhere.

---

### Post by backflip on 2008-04-07
You can boot in any order you like, BIOS will search through the list until it finds a bootable device. OS/Live CD etc..

---

### Post by Berean on 2008-04-07
Thanks Sand Lee and Backflip,

What I essentially would like to understand is whether [Removable Dev.] means a USB.  I don't actually have a OS upon a USB, so how would I go into the BIOS to see if it's recognised?  Regards,

---

### Post by Sand Lee on 2008-04-07
> **Sand Lee said:**
>  Plug in a usb drive and look around the bios to see if its label appears anywhere.

Though you have to reboot your computer first. Under the BIOS boot option, there's usually a dropdown/sub menu under Hard Drive or Removable Device; your FD label might appear here. There are other places as well, but it depends on your BIOS...

---

### Post by Berean on 2008-04-07
> **Sand Lee said:**
> Though you have to reboot your computer first. Under the BIOS boot option, there's usually a dropdown/sub menu under Hard Drive or Removable Device; your FD label might appear here. There are other places as well, but it depends on your BIOS...

Sand Lee,

I've put a 4GB flash drive in the USB, and restarted the system, entering the BIOS setup at the prompt.  It definitely says [Removable Dev.] but on the drop down it only enables me to change the sequence at start up.  However, coming out of the BIOS setup the system continued to boot, but straight to Ubuntu!  Is this because there's no executable program upon the flash drive?  Your advice is welcomed.  Regards,

---

### Post by metol on 2008-04-07
> **Berean said:**
> Sand Lee,

....  Is this because there's no executable program upon the flash drive?  

The flash drive is probably not properly setup to boot from, after that failed the BIOS just went to the next device in the boot sequence.

Check out [Pen Drive Linux]("http://www.pendrivelinux.com/").  It has many tutorials on setting up different operating systems on flash drives.  It is an excellent resource.

---

### Post by dondad on 2008-04-07
Try writing an ubuntu image to the usb drive, put it in ans see if it boots from it. That should tell you.spelling error

---

### Post by Berean on 2008-04-08
Thanks guys: yes, it does!  Yippee!

---

