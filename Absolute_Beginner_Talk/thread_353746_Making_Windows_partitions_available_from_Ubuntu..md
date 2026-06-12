---
title: "Making Windows partitions available from Ubuntu."
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Mouleagaufres on 2007-02-05
I have problem making Windows partitions available from Ubuntu.

The Ubuntu 6.10 Desktop Guide states:

[I]“Windows partitions should be automatically available from any Ubuntu system. If they are not, you can make them available using the Disks Manager.
1. Open System&#61472;&#61614;&#61472;Administration&#61472;&#61614;&#61472;Disks .
2. Select the correct hard disk, and click Partitions.
3. Select the relevant partition, and click Enable.”[/I]

In my case, Windows partitions were not automatically available and there is no “disk manager” available from the “Administration” menu.

A lot of good advices are available in the forum using command line but the method as described in the Desktop Guide would be much more elegant for beginners like me. 

Did I miss something to make it work?

Thanks

---

### Post by gazzadtfan on 2007-02-05
Hi

I'm in a similar situation. Read the reviews of Ubuntu and thought I would give it a go.

Managed to get Ubuntu dual booting with XP but it doesn't "see" my XP partition. Like the previous writer, there is no 'Disk Manager' available through 'System / Administration'

I'm presuming that because it doesn't see that, then there is no way it will recognise my broadband modem in order to get online. It is frustrating to have to keep rebooting to back and forth between OS's to look up stuff online and then to reboot to go back to Ubuntu to see if it will work.

Can someone please help a rookie before I get completely frustrated?

---

### Post by MiCovran on 2007-02-05
> In my case, Windows partitions were not automatically available and there is no “disk manager” available from the “Administration” menu.
This guide was initially made for the 6.06, and there are still some leftovers. 6.10 doesn't make windows partitions automatically available and there is no disk manager in Administration menu. It confused me too.

> A lot of good advices are available in the forum using command line but the method as described in the Desktop Guide would be much more elegant for beginners like me.
Don't be afraid of the command line. It's a nice and fast way to do things. Once you prepare everything you will have your partitions available with just one simple command.

Try this: [https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29)
I advise you to use "Method 1". The only difference between 6.06 and 6.10 is that you won't be able to use "Step 5". Instead use ```
pmount hda5
``` in terminal or "Run Application" (Alt-F2) and your windows partition will be located in /media/hda5. Use your partition name instead of 'hda5'.
This will give you a read-only access to NTFS partitions. For read-write try some other how-to. I don't use read-write.

---

### Post by dgub on 2007-02-05
> **Mouleagaufres said:**
> I have problem making Windows partitions available from Ubuntu.

The Ubuntu 6.10 Desktop Guide states:

[I]&#8220;Windows partitions should be automatically available from any Ubuntu system. If they are not, you can make them available using the Disks Manager.

In my case, Windows partitions were not automatically available and there is no &#8220;disk manager&#8221; available from the &#8220;Administration&#8221; menu.

A lot of good advices are available in the forum using command line but the method as described in the Desktop Guide would be much more elegant for beginners like me. 

Did I miss something to make it work?

Thanks

I have just been through this problem. Everyone directs you to the command line and I really don't want to go back to that. Anyway someone posted me a link and through that found an automated way of doing it. No guarantees it will work with yours but maybe worth giving it a try

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

With me it reads FAT and NTFS.

---

### Post by Mouleagaufres on 2007-02-05
Thanks all of you for the quick reply. I tried the last one from “dgub” and it worked fine. It is a mystery to me why such an easy script is not implemented as a standard feature on the CD Rom. At the end of the day, most users install Linux on a system already running Windows and all of them will want access to their existing Windows files.

Thanks again,

Stéfane

---

### Post by bodhi.zazen on 2007-02-05
> **MiCovran said:**
> Instead use ```
pmount hda5
``` in terminal or "Run Application" (Alt-F2) and your windows partition will be located in /media/hda5. Use your partition name instead of 'hda5'.

1. pmount normally works for removable media. It works on internal HD only if you add the device to /etc/pmount.allow


2. For read-write access to ntfs see here:

[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

---

### Post by gazzadtfan on 2007-02-06
Thanks MiCovran. 

I followed your suggestions and now have my XP partition mounted and up and running. :) It is read only at the moment but I'll try and get read / write access later. 

Once you do a few terminals it isn't quite as scary, although a howto I read for getting my USB ADSL broadband up and running does look a bit of a challenge...for a newcomer that is!!

Thanks again for your help

gazzadtfan

---

