---
title: "Pls. Help: Add new /Home directory"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2007-04-15
Hi,

I have a laptop with Windoz XP Pro and Feisty.  Feisty was automatically set up with root and swap partitions.  Turned off machine.  Rebooted into Windows.  Put Knoppix Live CD in computer.  When I boot up Knoppix LiveCD  and bring up Qtparted, I saw Linux (root?) partitions being "Active".  When I highlighted Linux hoping to be able to resize it, so that I can add a new /Home partition, the Resize option was greyed out.  There are still rooms in Linux partition.  Could you please help me "deactivate" or "inactivate" Linux temporarily so that I can add /Home?

Thanks a lot for your help.

:confused:

PS: How do I set the thread subject title in Bold?

---

### Post by Adramelech on 2007-04-15
KNoppix detects your linux partitions and mount them, as you can see, your root and swap partition are mounted, and you cannot work on mounted partitons, so, unmount them:

umount /dev/MYPARTITION

and then use the partiton tool

---

### Post by silkstone on 2007-04-15
If you resize the root partition, will you need to reinstall Grub?

---

### Post by iClouseau88 on 2007-04-15
Thanks for your quick response. I will give it a try.

:)

---

### Post by iClouseau88 on 2007-04-15
I don't know if I will need to reinstall GRUB.  Can anyone with more experience chime in?
Thanks.

---

### Post by confused57 on 2007-04-15
> **iClouseau88 said:**
> I don't know if I will need to reinstall GRUB.  Can anyone with more experience chime in?
Thanks.

You've probably seen this guide for creating a separate /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You shouldn't have to reinstall grub if you're resizing the Ubuntu partition from the end and the root partition number doesn't change.  If your root partition did happen to change, which it shouldn't, you wouldn't reinstall grub, but edit it to correct for a new root partition....this can be done from the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Everything should work fine, especially if you're following the first link I provided.

---

### Post by louieb on 2007-04-15
Koppinx makes it easy to unmount a partition. Right click on partitions desktop icon > Unmount.

---

### Post by steve.horsley on 2007-04-15
> **silkstone said:**
> If you resize the root partition, will you need to reinstall Grub?

No. Grub can understand the filesystem and can find the files it needs.

However: If you create a new partition such that the root partition now has a different partition number, then a whole lot of things change. Frinstance, if the root was /dev/hda5 and you insert a new partition before that so the root is now on /dev/hda6, you will need to reinstall GRUB to tell it that it now must read /dev/hda6/boot/grub/menu.lst instead. Also, menu.lst will need editing. Also, you may need to edit /etc/fstab.

---

### Post by bapoumba on 2007-04-15
> **iClouseau88 said:**
> 
PS: How do I set the thread subject title in Bold?
Hello :)
Bold font on threads titles means _you_ have unread posts in them ;)

---

