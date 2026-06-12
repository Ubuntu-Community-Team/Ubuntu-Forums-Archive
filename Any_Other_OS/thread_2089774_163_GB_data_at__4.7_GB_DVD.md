---
title: "163 GB data at  4.7 GB DVD"
date: 2012-11-30
forum: Any Other OS
---

### Post by ramakanta on 2012-11-30
I was shocked when want to copy of movies Oh My God! in my computer that recently purchased - there is not enough space on Disk. when i was see inside there is DVD data contains 163GB . all the screen shot avail(below).
 
[[img]http://s19.postimage.org/nac79k59b/image.jpg[/img]](http://postimage.org/image/nac79k59b/)
[[img]http://s19.postimage.org/r7zgyys2n/image.jpg[/img]](http://postimage.org/image/r7zgyys2n/)
[[img]http://s19.postimage.org/492rg1w2n/image.jpg[/img]](http://postimage.org/image/492rg1w2n/)
 
Is it possible 163GB of data can store in 4.7 GB of DVD . please any one help me how it possible outside memory 4.37 GB and inside 163GB  . i am confused.
Thank you

---

### Post by nuttzo31 on 2012-11-30
That's some kind of copy protection on the disk where it is padded out with dummy files.

---

### Post by ramakanta on 2012-11-30
> **nuttzo31 said:**
> That's some kind of copy protection on the disk where it is padded out with dummy files.
 
is it possible ?? if , then How.??

---

### Post by pompel9 on 2012-11-30
No it is not possible.

As the one above you said, there are copy-protection on the DVD so your system can't read it right.

---

### Post by nuttzo31 on 2012-11-30
There's not actually 163gb of data on the dvd the files are just filled with 0's or something like that.

---

### Post by ramakanta on 2012-11-30
> **pompel9 said:**
> No it is not possible.
 
As the one above you said, there are copy-protection on the DVD so your system can't read it right.
 
i have tested all .vob file . all are playing ok . 
 
**VTS_01_1.vob, VTS_01_2.vob** **......** **VTS_01_5.vob** contain movie
 
also **VTS_02_1.vob** to **VTS_02_5 .vob **contain same movie and playing ok
 
.
.
.
.
**VTS_39_1.vob** to **VTS_39_5 .vob **also contain same movie and playing ok
 
[[img]http://s19.postimage.org/4oj366obj/image.jpg[/img]](http://postimage.org/image/4oj366obj/)
.
.
.
 
[[img]http://s19.postimage.org/9ogje4ty7/image.jpg[/img]](http://postimage.org/image/9ogje4ty7/)

---

### Post by Wim Sturkenboom on 2012-11-30
Read up on sparse files ;)

**Step 1**
Check diskspace before creating a 1GB file
```

wim@i3-2120:/mnt$ du --max-depth=1
32	./boot-sav
**219602196	./photos**
219602232	.
wim@i3-2120:/mnt$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       138G  4,9G  126G   4% /
udev            3,7G  4,0K  3,7G   1% /dev
tmpfs           1,5G  856K  1,5G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,7G  216K  3,7G   1% /run/shm
/dev/sda6       532G   14G  491G   3% /home
**/dev/sdc1       925G  210G  706G  23% /mnt/photos**

```
**Step 2**
Create a 1GB file
```

wim@i3-2120:/mnt$ cd photos/wim/
wim@i3-2120:/mnt/photos/wim$ [COLOR="Red"]dd if=/dev/null of=sparse-file bs=1k seek=1000000 count=1[/COLOR]
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2,112e-05 s, 0,0 kB/s
wim@i3-2120:/mnt/photos/wim$ ls -l
total 33016
-rwxr-xr-x 1 wim wim    6068196 Jan 11  2011 IMGP2310 (copy).jpg
-rwxr-xr-x 1 wim wim   10801944 Jan 11  2011 IMGP2310 (copy).PEF
-rwxr-xr-x 1 wim wim    6068196 Jan 11  2011 IMGP2310.jpg
-rwxr-xr-x 1 wim wim   10801944 Jan 11  2011 IMGP2310.PEF
**-rw-rw-r-- 1 wim wim 1024000000 Nov 30 16:05 sparse-file**

```
**Step 3**
Check available diskspace after creating 1GB file
```

wim@i3-2120:/mnt/photos/wim$ du --max-depth=1 /mnt
32	/mnt/boot-sav
**219602196	/mnt/photos**
219602232	/mnt
wim@i3-2120:/mnt/photos/wim$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       138G  4,9G  126G   4% /
udev            3,7G  4,0K  3,7G   1% /dev
tmpfs           1,5G  856K  1,5G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,7G  216K  3,7G   1% /run/shm
/dev/sda6       532G   14G  491G   3% /home
**/dev/sdc1       925G  210G  706G  23% /mnt/photos**

```
Note that the disk usage / free space did not change :lol:

---

### Post by dcottingham on 2012-11-30
That screen shot appears to be from Windows, not Ubuntu. Am I missing something?

---

### Post by Wim Sturkenboom on 2012-11-30
> **ramakanta said:**
> is it possible ?? if , then How.??
Yes, it is possible

> **pompel9 said:**
> No it is not possible.
As proven above, it is possible to create a file that does not take space but is reported as 1GB.

You can writes a utility that copies a normal file, next seeks behind the end of the copied data, write some more bytes and close the file.

---

### Post by ramakanta on 2012-11-30
> **Wim Sturkenboom said:**
> Read up on sparse files ;)
 
**Step 1**
Check diskspace before creating a 1GB file
```

wim@i3-2120:/mnt$ du --max-depth=1
32    ./boot-sav
**219602196    ./photos**
219602232    .
wim@i3-2120:/mnt$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       138G  4,9G  126G   4% /
udev            3,7G  4,0K  3,7G   1% /dev
tmpfs           1,5G  856K  1,5G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,7G  216K  3,7G   1% /run/shm
/dev/sda6       532G   14G  491G   3% /home
**/dev/sdc1       925G  210G  706G  23% /mnt/photos**

```
**Step 2**
Create a 1GB file
```

wim@i3-2120:/mnt$ cd photos/wim/
wim@i3-2120:/mnt/photos/wim$ [COLOR=red]dd if=/dev/null of=sparse-file bs=1k seek=1000000 count=1[/COLOR]
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2,112e-05 s, 0,0 kB/s
wim@i3-2120:/mnt/photos/wim$ ls -l
total 33016
-rwxr-xr-x 1 wim wim    6068196 Jan 11  2011 IMGP2310 (copy).jpg
-rwxr-xr-x 1 wim wim   10801944 Jan 11  2011 IMGP2310 (copy).PEF
-rwxr-xr-x 1 wim wim    6068196 Jan 11  2011 IMGP2310.jpg
-rwxr-xr-x 1 wim wim   10801944 Jan 11  2011 IMGP2310.PEF
**-rw-rw-r-- 1 wim wim 1024000000 Nov 30 16:05 sparse-file**

```
**Step 3**
Check available diskspace after creating 1GB file
```

wim@i3-2120:/mnt/photos/wim$ du --max-depth=1 /mnt
32    /mnt/boot-sav
**219602196    /mnt/photos**
219602232    /mnt
wim@i3-2120:/mnt/photos/wim$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       138G  4,9G  126G   4% /
udev            3,7G  4,0K  3,7G   1% /dev
tmpfs           1,5G  856K  1,5G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,7G  216K  3,7G   1% /run/shm
/dev/sda6       532G   14G  491G   3% /home
**/dev/sdc1       925G  210G  706G  23% /mnt/photos**

```
Note that the disk usage / free space did not change :lol:
 
 
what does it mean . please explain with details . i am not export in programme. 
thank you.

---

### Post by dannyboy79 on 2012-11-30
> **Wim Sturkenboom said:**
> Read up on sparse files ;)

**Step 1**
Check diskspace before creating a 1GB file
```

wim@i3-2120:/mnt$ du --max-depth=1
32	./boot-sav
**219602196	./photos**
219602232	.
wim@i3-2120:/mnt$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       138G  4,9G  126G   4% /
udev            3,7G  4,0K  3,7G   1% /dev
tmpfs           1,5G  856K  1,5G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,7G  216K  3,7G   1% /run/shm
/dev/sda6       532G   14G  491G   3% /home
**/dev/sdc1       925G  210G  706G  23% /mnt/photos**

```
**Step 2**
Create a 1GB file
```

wim@i3-2120:/mnt$ cd photos/wim/
wim@i3-2120:/mnt/photos/wim$ [COLOR="Red"]dd if=/dev/null of=sparse-file bs=1k seek=1000000 count=1[/COLOR]
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2,112e-05 s, 0,0 kB/s
wim@i3-2120:/mnt/photos/wim$ ls -l
total 33016
-rwxr-xr-x 1 wim wim    6068196 Jan 11  2011 IMGP2310 (copy).jpg
-rwxr-xr-x 1 wim wim   10801944 Jan 11  2011 IMGP2310 (copy).PEF
-rwxr-xr-x 1 wim wim    6068196 Jan 11  2011 IMGP2310.jpg
-rwxr-xr-x 1 wim wim   10801944 Jan 11  2011 IMGP2310.PEF
**-rw-rw-r-- 1 wim wim 1024000000 Nov 30 16:05 sparse-file**

```
**Step 3**
Check available diskspace after creating 1GB file
```

wim@i3-2120:/mnt/photos/wim$ du --max-depth=1 /mnt
32	/mnt/boot-sav
**219602196	/mnt/photos**
219602232	/mnt
wim@i3-2120:/mnt/photos/wim$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       138G  4,9G  126G   4% /
udev            3,7G  4,0K  3,7G   1% /dev
tmpfs           1,5G  856K  1,5G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,7G  216K  3,7G   1% /run/shm
/dev/sda6       532G   14G  491G   3% /home
**/dev/sdc1       925G  210G  706G  23% /mnt/photos**

```
Note that the disk usage / free space did not change :lol:Of course it didn't change, you created the 1GB file on sdc1 partition, NOT the / partition.

---

### Post by Wim Sturkenboom on 2012-11-30
> **dannyboy79 said:**
> Of course it didn't change, you created the 1GB file on sdc1 partition, NOT the / partition.
Please explain :confused:

I create a sparse file on /dev/sdc1 (mounted on /mnt/photos), check the diskspace on sdc1 with df and the disk usage on /mnt/photos with du. A 100% valid test (and proof) in my opinion.

---

### Post by Wim Sturkenboom on 2012-11-30
> **ramakanta said:**
> what does it mean . please explain with details . i am not export in programme. 
thank you.I can not explain more; it just shows that you can create files that seem to be 1GB in size but actually don't occupy that much space.

---

### Post by dannyboy79 on 2012-11-30
> **Wim Sturkenboom said:**
> Please explain :confused:

I create a sparse file on /dev/sdc1 (mounted on /mnt/photos), check the diskspace on sdc1 with df and the disk usage on /mnt/photos with du. A 100% valid test (and proof) in my opinion.
I thought you were trying to say that / partition didn't change in size BUT I see now that you meant that /dev/sdc1/ didn't change in size. It still remained 706GB available. df -h must not be very exact. A 1GB file will take up 1GB, there's no way around that IMO.

This is getting off topic IMO. I am done with this thread but would like to say that 163GB of data will NOT fit on a 4.7GB dvd.

---

### Post by coffeecat on 2012-11-30
> **dcottingham said:**
> That screen shot appears to be from Windows, not Ubuntu. Am I missing something?

I don't think so. The OP has posted screenshots from Windows in two posts.

@ramakanta, it would appear that you are trying to copy a copy-protected DVD in Windows. That is not something that we can help you with here. I suggest you try a Windows forum.

*Thread moved to **Other OS/Distro Talk**, and closed.*

---

