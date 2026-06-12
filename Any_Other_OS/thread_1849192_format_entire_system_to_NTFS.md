---
title: "format entire system to NTFS"
date: 2011-09-24
forum: Any Other OS
---

### Post by _Pieter_ on 2011-09-24
Hi guys, 

I'm giving my laptop to a younger family member who wants and needs Windows 7 on it. Current filesystem is FAT32 and Win7 needs NTFS. 

How do I format everything (I backed up all my data) to NTFS? 

thank you.

---

### Post by Elfy on 2011-09-24
with a partition editor - does not the win7 installer have the option to create/edit partitions?

moved to other o/s

---

### Post by _Pieter_ on 2011-09-24
I'm currently trying GParted. 

Cannot unmount any of my 3 partitions and 'format to..' menu is not clickable. 

The Win7 installer does not have the option to edit partitions.

---

### Post by Elfy on 2011-09-24
Make sure that none of the partitions are locked/mounted - key symbol.

If there are any right click and unmount.

Other than that I've no idea - not installed windows for a long time - last version I used could deal with partitions.

Edit - maybe drive options - [http://www.buildeasypc.com/pics/windows_7/windows7_6.jpg](http://www.buildeasypc.com/pics/windows_7/windows7_6.jpg)

[http://www.techtalkz.com/gallery/files/1/Windows7-2008-11-04-14-55-10.jpg](http://www.techtalkz.com/gallery/files/1/Windows7-2008-11-04-14-55-10.jpg)

Seems so

---

### Post by _Pieter_ on 2011-09-24
There is a key-symbol next to the partition name (/dev/sda3). 

Right-click, unmount yields the following error: 

unmount: /home: device is busy.

---

### Post by Elfy on 2011-09-24
Check my previous post edits - if that doesn't help then I suggest you try a windows forum.

---

### Post by _Pieter_ on 2011-09-24
As you can see in the screenshot you uploaded; only the options 'new', 'load driver' and 'refresh' are clickable. 

No suggestions for the error "unmount: /home: device is busy."? 

thanks.

---

### Post by agillator on 2011-09-24
You are running gparted from your system, right, not from a live CD? If so, that is the problem. You are trying to do something to a partition you are using. If you can't unmount the partition then run gparted from a live CD (an Ubuntu installation CD, for example). Then you should be able to work with any of the partitions.

---

### Post by Elfy on 2011-09-24
You are trying to do this from a livecd aren't you?

If not then you'll need to.

@agillator - SNAP :)

---

### Post by Elfy on 2011-09-24
> As you can see in the screenshot you uploaded; only the options 'new', 'load driver' and 'refresh' are clickable. If that is always the case then I'm flabbergasted ...

---

### Post by _Pieter_ on 2011-09-24
Thanks Agillator - will give that a try.

---

### Post by coldraven on 2011-09-24
Download the Parted Magic CD. It uses the same program, "gparted", to format your disc but as it is smaller it will boot faster.
Bonus is that it has other useful tools for recovering lost data and is an essential in your computer "toolkit".
[http://partedmagic.com](http://partedmagic.com)

---

### Post by _Pieter_ on 2011-09-24
Thank you coldraven, that worked!

---

### Post by ottosykora on 2011-09-24
But if you are going to install w7, then let it do the partitioning and formating, it will do it all automatically , no need for other tools at all.

Particularly it will need the small 'system' partition otherwise it might then refuse to install big updates like servicepacks.

---

