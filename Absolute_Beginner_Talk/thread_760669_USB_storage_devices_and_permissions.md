---
title: "USB storage devices and permissions"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Sou Portugues on 2008-04-20
So whenever I plug in a usb device, the ownership by default is whatever user account that I am logged in as. If I switch accounts, the user still retains all ownership, and as I understand it the mount point, in their directory. The account that I log into however sees the device as a read only device, even if I log into the admin account.

Is there a way to make all usb devices have their default permission set to rwx for all users?

My thought on this is to create a dirctory that all users have acces to, I would then use that directory as the mount point for usb devices. I'm not sure where I should locate such a directory though.

Perhaps there is a better way of doing this? I am still a bit of a bumbling user.

Thanks in advance

ps- where is the spellcheck button for posting?

---

### Post by indiecast on 2008-04-20
i need to know this too...really badly

---

### Post by konungursvia on 2008-04-20
Just download a storage device configuration package, and make the usb drive a "shared" drive. Then all users can read and write to it. I wouldn't make shared mount points, it can be a security risk. Perceves?

---

### Post by indiecast on 2008-04-20
what does this program actually do to share your drives?  is this something that can easily be done with the command line?

---

### Post by sdennie on 2008-04-20
Plugged in usb devices should end up in /media.  It sounds like what you want to do can be accomplished by simply editing /etc/udev/rules.d/40-basic-permissions.rules and changing the umask for usb devices to something you prefer.  You may or may not have to restart udev before those rules start to work.

---

### Post by indiecast on 2008-04-20
sweet thanks!

i like how that works.  im geeky and love editing configuration files

---

### Post by ortizn on 2008-04-20
I had a similar question, I'm using an external hard drive that was formatted in vfat by windows.  I have no trouble accessing information on the drive, but the drive is owned by the root and does not allow write access.   I have tried to change the permissions with the terminal, but for some reason its not working.  Here's what I've been trying:

sudo chown [user] [directory]

a point in the right direction would be appreciated

Thanks

---

### Post by anewguy on 2008-04-21
VOR nailed it.  You can manipulate these permissions by the usb device id also.  If you lsusb, select the xxxx:xxxx id.  Then you can put entries similar to the following in.  I have included the title line and the default line for usb followed by 2 lines I use so I can universally access a couple of cameras that require libusb (and by default all the files where owned by root).

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0664"
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0dca", SYSFS{idProduct}=="0027", MODE="0666"
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="167b", SYSFS{idProduct}=="0101", MODE="0666"


:)

---

### Post by Sou Portugues on 2008-04-23
> **anewguy said:**
> If you lsusb, select the xxxx:xxxx id.

Here is the lsusb
Bus 005 Device 004: ID 04fc:0c15 Sunplus Technology Co., Ltd
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

> **anewguy said:**
> Then you can put entries similar to the following in....

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0664"
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0dca", SYSFS{idProduct}=="0027", MODE="0666"
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="167b", SYSFS{idProduct}=="0101", MODE="0666"

What the heck does all this mean? You lost me here, although I think what you are demonstrating is what I am trying to do.

thanks

---

