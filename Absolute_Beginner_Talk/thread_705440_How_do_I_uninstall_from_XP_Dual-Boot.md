---
title: "How do I uninstall from XP Dual-Boot?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by bmfgeorgin2 on 2008-02-23
If later after I have installed it how do I uninstall it if I dont want it anymore? I dont want it to effect XP at all.

---

### Post by TeoBigusGeekus on 2008-02-23
You probably need a tool like Norton Partition Magic.
It can reformat your Ubuntu partition to NTFS and then resize your xp partition to absord the space used by linux.

---

### Post by bmfgeorgin2 on 2008-02-23
Ok +Thanks

---

### Post by bmfgeorgin2 on 2008-02-23
where can I find this program?

---

### Post by Martje_001 on 2008-02-23
Just fire up an Ubuntu-live cd and do in a terminal:
```
sudo gparted
```
Here you can resize / delete / (re)format partitions of all kinds (this is grapical btw).

---

### Post by forestpixie on 2008-02-23
there is a linux tool - name of which escapes at the moment - with which to reinstall the mbr before you remove linux and grub, that said if you've got the xp disc you can use that instead

you delete partition, fix mbr with windisc recovery nad reformat partition to ntfs

---

### Post by Martje_001 on 2008-02-23
> **bmfgeorgin2 said:**
> where can I find this program?
You have to pay for it, as far as I know.

---

### Post by forestpixie on 2008-02-23
> **Martje_001 said:**
> You have to pay for it, as far as I know.

so much more satisfying to use something you don't pay for :) especially when it's legal

---

### Post by slimx3m on 2008-02-23
i would recommend gparted, the progeam what Martje_001  recommend

---

### Post by bmfgeorgin2 on 2008-02-23
ok thanks

---

### Post by mickinator on 2008-02-23
Theres one called fixmbr tis free, just google it, it comes with instructions, run this before you delete linux or else your pretty knackered! The just reformat your partitions to ntfs and bobs ur uncle!

---

### Post by Nirevus on 2008-02-23
My recommendation would be to use GParted (available on the Ubuntu liveCD) and [SuperGRUB]("supergrub.forjamari.linex.org") to solve this.

Load up into the liveCD and delete the Ubuntu partition, then resize the XP partition to use all the new space on your hard drive. Apply the changes and then when you restart use the SuperGRUB CD with the 'Fix Windows Boot Loader' option; once this has finished you can restart and you'll be back in Windows.

Don't forget that some of your issues may be solved by Hardy Heron releasing in April. Come back and give it a go!

---

