---
title: "Check sum"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2006-09-10
I just downloaded the standard Ubuntu Desktop CD (the one that works for pentium processors).  Could someone give me step-by-step instructions for verifying the ISO I just downloaded?  I read the standard pages you can get to from the download page, but they didn't really make too much sense to me.  Thanks! ^_^

---

### Post by aysiu on 2006-09-10
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by YeahBuntu on 2006-09-10
Do you just want to check that the CD is ok or are you sure you want to verify the MD5 Cheksum.

Did you download it from the Ubuntu website?  Most likely they are not going to 'poison' the files on thier own website.

However the checksum can be used to verify a poor download.  But you most likely would have gotten download errors and you would then know that you may want to re-download or verify the download.

Here is the best Layman type explaination of MD5 I can give you.

When any file is saved to the hard drive there is a digital 'fingerprint' or 'checksum' that is automatically created simply by the creation of the file.

There are some programs that allow you to view or check this 'fingerprint' or 'checksum' the question you want to ask yourself is ' why? '

Well one simple response is if someone decided to change or 'poison' the file.. when that file was resaved with the changes the digtial fingerprint or checksum would also change.  It is therefore theoretically improbable that you could change a file- save it and have the fingerprint be the same as it was when it was saved the first time.

Also a bad download will cause you to get a different checksum and im sure theres other reasons.

The live Ubuntu cd has its own cd checker tho (and probably other distros do too).  You should be ok with that unless you mayhaps downloaded your copy of Ubuntu from a source that is questionable.

I hope someone still reads this I couldnt get it posted as the forum timed out on me.

---

### Post by bodhi.zazen on 2006-09-10
> **Darklighter137 said:**
> I just downloaded the standard Ubuntu Desktop CD (the one that works for pentium processors).  Could someone give me step-by-step instructions for verifying the ISO I just downloaded?  I read the standard pages you can get to from the download page, but they didn't really make too much sense to me.  Thanks! ^_^

In linux:
```
md5sum <name_of_iso>
```
This will print the md5sum to the terminal.

If you download a md5sum text file md5sum will compare for you automatically:
```
md5sum <xyz.iso> -c <md5sum.txt>
```
where
<xyz.iso> = iso file
<md5sum.txt> = downloaded md5sum text.

To confirm a proper burn to CD, check the CD.
If yo use K3b it will show and confirm this information.
Without kK3b:
[indent]burn iso[/indent]
[indent]with CD in drive type:[/indent]
[indent]md5sum md5sum /dev/hda[/indent]
use proper device, your CD may well be /dev/hdb.

For windows see here:
[Windows md5sum](http://www.nullriver.com/index/products/winmd5sum)

---

### Post by Darklighter137 on 2006-09-10
Thanks guys!  Now all I need to do is burn the ISO.

---

