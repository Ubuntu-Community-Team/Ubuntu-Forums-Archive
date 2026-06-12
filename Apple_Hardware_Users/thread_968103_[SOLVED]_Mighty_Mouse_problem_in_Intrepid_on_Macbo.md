---
title: "[SOLVED] Mighty Mouse problem in Intrepid on Macbook Pro 4,1 (Penryn)"
date: 2008-11-02
forum: Apple Hardware Users
---

### Post by hyperboloid on 2008-11-02
I did a fresh install of the release version of Ubuntu 8.10 (Intrepid) last week on my Macbook Pro 4,1 Penryn. Everything seems to be working pretty well now, except for the Mighty Mouse. Initially I got it to work by running ```
sudo hciconfig hci0 reset
``` from a terminal. After that it paired and worked great, but after a shutdown and reboot I cannot get it paired any more, and the above reset trick doesn't help. 

Has anyone else run into this? Any suggestions would be welcome.

---

### Post by hyperboloid on 2008-11-04
UPDATE: Through some experimentation, I found that if I right click on the Bluetooth icon and select Preferences (or System -> Bluetooth) and then delete my mouse from the list of known devices, I can then go through the whole setup procedure to re-pair the mouse, and that often works. 

It does not seem to be necessary to run "hciconfig hci0 reset" as I stated above, and I'm nut sure that command does anything. 

Seems like one needs to go through the whole process on every reboot: delete the mouse from the list of known devices, and then go through a new setup. This seems to be a new bug affecting many people using Bluetooth in Intrepid, see this thread: [http://ubuntuforums.org/showthread.php?t=964139]("http://ubuntuforums.org/showthread.php?t=964139")

---

### Post by cyberdork33 on 2008-11-04
They revamped the bluetooth stuff again for Intrepid and, of course, messed everything up that people had working in 8.04.

The hci reset is still needed on Macs, but I think that the HID2HCI tool does this correctly now so manual entry of the command you posted is not needed anymore.

You can find more info about what that does here:
[http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)

---

### Post by hyperboloid on 2008-11-06
> **cyberdork33 said:**
> They revamped the bluetooth stuff again for Intrepid and, of course, messed everything up that people had working in 8.04.

The hci reset is still needed on Macs, but I think that the HID2HCI tool does this correctly now so manual entry of the command you posted is not needed anymore.

That's good to know, thanks. It seems I have solved the issue, however, by following a workaround in this thread:  [http://ubuntuforums.org/showthread.php?t=966436]("http://ubuntuforums.org/showthread.php?t=966436").

The workaround is trivial. Simply open up Bluetooth Preferences (right-click on the BT icon, or use System -> Preferences -> Bluetooth), click on "Hidden" and then select "Always Visible". After that the mouse survives cold boots and suspend.

I'm marking this thread "solved".

---

