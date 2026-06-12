---
title: "ubuntu on a dual o boot first os"
date: 2008-03-11
forum: Apple Intel Users
---

### Post by Hotchilli on 2008-03-11
Is it possible on a imac to place ubuntu as the first OS on a HD then OSX

hotchilli

---

### Post by cyberdork33 on 2008-03-11
> **Hotchilli said:**
> Is it possible on a imac to place ubuntu as the first OS on a HD then OSX
it depends on what you mean, but the answer is yes for either way I am interpreting it.
Do you want Ubuntu to be the default OS to boot? Use rEFIt

Do you want the Ubuntu partition to be in front of the OS X partition? Yes, that will work fine...

---

### Post by Hotchilli on 2008-03-12
cyberdork:

Yes i  think your post answered my question.

I know this is very off-topic but if the need ever arose would it be possible to place xp
on the boot partition?

thankyou

hotchilli

---

### Post by lex1 on 2008-03-12
You can if you really want :

This is really off-topic, You'll need to do a couple things. Clone OS X to external drive and  use Disk Utility to create the FAT and Mac Extended partitions. Then install XP as you normally would, and boot from the CD.

lex1

---

### Post by cyberdork33 on 2008-03-12
> **Hotchilli said:**
> I know this is very off-topic but if the need ever arose would it be possible to place xp on the boot partition?Not directly. You can only choose between OSX and "legacy OS" in rEFIt. but you can boot windows from grub, and make it the default in grub and it should be OK, just not an elegant solution.

---

### Post by Hotchilli on 2008-03-13
so would the ubuntu live cd also create a xp partition or would i use the disk utility as lex1 pointed out?


hotchilli

---

### Post by cyberdork33 on 2008-03-13
> **Hotchilli said:**
> so would the ubuntu live cd also create a xp partition or would i use the disk utility as lex1 pointed out?


hotchilli
You will probably have to recreate your partitions anyway, so just make sure that your OSX partition is the size you want. Then you can use gparted on the Live CD to create your linux partition (ext3) and your windows partition (fat32 or ntfs).

---

### Post by Hotchilli on 2008-03-14
ok just to sum up , since i want xp as boot then live ubuntu cd and make that and the ext3 
then with the OSX disk creste the extended jurnal partition.

the reason for xp on boot is that it needs to be as i am to use a sofware truecrypt with xp
its also available for OSX and ubuntu but its advanced disk encrption utility is works with
xp best.

Thanks to all the posters on the thread

hotchilli

---

### Post by cyberdork33 on 2008-03-14
I have no idea what you are asking in your last post...

Make Windows the last partition <= #4
You can configure what OS boots by default later.

If you are planning to do total drive encryption, you may run into other issues. The best I can say is 'try it'.

---

