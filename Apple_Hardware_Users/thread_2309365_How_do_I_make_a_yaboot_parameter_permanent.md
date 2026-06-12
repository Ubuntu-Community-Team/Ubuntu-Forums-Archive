---
title: "How do I make a yaboot parameter permanent?"
date: 2016-01-09
forum: Apple Hardware Users
---

### Post by thomas62 on 2016-01-09
Hi

I followed the guide here

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F)

I open this file
sudo nano /etc/yaboot.conf

I edit the 'append' line as suggested I save the file and run

sudo ybin -v to copy the file across to the boot partition.

Reboot, and the settings have not been invoked.

However, when I open the  yaboot.conf file again, I can see the change are there.

-------------------

The parameters I am adding are as follows - Linux video=ofonly radeon.agpmode=-1

Cheers

---

### Post by kyle69 on 2016-01-10
Most reliable way I have found so far is to boot "Linux single", make your edits, then run ybin -v.

---

### Post by rsavage on 2016-01-10
Have you added them to the correct append line?  You usually have two in the file.

---

### Post by thomas62 on 2016-01-17
That was it, I had them in the wrong line:)

Thanks so much!

---

