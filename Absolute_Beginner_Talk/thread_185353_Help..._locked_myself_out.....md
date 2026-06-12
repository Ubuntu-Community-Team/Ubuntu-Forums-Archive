---
title: "Help... locked myself out...."
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by mike_m on 2006-05-31
ok I did it now,:oops: 
I had to change the choms on a file and change it on 2 flolders instead....

Home + Mike

Now I can't get log back in ](*,) 

OK, I see I can get to the recovery at boot & get a termal prompt
please send me the code to change my choms back, I'll print it out.

Thanks, Mike

(ps, thank god for this live disk :-D , to bad I can't get to my HD files & choms them.... I tried)

---

### Post by aysiu on 2006-05-31
[QUOTE=mike_m](ps, thank god for this live disk :-D , to bad I can't get to my HD files & choms them.... I tried)[/QUOTE] Sure you can.

```
sudo fdisk -l
``` Find your Ubuntu partition. Let's say it's /dev/hda1

```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
gksudo nautilus
``` Or, if you're using Kubuntu substitute ```
kdesu konqueror
``` for that last line. Your HD files will be in the /recovery folder.

---

### Post by mike_m on 2006-06-01
Thanks, You Rock!!

---

