---
title: "Grub Wont uninstall? Windows won't boot!?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by battleroyalex on 2006-07-04
Ok so I decided I wanted to have a full linux pc and a full windows pc. So I deleted the linux partiton on one of my pcs.

now I get this error everytime I boot It up!
```
Boooting from local disk...
Grub loading stage1.5.

Grub loading, please wait...
Error 22
```

how do I get my windows bootloader back without formating :(

---

### Post by Jagot on 2006-07-04
Put in your Windows CD and get to the recovery console.  When you get to the command prompt type this:

```
fixmbr
```

Alternatively, download and burn the iso for the FreeDOS bootdisk:

[http://www.freedos.org/](http://www.freedos.org/)  

Put the disk in and reboot and work your way to the command prompt - it's fairly easy from the menu system.  Then at the prompt, type:

```
fdisk /mbr
```

---

### Post by Average_Joe on 2006-07-04
If you insert your WIndows installation CD and get to Recovery Console (key 'R') and find that you cannot remember your Administrator's Password (or, if you had never set an Admin Password), then it will be time for GAG Boot Manager, here:
[http://gag.sourceforge.net/download.html](http://gag.sourceforge.net/download.html)

---

### Post by battleroyalex on 2006-07-04
[QUOTE=Jagot]Put in your Windows CD and get to the recovery console.  When you get to the command prompt type this:

```
fixmbr
```

Alternatively, download and burn the iso for the FreeDOS bootdisk:

[http://www.freedos.org/](http://www.freedos.org/)  

Put the disk in and reboot and work your way to the command prompt - it's fairly easy from the menu system.  Then at the prompt, type:

```
fdisk /mbr
```[/QUOTE]

my pc doesn't have a floppy :cry:

---

### Post by Jagot on 2006-07-04
It's a CD boot disk - not floppy.

---

### Post by battleroyalex on 2006-07-04
i used my windows cd and  went to the system recovery console. I typed fixmbr and then fixboot

now I get the windows logo but after that a bluescreen flashes fast and the system restarts :cry:

---

### Post by Average_Joe on 2006-07-04
[QUOTE=battleroyalex]i used my windows cd and  went to the system recovery console. I typed fixmbr and then fixboot

now I get the windows logo but after that a bluescreen flashes fast and the system restarts :cry:[/QUOTE]

It doesn't sound good, but, you can try the GAG boot manager listed in my earlier post above.  It can usually boot into Windows even during these frustrating times.

By the way, you didn't happen to back up your MBR did you before all of the troubles?  That would be another way to get back in.

---

### Post by battleroyalex on 2006-07-04
[QUOTE=Average_Joe]It doesn't sound good, but, you can try the GAG boot manager listed in my earlier post above.  It can usually boot into Windows even during these frustrating times.

By the way, you didn't happen to back up your MBR did you before all of the troubles?  That would be another way to get back in.[/QUOTE]

i wouldn't even know how to do that

---

### Post by shoot2kill on 2006-07-04
using a different boot manager would onl do the same problem i think... :(

you could also use the windows disk and choose the second option to recover a previous installation, all of your files SHOULD still be ok if you hoose this,

hope this helps

---

### Post by Average_Joe on 2006-07-04
You would need to read the web page link that I inserted into my first post, above.

Short and dirty: Just burn the GAG boot manager .iso onto CD.
Pop in the CD, and reboot.
Follow the on-screen directions to get GAG to boot into your wayward Windows partition.

---

### Post by Jagot on 2006-07-04
If he's getting the Windows logo then there is no need for another bootloader.  The problem sounds like it's with Windows now, which won't be fixed by adding another bootloader.

---

### Post by mit on 2006-07-04
[QUOTE=Average_Joe]It doesn't sound good, but, you can try the GAG boot manager listed in my earlier post above.  It can usually boot into Windows even during these frustrating times.

By the way, you didn't happen to back up your MBR did you before all of the troubles?  That would be another way to get back in.[/QUOTE]

how do you back up the mbr with/without a linux partition?

thanks
mit

---

### Post by Average_Joe on 2006-07-04
mit --

Here are instructions for backup of mbr within Linux/GNU :
[http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd](http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd)

---

### Post by battleroyalex on 2006-07-04
ok this experience really angered me that linux wouldn't have support for such a thing like an uninstall option that safely uninstalls the OS. I decided to just go windows without linux. The linux gui is great, customizing things is great, but I honestly don't find it anymore stable than windows.

My laptop is really fast 2GB of ram with 2.0ghz P4M, Don't let numbers fool you its a PM. I never have problems with lockups on windows

In unbuntu I experinced a lockup witch I had to shut linux off. This killed my linux and I could not get my desktop back. It just doesn't seem worth the effort.

More bootloaders will not help me as it does bootload but gives me a bluescreen. It did warn me that fixing MBR could destroy the partiton. Im sure theres a way to get it back but I could retrive my files VIA downloading by the time I figured it out. So I reformatted clean.

---

### Post by catlett on 2006-07-04
>  battleroyalex  	ok this experience really angered me that linux wouldn't have support for such a thing like an uninstall option As opposed to the windows uninstall option?

---

### Post by battleroyalex on 2006-07-04
[QUOTE=catlett]As opposed to the windows uninstall option?[/QUOTE]
I knew someone would make that wise remark. Linux is a free OS and they know many users dual boot with linux. If they really cared about their users they would add one. But if you want to compare linux to windows and say linuxs has the same faults, by all means go ahead.

---

