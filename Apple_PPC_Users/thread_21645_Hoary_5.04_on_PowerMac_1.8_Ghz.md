---
title: "Hoary 5.04 on PowerMac 1.8 Ghz"
date: 2005-03-23
forum: Apple PPC Users
---

### Post by wimds on 2005-03-23
I can't boot from the Hoary 5.04 cd... even with "C" or/and option +C will not help, what can i do boot from the installation cd of the Hoary 5.04? (from the live cd i can't boot also).

My system is a PowerMac 1.8 Ghz dual CPU 64bit, 1256MB ram, 250 GB sata, ATI 9600 128 MB, 20" Cinema display.

---

### Post by DJ_Max on 2005-03-23
Check your md5sums of both ISO images, be sure thet match the official md5sums ubuntu has.

---

### Post by wimds on 2005-03-23
How can i check md5sums?

Btw, i even can't boot from a original Unbuntu (Live) cd on my PowerMac, on my brother his iMac G5 it works perfect...

---

### Post by Brian McConnell on 2005-03-24
so if you're holding down the "C" key during boot, it still loads OSX instead of booting to cd? Will it boot to the OSX cd? I am running Hoary Array 6 on my dual 1.8ghz and used the install-power4 option and other than **SOUND STILL NOT WORKING** things are fine.


**FIX THE G5 SOUND ISSUE, ALREADY**

---

### Post by wimds on 2005-03-24
[QUOTE=Brian McConnell]so if you're holding down the "C" key during boot, it still loads OSX instead of booting to cd? Will it boot to the OSX cd? I am running Hoary Array 6 on my dual 1.8ghz and used the install-power4 option and other than **SOUND STILL NOT WORKING** things are fine.


**FIX THE G5 SOUND ISSUE, ALREADY**[/QUOTE]

My Mac still boot to OS X, i can not boot from the OS X vd also buth i can fix it in the configpanel to selcet a bootdevice.

What is "install-power4 option"?

---

### Post by DJ_Max on 2005-03-24
[QUOTE=wimds]My Mac still boot to OS X, i can not boot from the OS X vd also buth i can fix it in the configpanel to selcet a bootdevice.

What is "install-power4 option"?[/QUOTE]
 The install-power4 are for the orginal IBM PowerPC computers, and I believe for the G5, not sure. 

What sound manager are you using Brian? ESD? As you can see here, [http://ubuntuppc.webplazahosting.com/index.php?Ubuntu%20Linux%205.04%20%28Alpha%29%20iMac%20G3](http://ubuntuppc.webplazahosting.com/index.php?Ubuntu%20Linux%205.04%20%28Alpha%29%20iMac%20G3) I had an sound issue, but fixed it.

---

### Post by Brian McConnell on 2005-03-24
Well, I've tried selecting alsa, esd and oss. For alsa and OSS a pipeline is failed to construct. When I select esd and then choose test, it acts like it's working but no sound comes out. There are sound/mixer errors present during kernel boot and shutdown. It is my understanding that the linux kernel is not yey able to support the built in audio chips on G5's. Yellow-Dog 4 with either Gnome or KDE is also silent on the G5.

the install-power4 option is for g5 machines. But obviously you'll need to have been able to get the cd to boot first.

---

