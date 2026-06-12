---
title: "USB &amp; Floppy - UDI not mountable"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by Bartender on 2005-12-17
I just installed Ubuntu last night.  Gingerly poking at it to see what happens.  Floppy drive and my trusty old Simpletech CF/SM USB card reader are both inoperative.  In both cases I can see the devices in "Computer" but clicking on them gives me the "Unable to mount the selected volume" message.  Under "Show More Details" it says "given UDI is not a mountable volume".
Did a search on both of these issues and was bewildered by the advice - fstab this, pmount that....  Should I just accept that these aren't going to work until I learn a LOT more about Ubuntu?
If I go "Accessories>System Tools>Floppy Formatter" the drive formats a floppy.  I don't know how to prod at the card reader.

---

### Post by paulmilliken on 2005-12-18
[QUOTE=Bartender]I just installed Ubuntu last night.  Gingerly poking at it to see what happens.  Floppy drive and my trusty old Simpletech CF/SM USB card reader are both inoperative.  In both cases I can see the devices in "Computer" but clicking on them gives me the "Unable to mount the selected volume" message.  Under "Show More Details" it says "given UDI is not a mountable volume".
Did a search on both of these issues and was bewildered by the advice - fstab this, pmount that....  Should I just accept that these aren't going to work until I learn a LOT more about Ubuntu?
If I go "Accessories>System Tools>Floppy Formatter" the drive formats a floppy.  I don't know how to prod at the card reader.[/QUOTE]

Hi Bill,

It's the weekend here and I jumped online and saw your post.  Sounds like you got your disks and your install went OK - that's good.  To use a device in linux you normally have to mount it.  To mount your floppy, simply type "pmount /media/floppy" at the command line.  Then a floppy disk icon will appear on your screen.  Simple as that :)

The /etc/fstab file stands for "file-system table" and contains a list of all the storage devices on your system.  However, don't worry about messin' with that file as it should have been automatically (correctly) set up during your install.  In the old days that was all done manually of course.

When you want to remove your floppy disk from the computer you should unmount it by typing "pumount /media/floppy" (yes I did spell that correctly - there is no "n" in "pumount"). 

Regarding the card-reader, if it's a usb device then try plugging it in once your system is up-and-running to see if it is detected automatically by a daemon called "hotplug" (a relatively new feature in Linux).

Hope everything is going well.  Drop me a line to let me know how you're getting on.

Cheers,

Paul

---

### Post by Bartender on 2005-12-18
Hi, Paul - 
Good to hear from you!  Thanks for the guidance on floppy.  It worked.
Man am I lost.  O.K., tried jacking in the card reader after it was on.  The green "on" light comes on immediately.  Went to "Computer"; it took a few seconds for both USB devices (one device actually but two slots - CF & SM) to come up.  The two entries are "Datafab USB to CF+SM C" & "Datafab to CF+SM C (2)"
Under "Size" there is no data, "Type" says "Desktop configuration file", "Date modified" is "Unknown".  Double-click on either, I get the UDI error.
I discoverd how to change the left-hand column to Tree.  Under File System > media it shows cdrom, cdrom0, floppy, & floppy0.  Only have one of each device so don't understand second entry.  Should the USB card reader be showing up here?  
Took a WAG and hit Alt+F2, typed in "pmount /media/usb" and the command just disappeared, no error message, no laughing at me, nothing.

---

