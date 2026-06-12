---
title: "What did i do wrong?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Confusedalot on 2007-06-12
I install ubuntu normally yesterday, but my hard drive already had 4 partitions. so i deleted a very small, and seemingly empty partition. I reasized the XP partition and made a new extended partition containing the linux and swap parts. now ubuntu is working fine but when i try to boot windows it says "cannot boot windows file hal.dll not found. but when i used linux to acess the windows files i found hal.dll in the right spot. What did I do?

---

### Post by Crafty Kisses on 2007-06-12
You possibly could of corrupted the file. Just a guess.

---

### Post by haricharan on 2007-06-12
Nothing to panic..try this...
[http://www.informationweek.com/story/showArticle.jhtml?articleID=185301251](http://www.informationweek.com/story/showArticle.jhtml?articleID=185301251)

---

### Post by Confusedalot on 2007-06-12
the only problem with that is i didnt get an xp cd with my computer...

---

### Post by mijj on 2007-06-12
> **Confusedalot said:**
> I install ubuntu normally yesterday, but my hard drive already had 4 partitions. so i deleted a very small, and seemingly empty partition. I reasized the XP partition and made a new extended partition containing the linux and swap parts. now ubuntu is working fine but when i try to boot windows it says "cannot boot windows file hal.dll not found. but when i used linux to acess the windows files i found hal.dll in the right spot. What did I do?

I've seen this a couple of times in the past.

from what i remember .. it's because windows is confused about which partition it's booting up into.

You should check the C:/boot.ini file in the windows partition, and check that the windows partition is where the boot.ini thinks it should be (if you see what i mean).

I ent no expert .. but i think the problem is along those lines.

oh .. i guess this will definitely be true if the partition you delted was before the xp partition.  ... so you need to edit the boot.ini file to point to the correct partition.

---

### Post by bone43 on 2007-06-12
> **Confusedalot said:**
> the only problem with that is i didnt get an xp cd with my computer...

The very small, and seemingly empty partition may have been your backup partion from the manufature?

 Do you have a restore cd? if so maybe try and boot to it and see what it say?

Im guessing here but my laptop had a partion for restore and no MS disk but since i didnt want ms i just wiped it.

---

### Post by bone43 on 2007-06-12
Here is a little more on the recovery partion..

[http://en.wikipedia.org/wiki/Recovery_partition](http://en.wikipedia.org/wiki/Recovery_partition)

Hopfully thats not what you deleted when you resized?

---

### Post by Confusedalot on 2007-06-12
alright. i think i figured it out. in the boot.ini file it says at two parts, rdisk(0)partition(2) well it used to be the 2bd one but now its first.only problem is it's read only do I cant change it.

---

### Post by mijj on 2007-06-12
if your C:/boot.ini contains the following...
```
[boot loader]
;timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
```

if you deleted a partition before xp partition, edit C:/boot.ini partition(2) with partition(1) as follows ...
```
[boot loader]
;timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
```

---

### Post by mijj on 2007-06-12
oh .. you can edit the file while in Ubuntu ...

... you need .. erm ... ntfsconfig .. (i think it's called) ...

... hang on a sec ... i'll check.

---

### Post by ugm6hr on 2007-06-12
> **Confusedalot said:**
> alright. i think i figured it out. in the boot.ini file it says at two parts, rdisk(0)partition(2) well it used to be the 2bd one but now its first.only problem is it's read only do I cant change it.

Try:
```
gksudo nautilus
```

Find boot.ini and open with gedit - then you should be able to edit and resave (probably best to save a copy first).

---

### Post by Confusedalot on 2007-06-12
okay but i cant save it. will it work the same if i make a new boot.ini file with that change?

---

### Post by mijj on 2007-06-12
yes ... install [COLOR="Navy"]**ntfs-config**[/COLOR] into Ubuntu (via synaptic).

this will allow you read/write access to all ntfs partitions inclucing the xp partition.

:)

(i think, if you dont isntall ntfs-3g (via ntfs-config) you only have read access to ntfs partition files)

---

### Post by skymera on 2007-06-12
> **Confusedalot said:**
> the only problem with that is i didnt get an xp cd with my computer...

u didnt? how weird.
hmmm, tthat small partition, i have a small 49mb one on my Dell.
from Dell. small and useless. i think.
butt i kept it!

hopefully u can sort it out? or find a copy of XP.
*eBay*

---

### Post by Confusedalot on 2007-06-12
im in the synaptics pakage manager i cant find ntfs config. the huge problem is i just did this yesterday and my wireless card isnt working

---

### Post by skymera on 2007-06-12
search for NTFS.
or go add/remove

its definarely there!!!
read the description too

---

### Post by mijj on 2007-06-12
it's ntfs-config with the  "-" .. it's there ... honest.  I'm not making it up!  You can trust me.

:)

---

### Post by ugm6hr on 2007-06-12
> **Confusedalot said:**
> im in the synaptics pakage manager i cant find ntfs config. the huge problem is i just did this yesterday and my wireless card isnt working
In Synaptic (install ntfs-3g and ntfs-config), reboot, then Applications -> System -> NTFS Configuration Tool. Follow the instructions and voila.

Unfortunately, if your Ubuntu box isn't connected to the internet, this is not going to be easy.  In fact, if you don't have internet access from any computer, I'm not sure how it can be done.  If you do - you might be able to download all the components manually from:
[http://packages.ubuntu.com/feisty/admin/ntfs-config](http://packages.ubuntu.com/feisty/admin/ntfs-config)
But you will have to download each package that it depends on too (that isn't installed as default on Ubuntu).

---

### Post by Confusedalot on 2007-06-12
well i'll keep trying to get online... if that doesent work oh well but I do have internet on to seperate computers

---

### Post by mijj on 2007-06-12
.. or .. temporarily .. you could create a small  empty partition before xp partition just so's xp boots up.

Then, once you're in XP, edit the boot.ini bits from partition(2) to partition(1) ... 

and then ... come out of XP and delete the temp partition you created before XP.

XP will then boot up with boot.ini looking for Windows in the first partition.

:)

---

### Post by Confusedalot on 2007-06-12
that wouldent work. i have all 4 partitions full

---

### Post by mijj on 2007-06-12
oh ... looks like you'll need ntfs-config and edit boot.ini from Ubuntu.

do you know if ntfs-config is available on the ubuntu install disk?  ... if it's there, then you can edit the boot.ini from the Ubutnu install disk.

---

### Post by Confusedalot on 2007-06-12
okay. is it possible to download ntfs config to a windows computer, and put it on the linux with a cd, or jumpdrive?

---

### Post by Confusedalot on 2007-06-12
grrrr.... i put a partition before the xp partition, making the boot.ini file true, and it still isnt working!! i dont know what to do!

---

### Post by bone43 on 2007-06-12
> **Confusedalot said:**
> I install ubuntu normally yesterday, but my hard drive already had 4 partitions. so i deleted a very small, and seemingly empty partition. I reasized the XP partition and made a new extended partition containing the linux and swap parts. now ubuntu is working fine but when i try to boot windows it says "cannot boot windows file hal.dll not found. but when i used linux to acess the windows files i found hal.dll in the right spot. What did I do?


Do you still have Ubuntu working?

---

### Post by Confusedalot on 2007-06-12
yep ubuntu's fine, but i cant get internet on it

---

### Post by bone43 on 2007-06-12
> **Confusedalot said:**
> yep ubuntu's fine, but i cant get internet on it

You spoke of wireless do you have any way to hook up to a nic card maybe by moving your box to another room?

---

### Post by Confusedalot on 2007-06-12
well i can hook it to the wall from my cable modem, and it still wont work... ubuntu is hard:(

---

### Post by mijj on 2007-06-12
can you put a copy of what exactly is in the boot.ini file here? ... and confirm that the xp partition is now the second partition.

---

### Post by Confusedalot on 2007-06-12
okay boot.ini...

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home
Edition" /noexecute=optin /fastdetect

```
And yes, there's a partition in front of the windows partition, but it is only a verysmall, ext3 47 MiB partiton.
P.S. how do I get to Gparted without booting from the CD

---

### Post by Confusedalot on 2007-06-13
hello?

---

### Post by ugm6hr on 2007-06-13
I am not 100% certain about this, but I suspect the new partition you created may be physically *before* Windows on the HD, but it will pronanly be *labelled* as after (since it was created after.  That might be why that doesn't work.

Best option - try and get the Ethernet working to get online with Ubuntu (and then install ntfs-config).  Do the following:
Plug in Ethernet to cable modem.
Turn off computer, and then turn on with cable plugged in.
(Try internet to see if it works)

If not - in Terminal:
```
lspci
```
You are looking for the "Ethernet" or possibly "Network Controller" output
```
ifconfig
```

And post the results here.  Ubuntu is (almost) 100% compatible with ethernet cards, so, provided all the hardware works, it must be possible to get you back online.

PS: Are you using Feisty/Ubuntu7.04?
PPS: If this is not possible - my previous post had a link to download ntfs-config, but you will have to download al dependencies and transfer to your Ubuntu machine to install, but I haven't done this, and occasionally it is actually not possible.  Unfortunately, there is no way to know without trying.

---

### Post by mijj on 2007-06-13
> Confusedalot:  	hello?
... sorry ... paused for sleep.

So ... anyway ... how are you enjoying your Ubuntu adventure so far?  :)
(I dont think you can really blame this on Ubuntu .. it's a general boot manager thing that's designed to confuse everyone on any kind of system.)

... there's another layer of complexity i forgot about ...

.. you're not simply booting into XP directly .. XP booting is started after you've selected that option from the Ubuntu boot menu.

I *think* XP would boot properly if it booted directly into XP without going through Ubuntu's (grub) boot manager first. (because i think the ordering's gone askew as seen by the grub boot manager).

*<ponders the situation>*

However, the way that Ubuntu sees the ordering of partitions is different to the way XP sees the ordering of partitions.   As i understand it (and i wouldnt be suprised if i'm wrong) XP refers to the order in teh way you'd expect it ... i.e. in the order the partitions are placed on the disk.
Ubunutu, however, sees the partitions refers to the order in which they were created.  Just to make things interesting, Ubuntu also has an option of refering to the partitions by a unique identifier.

I suspect you may have to start fiddling round iwht the /grub/boot/menu.lst file.   (Ubuntu's more complicated equivalent of boot.ini)

*<ponders more>*

---

### Post by Confusedalot on 2007-06-13
okay. i'll try and get that icocfig and stuff. i have to find another ethernet cord. (i cant disconnect the router my family will get mad)

---

### Post by Confusedalot on 2007-06-13
okay here is iconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:15:C5:24:27:C4  
          inet6 addr: fe80::215:c5ff:fe24:27c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104749 (102.2 KiB)  TX bytes:5912 (5.7 KiB)
          Interrupt:22 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:24:27:C4  
          inet addr:169.254.6.124  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13896 (13.5 KiB)  TX bytes:13896 (13.5 KiB)


```
and on the first code i get two an ethernet(broadcom) and my wireless card. there is a guide for my wireless card, but i need internet to use it

---

### Post by Confusedalot on 2007-06-13
okay...  sorry for the trouble.. i got wired internet to work, but i'm still confused on what i have to do now

---

### Post by Happy_Man on 2007-06-13
Install ntfs-3g and ntfs-config, and follow ugm6hr's instructions.

---

### Post by Confusedalot on 2007-06-13
ntfs-config dosent work, it says

Mounting /media/sda2 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/1E6CA4456CA41993': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
i can even boot windows at all . i dont get it

---

### Post by phr0ze on 2007-06-13
Look for this in synaptic try to install and run. It is saying windows did not shut down cleanly.

Run ntfsfix version 1.13.1 on Linux unless you have Vista.

---

### Post by Confusedalot on 2007-06-13
okay i have ntfsprogs from synaptic, but how do i run ntsf fix? i couldent find it in a search

---

### Post by Confusedalot on 2007-06-13
never mind i ran it in terminal, but it gives me
```

Refusing to operate on read-write mounted device /dev/sda2.

```

---

### Post by pistcivet on 2007-06-13
I believe ntfsfix forces Windows to repair a file system at next boot.
Since you can't boot Windows I don't think it will help you.

At this point, you need a live-CD with ntfs write support built in.
(Does such a thing exist?)
Knoppix maybe?

edit: An XP cd might be the only way to fix this.

---

### Post by Confusedalot on 2007-06-13
grrr.... i cant believe that! i should have backed up my stuff...

---

