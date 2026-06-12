---
title: "Grub question"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-18
I wasn't sure at first wether to use Gnome or KDE, so I installed Ubuntu/Kubuntu as dual boot on seperate partitions. I have decided I like Gnome, so I want to delete the Kubuntu partition. Kubuntu was installed after Ubuntu, so it controls grub. If I delete the Kubuntu partition will it destroy grub, or will it still boot with the Ubuntu installation?

---

### Post by divague on 2007-03-19
I think it will destroy grub, but you can reinstall grub, here's a link that could help you reinstall it

[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation](http://easylinux.info/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation)

---

### Post by rsambuca on 2007-03-19
It is actually really easy to fix now, before you delete the partition.

From the ubuntu terminal```
sudo grub
```

You will get a grub> prompt.  Enter ```
find /boot/grub/stage1
```

You should see two locations for the stage1 grub.  ie. (hd0,0) and (hd0,1)

One will be your ubuntu grub and one will be your kubuntu grub.  As long as you know which is which (Let's assume (hd0,0) for this example), just enter at the grub prompt```
root (hd0,0)
```You would of course enter the location for your specific stage1 location

then write the instructions to the MBR```
setup (hd0)
```

type "quit" to exit grub and your rig should  now be using your ubuntu grub loader.

---

### Post by 67GTA on 2007-03-19
Thanks rsambuca, that worked perfect. I put this in my favorites. One of these days I will be all grown up.

P.S. Is there a list of these types of commands that are put together already? I mean, I have found several web sites that list the commands from a-z, but I am not exactly sure how to put them together sometimes to get the desired effect.

---

### Post by rsambuca on 2007-03-19
Yeah, finding your way around can be tough.  I am still just mixing and matching ideas from all over the place.  If you find a good comprehensive list, let me know!

---

### Post by LanDan on 2007-03-19
if you want to know some details about a command there is an excellent thing called "man pages"


for instance you could go to the terminal and type "man grub"

there is a lot of these ;)

---

### Post by rsambuca on 2007-03-23
> **67GTA said:**
> Thanks rsambuca, that worked perfect. I put this in my favorites. One of these days I will be all grown up.

P.S. Is there a list of these types of commands that are put together already? I mean, I have found several web sites that list the commands from a-z, but I am not exactly sure how to put them together sometimes to get the desired effect.

This is also a pretty comprehensive guide:

[http://easylinux.info/wiki/Ubuntu_Edgy](http://easylinux.info/wiki/Ubuntu_Edgy)

---

