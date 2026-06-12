---
title: "Question about booting with different kernels"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by qiezi! on 2005-10-03
Hello! I've had Ubuntu (Hoary 32bit) up and running for a couple of days now, so happy :p. After everything I'd read I was amazed at how simple it was to install. I had a spare HDD just for Ubuntu though, and this probably helped. So far I've gotten most issues sorted relating to hardware; NVIDIA drivers, sound, powernow! and dual-core support. I used Synaptic to install a smp enabled kernel (2.6.10.5-k7), and can choose to use it or the normal 2.6.10.5 kernel from GRUB. 

Could someone explain how Linux/Ubuntu loads these kernels so that you can have several different versions installed?? I don't understand the principle yet. Also, can I compile a 64bit kernel and have the option to load it, or do I need a separate partition for 64bit Ubuntu??

---

### Post by mlomker on 2005-10-03
>  I used Synaptic to install a smp enabled kernel (2.6.10.5-k7), and can choose to use it or the normal 2.6.10.5 kernel from GRUB. 

You can take a look in the /boot directory and the contents of /boot/grub/menu.lst for some more insight into that.

> do I need a separate partition for 64bit Ubuntu??

Yes.

---

### Post by qiezi! on 2005-10-04
Thanks!! If I wanted install the 64bit version and scrap the 32bit version, but leave other partitions on the HDD intact, could I just re-format the partition containing the 32bit version with the 64bit installer?? (Did that make sense?? :???:)

---

### Post by Mustard on 2005-10-04
> Thanks!! If I wanted install the 64bit version and scrap the 32bit version, but leave other partitions on the HDD intact, could I just re-format the partition containing the 32bit version with the 64bit installer?? (Did that make sense?? )

If its anything like the 32bit installer in expert mode, I imagine you could.  I haven't tried it.  If that is the case , you would type in 'expert' at the boot prompt and then manually set up your partitions (formatting and reassigning the relevant ones and choosing the ones to install.  I would assume it then installs a new grub boot loader to reflect the changes.

I've only just discovered this flexible nature of linux.  I find myself often daydreaming of the perfect partition setup, and the perfect kernel setups. :)

How do you have your partitions set up atm?

---

### Post by qiezi! on 2005-10-04
Ahh the perfect setup :cool: with no extra crap/apps lying around the place messing things up....

oh yes my partitions; well I noobed it up and didn't change too much, at that stage I didn't know what Ubuntu would need or how the structure of the OS worked... 

I divided a 120GB HDD into a 80GB ext3 for Ubuntu (a swap of 2GB is in there, I don't think I really need that much though), and the rest is a FAT32 partition, where my music resides... I just used the partition thingo in the Ubuntu installer, which was pretty easy to use. On the whole getting Ubuntu up and running was a lot easier than I thought, definately easier/faster than WinXP by a mile. Getting stuff optimised for my hardware was a bit harder, but everything I needed was here somewhere on the forums :D

---

### Post by Mustard on 2005-10-04
When I setup last using expert mode, I went for the multi user environment for a choice of preset partition choices and it divided the partitions up pretty nicely, with seperate root, home, usr, var partitions.  I think it makes reinstalling and tinkering easier to have them all partitioned seperately.  

Your swap partition is nearly as big as my /home partition. :)

---

### Post by qiezi! on 2005-10-04
[quote=Mustard]When I setup last using expert mode, I went for the multi user environment for a choice of preset partition choices and it divided the partitions up pretty nicely, with seperate root, home, usr, var partitions. I think it makes reinstalling and tinkering easier to have them all partitioned seperately. 

Your swap partition is nearly as big as my /home partition. :)[/quote]

In hindsight, I would have liked to have had different partitions for those you mentioned...maybe a fresh install for breezy...

Yeah and I don't think that 2.5GB is really necessary :eek: (that was an auto from the installer), I have 1GB of RAM, so I'd probably free some more space from swap If I do a fresh install.

---

### Post by mlomker on 2005-10-04
> Yeah and I don't think that 2.5GB is really necessary :eek: (that was an auto from the installer), I have 1GB of RAM, so I'd probably free some more space from swap If I do a fresh install.

I think you'd get by fine if your /home was on a different partition.  You could use your VFAT partition for that if it had enough space.

---

### Post by qiezi! on 2005-10-04
[quote=mlomker]I think you'd get by fine if your /home was on a different partition. You could use your VFAT partition for that if it had enough space.[/quote]

That would mean I could write straight over the remaining partitions with Breezy leaving /home intact, right??

---

### Post by mlomker on 2005-10-04
[QUOTE=qiezi!]That would mean I could write straight over the remaining partitions with Breezy leaving /home intact, right??[/QUOTE]

Right.  If you have /home in another place then you can reload your operating system and not lose very much.  Your gnome menus and most customization is in /home.  

There are some fancy things that you can do to reload your operating system if it gets damaged.  There's a dpkg command that lets you import/export your package selections and then you back up the /etc directory....you can reload the operating system to the same version (wipe breezy and then reload it for example) and lose almost nothing.

In your case, though, you're going from 32 to 64-bit and you might not want to keep anything other than /home.

---

