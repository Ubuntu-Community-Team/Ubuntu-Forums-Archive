---
title: "Asus USB adsl Modem and Ubuntu"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by flyingkip on 2005-11-23
I've been trying to install my modem on ubuntu, but so far I haven't succeeded in my mission.
I've tried installing EciAdsl (I've tried with the .deb file, tar.gz file and .rpm file)
But I always get errors.
So if anybody ever succeeded in installing an asus usb modem please let me know how you've done it (if possible with all the codes/packages that you used; )

Thanks in advance.
Thomas

---

### Post by endy on 2005-11-23
I've not got this modem but posting more details about it could help finding the problem.

Do you know the exact model of the modem? What's the output when you run the command "lsusb"?

I don't know if I can help but the more information you can post about what's going on, the better :)

---

### Post by flyingkip on 2005-11-23
Ok its a Asus AAM6000UG USB modem.
I've tried installing the EciAdsl again (.deb file); and this time I got the error; PPPoe not installed. What can I do now?? Is there a file that I need to install to have PPPoe installed??
Thanks,
Thomas

---

### Post by endy on 2005-11-23
You need to have the "Universe" repositories added to your apt sources (you can do this in Synaptic: Settings > Repositories > Add) then use Synaptic to install it by searching for "pppoe" or run the following command:

```
sudo apt-get install pppoe
```

---

### Post by flyingkip on 2005-11-23
OK I've tried that; 
And again I get an error;
Pakket PPPoe not found.

Can I download this pakket somewhere?

Thomas

---

### Post by flyingkip on 2005-11-23
OK the instalation of EciAdsl worked. But now he can't find the modem when I start connecting to the internet..
Anybody any idea how I can fix this??
Thomas

---

