---
title: "Another Noob"
date: 2007-06-20
forum: Apple Intel Users
---

### Post by HUKI365 on 2007-06-20
Hey guys!

Just starting out. Thinking of triple booting Feisty on my Macbook (2nd gen, not Core 2 Duo). A couple of questions, though.

From the walk through ( [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu) ) I understand once you set the partitions in terminal they're set. For life? Can I reinstall OS X onto a clean unified 120gb hard disk if I want to go back from Linux?

Also, will my Vista/OS X still operate fine retrieving software updates?

Any suggestions to enable my three operating systems to share files (or at least Vista and Feisty?)

Thanks for any help!

---

### Post by Greywhind on 2007-06-20
You can reinstall OS X to get rid of the extra partitions.

The updates will work.

Feisty automatically saw my Mac partition (though it can't write to it) and I would assume it will see your Windows partition. There's a slightly buggy Mac tool (ext2fsx) on Sourceforge for reading (and maybe writing to) Linux hard-drive partitions. I believe there's a Windows tool somewhere as well...

---

### Post by HUKI365 on 2007-06-20
Okay, so I can just boot with the OS X cd in, and reunifying the partitions and then reinstall? Fantastic.

---

### Post by ronocdh on 2007-06-20
> **HUKI365 said:**
> Okay, so I can just boot with the OS X cd in, and reunifying the partitions and then reinstall? Fantastic.
Right, but obviously this will be a total wipe of your drive and you'll have nothing left over from your previous installs. Just a fresh OS X Tiger.

---

### Post by HUKI365 on 2007-06-21
How exactly do I do this?

I've rebooted with the OSX DVD in, opened up terminal, used gpt show to get info and tried to run "gpt remove -i 3 disk0s3" to remove one of the volumes/partitions but it gave me an error that the image was "busy".

I tried mounting and unmounting it. If this isn't really something you guys can help me with, any ideas on a good Mac forum to ask?

Basically all I want to do is combine the volumes/partitions so I can have 120gb back (currently there are three volumes amounting to 111gb). Then I will resintall OSX and rEFIt and partition up.

---

### Post by ivesjd on 2007-06-21
Why do you need to reinstall, if you already have three partitions, you could just start  by installing Windows.

---

### Post by ronocdh on 2007-06-21
> **HUKI365 said:**
> How exactly do I do this?

I've rebooted with the OSX DVD in, opened up terminal, used gpt show to get info and tried to run "gpt remove -i 3 disk0s3" to remove one of the volumes/partitions but it gave me an error that the image was "busy".

I tried mounting and unmounting it. If this isn't really something you guys can help me with, any ideas on a good Mac forum to ask?

Basically all I want to do is combine the volumes/partitions so I can have 120gb back (currently there are three volumes amounting to 111gb). Then I will resintall OSX and rEFIt and partition up.
Try opening Disk Utility once you've booted from the OS X installer disc. It'll be up in the menubar somewhere. Once inside that, you should be able to delete and/or reformat partitions. Once this is done, proceed with a full installation (hit the Options button in the lower lefthand corner to customize installed packages, such as removing iLife or additional languages).

---

### Post by HUKI365 on 2007-06-21
Hey - thanks! I managed to find that disk utility by myself last night, and reunifying the partititons.

However, I am still missing 9g (I've partitioned my system twice previously with Bootcamp, each time losing 4.5g - my hard disk is at 111.5g currently). Trying to get help via the Apple Support forum to work it out. Because I want as much space for my new found love of triple boot! (If you guys know a way - feel free to reply.)

Thanks again for answering my noob-ish questions!

Oh and in anser to why I wanted to reinstall when I already had the partitions: I wanted to try and reclaim that 9g.

---

### Post by ivesjd on 2007-06-22
Maybe try booting the Ubuntu cd and run gparted, Itll atleast let you format that 9Gbs to something OS X will reconize.

---

### Post by HUKI365 on 2007-06-22
Actually I have received some info that MacBook 120G hard disks are actually only 111G in size! So It seems as if I'm not missing any space. Thanks anyway.

---

### Post by ivesjd on 2007-06-22
Ya, same as my 55Gb "60Gb" drive :)

---

