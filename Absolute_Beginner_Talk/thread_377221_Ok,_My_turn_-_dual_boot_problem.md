---
title: "Ok, My turn - dual boot problem"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Chopperman on 2007-03-05
I have had a very pleasant Ubuntu experience thus far. For a week now I have been running 6.10 32 and 64bit versions on a new hard drive on my HP DV9010us laptop. I had the windows HD pulled out while I got Ubuntu running and was waiting on the mountkit so I can have two drives (windows dedicated and linux dedicated)

Because I enjoy the media boot play features I understand I have to have the windows bootloader handle the OS selection. 

I followed (generally) the instructions at: [http://pervasivecomputing.net/ubuntu_edgy_on_dell_inspiron_e1505](http://pervasivecomputing.net/ubuntu_edgy_on_dell_inspiron_e1505)

Where I deviated was:

I booted to 32bit ubuntu and did the linux.bin creation as sudo in the terminal window.
I copied the 512k file to an SD card (linux and windows work well with the built in reader)

After copying linux.bin to the C: drive and adding the bootloader entry in Boot.ini, I do get the OS selection menu as expected, but when I select Linux, the screen blanks and I am left with a single flashing "_" in the upper left corner of the screen. The only input I can do is the three finger salute to reboot.  

When I examine the linux.bin file in notepad, it appears to be just whitespace, no random ascii like I would expect in a binary file. 

The article does mention booting to a command prompt using a disk called RPL which I am totally clueless about. 

SO - is booting with that disk necessary? or should the terminal window creation of linux.bin work? What should the linux.bin look like if I open it in a text editor to confirm that it is correct(er)?

Any thoughts are of course appreciated

Cheers
Chop

---

### Post by martinw89 on 2007-03-25
Hi Chopperman,
I myself have an HP DV6000t which also has QuickPlay.  I got rid of QuickPlay but I think I may be able to help you.

I'm very confused about what you did.  The guide specifies that you install Ubuntu using the Alternate installation CD, and that you do this so you can install Ubuntu with GRUB on it root partition, not the MBR.  But you mentioned that you tried those commands in your Ubuntu installation (I hope I an correct in this).

The following section boots you into your Ubuntu installation:
```
root (hd0,X)
kernel /boot/vmlinuz-2.6.17.10-generic root=/dev/sdaY ro quiet
initrd /boot/initrd-2.6.17-10-generic
boot
```These are run on a disc because they are what boots your Ubuntu installation.  So, if you were already in it, you would not have had to run these.

There are a lot of deviations here based on what you did in your installation, so tell me if you used a normal Desktop disk or you installed using an Alternate disk and installed GRUB on the root partition.  I can help you get quickplay back on your Windows boot loader if you used GRUB.  Also, just a quick check, both Windows and Ubuntu are available upon boot, right?

-Martin

---

