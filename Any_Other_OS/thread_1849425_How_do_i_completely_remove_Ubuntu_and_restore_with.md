---
title: "How do i completely remove Ubuntu and restore with Windows 7?"
date: 2011-09-24
forum: Any Other OS
---

### Post by RichLovell1989 on 2011-09-24
So i done a full installation of ubuntu, its been good but i want to go back to windows 7 but i cant find out how to remove my full Ubuntu installation to restore using my Windows 7 Op system disc... help?

---

### Post by Crempel on 2011-09-24
How about asking this question in a windows forum?:lolflag:

---

### Post by Elfy on 2011-09-24
If you have a restore disc I'd assume you can boot with it and do so.

If you just have install discs AND no windows currently installed - boot a partition editor - remove the ubuntu and then reinstall windows. 

If you have windows then I'd use it to remove the linux partitions. 

moving to other o/s

---

### Post by haqking on 2011-09-24
> **RichLovell1989 said:**
> So i done a full installation of ubuntu, its been good but i want to go back to windows 7 but i cant find out how to remove my full Ubuntu installation to restore using my Windows 7 Op system disc... help?



depending on your system you may have a restore option from the hidden partition ?

What machine is it ?

try pressing f8 on boot to see if you get that option.

If not then boot to your windows disc and hey presto wipe ubuntu and your back to windows

---

### Post by JSchultheis on 2011-09-24
> **RichLovell1989 said:**
> So i done a full installation of ubuntu, its been good but i want to go back to windows 7 but i cant find out how to remove my full Ubuntu installation to restore using my Windows 7 Op system disc... help?

Seems that simply putting the disk in and restarting the machine, adjusting bios to boot from CD, then selecting fresh install, delete all partions. 
Of course, that will mean losing all data. And you'll likely need the install key as well. 


If the Ubuntu is on its own partition, you can just delete that partition. But use caution here because changing partitions can cause loss in data.

---

### Post by nthekkethil on 2011-09-24
When i was uninstalling ubuntu from my friends pc I booted into windows, deleted all the ubuntu partitions, then rebooted with the windows vista cd in and it repaired the windows bootloader. After that, i just went to windows and reclaimed the space the ubuntu partitions were taking. He had vista but it should work for 7 too but back up your files just in case.

---

### Post by RichLovell1989 on 2011-09-24
> **forestpiskie said:**
> If you have a restore disc I'd assume you can boot with it and do so.

If you just have install discs AND no windows currently installed - boot a partition editor - remove the ubuntu and then reinstall windows. 

If you have windows then I'd use it to remove the linux partitions. 

moving to other o/s

what do i do to "boot a partition editor"?

---

### Post by Elfy on 2011-09-24
From what I've read there's not one on the win7 discs - whether that's the case I have absolutely no idea, never having seen one. 

There's one on the livecd you installed from.

---

### Post by Elfy on 2011-09-24
From what I've read there's not one on the win7 discs - whether that's the case I have absolutely no idea, never having seen one. 

There's one on the livecd you installed from.

---

### Post by RichLovell1989 on 2011-09-24
You say to remove ubuntu.. that exactly what i cant see how to do...

I have a Dell Inspiron 15R, i boot from disc after tapping F12 and it runs the windows 7 operating disc, but i cannot find any options to remove anything...

---

### Post by Elfy on 2011-09-24
I have as I've no idea how to use a windows disc - this is a linux forum :)

If you can't see how to do it with a windows disc - use the ubuntu one to delete the partition editor from there to remove the partitions. 

If that doesn't help you'll have to wait to see if someone else has the info you need, if not search for it on google or something.

---

### Post by haqking on 2011-09-24
> **RichLovell1989 said:**
> You say to remove ubuntu.. that exactly what i cant see how to do...

I have a Dell Inspiron 15R, i boot from disc after tapping F12 and it runs the windows 7 operating disc, but i cannot find any options to remove anything...

F8 or Ctrl+F11

when you see the dell logo and you should get the option to do a system recovery to factory default, however if at some time you got rid of the recovery partition then it wont work.

Other than that use a Ubuntu Disc and use the partition editor to wipe your partitions and then reboot to the windows disc.

or use a gparted boot disc to do the same.


or just boot to your windows disc

see here [http://www.techtalkz.com/windows-7/514412-windows-7-installation-guide-tutorial.html](http://www.techtalkz.com/windows-7/514412-windows-7-installation-guide-tutorial.html)

a little ways down you will see the partition menu where you can wipe the drives, though it may not see the ext3 or ext4 partitions etc.

However windows usually likes to take complete control of everything ;-)

---

