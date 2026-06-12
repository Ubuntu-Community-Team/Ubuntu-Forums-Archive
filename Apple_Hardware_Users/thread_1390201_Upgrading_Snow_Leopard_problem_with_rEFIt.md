---
title: "Upgrading Snow Leopard problem with rEFIt"
date: 2010-01-25
forum: Apple Hardware Users
---

### Post by luigi.viggiano on 2010-01-25
Hi.

I am trying to update to Snow Leopard.

I get this screen: 

[IMG]http://img407.imageshack.us/img407/6822/picture2k.png[/IMG]
Any hint?

I have rEFIt and a working Ubuntu Linux 9.10 (ext3 filesystem, upgraded from 9.04)

I'd like also to convert ext3 to ext4, is that possible? How?

Thanks.
Luigi.

---

### Post by buntuLo on 2010-01-25
> **luigi.viggiano said:**
> I'd like also to convert ext3 to ext4, is that possible?
ciao Luigi,
the conversion from ext3 to ext4 is possible, but it doesn't let you enjoy the full performance upgrade of ext4: only the newly written files will benefit from it. i would recommend you to format the partitions and copy over the backupped data, easy to do at least on partitions other than /.
sorry, can't help you with the macosx update.

---

### Post by luigi.viggiano on 2010-01-25
> **buntuLo said:**
> the conversion from ext3 to ext4 is possible, but it doesn't let you enjoy the full performance upgrade of ext4: only the newly written files will benefit from it. 

Why this? Sounds surprising for me.

I found this [howto]("http://ubuntuforums.org/showthread.php?t=1118295") should work nice. But if I won't get any benefit, possibly I'll keep ext3 (I'll check better why).

> **buntuLo said:**
> sorry, can't help you with the macosx update.

I erased OSX disk and installed Leopard from scratch. It worked.

I removed rEFIt and did 'sudo bless' stuff to enable linux as default disk.

---

### Post by buntuLo on 2010-01-26
> **luigi.viggiano said:**
> Why this? Sounds surprising for me.
not that surprising, if you keep on reading the comments following that howto.
i quote from:
[http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4")
> by enabling the extents feature new files will be created in extents format, but this will not convert existing files to use extents. Non-extent files can be transparently read and written by Ext4.
and by the way, data backup (better in two copies), formatting, and copying over again helps you to eliminate fragmentation of data too.

---

