---
title: "Re-install Ubuntu"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-10-09
Hi,

For some reasons I would like to reinstall ubuntu dapper over existing ubuntu on same hard 
disk and same partition.

I have window me also resided on the same hard disk. I don't want anything affected to windows me.

My guess is that just follow the normal installation procedure. Overwrite existing ubuntu.
Am I right?

Anyother suggestions to make the reinstallation process smooth?

Thank you.

---

### Post by meng on 2006-10-09
Correct, overwrite existing ubuntu. Do you have a separate data (or /home) partition? If not, consider moving any data files to a separate partition before reinstalling.

---

### Post by i-m-p on 2006-10-09
Thank you.

I don't have a separate data partition. It is a good idea to make it. How do I make it? I can make it with installation cd perhaps?

---

### Post by Kateikyoushi on 2006-10-09
Yes you can do it during installation, coose to partition manually, create a swap and two other partitions, one for / and another for /home.

---

### Post by meng on 2006-10-09
Here's a good link:
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by i-m-p on 2006-10-10
Thank you.

 I read through [http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/) about partition. It is really good for me because I like to clean up everything and re-install the system again. I feel better as same as I cleaned my room.

Let me confirm if I understand this home partition issue correctly.

If I create / partion plus /home partition. It is probably better do it before the next re-installation process.

 When I reinstall ubuntu next time. All I have to manupulate is a / partition. (root partition isn't it?) but /home partition stays untouched. 
 Since files in /home partition are Non pragram files. All of my settings ,for example my Japanese keyboard settings or browser-plugins or Email programs setting, I have to install or redo those settings again after I re-installed ubuntu. 

 I am not so sure about this. Maybe I am wrong.

 If the /home partition only keeps the same files as in my /home folder I have now. What the difference between burn /home folder to CD and create a /home partion?

---

### Post by Kateikyoushi on 2006-10-10
You do not have to burn the home folder to cd if you make a partition for it, also after an installation won't have to copy it back to your hdd.
It also contains config files for programs, unhide hidden files and you will see. So you won't have to set up applications again.
I have config file for xim in the home folder but as I recall it has some others elsewhere so yes you have to configure it one more time.

---

### Post by i-m-p on 2006-10-10
Thank you.

> You do not have to burn the home folder to cd if you make a partition for it, also after an installation won't have to copy it back to your hdd.

OK, so I understand it quite correctly. So it can save the time and some cds. Good.

And probably I am going to learn something from doing create home partition and re-install 
 ubuntu again.

I will do it sooner.

Thanks again for all!

---

### Post by salguod on 2006-10-10
I was able to upgrade from kubuntu 5.10 to 6.06 simply by changing the /etc/apt/sources.list file (sudo pico /etc/apt/sources.list).

replace all the words "breezy" in the URLs with the word "dapper" save the file (ctrl x) then go you adept (or synaptic), update the sources then mark it for "full upgrade."

It takes a LONG time (4 hours?), but when it is done, reboot and you have the new system.

---

