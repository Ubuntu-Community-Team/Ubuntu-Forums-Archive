---
title: "Unmount USB Drive or just pull it out?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-11-10
Is it necessary to unmount it? Will I have any issues if I just pull it out?

---

### Post by Pablo_Escobar on 2005-11-10
I don't umount it. Pop the pendrive out and no problems yet :)

---

### Post by earobinson on 2005-11-10
In theroy no (since the drive stays pluged in and should handle stopage of input half way through).

But unmounting it will make sure that the computer is not reading or writing to the drive makeing sure you will not lose any data.

---

### Post by HJThis on 2005-11-10
Hey,All

@earobinson

Thanks for the heads-up i would just pull it out 

BOL

---

### Post by ssam on 2005-11-10
there is a chance that recently writen files would not have been fully writen to the usb drive. data can sit in the buffer for a while before being writen. the
```
sync
```
command makes sure the buffered data is writen.

i'd recomend unmounting, if you want to be sure that everything is safe.

---

### Post by vtec on 2005-11-10
I have found that if you write a large file and then unmount the drive by left clicking on it. It will appear to be unmount even though it is still writing to it. If you unmount from the command line the command will not return untill it is complete. The is somthing in gnome that i think should be changed. The icon should not disappear untill its finished writing. To see for your sell try to write a 300+MB file. then right after it says the copy is complete left click and unmount. The icon will dissapear but you can see the the light blink on the usb stick (if yours blinks while its read/writing).

---

### Post by Darrin on 2005-11-10
Thanks for all the info.

---

### Post by patrick295767 on 2005-11-10
[QUOTE=Pablo_Escobar]I don't umount it. Pop the pendrive out and no problems yet :)[/QUOTE]
  
Usually, the operation of writing is rather done pretty fast with pendrives...
After a delay, u'll see no led on ur pendrive... u can remove it wihotu unmounting but that's always risky a bit.
Better unmount 
  
I am using rox-filer & it's asking me to umount it via popup window... very easy !

greetz

---

### Post by transactionlogfiller on 2005-11-10
Just to add to this, I always unmount my usbdrive using umount from the terminal because of the problems listed above, but why do I need to be root to do it?

If I right click the icon on my desktop I can unmount it as a user but from the terminal I get /media/usbdisk is not in the fstab (and you are not root). This applies whether it was auto detected or manually mounted using pmount (which I can also do as a regular user).

Obviously it's not much effort to type "sudo" but it's just something that's bugging me.

---

### Post by aysiu on 2005-11-10
You may not get hurt if you jump out of a car before it fully stops, but I usually wait until it's stopped completely.

Eject (Mac)
Safely Remove (Windows)
Unmount (Linux)

I always do it... just to be safe.

---

### Post by ssam on 2005-11-10
the icon disapearing before its unmounted in gnome should probably be filed as a bug. mention the possiblility of data lose.

---

### Post by steve.horsley on 2005-11-10
Any write data could sit in the cache for quite a while without being written out. If you have written to the USB drive then you really should sync or unmount it before unplugging it.

---

### Post by stfu on 2005-11-10
I always unmount. There's been cases that the data was not written when I just dragged and dropped the files in nautilus. It's annoying to notice that when you're miles away on another computer.

---

### Post by vtec on 2005-11-10
I submitted a usablity bug to gnome...

---

### Post by reedlaw on 2005-11-13
Another annoyance is Gnome will place the mounted USB drive's icon on the very left edge of the screen so I don't even see the full text of the drive name (i.e. instead of 123MB USB drive I see 23MB USB drive).
Also, the trash folder that always gets created on the USB drive.  I know that I have to do a rm -rf /media/usbdisk/.Trash-reed before I free up space from deleted files, but how many newbies out there will realize this?

---

### Post by onesojourner on 2005-11-14
I am having major problems writting to my usb drive. It rarely works actually. I will give the unmount thing a shot along with leaving it plugged in for a minute or 5 after to let it write. 

This bug is horrible. I am actually embarrased with this one. with as popular as flash drives and cards are today this needs to be fixed. it sucks having to explain to a windows user why you have no data on you thumb drive...

---

### Post by eeried on 2005-11-14
[QUOTE=reedlaw]
Also, the trash folder that always gets created on the USB drive.  I know that I have to do a rm -rf /media/usbdisk/.Trash-reed before I free up space from deleted files, but how many newbies out there will realize this?[/QUOTE]

It is a real nuisance -- the same on Zip disk -- Mac OS X does something similar.  I never had Gnome before Hoary and it took me some time before realizing the trash was there.

---

### Post by Petrush on 2005-12-05
Could this behaviour with not syncing immediately be changed to mount it as a "sync" device? How is the mount parameters passed to the system, if no /etc/fstab entry is present?

It is very user-friendly to at least in theory be able to pull out the stick witout worries. We have experienced several cases with "disappering" files on USB sticks due to not-unmounting.

---

### Post by atoponce on 2005-12-05
[quote=Darrin]Is it necessary to unmount it? Will I have any issues if I just pull it out?[/quote]

I did have one issue losing all the data on the USB thumb drive when I just pulled it out.  It sucked!  I have no idea how I lost the data, I just know I did.  At the time I pulled it out, it was sitting idle not reading or writing.  Ever since, I have always unmounted the drive before pulling it out.  You just can't be too careful.

---

### Post by neonlug on 2005-12-05
I have found that every time I try to unmout the USB drive it says it can not, and that it is busy.  This can be well over a hour after I have closed all communications with that drive or the files on it.

So I just yank it, but that is really annoying... what can't I unmount it?

Also I get the same thing when I try to unmount a ISO or CUE/BIN file using cdemu.

Any ideas?

---

### Post by perfect_intelligence on 2005-12-05
Here is the video on The Flash Memory Which I Recorded form a bbc program Click Online......In the end A man Recommends to Safely Remove The Flash before removing it from computer...
[http://www.geocities.com/perfect_intelligence/reviews/flash.html](http://www.geocities.com/perfect_intelligence/reviews/flash.html)

---

