---
title: "Used harddrive size increased two times of downloaded file size"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by zhangqing6 on 2006-12-09
Hi everyone,

When I download MP3 to my /home/music.the size of mp3 is, for example, 5 MB.after download if I check using df -h,the used size for hda6 (my home disk) increased roughtly 10 MB.


can anyone give a right direction?
thanks in advance

---

### Post by ReaderRat on 2006-12-09
Was the downloaded file compressed, and was it de-compressed on the HDD?

---

### Post by zhangqing6 on 2006-12-09
thxs for your reply

no,just .mp3 and if I checked from places->home folder,open \music,check the properties of the file,only 5 Mb

---

### Post by louieb on 2006-12-09
Probably [COLOR=DarkRed]df -h[/COLOR] is just doing some rounding up. How big is hda6? Is it reporting size in Gig or Meg?

---

### Post by zhangqing6 on 2006-12-11
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              16G  2.3G   13G  16% /
varrun                126M   80K  125M   1% /var/run
varlock               126M     0  126M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   18M  108M  14% /lib/modules/2.6.17-10-generic/volatile
/dev/hda6              13G  393M   12G   4% /home
/dev/disk/by-uuid/16E44AC9E44AAB37
                       21G  8.1G   12G  41% /windows

when I did the fresh installation,used space for hda6 was 130M,and When I download MP3 to my /home/music.the size of mp3 is, for example, 5 MB.after download if I check using df -h,the used size for hda6 (my home disk) increased roughtly 10 MB


but now,I mean after downloaded 30 mp3,the increased used size is similiar to the size of downloaded file,I have no idea:) 

thanks tho and sorry for late reply.

---

### Post by zhangqing6 on 2006-12-12
sorry,now back tp before

"When I download MP3 to my /home/music.the size of mp3 is, for example, 5 MB.after download if I check using df -h,the used size for hda6 (my home disk) increased roughtly 10 MB](*,)

---

### Post by zhangqing6 on 2006-12-13
:) 
I think I got it.

after clear firefox Private Data,the increased used size (df -h) is exactly the downloaded file size

Firefox\Tools\Clear Private Data...

:-D

---

### Post by drphilngood on 2006-12-13
> **zhangqing6 said:**
> :) 
I think I got it.

after clear firefox Private Data,the increased used size (df -h) is exactly the downloaded file size

Firefox\Tools\Clear Private Data...

:-D

So, it was just a temp file, all along.:)

---

