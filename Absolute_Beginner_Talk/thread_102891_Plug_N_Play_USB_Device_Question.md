---
title: "Plug N Play USB Device Question"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by nmatheis on 2005-12-13
Hello!

First post :)  New to Linux, used to Windows NT (home and work).  Decided to make the move at home to open source software in the past week - reformatted the HD on my fiancee's unused laptop and loaded Kubuntu.  Threw Mandriva 2006 Free Edition on a partition on my desktop box, as well for comparison.  I think I like Kubuntu better so far, though.  Pretty nice, although I definitely need to spend some time playing around!  

Anyhow, running Kubuntu on a Gateway Solo 1200 laptop (Celeron 800mHz, 13GB HD, USB 1.0).  When I plug in my iRiver IHP-120 dap through the USB port, I get an error message: "An error occured while loading **media:/sda1**: the file or folder media:sda1 does not exist".  But if I type **/media** into Konqueror, I the dap shows up there named **H100**.  I can access the files and copy them to HD if I want.  

Same drill with my Lacie 250GB external HD.

Problem is, since the two Plug N Play devices are showing up as media instead of as drives, there is no **Unmount** option when I right-click on them, making disconnecting more of a crap-shoot than I'd prefer.  With Mandriva on my desktop box, the two Plug N Play devices mount as drives and not as media, allowing me to unmount them.

So how do I get the devices to mount up as drives instead of as media?  Any help would be greatly appreciated!

Thanks!
Nikolaus

---

### Post by matthewv on 2005-12-13
Media and drives makes no difference: Different language for the same thing. You shouldn't have to unmount your drives, it should be managed automatically...

PS Welcome to the forums

---

### Post by nmatheis on 2005-12-13
[QUOTE=matthewv]Media and drives makes no difference: Different language for the same thing. You shouldn't have to unmount your drives, it should be managed automatically...

PS Welcome to the forums[/QUOTE]

Thanks for the quick reply!

So the **/media** directory that the Plug N Play devices show up in is the same directory that CDs and Floppies show up in.  CD & CD0 + Floppy & Floppy0.  Seems like when I plug the devices in, they should show up on the desktop or in the System/Storage Media folder - but instead I get the error message at plug-in time and have to browse to the folder, which I discovered by accident, actually.  Shouldn't it be a bit more intuitive?  Feels like something's wrong.

And I really don't need to Unmount the devices?  On the iRiver user forum, users indicate that you need to Eject the device (in Windows, of course) before unplugging it - the fear being that if you unplug while the device is writing to HD you might fizzle it up.  Is this somehow different in Linux?  I know I'd *feel* better if I could Unmount the drives!

Thanks!
Nikolaus

---

### Post by matthewv on 2005-12-13
I'm not too sure with about the iRiver. I've never had any trouble with flash disks and other usb devices. If you did need to eject it, it would be by right-clicking on the device (on your desktop or in Computer:///) and pressing unmount volume. 
Something is wrong, because whatever you plug in should show up in the Places --> Computer, and you should have no error message. Do you have the live cd?? Maybe you could try it on that, see what happens...

---

### Post by nmatheis on 2005-12-13
[QUOTE=matthewv]I'm not too sure with about the iRiver. I've never had any trouble with flash disks and other usb devices. If you did need to eject it, it would be by right-clicking on the device (on your desktop or in Computer:///) and pressing unmount volume. 
Something is wrong, because whatever you plug in should show up in the Places --> Computer, and you should have no error message. Do you have the live cd?? Maybe you could try it on that, see what happens...[/QUOTE]
no live cd - just the install .iso...  
other than that, i'm happy with what i've encountered so far.  i'd be happier if i could load it up onto my work box and have to live with it for awhile, though - for a little more fluency...

---

### Post by nmatheis on 2005-12-15
So, just to bump this up and see if I can get any more replies...

Running Kubuntu I get an error message whenever I use a Plug N Play USB device.  If I poke around, I can find the device in /media - but it doesn't show up as a mounted drive on my desktop but as a folder which I can't unmount before unplugging.

I've also tried Mandriva and Ubuntu, and both of those mount the USB Plug N Play devices as a drive.  The mounted drive shows up on my desktop, and I can unmount it before unplugging the device.

So, what gives that Kubuntu is giving me problems?  I've installed Kubuntu on two computers now and get the smae error.  Any advice would be appreciated.

Thanks!
Nikolaus

---

