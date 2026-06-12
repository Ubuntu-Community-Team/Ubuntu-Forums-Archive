---
title: "how to un-eject ipod (get comp to mount ipod without manually re-connecting iPod)"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-07-03
Hi. 
When I plug in my iPod to the computer, Ubuntu is able to automatically mount it. And an Ipod icon appears on my desktop. For a few reasons, I sometimes have to do [Right click iPod icon -> Eject]. How can I "un-eject"? I want to be able to see the iPod icon again. I want the computer to be able to "re-connect" with the iPod again.

I know one way of accomplishing my goal: by physically disconnecting the USB cable from computer and then reconnecting. But I want to reconnect without doing so. Please advise.

Thank you.

---

### Post by PaulFr on 2007-07-03
I was able to get partial success - if your ipod was mounted on /dev/sda1 (for example), then you can mount it again using ```
pmount-hal /dev/sda1
```.

However, this command gives some error regarding > libhal-storage.c 1401 : INFO: called LIBHAL_FREE_DBUS_ERROR but dbusError was not set.
process 1912: Applications must not close shared connections - see dbus_connection_close() docs. This is a bug in the application. which I cannot decipher. Still the device is mounted properly and you can see it in Places menu.

Please note that you cannot unmount such a volume from the GUI - it gives you an error indicating that it was probably mounted manually. You have to ```
pumount /dev/sda1
``` to unmount the device. Hope this helps.

---

### Post by rfurman24 on 2007-07-03
I may be wrong and I am not at home to check, but I am pretty sure that the Ipod stays in places-computer as long as it is plugged in and can be mounted or unmounted with a right click.

---

### Post by hanzj on 2007-07-03
rfurman24,
Yes, I see iPod ("Apple iPod Music Player") in places/computer (computer:///), but when I right-click the icon and select "Mount Volume", I get a window that says:
> 
Unable to mount media.
There is probably no media in the drive.

---

### Post by hanzj on 2007-07-03
How can I tell where my iPod is mounted?

---

### Post by hanzj on 2007-07-03
Whether I do [Eject] or [Unmount], it seems that I cannot mount the iPod again without physically unplugging and re-plugging iPod to computer.

---

### Post by hanzj on 2007-07-05
bump.

---

### Post by PaulFr on 2007-07-05
1. To see where your IPOD is mounted, open a terminal (in Applications -> Accessories menu), and type the command```
mount
``` This will tell you all the filesystems mounted including your IPOD. Typically your IPOD will be mounted in /media/xxx. The device that was actually mounted will be the _first column of that line (something like /dev/xxx)_.

2. When you umount / eject the IPOD, agaiin run the **mount** command. You should see one line missing - that will be your IPOD line.

3. So my suggestion is enter the command ```
pmount-hal /dev/xxx
``` in the terminal where /dev/xxx is the device you found in step 1.

If that succeeds, you can use the Places menu to navigate to the IPOD. When you want to unmount the device again, please enter the command ```
pumount /dev/xxx
``` in the terminal. Hope this helps.

---

### Post by hanzj on 2007-07-05
Thanks for your input, Paul.
1. Output of "mount":
> /dev/sdb2 on /media/HANNY SMITH type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
2. So from that, I gather that the device is /dev/sdb2
3. I try 
```
 pmount-hal /dev/sdb2
```But I get 
> Error: given UDI is not a mountable volume

---

### Post by PaulFr on 2007-07-05
1. Try **pmount /dev/sdb2** instead of **pmount-hal /dev/sdb2** and see if it mounts.

2. Can you post the contents of the **/etc/fstab** file ? Type the following in the terminal```
cat /etc/fstab
``` and select the output and right click -> Copy, then paste it in your reply.

---

### Post by hanzj on 2007-07-05
1.
After I eject/unmount iPod
> $ pmount /dev/sdb2 
Error: device /dev/sdb2 does not exist
2.

cat /etc/fstab when my iPod is ejected (By ejected, I mean Right-Clicking on iPod icon on Desktop or nautilus, and then selecting "Eject")
> $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9d52bce6-e001-4423-a8e8-8afcccadd568 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8ae488db-4213-4f85-9410-dc835e6d9163 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
When my iPod is plugged in and auto-mounted
> $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9d52bce6-e001-4423-a8e8-8afcccadd568 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8ae488db-4213-4f85-9410-dc835e6d9163 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

The printouts for cat /etc/fstab when iPod is ejected is the same as when iPod is auto-mounted.

---

### Post by PaulFr on 2007-07-05
The command I gave was for mounting only. Can you try to unmount the IPOD and then try my suggested commands ?

To handle eject, there may be two additional steps : 1. the module may be unloaded from kernel, 2. hald needs to rescan for the device. I am looking at that.

**Update: This seems to be problematic, as the device needs to be reintroduced - short of restarting, I do not know how to rescan - anyone ?**

---

### Post by hanzj on 2007-08-31
In Terminal,
The 2 commands:
> pmount /dev/sdb2and 
> pumount /dev/sdb2work for me.

However, when I do the pumount command, yes, it disappears from the nauitlus view, but I'm still unable to use my iPod while connected to the USB cable.  So I'm still stuck.

---

### Post by simonn on 2007-09-20
Better late than never?

> **hanzj said:**
> Hi. 
When I plug in my iPod to the computer, Ubuntu is able to automatically mount it. And an Ipod icon appears on my desktop. For a few reasons, I sometimes have to do [Right click iPod icon -> Eject]. How can I "un-eject"? I want to be able to see the iPod icon again. I want the computer to be able to "re-connect" with the iPod again.

I have just spent a load of time on this (with my HFS+ formatted 8Gb Nano) and...

The iPod has three states:

1) Ejected - this is when you see the menu, i.e. the "do not disconnect message" is not displayed. In this state the iPod both can be and may as well be considered to be physically disconnected from the PC*. There is nothing you can do to "un-eject" it other than re-plug it.

2) Unmounted - iPod is unmounted (as expected) and can be mounted on demand.  "Do not disconnect message" is displayed. 

3) Mounted - iPod is mounted (as expected) and files can be accessed (well... duh!).  "Do not disconnect message" is displayed. 

*to prove this compare the output of lshal when the ipod is in state 1  and when it is in states 2 and 3. You will notice that only /dev/sd? is available for state 1 while /dev/sd?, /dev/sd?1, /dev/sd?2 and /dev/sd?3 are available for states 2 and 3. NOTE: fat formatted iPods only have /dev/sd?, /dev/sd?1 & /dev/sd?2. HFS+ iPods also have  /dev/sd?3 (which contains all the data).

> I know one way of accomplishing my goal: by physically disconnecting the USB cable from computer and then reconnecting. But I want to reconnect without doing so. Please advise.

This is the only way. However, I consider this a good thing. If it is ejected, it **is** ejected and cannot be un-ejected accidentally if left in an ejected state. This means that there is slightly less chance of corrupting it by unplugging while it is not ejected.

---

### Post by hanzj on 2007-09-21
Yes, Simonn,
Better late than never! Much better, in fact!

Thanks to the ability to subscribe to a post.

---

### Post by asmoore82 on 2007-09-21
Yes there is a much larger issue here with the Gnome UI ...
If you have Ubuntu set to "not mount drives when hot-plugged"
you get a bogus error message when you try to "eject" them
even though "unmounting," what you really wanted to do, was successful.

I understand that we are trying to make the "eject" concept more user friendly,
but we've just got to face the facts that "unmount" and "eject" are 2 separate
operations and while "ejecting" always implies "unmount," it doesn't work
the other way 'round. IMO, "unmount" **and** "eject" need to **both** be
in the right-click menu on all removable drives and media so that those who
know the difference can pick what they need. This is a prime example of the
all too common trend where "user friendly" is synonymous with the
root of all design/engineering/programming evil, "ambiguity."

---

### Post by simonn on 2007-09-21
If a device requires ejecting or not can be queried using HAL. The CVS/SVN version Thunar (XFCE's filemanager) uses this to determine whether a device should be unmounted or ejected (a suggestiong from me due to ipods not having an eject option only unmount). IMHO this is what should be done, much simpler and works very will in OSX (and windows for that matter!).

---

### Post by asmoore82 on 2007-09-21
> **simonn said:**
> If a device requires ejecting or not can be queried using HAL. The CVS/SVN version Thunar (XFCE's filemanager) uses this to determine whether a device should be unmounted or ejected (a suggestiong from me due to ipods not having an eject option only unmount). IMHO this is what should be done, much simpler and works very will in OSX (and windows for that matter!).

I feel essentially the same "loss of ease of use" in OSX as well;
when I drag a firewire drive to the trashcan and eject it, the only
easy way to re-attach it seems to be physically re-plugging it.

---

### Post by locutus42 on 2007-10-06
I'm doing some development on a USB device and have the same problem of "resetting" the device with a physical disconnect/connect operation. I'm thinking of a somewhat simpler solution and that's to put a momentary switch on the power line of a short cable.

What would be much better is a way to programatically shut off that USB port power and then turn it back on. I'm still looking for this solution before the hardware hacking.

And I'm very surprised that OSX requires physical resetting for firewire. Do you know if OSX requires the same for USB?

I'll post back as to what I end up doing.

---

### Post by hanzj on 2007-10-06
Locutus42,
I don't know about OSX (I don't have the funds for a Mac 8-)  ).

Yes, please keep us updated on your experiment!

From the OP.

---

