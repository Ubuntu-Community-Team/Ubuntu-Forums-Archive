---
title: "USB Issue in VirtualBox"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by dodgerwv on 2007-06-21
This is probably a pretty simple permissions issue, but this newbie is lost while trying to use a USB in Virtual Box.  

I get the following:  Not permitted to open the USB device.  check usbfs options.

I'd appreciate some help on a workaround and many thanks in advance.

---

### Post by felicity on 2007-06-22
I found this on the VirtualBox website:

Setting up USB on Ubuntu 7.04 ¶

Contributed by Ibrahim Ben Faruhn, 2007/06/14

After I had a taken a look into the insides of Ubuntu 7.04, I managed to get VirtualBox's USB-Support working there in such a way that the user only needs to be a member of a group called usbusers. This howto describes how I did it.

Basically, you just have to tell Ubuntu that a group called usbusers should have read and write access to all usb devices.

1. Create a group called usbusers

2. Add yourself to this group

3. Edit the file /etc/udev/rules.d/40-permissions.rules (for this, you must have administrative privileges)

    3.1 Search for the following lines

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb_device",                    MODE="0664"

    3.2 Change them to the following

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb_device", GROUP="usbusers", MODE="0664"

4. Restart your PC

5. You should now have write access to all usb devices.

Also under the FAQ it says: 
If USB doesn't work, check your usbfs permissions. See "Troubleshooting" -> "Linux hosts" in the User Manual for a solution.

---

### Post by Cam1223 on 2007-06-23
can someone tell me why no one seems to want to  do 
```
sudo VirtualBox
```

is there something wrong with doing this?? i have seen a bunch of permission problems with virtualbox but why dont people jus run it as root?

must be some security thing i know nothing about....

---

### Post by redunbar on 2008-02-24
I see a lot of people having trouble with accessing USB drives in virtualBox, but it is really easy, and if you do it the easy way, it will work even with the OSE version of VBox.  All you have to do is use the shared folder feature of virtualBox.  This is what  you do for a virtual XP in a Ubuntu host.

1.  Make sure that the Guest Additions are installed.  To do this, start your virtual XP system, then select Devices > Install Guest Additions.  Sometimes it's a little slow, and sometimes it ignores you, but be patient or try it again if nothing happens.  Once it's installed, then...

2. Set up a shared folder.  You don't have to make a special folder for this in Ubuntu, you can use any existing folder, including a mounted USB drive.  And you don't need to use ANY command line instructions to do it.  In your virtual XP or W2K window, select Devices > Shared Folders.  This will bring up the Shared Folders dialog box.  Click on the Add A New Shared Folder button, which is in the upper right corner of the dialog box, with a + symbol on it.  This will bring up the Add Share dialog box.  In the Folder Path field, enter the Ubuntu path of the folder you want to share, for example: /media/USBdrive (if you have a USB drive mounted in Ubuntu as /media/USBdrive) or whatever the path to the folder is.  In the Folder Name field, put in whatever name you want to use for the share in Windows.  This name doesn't have to match the Ubuntu folder name.  Once these fields are filled in, click on OK to exit the Add Share box, click on OK to exit the Shared Folders box, and your shared folder is set up.  Now, to access the shared folder in Windows...

3.  Find My Network Places, either on the Windows desktop if you put it there, or in the Start menu.  Right click on it and select Map Network Drive from the menu that comes up.  This will bring up the Map Network Drive dialog box, which contains a Drive field and a Folder field.  The Drive field will have a suggested drive letter already entered, but if you don't like it, you can change it.  The Folder field will be blank.  You can either enter the shared folder name directly in it, for example \\VBOXSVR\FolderName (where FolderName is the same name you used in the Folder Name field in step 2, or you can use the browse option to select your folder.  You will find your shared folder in the VirtualBox Shared Folders folder.  The browse interface is a little slow and flakey on my system, so you have to select the one you want, then select something else, then select the one you want again before you can click on OK to get back to the Map Network Drive box.  Once your folder is selected, check the Reconnect at logon box unless you want to do step 3 every time you bring up Windows.  Then click on OK, and your shared folder/drive is set up.  Go to My Computer and you will see it as a network drive which you can use like any other drive or folder.

---

