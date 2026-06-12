---
title: "how to grow ext3?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-10
Hi,

i have in order NTFS partition, Unallocated partition, ETX3 Partition...

How do i make the EXT3 bigger? :confused: i tried Gparted but i think i can only make it smaller? i dunno how to use it properly...

thanks

---

### Post by bodhi.zazen on 2007-08-10
You need a newer version of gparted (this is a well known limitation of odler versions)

Either dowload the gparted live CD or Gutsy, tribe 4

Gparted  Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

### Post by Hopeless on 2007-08-10
Hi thanks...

How do i update the software?

type update gparted in a terminal?

---

### Post by bodhi.zazen on 2007-08-10
Unless you upgrade to gutsy, the latest version of gparted is NOT in the ubuntu repositories.

Also it is inadvisable, to say the least, to resize a partition that is mounted, such as your ubuntu root partition using gparted as you suggest.

So you will need a live CD ... you could try either the gparted live CD or the Gutsy CD.

---

### Post by logos34 on 2007-08-10
bodhi-zazen is right--you need to work from the gparted live cd if you're resizing root partition.

But if you want a newer Gparted installed, someone has created an unofficial .deb pkg (gparted_0.3.3-1_i386.deb).   I use it.  [edit]

[http://ubuntuforums.org/showthread.php?p=2787767](http://ubuntuforums.org/showthread.php?p=2787767)

---

### Post by Hopeless on 2007-08-10
thanks for the advise...

its a spare NTFS drive that i want to convert to ext3... so im shrank ntfs and made ext3....shrank ntfs again...and this is where i am...

thanks for the link to gparted...:)

---

### Post by Hopeless on 2007-08-10
hi,

i uninstalled gparted and installed the newer link posted....

but i can't find it in any menus...any ideas?

---

### Post by bodhi.zazen on 2007-08-10
> **logos34 said:**
> bodhi-zazen is right--you need to work from the gparted live cd if you're resizing root partition.

But if you want a newer Gparted installed, someone has created an unofficial .deb pkg (gparted_0.3.3-1_i386.deb).   I use it.  [edit]

[http://ubuntuforums.org/showthread.php?p=2787767](http://ubuntuforums.org/showthread.php?p=2787767)

thanks for the link ...

you can also get it here : [http://packages.ubuntu.com/gutsy/gnome/gparted](http://packages.ubuntu.com/gutsy/gnome/gparted)

(just showing how to find packages is all)

---

