---
title: "can i install ubuntu along with windows xp?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by cooldudeny on 2007-05-24
Hi i am really new to linux but i had an oppurtunity to use ubuntu for few days and i simple love it now but i have a question 

can i install ubuntu on my laptop but i already have windows xp running on it and i dont want to delete it coz i dont want to loose all my data but i will love to have ubuntu running on my laptop too so that i can switch back and forth between linux and windows 

can someone advice me the best way to do it 

Thanks

---

### Post by Sparkster185 on 2007-05-24
You most certain can and it's quite easy.

First, I recommend you defrag your Windows XP parition, so all the data is concentrated at the beginning of the disk.

The LiveCD that installs Ubuntu for you will allow you to setup partitions.  All you need to do is resize your existing NTFS partition, this will free up some space.  Then you want to create a new partition for you Ubuntu install.  I recommend separating it into one partition for / (system files), one partition for /home (user data) and one for swap.

---

### Post by theicyj on 2007-05-24
Yeah, you can do that without too much difficulty.  Check out this guide:  [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu]("http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu")

---

### Post by akudewan on 2007-05-24
Yes, its possible, and a lot of us are doing it. All you need is an empty partition, or maybe some free space so you can make a partition from it.

Take a backup of important data just in case. Also, installing another OS on your laptop may cause your warranty to be void. Don't mean to scare you, but you should just know...

---

### Post by Inxsible on 2007-05-24
Yes it is definitely possible 
 
Try these links which explain how to partition and install
 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by az on 2007-05-24
> **Sparkster185 said:**
>  All you need to do is resize your existing NTFS partition, this will free up some space.  Then you want to create a new partition for you Ubuntu install.  I recommend separating it into one partition for / (system files), one partition for /home (user data) and one for swap.

By default, the installer can shrink your windows partition for you.  And you do not need to make a seperate home partition - this only complicates the install process and can lead to frustration if you miscalculate the size of your / or home partiiton.  Just take the default and let the installer do that partitioning for you.  

I recommend staying away from anything but the default installation for someone who is not experienced.

Anyway, there are easier ways to back up your data rather than creating a seperate home partition.

---

