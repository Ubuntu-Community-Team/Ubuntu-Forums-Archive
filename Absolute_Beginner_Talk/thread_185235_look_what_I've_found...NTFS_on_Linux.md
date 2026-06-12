---
title: "look what I've found...NTFS on Linux"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-05-31
yes ... you read it right
now you can write and read and mount NTFS on linux
it isn't completley done yet but it still works.
check it out :

[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

tell me what you think...

---

### Post by ComplexNumber on 2006-05-31
[quote=MAXDDARK]yes ... you read it right
now you can write and read and mount NTFS on linux
it isn't completley done yet but it still works.
check it out :

[http://www.linux-ntfs.org/]("http://www.linux-ntfs.org/")
[http://www.jankratochvil.net/project/captive/]("http://www.jankratochvil.net/project/captive/")

tell me what you think...[/quote] thats old news. well, i've got that and it doesn't allow you to write to NTFS even when the umask is set to "0000" in the fstab. it can only read it.

---

### Post by bluenova on 2006-05-31
err, you could before. I used to be able to mount and edit my NTFS partition when I still had win xp installed.

Was with Fedora Core 4 though.

---

### Post by xtacocorex on 2006-05-31
You can edit, but it won't allow you to change the size of the file or create new ones.

---

### Post by MaximB on 2006-05-31
damn...and I've thought that I'm up to somthing....
but I still belive that it would be possable to write to NTFS in linux...
by the way - did you check both sites or just one ?
check them both

---

### Post by xtacocorex on 2006-05-31
I will retract part of what I said, I have heard that you can mostly write with captive, but is still a little iffy. 

The linux-ntfs site is what is in the linux kernel, I think. They have the rpm's because I remember needing to download them when I ran Fedora on a previous dual boot setup.

I lost my Hoary/XP dual boot to a hd failure and I'm glad because why waste time trying to read/write to a poorly created filesystem. I just moved my external hd to ext3 last night because it's far superior to the fat16 that mkfs can create that I had on there originally. If I need that drive to have compatibility with my wife's XP box, I'll just install the ext3 drivers for windows.

---

### Post by patrick295767 on 2006-05-31
[QUOTE=xtacocorex]I will retract part of what I said, I have heard that you can mostly write with captive, but is still a little iffy. 

The linux-ntfs site is what is in the linux kernel, I think. They have the rpm's because I remember needing to download them when I ran Fedora on a previous dual boot setup.

I lost my Hoary/XP dual boot to a hd failure and I'm glad because why waste time trying to read/write to a poorly created filesystem. I just moved my external hd to ext3 last night because it's far superior to the fat16 that mkfs can create that I had on there originally. If I need that drive to have compatibility with my wife's XP box, I'll just install the ext3 drivers for windows.[/QUOTE]
  
A program that was working nicely was Paragon ntfs for linux (pay)
[http://www.ntfs-linux.com/](http://www.ntfs-linux.com/)   but but very risky !
  I converted all the hdds to fat32, that's the best to do !!
 
Or install a Linux Server With SAMBA !! :- )
You can also buy a damn old machine to transform it as server 
(no X required)

---

### Post by joshrobinson on 2006-05-31
[QUOTE=patrick295767]A program that was working nicely was Paragon ntfs for linux (pay)
[http://www.ntfs-linux.com/](http://www.ntfs-linux.com/)   but but very risky !
  I converted all the hdds to fat32, that's the best to do !!
 
Or install a Linux Server With SAMBA !! :- )
You can also buy a damn old machine to transform it as server 
(no X required)[/QUOTE]

yeah i ran an old linux server for awhile. until i bought a new hard-drive and backed up all of my data and converted my filesystems.. no more damn ntfs

its just kinda hard to shift around 600+ gigs of data to change filesystems.. but now that i have over 1terabyte i got the job done :-D

i never trusted ntfs writing in linux too risky

---

