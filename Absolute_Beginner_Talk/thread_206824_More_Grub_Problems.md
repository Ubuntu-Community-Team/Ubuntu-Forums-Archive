---
title: "More Grub Problems"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by chameleonkid on 2006-06-30
Well this may have little to do with ubuntu but this is the only place i know to ask of this question. I recently tried to put slackware 10.2 onto my computer. Everything went well  untill the booting part. I decided not to install LILO but just add it to my grub menu. First i tried to update-grub, this did not find slackware partition. So I manually added Slackware to my grub confg lst as best I could. here it is:

[FONT="Verdana"]title		Slackware
root		(hd0,0)  	
kernel		(hd0,0)/boot/vmlinuz-ide-2.4.31 ro root=/dev/sda1
boot[/FONT]

on reboot I received this message

[FONT="Verdana"]Please append correct "root=" boot option
Unable to mount root fs on 08:01[/FONT]

(and some other /sbin/kmod message)I have no idea what this means. Any help would be appreciated.

---

### Post by klytu on 2006-06-30
[QUOTE=chameleonkid]
kernel		(hd0,0)/boot/vmlinuz-ide-2.4.31 ro root=/dev/sda1
[/QUOTE]

This line looks suspect. Try substituting instead:

```
kernel		/boot/vmlinuz-ide-2.4.31 root=/dev/sda1 ro
```

I am guessing that in your device.map file there is a line:

(hd0) /dev/sda

But this is only a guess.

---

### Post by catlett on 2006-06-30
There are a few ways to edit the grub menu when you don't know the vmlinuz and initrd. Assuiming slackware was installed to the first partition of your first hard drive i.e. hd0,0 you can try these. They all should work but you never know
```
title slackware
root   (hd0,0)
chainloader +1
boot
```
```
title  slackware
rootnoverify  (hd0,0)
chainloader +1
boot
```
```
title  slackware
root   (hd0,0)
kernel  /boot/loader
boot
```

Try them and see if one of them works. If not we can mount the slackware partition and get the vmlinuz and initrd information and add that to the entry. Hopefully that will do it. But first try these.


[COLOR="Red"]EDIT[/COLOR]
P.S. Here is another one you could try
```

title Slackware
root (hd0,0)
kernel /boot/vmlinuz-ide-2.4.31 ro root=/dev/sda1
```

I just realised this was klytu's recommended entry. I didn't realise it when posting it. I found an entry at a slackware forum and copy/pasted that entry but edited in your info. After I posted it and looked at the thread again I realised the entry was just like klytu's. So basically disregard my reply, Klytu took care of it and in alot less space :D

---

### Post by chameleonkid on 2006-06-30
Ahhh I'm afraid none of those actually worked. But I did go through a big process of loading lilo and testing it out. I was impressed by the look and feel, but I was hugely disappointed in the fact that I could not get on the internet through my LAN, and searching for somewhere to configure it, and not finding it, left me hugely dissapointed. I'll just have to try another distro flavor I am thinking...
maybe it had something to with it not running GNOME ;) . Thanks guys

---

### Post by catlett on 2006-06-30
Slackware is a tough one. What are you looking for in a distro? Do you just want to get away from gnome and kde? Do you want to configure more of your system instead of having alot of preinstalled default stuff? Or do you want a system that uses the least resources?

Just curious. Also was slackware on your first hard drives first partition? I only ask bvecause I am curious why those entries do not work. I use the rootnoverify/chainloder entry to boot PC Bsd, Fedora, Sylable and windows. It is a basic entry that just sends grub to that partition and tells it to load whatever it finds (sort of. the main thing about the noverify and chainloading is you dopn't have to give specific paths to the images etc). I am surprised it didn't work.

---

### Post by chameleonkid on 2006-06-30
[QUOTE=catlett]Slackware is a tough one. What are you looking for in a distro? Do you just want to get away from gnome and kde? Do you want to configure more of your system instead of having alot of preinstalled default stuff? Or do you want a system that uses the least resources?

Just curious. Also was slackware on your first hard drives first partition? I only ask bvecause I am curious why those entries do not work. I use the rootnoverify/chainloder entry to boot PC Bsd, Fedora, Sylable and windows. It is a basic entry that just sends grub to that partition and tells it to load whatever it finds (sort of. the main thing about the noverify and chainloading is you dopn't have to give specific paths to the images etc). I am surprised it didn't work.[/QUOTE]

Well I was just looking to try out another distro, get the feel for what is out there really. The slackware is on my hard drive's first partition (located before the ubuntu partition). Could this have to do with it not loading? I guess it's time to try some other distros, haha, maybe some easier or less fidgety ones than slackware.

---

### Post by Herman on 2006-06-30
> Ahhh I'm afraid none of those actually worked. But I did go through a big process of loading lilo and testing it out. I was impressed by the look and feel, but I was hugely disappointed in the fact that I could not get on the internet through my LAN, and searching for somewhere to configure it, and not finding it, left me hugely dissapointed. I'll just have to try another distro flavor I am thinking... GAG Boot Manager is the best for people who like to do a lot of installing and deleting of operating systems, or change hard disks a lot. GAG is a graphical boot manager, so it is very quick and simple to re-configure. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm") for a How-To on GAG.

You should be able to use GRUB's command line interface to find out the right commands to use and boot any operating system, [*click here*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") for how to do that.
> The slackware is on my hard drive's first partition (located before the ubuntu partition). Could this have to do with it not loading? I don't think so, as long as the partition numbers didn't get changed. It doesn't seem to matter where on a disk a partition is located, even Windows can be moved to the end of a disk *as long as we don't allow its partition number to be changed*, and it will still boot. (Mine works like that anyway).
Regards, Herman :)

---

### Post by catlett on 2006-06-30
Herman it's great to see you active. That site of yours is encyclopedic. I never saw gag before. Thanks for pointing me to it.
I hope you make a gparted live page. You really got me thinking in the thread from a week or so ago when I mentioned the home partition and you said because of gparted live we need to rethink things., You are absolutely right.
I enjoy installing new distros and such. I am trying to get better at partition moving and your posts set my mind turning.  
Any time you post I learn something. I'm off to your site for some research.

---

