---
title: "dd command- USB -- is a directory?"
date: 2014-06-09
forum: Any Other OS
---

### Post by angusmak48 on 2014-06-09
im still learning to drive a terminal properly-- and rather irritated with Backtrack for switching over to debian as I was just getting the nack of using terminals properly and starting to focus on metasploit and other gadgets (as a hobby not for malicious use as I intend on studying online courses based on pentesting)-- but trying to do this has done my head in.

I understand that the USB drive is not located in the dev/sdb but in the media under the user directory as media/*user*/usb 

[B]
tyler@F*******:~/Desktop$ dd if=kali-linux-1.0.6-i386.iso of=/media/tyler/101 bs=512[/B]

 is the correct command as the iso is located on the Desktop- and the media location is specified as the correct location- the response in the terminal I am getting is:

[B]
dd: failed to open ‘/media/tyler/101’: Is a directory[/B]

I was thinking of using the force command but I am not sure if this would work- 

can anyone help on this?

---

### Post by rahul4557 on 2014-06-09
**you cannot use the location where the device/drive is mounted.**

If you using command "dd" you first have to **unmount** the media/usb and then use the right device ie. /dev/sd[that 1 letter of drive]

> sudo dd bs=4M if=[ur .iso file] of=/dev/sd[that 1 letter of drive]

---

### Post by Impavidus on 2014-06-09
The usb drive is located at /dev/sdb as a raw collection of bytes, the file system on the usb drive is located (mounted) at /media/*user*/usb as a structured system of directories and ordinary files. The dd command can copy bits from one named file to another named file, not to a directory. So you need a file name, not a directory. I think you're trying to make a live disk, in which case you have to copy the data as an image to the usb drive. Now, the drive itself is considered a file in Linux, so that means copying to /dev/sdb. And unmount it first.

Be careful, dd is a very powerful command. There are tools to do this safer.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by oldos2er on 2014-06-09
OP doesn't appear to be using Ubuntu; moved to Other OS/Distro Support.

---

