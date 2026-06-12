---
title: "New to Ubuntu."
date: 2009-11-21
forum: Apple Hardware Users
---

### Post by Tuesdays on 2009-11-21
[FONT="Arial Narrow"][SIZE="2"]Hey guys, basically I want to install Ubuntu on my Macbook, but don't know whether the drawbacks will be that hard to get-by. I'm new to Ubuntu and want to get used to it as fast as possible due to my annoyance with Microsoft and boredom with Apple.  

I will list the specs of my macbook, so would anybody care to tell me the problems I will have if I install Ubuntu such as no sound...

Version: 10.6.2
Processor: 2 GHz Intel Core 2 Duo
Memory: 2GB 667 MHz DDR2 SDRAM
Model Identifier: MacBook5,2

Any help would be greatly appreciated.

Tuesdays.[/SIZE][/FONT]
:KS

---

### Post by hal10000 on 2009-11-21
Just download the live-cd, burn the iso, boot it (without installing) and try it out.

---

### Post by Tuesdays on 2009-11-21
[FONT="Arial Narrow"]A little more help would be great as I have already done that and the Ubuntu installer doesn't load after selecting the "Install Ubuntu" option, it stays as a black screen.

Tuesdays.
:KS[/FONT]

---

### Post by h00ver on 2009-11-21
Wiki
----
[Mac Generic Installation Instructions]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")
[Enable all features on MacBook 5.2]("https://help.ubuntu.com/community/MacBook5-2/Karmic")

---

### Post by Tuesdays on 2009-11-22
I followed all of that and now im really stuck.
Basically i tried to install just Ubuntu and wipe out everything else, i partitioned it like it said and it installed fine, however when i now try and boot up it freezes after the grub bit, just after the flashing dash. When i try to boot up the live cd again it freezes at the first bit with the copyright text. And when i try and install leopard again it shows the circle with a line through it, can anyone help?

---

### Post by linuxopjemac on 2009-11-22
are you sure that your Mac is still ok ? It sounds like a hardware failure..CDROM still working properly ?

---

### Post by Tuesdays on 2009-11-22
Right, got the Leopard disk to work, just had to remove the battery and put it back in, which also solved the Ubuntu freezing at the first screen.
 
Is there anyway I can get Ubuntu to work without having to install Leopard again?

---

### Post by tom4everitt on 2009-11-22
Actually, dual booting a mac is usually easier than single booting it. Therefore I always create a 15-20 gb mac partition or so, and install linux on the rest. You can always set it to automatically boot into ubuntu, so os x won't bother you much but its good to have while setting it up (the reason for this is basically that macs are booted in a different way than standard pcs).

If you're fine with that, this guide is good:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Basically:
1. Install mac os x on a small partition, leave the rest of the space free (do the partition set up in disk util in the os x installer.
2. Install rEFIt in os x (without this it will be tricky to boot linux)
3. go ahead and install linux on the free space (install boot loader to hd0)
4. sync your partition tables with the refit partition thingie (whatever its called)
5. boot ubuntu

As said, the reason you have to do it this way is that macs are booted by efi, and not MBR which is the ancient but standard way to boot pcs. Therefore you have to install something such as refit that will take the computer from efi to linux. Soon enough this probably won't be necessary anymore, since the new linux boot loader grub 2 is in principle supporting efi boot. Setting this is up is still pretty tricky though, if you want you can google "grub2 efi" for more info. For now the rEFIt way is much easier!

---

### Post by tom4everitt on 2009-11-22
Also, make sure you get the refit menu every time you boot. If you don't, run the following the os x terminal:

sudo /efi/refit/enable.sh

---

### Post by Tuesdays on 2009-11-22
Thanks alot for that reply, it was actually very helpful for once lol.
I am currently re-installing Leopard onto my Macbook, and will try installing it that way.
Hopefully it will work so I can get back to University work ^^
 
:KS

---

### Post by Tuesdays on 2009-11-22
That didn't work :(
 
Are you sure this bit is correct?
"3. go ahead and install linux on the free space (install boot loader to hd0)"

---

