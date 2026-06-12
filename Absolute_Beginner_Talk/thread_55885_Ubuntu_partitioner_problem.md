---
title: "Ubuntu partitioner problem"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by elenie on 2005-08-10
Hello!

I tried to install Ubuntu 5.04. However, when I choose manual editing of the partition table, the installer does not list my partitions but shows only the device (hda1). I have two windows partitions (FAT32) and one (old) linux partition.

I tried booting from a Knoppix CD, and Knoppix recognized all the partitions, but the ubuntu installer does not.

I want to keep the Windows partitions and use the linux partition for Ubuntu. What can I do? Did I miss something?

Thanks in advance,
elenie

---

### Post by aysiu on 2005-08-10
Not having the installer dialogue right in front of me, I'm guessing when it prevents you with only hda1, it's asking which *hard drive* you want to use. After you select that, does it then give you a choice of partitions? Be very specific about what exactly is on your screen--what does it say?

---

### Post by elenie on 2005-08-10
Thanks for your quick response!

If I choose "IDE1 master (hda1)" on the first screen, a dialog appears:
"
You have selected an entire device to partition. If you proceed with creating a new partition table on the device, then all current partitions will be removed.

Create new empty partition table on this device?
"

I don't want to do that, because I don't want to remove my partitions.

According to the help text I think that the partitions should already be listed on the first screen (it says "Select a partition to modify its settings, a free space to create partitions, or a device to initialise its partition table" - however, I see only one device and no partitions at all).

---

### Post by aysiu on 2005-08-10
That's weird. Does anyone else know what's going on?

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=elenie]Thanks for your quick response!

If I choose "IDE1 master (hda1)" on the first screen, a dialog appears:
"
You have selected an entire device to partition. If you proceed with creating a new partition table on the device, then all current partitions will be removed.

Create new empty partition table on this device?
"

I don't want to do that, because I don't want to remove my partitions.

According to the help text I think that the partitions should already be listed on the first screen (it says "Select a partition to modify its settings, a free space to create partitions, or a device to initialise its partition table" - however, I see only one device and no partitions at all).[/QUOTE]

Hmmmm..............what happens when you say "no" to that question? Does it send you to the advanced partitioner? (where you can pick what partition you want ot install over)

Try saying no there.

---

### Post by az on 2005-08-10
I do not have it before me, at the moment, but you need to chose "Manually edit partition table."

There was a site with the screenshots and everything.  I think it is on the wiki.ubuntu.com/UserDocumentation site...

---

### Post by az on 2005-08-10
[http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

Look at this:
[http://www.mrbass.org/linux/ubuntu/install/006partitionauto.png](http://www.mrbass.org/linux/ubuntu/install/006partitionauto.png)

Do you ever see the "manually edit partition table" question?

---

### Post by elenie on 2005-08-11
[QUOTE=azz]Do you ever see the "manually edit partition table" question?[/QUOTE]
yes, this one:
[http://www.mrbass.org/linux/ubuntu/install/006partitionauto.png](http://www.mrbass.org/linux/ubuntu/install/006partitionauto.png)

There I choose "Manually edit partition table".

Then, basically this dialog appears:
[http://www.mrbass.org/linux/ubuntu/install/007overviewpartition.png](http://www.mrbass.org/linux/ubuntu/install/007overviewpartition.png)
But I can only see the "IDE1 master (hda)..." line - no partitions.
There should be two FAT32 partitions and at least one linux partition...


[QUOTE=poofyhairguy]Does it send you to the advanced partitioner? (where you can pick what partition you want ot install over)[/QUOTE]
The problem is, that I can't see any partitions...

---

### Post by fabiom on 2005-08-19
I'm having the exactly same problem. Did you find a soluction? Or does anyone else has a solution?

thanks!

---

### Post by nic2 on 2005-08-20
[QUOTE=elenie]Hello!

I tried to install Ubuntu 5.04. However, when I choose manual editing of the partition table, the installer does not list my partitions but shows only the device (hda1). I have two windows partitions (FAT32) and one (old) linux partition.

I tried booting from a Knoppix CD, and Knoppix recognized all the partitions, but the ubuntu installer does not.

I want to keep the Windows partitions and use the linux partition for Ubuntu. What can I do? Did I miss something?

Thanks in advance,
elenie[/QUOTE]

If you are going to use the existing Linux partition, why don't you delete the Linux partitions under Windows.  This should create free space which should be picked up by the Ubuntu installer.

---

