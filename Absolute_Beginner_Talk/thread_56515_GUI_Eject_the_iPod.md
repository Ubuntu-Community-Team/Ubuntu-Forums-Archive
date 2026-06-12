---
title: "GUI Eject the iPod?"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-08-12
Recently, someone on these boards has been making a big deal about things like the viewing of IP addresses not being available via GUI. I happen to not care, and I think most users wouldn't care.

What does seem to be a major deal is a GUI ejector for the iPod. Even regular users use iPods.

I can't find a good GUI for it. In Rhythmbox, the iPod shows up, but there's no way to eject it. In Gtkpod, same thing. If I right-click on the actual device icon (on the desktop), the only option I get is "unmount volume," which doesn't do anything. The iPod display still says "do not disconnect."

So, I created a launcher called "eject iPod," but the problem is that each time the device name is different. One time it'll be /dev/sda1, another time it'll be /dev/sde1. So the launcher's no good.

Personally, I don't have a problem going into terminal, typing *df*, then *eject /dev/sd__*, but a GUI would be particularly handy for an everyday device that even non-computer literates use.

Any ideas?

---

### Post by castrojo on 2005-08-12
The UI in breezy is much better for this, it even displays an ipod icon instead of a generic usb drive, so this is an area that has seen lots of improvements.

---

### Post by aysiu on 2005-08-12
Looking forward to it.

---

### Post by astoltz on 2005-08-13
I've been told the simply unmounting the ipod is enough and the fact that the ipod still says "Do Not Disconnect" doesn't matter.  I'm not brave enough however and always use the eject command.

That said, eject will also look in /media/* (in addition to /dev/sd*) for the device, so if your ipod is mounted at /media/My_iPod, your launcher command (not just the name of the launcher) could be ```
eject My_iPod
``` regardless of the /dev/sd* that Ubuntu actually creates.

You could also look into creating a custom udev rule so that the ipod always gets assigned the same device node - /dev/ipod for example.  Google "udev rules" will give you lots of help.

---

### Post by wmcbrine on 2005-08-13
I've been unmounting, pulling the cord, and worrying each time. I didn't even realize I *could* "eject" it.  ](*,) 

So far, so good... except, my front Firewire port no longer works, and I had to switch to USB. I don't know if that's related to not ejecting it, or what. (It's not the iPod, since it still works via Firewire on my Mac Mini.)

I did trash my iPod's filesystem once, but that was when gtkpod crashed in the middle of updating it.

---

### Post by aysiu on 2005-08-13
[QUOTE=astoltz]I've been told the simply unmounting the ipod is enough and the fact that the ipod still says "Do Not Disconnect" doesn't matter.  I'm not brave enough however and always use the eject command.[/quote] Yeah, me neither.

> 
That said, eject will also look in /media/* (in addition to /dev/sd*) for the device, so if your ipod is mounted at /media/My_iPod, your launcher command (not just the name of the launcher) could be ```
eject My_iPod
``` regardless of the /dev/sd* that Ubuntu actually creates. Wow! I'll give that a try.

P.S. When you said My_iPod, did you mean literally the word *My_iPod* or the actual name of the iPod itself? Because the word My_iPod does not work, but the name of the iPod does.

---

### Post by crane on 2005-08-20
[QUOTE=aysiu]Yeah, me neither.

 Wow! I'll give that a try.

P.S. When you said My_iPod, did you mean literally the word *My_iPod* or the actual name of the iPod itself? Because the word My_iPod does not work, but the name of the iPod does.[/QUOTE]

I wonder why they show up so different. Maine actually shows up as IPOD, not my_ipod or iPod or Ipod. Funny!

---

### Post by talkingwires on 2005-08-26
I believe the name comes from the name you assigned your iPod in iTunes. For example, I named mine iTumble (to go with my desktop and laptop, named Crash-o-matic and Tumble-o-tron, respectively). So in Ubuntu, it is mounted as ITUMBLE. If you didn't give it a name, it defaults to iPod. I'm not sure what the deal the all caps is, though...

---

### Post by crthomas on 2005-09-03
I tried eject ipod-name, and eject /dev/sda#.  They give me an invalid argument error, but the ipod is unmounted, and still says do not disconnect.  Am I doing something wrong?

---

### Post by aysiu on 2005-09-03
[QUOTE=crthomas]I tried eject ipod-name, and eject /dev/sda#.  They give me an invalid argument error, but the ipod is unmounted, and still says do not disconnect.  Am I doing something wrong?[/QUOTE] I do *eject /media/iPod-name*. Also, sometimes it's sda1, sometimes it's sdb1, or even sde1 (or 2, 3, 4). It depends on how many other things you have plugged in.

---

### Post by the_purulent on 2005-09-07
I've tried the "eject my_ipod" command, but all it does is unmount my ipod and leave the device flashing "Do not Disconnect"

How do I make that pesky "Ok to Disconnect" Screen appear?

---

### Post by aysiu on 2005-09-07
Have you tried *eject /dev/sda1*? Or *eject /dev/sde1*?
If you type *sudo fdisk -l* it should tell you what /dev is connected.

---

### Post by the_purulent on 2005-09-07
It's /dev/sda1 as I recall.  I will give it a try when I get home. It always seems to be the same ID.

Thanks!
Here's hoping!

---

### Post by the_purulent on 2005-09-08
Well, that didn't work, it unmounts the drive, but still doesn't display the 'ok to connect' message.  It wouldn't be a real prblem, but I've been having wierd issues with gtkpod saying my iTunes.db is corrupt and losing all my songs.  

I feel it may be caused by this issue, as it worked for a while, then stopped working when I disconected without stopping the device.

---

### Post by aysiu on 2005-09-08
Can you post the output of this command when your iPod's connected?

sudo fdisk -l

---

### Post by Klin'Targ on 2005-09-09
The "Do Not Disconnect" screen only goes away for me if I eject the ipod as root.
```
sudo eject /dev/sda1
```
This is so inconvenient, that I usually just pull it with the warning showing.

EDIT: I just read a nice workaround for this: give eject root execute privileges:
```
sudo chmod +s /usr/bin/eject
```
Note that giving root execute privileges to any binary has some inherent security risks, though I believe they are pretty minimal in this case.

---

### Post by aysiu on 2005-09-09
[QUOTE=Klin'Targ]The "Do Not Disconnect" screen only goes away for me if I eject the ipod as root.
```
sudo eject /dev/sda1
```
This is so inconvenient, that I usually just pull it with the warning showing.[/QUOTE] That can't be good. Why not create a launcher or keyboard shortcut to execute that command? Or put something in the /etc/fstab so that the iPod doesn't isn't mount by root?

---

### Post by the_purulent on 2005-09-09
```

Disk /dev/hdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9538    76613953+  83  Linux
/dev/hdb2            9539        9726     1510110    5  Extended
/dev/hdb5            9539        9726     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 4095 MB, 4095737856 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131    0  Empty
/dev/sda2   *           6         497     3951990    b  W95 FAT32


```

Here is my sudo fdisk -I output...

Edit: Yes! I got it, all I needed was the sudo command added to my launcher I made. Worked like a charm,... now I feel dumb lol

---

### Post by menawollas on 2005-09-09
Personally, I can't understand why anyone who supports open source software would want to get saddled with the bag of spanners that an iPod, and in particular iTunes is.  [-X 

Get an iRiver, it supports ogg and doesn't fcuk your files up into a proprietary format when you cop things to it.  :-P

---

### Post by aysiu on 2005-09-09
[QUOTE=menawollas]Personally, I can't understand why anyone who supports open source software would want to get saddled with the bag of spanners that an iPod, and in particular iTunes is.  [-X 

Get an iRiver, it supports ogg and doesn't fcuk your files up into a proprietary format when you cop things to it.  :-P[/QUOTE] I can't speak for anyone else, but we got my wife's iPod long before we got Linux, and my wife doesn't really dig Linux all that much (she has a Mac Powerbook). Also, our car's stereo (which we also bought long before I started using Linux) plays MP3s but not Oggs.

---

### Post by dcraven on 2005-09-09
Uh.. Because the iRiver doesn't have commercials with Bono and dancing sihlouette hipsters in them?

~djc

---

### Post by the_purulent on 2005-09-09
I have two iPods (have for about 2 years now) and I got them both for free (one of the benefits of working for HP. :) Free gadgets from promotions at work.

why pay for an iriver when my ipods (which lets face, just look friggin slick) are set at such a great price?  :)

---

### Post by aysiu on 2005-09-28
I don't know what version of KDE Kubuntu Breezy uses, but we finally have GUI eject for the iPod built in! [Here I am right-clicking the iPod icon to eject it](http://i22.photobucket.com/albums/b337/psychocats/47ac886b.png), and it actually changed the iPod screen from saying "Do not disconnect" to "OK to disconnect."

---

### Post by MetalMusicAddict on 2005-09-28
[QUOTE=dcraven]Uh.. Because the iRiver doesn't have commercials with Bono and dancing sihlouette hipsters in them?
~djc[/QUOTE]
HA! I love my H340.
[IMG]http://images.tigerdirect.com/SKUimages/medium/I116-3018-main.jpg[/IMG]

---

### Post by ltmon on 2005-09-28
[QUOTE=aysiu]I don't know what version of KDE Kubuntu Breezy uses, but we finally have GUI eject for the iPod built in! [Here I am right-clicking the iPod icon to eject it](http://i22.photobucket.com/albums/b337/psychocats/47ac886b.png), and it actually changed the iPod screen from saying "Do not disconnect" to "OK to disconnect."[/QUOTE]
Hi,
Breezy uses KDE 3.4.2 unless you've deliberately installed 3.5 beta 1.
On hoary (with both versions of kde) I get the same command in my context menu as you do ("Safely Remove"), but it unmounts and doesn't eject.

I wonder what's changed in Breezy to cause it properly eject.... ?

Cheers,
L.

---

### Post by Redindian on 2005-09-28
I'm sorry if this is not relevant to the topic discussed here..... Did you guys read this howto [https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29](https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29)
I followed this howto to install gtkpod and access my ipod. Everything is working perfect. Whenever i close gtkpod, my ipod automatically unmounts and I won't see "Do not disconnect" in my ipod.

---

### Post by aysiu on 2005-09-28
[QUOTE=ltmon]Hi,
Breezy uses KDE 3.4.2 unless you've deliberately installed 3.5 beta 1.
On hoary (with both versions of kde) I get the same command in my context menu as you do ("Safely Remove"), but it unmounts and doesn't eject.
I wonder what's changed in Breezy to cause it properly eject.... ?[/QUOTE] Thanks for the info. Maybe it is KDE 3.4.2 that's changed, or maybe the updated Linux kernel? Yeah, before, regardless of distribution or desktop environment, safely removing or unmounting did nothing to properly disconnect the iPod.

---

### Post by GreyFox503 on 2005-09-28
[QUOTE=menawollas]Personally, I can't understand why anyone who supports open source software would want to get saddled with the bag of spanners that an iPod, and in particular iTunes is.  [-X 
Get an iRiver, it supports ogg and doesn't fcuk your files up into a proprietary format when you cop things to it.  :-P[/QUOTE]
I like my iPod.  I bought it before I started using Ubuntu and I bet others have done this also.  It's true that it doesn't play ogg files (at least I think so, I don't have any), however whenever I put music onto it it doesn't "fcuk" up my files, as you say.  If you mean its strange directory structure, yeah that's kinda annoying, but gtkpod serves its purpose.
I like iTunes also.  The only problem with it is that it isn't Free.  And of course there's no native-linux version.
On another note, if you add the item called "Disk Mounter" to your gnome panel, it will use little icons to represent media on your computer like floppies, iPods, etc.  and you can use it to eject the iPod also.

---

### Post by 23meg on 2005-09-28
i bought my ipod mini *after* i started using ubuntu on a daily basis, and i must say gtkpod and [ipod linux project](http://ipodlinux.org/Main_Page) were the deciding factors. i was fully aware that i'd never be able to play ogg files (an apple spokesperson said this won't be possible even with a firmware update since the ipod doesn't have enough processing power to decode the format) even though i favor ogg and flac over mp3, but it's not hard to convert back and forth between formats with a few nautilus scripts. irivers are hard to find and very expensive where i live, and AFAIK aren't supported as well as ipods on linux.

---

### Post by veloct on 2005-11-23
[QUOTE=Redindian]I'm sorry if this is not relevant to the topic discussed here..... Did you guys read this howto [https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29](https://wiki.ubuntu.com/IPodHowto?highlight=%28ipod%29)
I followed this howto to install gtkpod and access my ipod. Everything is working perfect. Whenever i close gtkpod, my ipod automatically unmounts and I won't see "Do not disconnect" in my ipod.[/QUOTE]

That works like a charm. Thanks a lot.  Works in both gtkpod and banshee.

---

### Post by bschuteker on 2006-01-24
i COULDN'T FIND ANY RECENT POSTS ON THIS. (oops I hate the caps lock key) I am having similar problem. I cant seem to eject my ipod. It auto mounts fine and gtkpod works great but I cant eject it. I can un mount it, but that has no effect. on the ipod. when I followed the instrustions above my terminal locks.

bill@ubuntu-bill:~$ sudo eject BILL'S IPOD
>


It just sits there like that.

Any help????

oops again, just found this post but it is about the same advice.
[http://ubuntuforums.org/showthread.php?t=103239&highlight=eject+ipod](http://ubuntuforums.org/showthread.php?t=103239&highlight=eject+ipod)

---

### Post by aysiu on 2006-01-24
Try doing it from the /dev instead of the mount point.
For example, if it's at /dev/sda1, ```
sudo eject /dev/sda1
```

/mnt/BILLS_IPOD or /media/BILLS_IPOD is probably the mount point.

---

### Post by endersshadow on 2006-01-25
After following the instructions on the [Wiki](https://wiki.ubuntu.com/IPodHowto), sans the automation of unmounting on gtkpod closing, I wrote this script, which seems to work very well for me:

```
#!/bin/bash

if fdisk -l | grep sda2 ; then
	sudo /usr/bin/eject /dev/sda2
elif  fdisk -l | grep sdb2 ; then
	sudo /usr/bin/eject /dev/sdb2
elif  fdisk -l | grep sdc2 ; then
	sudo /usr/bin/eject /dev/sdc2
elif  fdisk -l | grep sdd2 ; then
	sudo /usr/bin/eject /dev/sdd2
else
	zenity --info --title "iPod Eject" --text "Device not found."
	exit 0;
fi
exit 0;
```

I should note that my iPod mounts at different points nearly every time I mount it, but it's the only thing that's mounted when it is mounted.  If yours is not, I suggest you don't use the script...

---

### Post by bschuteker on 2006-01-25
OK, 

When I did the, sudo eject /dev/sda2 it worked.

Now my question is can I make it mount as the same thing each time? I am using this laptop as a desktop replacement and have multiple external hard drives and an external DVD burner. Am I goilg to have to look up it's mount point every time and eject it from terminal or is there a way to set it up through the GUI? I much prefer one click to having to type commands.

Thanks,

---

### Post by astoltz on 2006-01-25
[QUOTE=bschuteker]Now my question is can I make it mount as the same thing each time?[/QUOTE]
When your ipod is connected, look at the name of the mount point in /media.  Mine is "/media/ipod" but your's may be different.  The name of that mount point  - /media/[whatever] - should be the same every time.  You can then use the command ```
sudo eject [whatever]
```I think there is a post about making a "click-able" link with that command earlier in this thread.

The other suggestion I have is to make a custom udev rule that will define a symlink from /dev/sd? to /dev/ipod.  Then, the device node /dev/ipod will be available regardless of which /dev/sd? it actually gets.  This isn't as hard as it sounds - google has some good links when you search "udev rules".

---

### Post by hanzj on 2006-08-03
Veloct, i went to that wiki page but i don't see the instructions on how closing gtkpod will eject the ipod. please let us know.

---

### Post by hanzj on 2006-08-03
So i am able to eject the ipod.

but what if i want to mount it again. Without unplugging and then re-plugging the iPod to the cable, what can we do/type?

---

